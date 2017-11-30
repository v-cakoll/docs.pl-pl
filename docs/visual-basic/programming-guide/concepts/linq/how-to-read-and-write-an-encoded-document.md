---
title: 'Porady: Odczyt i zapis dokumentu zakodowanego (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7dd871b4ab58103897bd5884581bf2e1353a3c60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>Porady: Odczyt i zapis dokumentu zakodowanego (Visual Basic)
Aby utworzyć dokumentu XML zakodowane, należy dodać <xref:System.Xml.Linq.XDeclaration> do drzewa XML ustawienie Kodowanie nazwy strony odpowiedni kod.  
  
 Każda wartość zwracana przez <xref:System.Text.Encoding.WebName%2A> jest prawidłową wartością.  
  
 Jeśli odczytać dokument zakodowany <xref:System.Xml.Linq.XDeclaration.Encoding%2A> właściwość zostanie ustawiona na nazwę strony kodu.  
  
 Jeśli ustawisz <xref:System.Xml.Linq.XDeclaration.Encoding%2A> na nazwę strony prawidłowy kod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] będzie serializować z określonego kodowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa dokumenty, jeden z kodowania utf-8 i jeden z kodowania utf-16. Następnie ładuje dokumenty i wyświetla kodowanie do konsoli.  
  
```vb  
Console.WriteLine("Creating a document with utf-8 encoding")  
Dim encodedDoc8 As XDocument = _  
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>  
        <Root>Content</Root>   
  
encodedDoc8.Save("EncodedUtf8.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Console.WriteLine("Creating a document with utf-16 encoding")  
Dim encodedDoc16 As XDocument = _  
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>  
        <Root>Content</Root>  
  
encodedDoc16.Save("EncodedUtf16.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
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
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>  
 [Zaawansowane LINQ do XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
