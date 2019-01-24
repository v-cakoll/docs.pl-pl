---
title: 'Instrukcje: Znajdź pojedynczego elementu potomnego przy użyciu metody elementów potomnych (C#)'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: a13a4aef6a3d22d2b7c3adb8e37996de08978b6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690530"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="bfd86-102">Instrukcje: Znajdź pojedynczego elementu potomnego przy użyciu metody elementów potomnych (C#)</span><span class="sxs-lookup"><span data-stu-id="bfd86-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="bfd86-103">Możesz użyć <xref:System.Xml.Linq.XContainer.Descendants%2A> metodę osi, aby szybko napisać kod, aby znaleźć pojedynczy jednoznacznie o nazwie elementu.</span><span class="sxs-lookup"><span data-stu-id="bfd86-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="bfd86-104">Ta technika jest szczególnie przydatne, gdy chcesz znaleźć określonego obiektu podrzędnego o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="bfd86-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="bfd86-105">Można napisać kod, aby przejść do żądanego elementu, ale często jest szybsze i prostsze do pisania kodu za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="bfd86-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd86-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="bfd86-106">Example</span></span>  
 <span data-ttu-id="bfd86-107">W tym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> standardowego operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="bfd86-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
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
  
 <span data-ttu-id="bfd86-108">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bfd86-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="bfd86-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="bfd86-109">Example</span></span>  
 <span data-ttu-id="bfd86-110">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bfd86-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="bfd86-111">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="bfd86-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="bfd86-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bfd86-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfd86-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfd86-113">See also</span></span>

- [<span data-ttu-id="bfd86-114">Podstawowe zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bfd86-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
