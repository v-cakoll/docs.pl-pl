---
title: Praca z globalnymi przestrzeniami nazw (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 80510e370e0a9c7ab27cb5177d9b547ead82715c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350997"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="fadab-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fadab-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="fadab-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="fadab-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="fadab-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span><span class="sxs-lookup"><span data-stu-id="fadab-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="fadab-105">This capability is useful in two situations.</span><span class="sxs-lookup"><span data-stu-id="fadab-105">This capability is useful in two situations.</span></span> <span data-ttu-id="fadab-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span><span class="sxs-lookup"><span data-stu-id="fadab-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="fadab-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span><span class="sxs-lookup"><span data-stu-id="fadab-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="fadab-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span><span class="sxs-lookup"><span data-stu-id="fadab-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="fadab-109">You can declare global namespaces at the project level.</span><span class="sxs-lookup"><span data-stu-id="fadab-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="fadab-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span><span class="sxs-lookup"><span data-stu-id="fadab-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="fadab-111">Finally, you can override global namespaces in an XML literal.</span><span class="sxs-lookup"><span data-stu-id="fadab-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="fadab-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fadab-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="fadab-113">You will see the expanded name in a tooltip.</span><span class="sxs-lookup"><span data-stu-id="fadab-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="fadab-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span><span class="sxs-lookup"><span data-stu-id="fadab-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="fadab-115">Examples of Global Namespaces</span><span class="sxs-lookup"><span data-stu-id="fadab-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="fadab-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span><span class="sxs-lookup"><span data-stu-id="fadab-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fadab-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fadab-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="fadab-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span><span class="sxs-lookup"><span data-stu-id="fadab-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fadab-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fadab-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="fadab-120">Global Namespaces and Embedded Expressions</span><span class="sxs-lookup"><span data-stu-id="fadab-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="fadab-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span><span class="sxs-lookup"><span data-stu-id="fadab-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="fadab-122">The following example declares a default namespace.</span><span class="sxs-lookup"><span data-stu-id="fadab-122">The following example declares a default namespace.</span></span> <span data-ttu-id="fadab-123">It then uses an embedded expression for the `Child` element.</span><span class="sxs-lookup"><span data-stu-id="fadab-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="fadab-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fadab-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="fadab-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span><span class="sxs-lookup"><span data-stu-id="fadab-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="fadab-126">You could re-declare the namespace in the embedded expression, as follows:</span><span class="sxs-lookup"><span data-stu-id="fadab-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="fadab-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fadab-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="fadab-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span><span class="sxs-lookup"><span data-stu-id="fadab-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="fadab-129">With the global default namespace, you can use XML literals without declaring namespaces.</span><span class="sxs-lookup"><span data-stu-id="fadab-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="fadab-130">The resulting XML will be in the globally-declared default namespace.</span><span class="sxs-lookup"><span data-stu-id="fadab-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fadab-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fadab-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="fadab-132">Using Namespaces with XML Properties</span><span class="sxs-lookup"><span data-stu-id="fadab-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="fadab-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span><span class="sxs-lookup"><span data-stu-id="fadab-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="fadab-134">The following example declares an XML tree in a namespace.</span><span class="sxs-lookup"><span data-stu-id="fadab-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="fadab-135">It then prints the count of `Child` elements.</span><span class="sxs-lookup"><span data-stu-id="fadab-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="fadab-136">This example indicates that there are no `Child` elements.</span><span class="sxs-lookup"><span data-stu-id="fadab-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="fadab-137">It produces the following output:</span><span class="sxs-lookup"><span data-stu-id="fadab-137">It produces the following output:</span></span>  
  
```console  
0  
```  
  
 <span data-ttu-id="fadab-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span><span class="sxs-lookup"><span data-stu-id="fadab-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fadab-139">This example indicates that there is one `Child` element.</span><span class="sxs-lookup"><span data-stu-id="fadab-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="fadab-140">It produces the following output:</span><span class="sxs-lookup"><span data-stu-id="fadab-140">It produces the following output:</span></span>  
  
```console  
1  
```  
  
 <span data-ttu-id="fadab-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span><span class="sxs-lookup"><span data-stu-id="fadab-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="fadab-142">XNamespace and Global Namespaces</span><span class="sxs-lookup"><span data-stu-id="fadab-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="fadab-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span><span class="sxs-lookup"><span data-stu-id="fadab-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fadab-144">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fadab-144">This example produces the following output:</span></span>  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="fadab-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fadab-145">See also</span></span>

- [<span data-ttu-id="fadab-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fadab-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
