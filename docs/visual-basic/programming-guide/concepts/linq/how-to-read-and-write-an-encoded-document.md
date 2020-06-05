---
title: 'Instrukcje: odczytywanie i zapisywanie zakodowanego dokumentu'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397911"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="8c938-102">Instrukcje: odczytywanie i pisanie zakodowanego dokumentu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c938-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>

<span data-ttu-id="8c938-103">Aby utworzyć zakodowany dokument XML, należy dodać <xref:System.Xml.Linq.XDeclaration> do drzewa XML, ustawiając kodowanie na żądaną nazwę strony kodowej.</span><span class="sxs-lookup"><span data-stu-id="8c938-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="8c938-104">Każda wartość zwrócona przez <xref:System.Text.Encoding.WebName%2A> jest prawidłową wartością.</span><span class="sxs-lookup"><span data-stu-id="8c938-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="8c938-105">Jeśli odczytasz zakodowany dokument, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> Właściwość zostanie ustawiona na nazwę strony kodowej.</span><span class="sxs-lookup"><span data-stu-id="8c938-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="8c938-106">W przypadku wybrania <xref:System.Xml.Linq.XDeclaration.Encoding%2A> prawidłowej nazwy strony kodowej program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zaserializacji z określonym kodowaniem.</span><span class="sxs-lookup"><span data-stu-id="8c938-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>

## <a name="example"></a><span data-ttu-id="8c938-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c938-107">Example</span></span>

<span data-ttu-id="8c938-108">Poniższy przykład tworzy dwa dokumenty, jeden z kodowaniem UTF-8 i jeden z kodowaniem UTF-16.</span><span class="sxs-lookup"><span data-stu-id="8c938-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="8c938-109">Następnie ładuje dokumenty i drukuje kodowanie do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="8c938-109">It then loads the documents and prints the encoding to the console.</span></span>

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

<span data-ttu-id="8c938-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8c938-110">This example produces the following output:</span></span>

```console
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

## <a name="see-also"></a><span data-ttu-id="8c938-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c938-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8c938-112">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c938-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
