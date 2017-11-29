---
title: "Porady: ładowanie XML z pliku (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7db51b4b0d6cebb443a9ff43ac8916d3004c1ea5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-load-xml-from-a-file-c"></a>Porady: ładowanie XML z pliku (C#)
W tym temacie przedstawiono sposób ładowanie XML z identyfikatora URI przy użyciu <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób ładowania dokumentu XML z pliku. W poniższym przykładzie ładuje books.xml i wyprowadza drzewa XML do konsoli.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
