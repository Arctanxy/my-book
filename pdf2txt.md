作者：xlzd
链接：https://www.zhihu.com/question/31586273/answer/113518895
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

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
