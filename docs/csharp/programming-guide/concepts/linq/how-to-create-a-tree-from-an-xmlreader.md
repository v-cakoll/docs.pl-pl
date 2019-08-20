---
title: 'Instrukcje: Utwórz drzewo na podstawie elementu XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: f632bbdad7d52ea37e2587516792dfd13178d702
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593873"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="8772b-102">Instrukcje: Utwórz drzewo na podstawie elementu XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="8772b-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="8772b-103">W tym temacie pokazano, jak utworzyć drzewo XML bezpośrednio z programu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="8772b-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="8772b-104">Aby utworzyć obiekt <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader>z poziomu <xref:System.Xml.XmlReader> , należy umieścić w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="8772b-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="8772b-105">Program pominie Komentarze i instrukcje przetwarzania, ale <xref:System.Xml.XmlReader> jeśli jest umieszczony w węźle tekstowym, zostanie wygenerowany błąd. <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="8772b-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="8772b-106">Aby uniknąć takich błędów, należy zawsze umieścić <xref:System.Xml.XmlReader> element na elemencie przed utworzeniem drzewa XML <xref:System.Xml.XmlReader>z.</span><span class="sxs-lookup"><span data-stu-id="8772b-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8772b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8772b-107">Example</span></span>  
 <span data-ttu-id="8772b-108">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8772b-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8772b-109">Poniższy kod tworzy `T:System.Xml.XmlReader` obiekt, a następnie odczytuje węzły do momentu znalezienia węzła pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="8772b-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="8772b-110">Następnie ładuje <xref:System.Xml.Linq.XElement> obiekt.</span><span class="sxs-lookup"><span data-stu-id="8772b-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="8772b-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8772b-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8772b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8772b-112">See also</span></span>

- [<span data-ttu-id="8772b-113">Analizowanie pliku XMLC#()</span><span class="sxs-lookup"><span data-stu-id="8772b-113">Parsing XML (C#)</span></span>](./parsing-xml.md)
