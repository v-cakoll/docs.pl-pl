---
title: Jak znaleźć element z określonym elementem podrzędnym (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141144"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="1caa6-102">Jak znaleźć element z określonym elementem podrzędnym (C#)</span><span class="sxs-lookup"><span data-stu-id="1caa6-102">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="1caa6-103">W tym temacie pokazano, jak znaleźć określony element, który ma element podrzędny o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="1caa6-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1caa6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1caa6-104">Example</span></span>  
 <span data-ttu-id="1caa6-105">Przykład znajduje `Test` element, który `CommandLine` ma element podrzędny o wartości "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="1caa6-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="1caa6-106">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Konfiguracja testu (LINQ do XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1caa6-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="1caa6-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1caa6-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="1caa6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1caa6-108">Example</span></span>  
 <span data-ttu-id="1caa6-109">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="1caa6-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1caa6-110">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1caa6-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1caa6-111">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Konfiguracja testu w obszarze nazw](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="1caa6-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="1caa6-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1caa6-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="1caa6-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1caa6-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="1caa6-114">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="1caa6-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1caa6-115">Operacje projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="1caa6-115">Projection Operations (C#)</span></span>](./projection-operations.md)
