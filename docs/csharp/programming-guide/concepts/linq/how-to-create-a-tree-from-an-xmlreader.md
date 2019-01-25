---
title: 'Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: fb65c7b74bf3bd006fd4f545e4587efe9a392131
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496190"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="9316c-102">Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="9316c-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="9316c-103">W tym temacie przedstawiono sposób tworzenia drzewa XML bezpośrednio z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9316c-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9316c-104">Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> węzeł elementu.</span><span class="sxs-lookup"><span data-stu-id="9316c-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="9316c-105"><xref:System.Xml.XmlReader> Pozwoli na pominięcie komentarze i przetwarzania instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekst, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="9316c-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="9316c-106">Aby uniknąć takich błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed przystąpieniem do tworzenia drzewa XML z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9316c-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9316c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9316c-107">Example</span></span>  
 <span data-ttu-id="9316c-108">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9316c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9316c-109">Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczytuje węzłów do momentu znalezienia pierwszego węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="9316c-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="9316c-110">Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9316c-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="9316c-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9316c-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9316c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9316c-112">See also</span></span>

- [<span data-ttu-id="9316c-113">Analizowanie kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9316c-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
