---
title: "Porady: tworzenie hierarchii za pomocą grupowania (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa0272e03022038c6dc464516998fad948f30e59
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="6aa79-102">Porady: tworzenie hierarchii za pomocą grupowania (C#)</span><span class="sxs-lookup"><span data-stu-id="6aa79-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="6aa79-103">W tym przykładzie przedstawiono sposób grupowania danych, a następnie wygeneruj XML oparte na grupowanie.</span><span class="sxs-lookup"><span data-stu-id="6aa79-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aa79-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6aa79-104">Example</span></span>  
 <span data-ttu-id="6aa79-105">Pierwszy to przykład grupuje dane według kategorii, następnie generuje nowy plik XML, w którym hierarchii XML odzwierciedla grupowanie.</span><span class="sxs-lookup"><span data-stu-id="6aa79-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="6aa79-106">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6aa79-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Load("Data.xml");  
var newData =  
    new XElement("Root",  
        from data in doc.Elements("Data")  
        group data by (string)data.Element("Category") into groupedData  
        select new XElement("Group",  
            new XAttribute("ID", groupedData.Key),  
            from g in groupedData  
            select new XElement("Data",  
                g.Element("Quantity"),  
                g.Element("Price")  
            )  
        )  
    );  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="6aa79-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6aa79-107">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6aa79-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6aa79-108">See Also</span></span>  
 [<span data-ttu-id="6aa79-109">Zaawansowane techniki zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6aa79-109">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
