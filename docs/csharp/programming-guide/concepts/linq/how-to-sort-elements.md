---
title: 'Instrukcje: Sortuj elementy (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: e5f76518437954ac683ec2e3e30ad9007c280f83
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253299"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="9b3b2-102">Instrukcje: Sortuj elementy (C#)</span><span class="sxs-lookup"><span data-stu-id="9b3b2-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="9b3b2-103">Ten przykład pokazuje, jak napisać zapytanie, które sortuje jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="9b3b2-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b3b2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b3b2-104">Example</span></span>  
 <span data-ttu-id="9b3b2-105">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9b3b2-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9b3b2-106">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9b3b2-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="9b3b2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b3b2-107">Example</span></span>  
 <span data-ttu-id="9b3b2-108">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9b3b2-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9b3b2-109">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9b3b2-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9b3b2-110">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe w przestrzeni nazw](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9b3b2-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9b3b2-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9b3b2-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b3b2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b3b2-112">See also</span></span>

- [<span data-ttu-id="9b3b2-113">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="9b3b2-113">Sorting Data (C#)</span></span>](./sorting-data.md)
