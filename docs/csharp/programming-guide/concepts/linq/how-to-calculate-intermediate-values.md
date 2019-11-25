---
title: Jak obliczyć wartości pośrednie (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141450"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="2a87f-102">Jak obliczyć wartości pośrednie (C#)</span><span class="sxs-lookup"><span data-stu-id="2a87f-102">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="2a87f-103">Ten przykład pokazuje sposób obliczania wartości pośrednich, które mogą być używane do sortowania, filtrowania i wybierania.</span><span class="sxs-lookup"><span data-stu-id="2a87f-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a87f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a87f-104">Example</span></span>  
 <span data-ttu-id="2a87f-105">W poniższym przykładzie zastosowano klauzulę `Let`.</span><span class="sxs-lookup"><span data-stu-id="2a87f-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="2a87f-106">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a87f-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="2a87f-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2a87f-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="2a87f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a87f-108">Example</span></span>  
 <span data-ttu-id="2a87f-109">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2a87f-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="2a87f-110">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a87f-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2a87f-111">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe w przestrzeni nazw](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2a87f-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="2a87f-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2a87f-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
