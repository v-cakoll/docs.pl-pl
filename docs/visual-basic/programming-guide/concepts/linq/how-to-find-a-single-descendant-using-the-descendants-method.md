---
title: 'Instrukcje: Znajdź pojedynczego elementu potomnego przy użyciu metody elementów potomnych (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: 24bad2bc6ac121cd2be16933161a38a6a6fcb1e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552453"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="4c27a-102">Instrukcje: Znajdź pojedynczego elementu potomnego przy użyciu metody elementów potomnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c27a-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="4c27a-103">Możesz użyć <xref:System.Xml.Linq.XContainer.Descendants%2A> metodę osi, aby szybko napisać kod, aby znaleźć pojedynczy jednoznacznie o nazwie elementu.</span><span class="sxs-lookup"><span data-stu-id="4c27a-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="4c27a-104">Ta technika jest szczególnie przydatne, gdy chcesz znaleźć określonego obiektu podrzędnego o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4c27a-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="4c27a-105">Można napisać kod, aby przejść do żądanego elementu, ale często jest szybsze i prostsze do pisania kodu za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="4c27a-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c27a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c27a-106">Example</span></span>  
 <span data-ttu-id="4c27a-107">W tym przykładzie użyto <xref:System.Linq.Enumerable.First%2A> standardowego operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="4c27a-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
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
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 <span data-ttu-id="4c27a-108">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4c27a-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="4c27a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c27a-109">Example</span></span>  
 <span data-ttu-id="4c27a-110">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4c27a-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4c27a-111">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4c27a-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
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
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4c27a-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4c27a-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c27a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c27a-113">See also</span></span>
- [<span data-ttu-id="4c27a-114">Podstawowe zapytania (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c27a-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
