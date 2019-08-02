---
title: 'Instrukcje: Znajdź pojedynczy element podrzędny przy użyciu metody Descendants (C#)'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 726c89b8fdd3df774de2d7ac9a824f2b3769d404
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709964"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="80729-102">Instrukcje: Znajdź pojedynczy element podrzędny przy użyciu metody Descendants (C#)</span><span class="sxs-lookup"><span data-stu-id="80729-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="80729-103">Możesz użyć metody osi <xref:System.Xml.Linq.XContainer.Descendants%2A> , aby szybko napisać kod w celu znalezienia pojedynczego elementu z unikatowymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="80729-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="80729-104">Ta technika jest szczególnie przydatna, gdy chcesz znaleźć konkretny element podrzędny o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="80729-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="80729-105">Można napisać kod, aby przejść do żądanego elementu, ale jest on często szybszy i łatwiejszy w pisaniu kodu przy użyciu <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="80729-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80729-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="80729-106">Example</span></span>  
 <span data-ttu-id="80729-107">W <xref:System.Linq.Enumerable.First%2A> tym przykładzie użyto standardowego operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="80729-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="80729-108">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="80729-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="80729-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="80729-109">Example</span></span>  
 <span data-ttu-id="80729-110">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80729-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="80729-111">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="80729-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="80729-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="80729-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
