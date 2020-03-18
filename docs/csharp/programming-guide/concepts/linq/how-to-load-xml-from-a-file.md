---
title: Jak załadować xml z pliku (C#)
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 635b338bbaf9c15779bccab4d4c824037858b338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169055"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="8b313-102">Jak załadować xml z pliku (C#)</span><span class="sxs-lookup"><span data-stu-id="8b313-102">How to load XML from a file (C#)</span></span>
<span data-ttu-id="8b313-103">W tym temacie pokazano, jak załadować <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> XML z identyfikatora URI przy użyciu tej metody.</span><span class="sxs-lookup"><span data-stu-id="8b313-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b313-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b313-104">Example</span></span>  
 <span data-ttu-id="8b313-105">W poniższym przykładzie pokazano, jak załadować dokument XML z pliku.</span><span class="sxs-lookup"><span data-stu-id="8b313-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="8b313-106">Poniższy przykład ładuje plik books.xml i wyświetla drzewo XML do konsoli.</span><span class="sxs-lookup"><span data-stu-id="8b313-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="8b313-107">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8b313-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="8b313-108">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8b313-108">This code produces the following output:</span></span>  
  
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
  