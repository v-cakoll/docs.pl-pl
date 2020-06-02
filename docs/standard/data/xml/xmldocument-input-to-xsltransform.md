---
title: Dane wejściowe obiektu XmlDocument klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: e990c8ca3bb2a7145157fcedd06da4ea769c6ad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290256"
---
# <a name="xmldocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDocument klasy XslTransform
<xref:System.Xml.XmlDocument>Klasa udostępnia możliwości edycji dokumentu XML. Jeśli plik XML musi być edytowany lub zmodyfikowany przed wysłaniem do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, Załaduj plik XML do <xref:System.Xml.XmlDocument> , edytuj go i Wyślij do <xref:System.Xml.Xsl.XslTransform> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.XmlDocument>Implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejs, dzięki czemu dokument może być przesłany do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody po edycji.  
  
 Ze względu na możliwość edycji <xref:System.Xml.XmlDocument> , użycie <xref:System.Xml.XmlDocument> klasy jako wejścia do transformacji jest wolniejsze niż użycie <xref:System.Xml.XPath.XPathDocument> dla transformacji Extensible Stylesheet Language for Transformations (XSLT), ponieważ <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowany pod kątem zapytań XML Path Language (XPath) z powodu wewnętrznego magazynu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje <xref:System.Xml.XmlDocument> , jak można dostarczyć do <xref:System.Xml.Xsl.XslTransform> , przy użyciu danych wyjściowych wysyłanych do <xref:System.Xml.XmlReader> .  
  
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
- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Klasa XPathNavigator w przekształceniach](xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](xmldatadocument-input-to-xsltransform.md)
