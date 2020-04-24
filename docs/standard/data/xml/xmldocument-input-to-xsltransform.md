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
# <a name="xmldocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDocument klasy XslTransform
<xref:System.Xml.XmlDocument> Klasa udostępnia możliwości edycji dokumentu XML. Jeśli plik XML musi być edytowany lub zmodyfikowany przed wysłaniem do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, Załaduj plik XML do <xref:System.Xml.XmlDocument>, edytuj go i Wyślij do. <xref:System.Xml.Xsl.XslTransform>  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Implementuje interfejs, dzięki czemu dokument może być przesłany do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody po edycji. <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlDocument>  
  
 <xref:System.Xml.XmlDocument>Ze względu na możliwość edycji, użycie <xref:System.Xml.XmlDocument> klasy jako wejścia do transformacji jest wolniejsze niż użycie <xref:System.Xml.XPath.XPathDocument> dla transformacji Extensible Stylesheet Language for Transformations (XSLT), ponieważ <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowany pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>, jak można dostarczyć do, przy użyciu danych wyjściowych wysyłanych do. <xref:System.Xml.XmlReader>  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
