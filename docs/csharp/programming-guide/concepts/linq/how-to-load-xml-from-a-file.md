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
# <a name="how-to-load-xml-from-a-file-c"></a>Jak załadować xml z pliku (C#)
W tym temacie pokazano, jak załadować <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> XML z identyfikatora URI przy użyciu tej metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak załadować dokument XML z pliku. Poniższy przykład ładuje plik books.xml i wyświetla drzewo XML do konsoli.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
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
  