---
title: Jak obliczyć wartości pośrednie (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141450"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="6b906-102">Jak obliczyć wartości pośrednie (C#)</span><span class="sxs-lookup"><span data-stu-id="6b906-102">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="6b906-103">W tym przykładzie pokazano, jak obliczyć wartości pośrednie, które mogą być używane do sortowania, filtrowania i wybierania.</span><span class="sxs-lookup"><span data-stu-id="6b906-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b906-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b906-104">Example</span></span>  
 <span data-ttu-id="6b906-105">Poniższy przykład używa `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6b906-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="6b906-106">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Dane numeryczne (LINQ do XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6b906-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6b906-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6b906-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="6b906-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b906-108">Example</span></span>  
 <span data-ttu-id="6b906-109">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="6b906-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6b906-110">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6b906-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="6b906-111">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Dane liczbowe w obszarze nazw](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="6b906-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="6b906-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6b906-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
