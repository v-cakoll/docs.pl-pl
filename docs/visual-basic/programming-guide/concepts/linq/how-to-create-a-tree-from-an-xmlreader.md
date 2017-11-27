---
title: 'Porady: Tworzenie drzewa z element XmlReader (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ceae7c2bee85e7b368322c8ba195dea9feff672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="5ebb5-102">Porady: Tworzenie drzewa z element XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ebb5-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="5ebb5-103">W tym temacie przedstawiono sposób tworzenia drzewo XML bezpośrednio z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="5ebb5-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="5ebb5-104">Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="5ebb5-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="5ebb5-105"><xref:System.Xml.XmlReader> Pominie komentarze i przetwarzanie instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekstu, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="5ebb5-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="5ebb5-106">Aby uniknąć tych błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed utworzeniem drzewo XML z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="5ebb5-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ebb5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ebb5-107">Example</span></span>  
 <span data-ttu-id="5ebb5-108">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5ebb5-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5ebb5-109">Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczyty węzłów aż do znalezienia pierwszy węzeł elementu.</span><span class="sxs-lookup"><span data-stu-id="5ebb5-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="5ebb5-110">Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ebb5-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="5ebb5-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5ebb5-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ebb5-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ebb5-112">See Also</span></span>  
 [<span data-ttu-id="5ebb5-113">Analiza kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ebb5-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
