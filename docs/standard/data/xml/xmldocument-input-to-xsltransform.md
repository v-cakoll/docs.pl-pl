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
Klasa <xref:System.Xml.XmlDocument> zapewnia możliwości edycji dla dokumentu XML. Jeśli plik XML musi być edytowany lub zmodyfikowany przed wysłaniem do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>, Załaduj plik XML do <xref:System.Xml.XmlDocument>, edytuj go i Wyślij do <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.XmlDocument> implementuje interfejs <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu dokument może zostać przesłany do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> po edycji.  
  
 Ze względu na możliwość edycji <xref:System.Xml.XmlDocument>przy użyciu klasy <xref:System.Xml.XmlDocument> jako danych wejściowych przekształcenia jest wolniejsza niż używanie <xref:System.Xml.XPath.XPathDocument> dla transformacji Extensible Stylesheet Language for Transformations (XSLT), ponieważ <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowany pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak <xref:System.Xml.XmlDocument> można dostarczyć do <xref:System.Xml.Xsl.XslTransform>, z danymi wyjściowymi wysyłanymi do <xref:System.Xml.XmlReader>.  
  
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
