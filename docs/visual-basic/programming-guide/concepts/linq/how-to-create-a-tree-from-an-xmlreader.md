---
title: 'Instrukcje: tworzenie drzewa na podstawie elementu XmlReader'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 25c15ff08563b12b26041a536dfbca1c9cce260a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414611"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)

W tym temacie pokazano, jak utworzyć drzewo XML bezpośrednio z programu <xref:System.Xml.XmlReader> . Aby utworzyć obiekt <xref:System.Xml.Linq.XElement> z poziomu <xref:System.Xml.XmlReader> , należy umieścić <xref:System.Xml.XmlReader> w węźle elementu. <xref:System.Xml.XmlReader>Program pominie Komentarze i instrukcje przetwarzania, ale jeśli <xref:System.Xml.XmlReader> jest umieszczony w węźle tekstowym, zostanie wygenerowany błąd. Aby uniknąć takich błędów, należy zawsze umieścić <xref:System.Xml.XmlReader> element na elemencie przed utworzeniem drzewa XML z <xref:System.Xml.XmlReader> .

## <a name="example"></a>Przykład

Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).

Poniższy kod tworzy `T:System.Xml.XmlReader` obiekt, a następnie odczytuje węzły do momentu znalezienia węzła pierwszego elementu. Następnie ładuje <xref:System.Xml.Linq.XElement> obiekt.

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
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

- [Analizowanie kodu XML (Visual Basic)](parsing-xml.md)
