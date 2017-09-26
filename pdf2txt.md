能够读取pdf的Python库很多，比较著名的有pdfminer和pypdf，下面来对比一下两个库的识别效果：
我们先从网上找一篇文献：
# pdfminer
```
from cStringIO import StringIO

from pdfminer.pdfinterp import PDFResourceManager, PDFPageInterpreter
from pdfminer.converter import TextConverter
from pdfminer.layout import LAParams
from pdfminer.pdfpage import PDFPage


def convert_pdf_2_text(path):

    rsrcmgr = PDFResourceManager()
    retstr = StringIO()

    device = TextConverter(rsrcmgr, retstr, codec='utf-8', laparams=LAParams())
    interpreter = PDFPageInterpreter(rsrcmgr, device)

    with open(path, 'rb') as fp:
        for page in PDFPage.get_pages(fp, set()):
            interpreter.process_page(page)
        text = retstr.getvalue()

    device.close()
    retstr.close()

    return text
```   
# pypdf
```
from pyPdf import PdfFileWriter, PdfFileReader

output = PdfFileWriter()
input1 = PdfFileReader(file("document1.pdf", "rb"))

# print the title of document1.pdf
print "title = %s" % (input1.getDocumentInfo().title)

# add page 1 from input1 to output document, unchanged
output.addPage(input1.getPage(0))

# add page 2 from input1, but rotated clockwise 90 degrees
output.addPage(input1.getPage(1).rotateClockwise(90))

# add page 3 from input1, rotated the other way:
output.addPage(input1.getPage(2).rotateCounterClockwise(90))
# alt: output.addPage(input1.getPage(2).rotateClockwise(270))

# add page 4 from input1, but first add a watermark from another pdf:
page4 = input1.getPage(3)
watermark = PdfFileReader(file("watermark.pdf", "rb"))
page4.mergePage(watermark.getPage(0))

# add page 5 from input1, but crop it to half size:
page5 = input1.getPage(4)
page5.mediaBox.upperRight = (
    page5.mediaBox.getUpperRight_x() / 2,
    page5.mediaBox.getUpperRight_y() / 2
)
output.addPage(page5)

# print how many pages input1 has:
print "document1.pdf has %s pages." % input1.getNumPages()

# finally, write "output" to document-output.pdf
outputStream = file("document-output.pdf", "wb")
output.write(outputStream)
outputStream.close()
```
采用这种方法得到的结果并不是很理想，实际处理中还要考虑到pdf中很多的分栏等格式问题，能真实使用的代码比这个要复杂得多。

这里推荐一个曲线救国的办法，可以先使用pdf2htmlex将pdf文件转换成html文件，然后再用我们熟悉的方式来解析html。

但是这些python库和工具都只能处理由word或者LaTeX导出的pdf，对于扫描版的pdf识别比较差，遇到这样的pdf文件，可以尝试使用我们在验证码那一节学到的Tesseract-OCR工具了，先将pdf转成图片格式，然后再分别对每一页pdf的图片进行识别，效果尚可，不过一般都会出现很多错别字。
