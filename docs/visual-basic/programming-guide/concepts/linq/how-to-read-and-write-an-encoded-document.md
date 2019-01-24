---
title: 'Instrukcje: Odczytywanie i zapisywanie zakodowanego dokumentu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: 52360b465e40a015e2cddee62ed4197d827bc560
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538703"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="bf3ae-102">Instrukcje: Odczytywanie i zapisywanie zakodowanego dokumentu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3ae-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>
<span data-ttu-id="bf3ae-103">Aby utworzyć zakodowanego dokumentu XML, należy dodać <xref:System.Xml.Linq.XDeclaration> do drzewa XML ustawienie Kodowanie do nazwy strony odpowiedni kod.</span><span class="sxs-lookup"><span data-stu-id="bf3ae-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="bf3ae-104">Każda wartość zwracana przez <xref:System.Text.Encoding.WebName%2A> jest prawidłową wartością.</span><span class="sxs-lookup"><span data-stu-id="bf3ae-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="bf3ae-105">Jeśli odczytu zakodowanego dokumentu <xref:System.Xml.Linq.XDeclaration.Encoding%2A> właściwość zostanie ustawiona na nazwę strony kodu.</span><span class="sxs-lookup"><span data-stu-id="bf3ae-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="bf3ae-106">Jeśli ustawisz <xref:System.Xml.Linq.XDeclaration.Encoding%2A> na nazwę prawidłowy kod strony [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] będzie serializacji przy użyciu określonego kodowania.</span><span class="sxs-lookup"><span data-stu-id="bf3ae-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf3ae-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf3ae-107">Example</span></span>  
 <span data-ttu-id="bf3ae-108">Poniższy przykład tworzy dwa dokumenty, jeden z kodowaniem utf-8 i jeden z kodowaniem utf-16.</span><span class="sxs-lookup"><span data-stu-id="bf3ae-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="bf3ae-109">Następnie ładuje dokumenty i drukuje kodowanie do konsoli.</span><span class="sxs-lookup"><span data-stu-id="bf3ae-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
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
  
 <span data-ttu-id="bf3ae-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="bf3ae-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf3ae-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf3ae-111">See also</span></span>
- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bf3ae-112">Zaawansowane LINQ to XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3ae-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
