---
title: 'Instrukcje: Odczytywanie i zapisywanie zakodowanego dokumentu (C#)'
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: 6340443fddbedb4e27e1d1f8ab3e7c006a039f25
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485141"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="d15d4-102">Instrukcje: Odczytywanie i zapisywanie zakodowanego dokumentu (C#)</span><span class="sxs-lookup"><span data-stu-id="d15d4-102">How to: Read and Write an Encoded Document (C#)</span></span>
<span data-ttu-id="d15d4-103">Aby utworzyć zakodowanego dokumentu XML, należy dodać <xref:System.Xml.Linq.XDeclaration> do drzewa XML ustawienie Kodowanie do nazwy strony odpowiedni kod.</span><span class="sxs-lookup"><span data-stu-id="d15d4-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="d15d4-104">Każda wartość zwracana przez <xref:System.Text.Encoding.WebName%2A> jest prawidłową wartością.</span><span class="sxs-lookup"><span data-stu-id="d15d4-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="d15d4-105">Jeśli odczytu zakodowanego dokumentu <xref:System.Xml.Linq.XDeclaration.Encoding%2A> właściwość zostanie ustawiona na nazwę strony kodu.</span><span class="sxs-lookup"><span data-stu-id="d15d4-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="d15d4-106">Jeśli ustawisz <xref:System.Xml.Linq.XDeclaration.Encoding%2A> na nazwę prawidłowy kod strony [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] będzie serializacji przy użyciu określonego kodowania.</span><span class="sxs-lookup"><span data-stu-id="d15d4-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d15d4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d15d4-107">Example</span></span>  
 <span data-ttu-id="d15d4-108">Poniższy przykład tworzy dwa dokumenty, jeden z kodowaniem utf-8 i jeden z kodowaniem utf-16.</span><span class="sxs-lookup"><span data-stu-id="d15d4-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="d15d4-109">Następnie ładuje dokumenty i drukuje kodowanie do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d15d4-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
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
  
 <span data-ttu-id="d15d4-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d15d4-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d15d4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d15d4-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
