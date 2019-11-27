---
title: 'Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 7d8d7f5b6389bef520e11fd2b7cc3e1c7e862e73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353085"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="c01b1-102">Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c01b1-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="c01b1-103">W tym temacie pokazano, jak utworzyć drzewo XML bezpośrednio z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c01b1-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c01b1-104">Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="c01b1-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="c01b1-105"><xref:System.Xml.XmlReader> pominie Komentarze i instrukcje przetwarzania, ale jeśli <xref:System.Xml.XmlReader> jest umieszczony w węźle tekstowym, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="c01b1-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="c01b1-106">Aby uniknąć takich błędów, należy zawsze umieścić <xref:System.Xml.XmlReader> w elemencie przed utworzeniem drzewa XML z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c01b1-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="c01b1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c01b1-107">Example</span></span>

<span data-ttu-id="c01b1-108">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c01b1-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="c01b1-109">Poniższy kod tworzy obiekt `T:System.Xml.XmlReader`, a następnie odczytuje węzły do momentu znalezienia węzła pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="c01b1-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="c01b1-110">Następnie ładuje obiekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c01b1-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="c01b1-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c01b1-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c01b1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c01b1-112">See also</span></span>

- [<span data-ttu-id="c01b1-113">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c01b1-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
