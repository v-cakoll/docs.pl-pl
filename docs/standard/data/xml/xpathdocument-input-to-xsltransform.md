---
title: Dane wejściowe obiektu XPathDocument klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: 66cdbae8b52ca1b7ed46e8f040fcbf51c969dea2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282977"
---
# <a name="xpathdocument-input-to-xsltransform"></a>Dane wejściowe obiektu XPathDocument klasy XslTransform
<xref:System.Xml.XPath.XPathDocument>Jest pamięcią podręczną tylko do odczytu, na potrzeby przetwarzania dokumentów przy użyciu programu <xref:System.Xml.Xsl.XslTransform> . Jest on strukturalnie podobny do Document Object Model XML (DOM), ale jest wysoce zoptymalizowany pod kątem przetwarzania Extensible Stylesheet Language for Transformations (XSLT) i modelu danych XML Path Language (XPath) przy użyciu funkcji optymalizacji XPath w <xref:System.Xml.XPath.XPathNavigator> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 Poniższy przykład kodu tworzy <xref:System.Xml.XPath.XPathDocument> jako dane wejściowe do przekształcenia.  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
