---
title: Jak znaleźć element z określonym elementem podrzędnym (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141144"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="57195-102">Jak znaleźć element z określonym elementem podrzędnym (C#)</span><span class="sxs-lookup"><span data-stu-id="57195-102">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="57195-103">W tym temacie pokazano, jak znaleźć konkretny element, który ma element podrzędny o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="57195-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57195-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="57195-104">Example</span></span>  
 <span data-ttu-id="57195-105">Przykład umożliwia znalezienie elementu `Test`, który ma `CommandLine` element podrzędny o wartości "Examp2. EXE".</span><span class="sxs-lookup"><span data-stu-id="57195-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="57195-106">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="57195-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="57195-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="57195-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="57195-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="57195-108">Example</span></span>  
 <span data-ttu-id="57195-109">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="57195-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="57195-110">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="57195-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="57195-111">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testowa w przestrzeni nazw](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="57195-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="57195-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="57195-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="57195-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57195-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="57195-114">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="57195-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="57195-115">Operacje projekcjiC#()</span><span class="sxs-lookup"><span data-stu-id="57195-115">Projection Operations (C#)</span></span>](./projection-operations.md)
