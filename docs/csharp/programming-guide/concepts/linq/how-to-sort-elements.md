---
title: Jak sortować elementy (C#)
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7fad9fcb43905072c88a5704c56672917bfc377c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347366"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="ac5cb-102">Jak sortować elementy (C#)</span><span class="sxs-lookup"><span data-stu-id="ac5cb-102">How to sort elements (C#)</span></span>
<span data-ttu-id="ac5cb-103">Ten przykład pokazuje, jak napisać zapytanie, które sortuje jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="ac5cb-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac5cb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac5cb-104">Example</span></span>  
 <span data-ttu-id="ac5cb-105">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ac5cb-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ac5cb-106">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ac5cb-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="ac5cb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac5cb-107">Example</span></span>  
 <span data-ttu-id="ac5cb-108">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ac5cb-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ac5cb-109">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ac5cb-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ac5cb-110">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe w przestrzeni nazw](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ac5cb-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="ac5cb-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ac5cb-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac5cb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac5cb-112">See also</span></span>

- [<span data-ttu-id="ac5cb-113">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="ac5cb-113">Sorting Data (C#)</span></span>](./sorting-data.md)
