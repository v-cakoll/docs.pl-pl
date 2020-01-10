---
title: Dane wejściowe obiektu XmlDocument klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: c7819c3cb6b1430dcdb8a78c43f7138f64e691a8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709845"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="f30f0-102">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="f30f0-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="f30f0-103">Klasa <xref:System.Xml.XmlDocument> zapewnia możliwości edycji dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f30f0-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="f30f0-104">Jeśli plik XML musi być edytowany lub zmodyfikowany przed wysłaniem do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>, Załaduj plik XML do <xref:System.Xml.XmlDocument>, edytuj go i Wyślij do <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="f30f0-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f30f0-105">Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f30f0-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="f30f0-106">Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f30f0-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f30f0-107">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="f30f0-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f30f0-108"><xref:System.Xml.XmlDocument> implementuje interfejs <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu dokument może zostać przesłany do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> po edycji.</span><span class="sxs-lookup"><span data-stu-id="f30f0-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="f30f0-109">Ze względu na możliwość edycji <xref:System.Xml.XmlDocument>przy użyciu klasy <xref:System.Xml.XmlDocument> jako danych wejściowych przekształcenia jest wolniejsza niż używanie <xref:System.Xml.XPath.XPathDocument> dla transformacji Extensible Stylesheet Language for Transformations (XSLT), ponieważ <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowany pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.</span><span class="sxs-lookup"><span data-stu-id="f30f0-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f30f0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f30f0-110">Example</span></span>  
 <span data-ttu-id="f30f0-111">Poniższy przykład kodu pokazuje, jak <xref:System.Xml.XmlDocument> można dostarczyć do <xref:System.Xml.Xsl.XslTransform>, z danymi wyjściowymi wysyłanymi do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="f30f0-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f30f0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f30f0-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="f30f0-113">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="f30f0-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="f30f0-114">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="f30f0-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="f30f0-115">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="f30f0-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="f30f0-116">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="f30f0-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="f30f0-117">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="f30f0-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="f30f0-118">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="f30f0-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
