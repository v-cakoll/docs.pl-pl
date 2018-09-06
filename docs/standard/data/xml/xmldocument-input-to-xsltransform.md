---
title: Dane wejściowe obiektu XmlDocument klasy xsltransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83cf82aee57b1f40f695700d8d0b38c12e0ac39
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038851"
---
# <a name="xmldocument-input-to-xsltransform"></a>Dane wejściowe obiektu XmlDocument klasy xsltransform
<xref:System.Xml.XmlDocument> Klasa oferuje funkcje edycji dokumentu XML. Jeśli plik XML musi edytowanie lub zmodyfikowany przed wysłaniem do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody ładowanie kodu XML do <xref:System.Xml.XmlDocument>, edytować i wyślij go do <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.XmlDocument> Implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu, dokument może być przekazywany do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda po zakończeniu edycji.  
  
 Ze względu na możliwość edytowania <xref:System.Xml.XmlDocument>przy użyciu <xref:System.Xml.XmlDocument> klasy jako dane wejściowe do transformacji jest mniejsza niż przy użyciu <xref:System.Xml.XPath.XPathDocument> dla rozszerzalny język arkusza stylów w mapowaniach przekształcenia (XSLT) jako <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowane pod kątem zapytań języka ścieżki XML (XPath) z powodu pamięci wewnętrznej.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposobu <xref:System.Xml.XmlDocument> mogą być dostarczane do <xref:System.Xml.Xsl.XslTransform>, z danymi wyjściowymi wysyłane do <xref:System.Xml.XmlReader>.  
  
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
