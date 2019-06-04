---
title: 'Instrukcje: Sortowanie elementów (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0b338dc67bca38f471f37abf28149e5080a01987
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484895"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="e6a7c-102">Instrukcje: Sortowanie elementów (C#)</span><span class="sxs-lookup"><span data-stu-id="e6a7c-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="e6a7c-103">W tym przykładzie pokazano, jak napisać zapytanie sortujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6a7c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6a7c-104">Example</span></span>  
 <span data-ttu-id="e6a7c-105">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e6a7c-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e6a7c-106">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e6a7c-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="e6a7c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6a7c-107">Example</span></span>  
 <span data-ttu-id="e6a7c-108">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e6a7c-109">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e6a7c-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e6a7c-110">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e6a7c-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="e6a7c-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e6a7c-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6a7c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6a7c-112">See also</span></span>

- [<span data-ttu-id="e6a7c-113">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="e6a7c-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)
