---
title: "Porady: obliczanie wartości pośredniego (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 93aa3683315b88c0ca85abc0eaff3efc8a15452a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="8215a-102">Porady: obliczanie wartości pośredniego (C#)</span><span class="sxs-lookup"><span data-stu-id="8215a-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="8215a-103">Ten przykład przedstawia sposób obliczania wartości pośrednich, które mogą być używane w sortowanie, filtrowanie i wybierając.</span><span class="sxs-lookup"><span data-stu-id="8215a-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8215a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8215a-104">Example</span></span>  
 <span data-ttu-id="8215a-105">W poniższym przykładzie użyto `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8215a-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="8215a-106">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8215a-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="8215a-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8215a-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="8215a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="8215a-108">Example</span></span>  
 <span data-ttu-id="8215a-109">W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8215a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8215a-110">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="8215a-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="8215a-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="8215a-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="8215a-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8215a-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="8215a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8215a-113">See Also</span></span>  
 [<span data-ttu-id="8215a-114">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8215a-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
