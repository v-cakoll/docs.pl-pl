---
title: Jak czytać i pisać zakodowany dokument (C#)
description: Dowiedz się, jak utworzyć zakodowany dokument XML w języku C#, dodając XDeclaration do drzewa XML i ustawiając kodowanie na żądaną nazwę strony kodowej.
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: ed02b7467f4de71455da516a6c894070337684e7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104312"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Jak czytać i pisać zakodowany dokument (C#)
Aby utworzyć zakodowany dokument XML, należy dodać <xref:System.Xml.Linq.XDeclaration> do drzewa XML, ustawiając kodowanie na żądaną nazwę strony kodowej.  
  
 Każda wartość zwrócona przez <xref:System.Text.Encoding.WebName%2A> jest prawidłową wartością.  
  
 Jeśli odczytasz zakodowany dokument, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> Właściwość zostanie ustawiona na nazwę strony kodowej.  
  
 W przypadku wybrania <xref:System.Xml.Linq.XDeclaration.Encoding%2A> prawidłowej nazwy strony kodowej program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zaserializacji z określonym kodowaniem.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
