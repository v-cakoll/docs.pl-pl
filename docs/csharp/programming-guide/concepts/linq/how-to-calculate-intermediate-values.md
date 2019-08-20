---
title: 'Instrukcje: Oblicz wartości pośrednie (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 7b2dfc4e26fc7648cbd93b1e590079e4b105ad43
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594129"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="0a234-102">Instrukcje: Oblicz wartości pośrednie (C#)</span><span class="sxs-lookup"><span data-stu-id="0a234-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="0a234-103">Ten przykład pokazuje sposób obliczania wartości pośrednich, które mogą być używane do sortowania, filtrowania i wybierania.</span><span class="sxs-lookup"><span data-stu-id="0a234-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a234-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a234-104">Example</span></span>  
 <span data-ttu-id="0a234-105">W poniższym przykładzie zastosowano `Let` klauzulę.</span><span class="sxs-lookup"><span data-stu-id="0a234-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="0a234-106">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0a234-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="0a234-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0a234-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="0a234-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a234-108">Example</span></span>  
 <span data-ttu-id="0a234-109">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0a234-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0a234-110">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0a234-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0a234-111">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe w przestrzeni nazw](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0a234-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="0a234-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0a234-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
