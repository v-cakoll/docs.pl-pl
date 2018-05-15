---
title: Dane wejściowe XmlDocument XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3179425597173e09a8c1ef1fbdfc582f8f4538e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="d521f-102">Dane wejściowe XmlDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="d521f-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="d521f-103"><xref:System.Xml.XmlDocument> Klasa udostępnia funkcje edycji dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d521f-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="d521f-104">Jeśli XML musi być edytowane lub zmodyfikować przed wysłaniem do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody załadować pliku XML do <xref:System.Xml.XmlDocument>, edytowania i wysyłać je do <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d521f-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d521f-105"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d521f-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="d521f-106">Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d521f-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d521f-107">Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d521f-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="d521f-108"><xref:System.Xml.XmlDocument> Implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu, więc dokumentu mogą zostać przekazane do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody po edycji.</span><span class="sxs-lookup"><span data-stu-id="d521f-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="d521f-109">Z powodu możliwości edycji <xref:System.Xml.XmlDocument>za pomocą <xref:System.Xml.XmlDocument> klasy jako dane wejściowe do przekształcenia jest mniejsza niż przy użyciu <xref:System.Xml.XPath.XPathDocument> rozszerzalnego języka arkusza stylów dla przekształceń przekształcenia XSLT () jako <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowana pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.</span><span class="sxs-lookup"><span data-stu-id="d521f-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d521f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d521f-110">Example</span></span>  
 <span data-ttu-id="d521f-111">Poniższy kod przedstawia przykład sposobu <xref:System.Xml.XmlDocument> mogą być dostarczane do <xref:System.Xml.Xsl.XslTransform>, przy czym dane wyjściowe, wysyłane do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d521f-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d521f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d521f-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 [<span data-ttu-id="d521f-113">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d521f-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="d521f-114">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d521f-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="d521f-115">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="d521f-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="d521f-116">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="d521f-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="d521f-117">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d521f-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="d521f-118">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d521f-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
