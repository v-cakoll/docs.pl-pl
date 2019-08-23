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
# <a name="xmldocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDocument klasy XslTransform
<xref:System.Xml.XmlDocument> Klasa udostępnia możliwości edycji dokumentu XML. Jeśli plik XML musi być edytowany lub zmodyfikowany przed wysłaniem do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, Załaduj plik XML <xref:System.Xml.XmlDocument>do, edytuj go i <xref:System.Xml.Xsl.XslTransform>Wyślij do.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Implementuje interfejs, dzięki czemu dokument <xref:System.Xml.Xsl.XslTransform.Transform%2A> może być przesłany do metody po edycji. <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlDocument>  
  
 <xref:System.Xml.XmlDocument>Ze względu na możliwość edycji, <xref:System.Xml.XmlDocument> użycie klasy jako wejścia do transformacji <xref:System.Xml.XPath.XPathDocument> jest wolniejsze niż użycie dla transformacji Extensible Stylesheet Language for <xref:System.Xml.XPath.XPathDocument> Transformations (XSLT), ponieważ jest to Optymalizacja pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>, jak można dostarczyć do, przy użyciu danych wyjściowych wysyłanych do <xref:System.Xml.XmlReader>.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
