---
title: 'Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 49769fea96f1ed09420f4646a21f75093ef35fce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502181"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="937c7-102">Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="937c7-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="937c7-103">W tym temacie przedstawiono sposób tworzenia drzewa XML bezpośrednio z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="937c7-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="937c7-104">Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> węzeł elementu.</span><span class="sxs-lookup"><span data-stu-id="937c7-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="937c7-105"><xref:System.Xml.XmlReader> Pozwoli na pominięcie komentarze i przetwarzania instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekst, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="937c7-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="937c7-106">Aby uniknąć takich błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed przystąpieniem do tworzenia drzewa XML z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="937c7-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="937c7-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="937c7-107">Example</span></span>  
 <span data-ttu-id="937c7-108">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="937c7-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="937c7-109">Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczytuje węzłów do momentu znalezienia pierwszego węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="937c7-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="937c7-110">Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="937c7-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="937c7-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="937c7-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="937c7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="937c7-112">See also</span></span>
- [<span data-ttu-id="937c7-113">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="937c7-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
