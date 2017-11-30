---
title: 'Porady: Tworzenie drzewa z element XmlReader (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28a052fb6de0a59503eba8c357cdd3c4745b71ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="9cc80-102">Porady: Tworzenie drzewa z element XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="9cc80-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="9cc80-103">W tym temacie przedstawiono sposób tworzenia drzewo XML bezpośrednio z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9cc80-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9cc80-104">Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="9cc80-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="9cc80-105"><xref:System.Xml.XmlReader> Pominie komentarze i przetwarzanie instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekstu, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="9cc80-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="9cc80-106">Aby uniknąć tych błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed utworzeniem drzewo XML z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9cc80-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cc80-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cc80-107">Example</span></span>  
 <span data-ttu-id="9cc80-108">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9cc80-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9cc80-109">Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczyty węzłów aż do znalezienia pierwszy węzeł elementu.</span><span class="sxs-lookup"><span data-stu-id="9cc80-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="9cc80-110">Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9cc80-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="9cc80-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9cc80-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cc80-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cc80-112">See Also</span></span>  
 [<span data-ttu-id="9cc80-113">Analiza kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9cc80-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
