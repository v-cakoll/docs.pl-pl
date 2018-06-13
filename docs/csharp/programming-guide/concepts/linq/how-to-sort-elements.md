---
title: 'Porady: sortowanie elementów (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: a49b4fea8410075ca8b28f2ef7792738d063e256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319770"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="f008a-102">Porady: sortowanie elementów (C#)</span><span class="sxs-lookup"><span data-stu-id="f008a-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="f008a-103">Ten przykład przedstawia, jak napisać zapytanie sortujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="f008a-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f008a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f008a-104">Example</span></span>  
 <span data-ttu-id="f008a-105">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f008a-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="f008a-106">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f008a-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="f008a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f008a-107">Example</span></span>  
 <span data-ttu-id="f008a-108">W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f008a-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="f008a-109">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="f008a-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f008a-110">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f008a-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="f008a-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f008a-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="f008a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f008a-112">See Also</span></span>  
 [<span data-ttu-id="f008a-113">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="f008a-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
 [<span data-ttu-id="f008a-114">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f008a-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
