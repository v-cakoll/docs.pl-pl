---
title: 'Instrukcje: Znajdź element z określonym elementem podrzędnym (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: f007bddcbecc1cb938d05c7d444d29b6047749e8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253744"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="cd10a-102">Instrukcje: Znajdź element z określonym elementem podrzędnym (C#)</span><span class="sxs-lookup"><span data-stu-id="cd10a-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="cd10a-103">W tym temacie pokazano, jak znaleźć konkretny element, który ma element podrzędny o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="cd10a-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd10a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd10a-104">Example</span></span>  
 <span data-ttu-id="cd10a-105">Przykład znajduje `Test` element, który `CommandLine` ma element podrzędny o wartości "Examp2. exe".</span><span class="sxs-lookup"><span data-stu-id="cd10a-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="cd10a-106">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Konfiguracja testu (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd10a-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="cd10a-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cd10a-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="cd10a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd10a-108">Example</span></span>  
 <span data-ttu-id="cd10a-109">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cd10a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cd10a-110">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd10a-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cd10a-111">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Konfiguracja testowa w przestrzeni nazw](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="cd10a-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="cd10a-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cd10a-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd10a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd10a-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="cd10a-114">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="cd10a-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="cd10a-115">Operacje projekcjiC#()</span><span class="sxs-lookup"><span data-stu-id="cd10a-115">Projection Operations (C#)</span></span>](./projection-operations.md)
