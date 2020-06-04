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
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="c822f-102">Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c822f-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="c822f-103">W tym temacie pokazano, jak utworzyć drzewo XML bezpośrednio z programu <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="c822f-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c822f-104">Aby utworzyć obiekt <xref:System.Xml.Linq.XElement> z poziomu <xref:System.Xml.XmlReader> , należy umieścić <xref:System.Xml.XmlReader> w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="c822f-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="c822f-105"><xref:System.Xml.XmlReader>Program pominie Komentarze i instrukcje przetwarzania, ale jeśli <xref:System.Xml.XmlReader> jest umieszczony w węźle tekstowym, zostanie wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="c822f-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="c822f-106">Aby uniknąć takich błędów, należy zawsze umieścić <xref:System.Xml.XmlReader> element na elemencie przed utworzeniem drzewa XML z <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="c822f-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="c822f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c822f-107">Example</span></span>

<span data-ttu-id="c822f-108">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c822f-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="c822f-109">Poniższy kod tworzy `T:System.Xml.XmlReader` obiekt, a następnie odczytuje węzły do momentu znalezienia węzła pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="c822f-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="c822f-110">Następnie ładuje <xref:System.Xml.Linq.XElement> obiekt.</span><span class="sxs-lookup"><span data-stu-id="c822f-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="c822f-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c822f-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c822f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c822f-112">See also</span></span>

- [<span data-ttu-id="c822f-113">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c822f-113">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
