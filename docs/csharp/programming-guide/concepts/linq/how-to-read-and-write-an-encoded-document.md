---
title: Jak czytać i pisać zakodowany dokument (C#)
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fa28c26845a0c6019943e0532ea0692a6dffd5a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347665"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Jak czytać i pisać zakodowany dokument (C#)
Aby utworzyć zakodowany dokument XML, należy dodać <xref:System.Xml.Linq.XDeclaration> do drzewa XML, ustawiając kodowanie na żądaną nazwę strony kodowej.  
  
 Każda wartość zwrócona przez <xref:System.Text.Encoding.WebName%2A> jest prawidłową wartością.  
  
 Jeśli odczytasz zakodowany dokument, właściwość <xref:System.Xml.Linq.XDeclaration.Encoding%2A> zostanie ustawiona na nazwę strony kodowej.  
  
 Jeśli ustawisz <xref:System.Xml.Linq.XDeclaration.Encoding%2A> na poprawną nazwę strony kodowej, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zostanie Zserializowany z określonym kodowaniem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa dokumenty, jeden z kodowaniem UTF-8 i jeden z kodowaniem UTF-16. Następnie ładuje dokumenty i drukuje kodowanie do konsoli programu.  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
