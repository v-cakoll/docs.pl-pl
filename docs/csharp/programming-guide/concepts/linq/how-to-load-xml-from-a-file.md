---
title: 'Instrukcje: Ładowanie kodu XML z pliku (C#)'
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: f97e99a3d5fb2dd5628e1dc00909b6608255a967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667915"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="00971-102">Instrukcje: Ładowanie kodu XML z pliku (C#)</span><span class="sxs-lookup"><span data-stu-id="00971-102">How to: Load XML from a File (C#)</span></span>
<span data-ttu-id="00971-103">W tym temacie pokazano, jak załadować XML z identyfikatora URI przy użyciu <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="00971-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00971-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="00971-104">Example</span></span>  
 <span data-ttu-id="00971-105">Poniższy przykład przedstawia sposób ładowania dokumentu XML z pliku.</span><span class="sxs-lookup"><span data-stu-id="00971-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="00971-106">Poniższy przykład załaduje books.xml i generuje drzewa XML do konsoli.</span><span class="sxs-lookup"><span data-stu-id="00971-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="00971-107">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="00971-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="00971-108">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="00971-108">This code produces the following output:</span></span>  
  
```xml  
<Catalog>  
  <Book id="bk101">  
    <Author>Garghentini, Davide</Author>  
    <Title>XML Developer's Guide</Title>  
    <Genre>Computer</Genre>  
    <Price>44.95</Price>  
    <PublishDate>2000-10-01</PublishDate>  
    <Description>An in-depth look at creating applications   
      with XML.</Description>  
  </Book>  
  <Book id="bk102">  
    <Author>Garcia, Debra</Author>  
    <Title>Midnight Rain</Title>  
    <Genre>Fantasy</Genre>  
    <Price>5.95</Price>  
    <PublishDate>2000-12-16</PublishDate>  
    <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
  </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00971-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00971-109">See also</span></span>

- [<span data-ttu-id="00971-110">Analizowanie kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="00971-110">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
