---
title: Jak obliczyć wartości pośrednie (C#)
description: Ten LINQ to XML przykład w języku C# pokazuje sposób obliczania wartości pośrednich, które mogą być używane do sortowania, filtrowania i wybierania.
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103622"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="16b50-103">Jak obliczyć wartości pośrednie (C#)</span><span class="sxs-lookup"><span data-stu-id="16b50-103">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="16b50-104">Ten przykład pokazuje sposób obliczania wartości pośrednich, które mogą być używane do sortowania, filtrowania i wybierania.</span><span class="sxs-lookup"><span data-stu-id="16b50-104">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16b50-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="16b50-105">Example</span></span>  
 <span data-ttu-id="16b50-106">W poniższym przykładzie zastosowano `Let` klauzulę.</span><span class="sxs-lookup"><span data-stu-id="16b50-106">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="16b50-107">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="16b50-108">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="16b50-108">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="16b50-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="16b50-109">Example</span></span>  
 <span data-ttu-id="16b50-110">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="16b50-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="16b50-111">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="16b50-112">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe w przestrzeni nazw](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="16b50-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="16b50-113">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="16b50-113">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
