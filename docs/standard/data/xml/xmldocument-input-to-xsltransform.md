---
title: Dane wejściowe obiektu XmlDocument klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60b9b66ea9b1c74dc34e2e99dcf651f9dac1725e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915971"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="4732e-102">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4732e-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="4732e-103"><xref:System.Xml.XmlDocument> Klasa udostępnia możliwości edycji dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4732e-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="4732e-104">Jeśli plik XML musi być edytowany lub zmodyfikowany przed wysłaniem do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, Załaduj plik XML <xref:System.Xml.XmlDocument>do, edytuj go i <xref:System.Xml.Xsl.XslTransform>Wyślij do.</span><span class="sxs-lookup"><span data-stu-id="4732e-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4732e-105"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4732e-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="4732e-106">Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="4732e-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4732e-107">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4732e-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="4732e-108">Implementuje interfejs, dzięki czemu dokument <xref:System.Xml.Xsl.XslTransform.Transform%2A> może być przesłany do metody po edycji. <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="4732e-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="4732e-109"><xref:System.Xml.XmlDocument>Ze względu na możliwość edycji, <xref:System.Xml.XmlDocument> użycie klasy jako wejścia do transformacji <xref:System.Xml.XPath.XPathDocument> jest wolniejsze niż użycie dla transformacji Extensible Stylesheet Language for <xref:System.Xml.XPath.XPathDocument> Transformations (XSLT), ponieważ jest to Optymalizacja pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.</span><span class="sxs-lookup"><span data-stu-id="4732e-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4732e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4732e-110">Example</span></span>  
 <span data-ttu-id="4732e-111">Poniższy przykład kodu pokazuje <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>, jak można dostarczyć do, przy użyciu danych wyjściowych wysyłanych do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4732e-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4732e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4732e-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="4732e-113">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4732e-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="4732e-114">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4732e-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="4732e-115">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="4732e-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="4732e-116">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="4732e-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="4732e-117">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4732e-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="4732e-118">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4732e-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
