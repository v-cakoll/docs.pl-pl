---
title: "Porady: tworzenie hierarchii za pomocą grupowania (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eb3ca6b-1aed-43de-b8b9-41c769c993f8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67019e2ab3d9057567969b34e276abba15174321
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-hierarchy-using-grouping-visual-basic"></a><span data-ttu-id="1ad8d-102">Porady: tworzenie hierarchii za pomocą grupowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ad8d-102">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>
<span data-ttu-id="1ad8d-103">W tym przykładzie przedstawiono sposób grupowania danych, a następnie wygeneruj XML oparte na grupowanie.</span><span class="sxs-lookup"><span data-stu-id="1ad8d-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ad8d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ad8d-104">Example</span></span>  
 <span data-ttu-id="1ad8d-105">Pierwszy to przykład grupuje dane według kategorii, następnie generuje nowy plik XML, w którym hierarchii XML odzwierciedla grupowanie.</span><span class="sxs-lookup"><span data-stu-id="1ad8d-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="1ad8d-106">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1ad8d-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim doc As XElement = XElement.Load("Data.xml")  
Dim newData As XElement = _  
    <Root>  
        <%= _  
            From data In doc.<Data> _  
            Group By category = data.<Category>(0).Value _  
            Into groupedData = Group _  
            Select <Group ID=<%= category %>>  
                       <%= _  
                           From g In groupedData _  
                           Select _  
                           <Data>  
                               <%= g.<Quantity>(0) %>  
                               <%= g.<Price>(0) %>  
                           </Data> _  
                       %>  
                   </Group> _  
        %>  
    </Root>  
Console.WriteLine(newData)  
```  
  
 <span data-ttu-id="1ad8d-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1ad8d-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ad8d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ad8d-108">See Also</span></span>  
 [<span data-ttu-id="1ad8d-109">Zaawansowane techniki zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ad8d-109">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
