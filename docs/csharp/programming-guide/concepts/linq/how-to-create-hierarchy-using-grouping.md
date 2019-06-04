---
title: 'Instrukcje: Tworzenie hierarchii przy użyciu grupowania (C#)'
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: 685c8ad1360ba2959dc81632ae084b935bd37c47
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485844"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="21da9-102">Instrukcje: Tworzenie hierarchii przy użyciu grupowania (C#)</span><span class="sxs-lookup"><span data-stu-id="21da9-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="21da9-103">W tym przykładzie przedstawiono sposób grupowania danych, a następnie wygeneruj XML, w oparciu o grupowania.</span><span class="sxs-lookup"><span data-stu-id="21da9-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21da9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="21da9-104">Example</span></span>  
 <span data-ttu-id="21da9-105">Pierwszy to przykład grupuje dane według kategorii, następnie generuje nowy plik XML, w którym hierarchię XML odzwierciedla grupowania.</span><span class="sxs-lookup"><span data-stu-id="21da9-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="21da9-106">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="21da9-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="21da9-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="21da9-107">This example produces the following output:</span></span>  
  
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
