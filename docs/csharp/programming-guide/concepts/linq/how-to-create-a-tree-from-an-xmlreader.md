---
title: Jak utworzyć drzewo z czytnika XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 9ead6352112d9e1b56bd70699c90133e432f96b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169275"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Jak utworzyć drzewo z czytnika XmlReader (C#)
W tym temacie pokazano, jak utworzyć <xref:System.Xml.XmlReader>drzewo XML bezpośrednio z pliku . Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy <xref:System.Xml.XmlReader> umieścić na węźle elementu. Pominie <xref:System.Xml.XmlReader> komentarze i instrukcje przetwarzania, ale jeśli <xref:System.Xml.XmlReader> jest umieszczony w węźle tekstowym, zostanie wygenerowany błąd. Aby uniknąć takich błędów, <xref:System.Xml.XmlReader> zawsze umieść na elemencie <xref:System.Xml.XmlReader>przed utworzeniem drzewa XML z pliku .  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).  
  
 Poniższy kod tworzy `T:System.Xml.XmlReader` obiekt, a następnie odczytuje węzły, dopóki nie znajdzie węzła pierwszego elementu. Następnie ładuje <xref:System.Xml.Linq.XElement> obiekt.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
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

- [Analizowanie języka XML (C#)](how-to-parse-a-string.md)
