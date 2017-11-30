---
title: Praca z globalnej przestrzeni nazw (LINQ do XML) (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 376a6d2dfbca22fb8efc6395f478839d716e14d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="1c227-102">Praca z globalnej przestrzeni nazw (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c227-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="1c227-103">Jednym z kluczowych funkcji usługi literałów XML w Visual Basic jest możliwość deklarowanie przestrzeni nazw XML za pomocą `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1c227-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="1c227-104">Tej funkcji można zadeklarować przestrzeni nazw XML, który zawiera prefiks lub mogą zadeklarować domyślnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="1c227-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="1c227-105">Ta funkcja jest przydatna w dwóch sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="1c227-105">This capability is useful in two situations.</span></span> <span data-ttu-id="1c227-106">Najpierw przestrzenie nazw zadeklarowany w literałach XML nie jest przenoszone do wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="1c227-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="1c227-107">Deklarowanie globalnej przestrzeni nazw zmniejsza ilość pracy, które należy wykonać, aby użyć wyrażenia osadzone z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="1c227-108">Po drugie należy zadeklarować globalnej przestrzeni nazw do przestrzeni nazw za pomocą właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="1c227-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="1c227-109">Można zadeklarować globalnej przestrzeni nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="1c227-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="1c227-110">Można również zadeklarować globalnej przestrzeni nazw na poziomie modułu, co zastępuje globalnej przestrzeni nazw poziom projektu.</span><span class="sxs-lookup"><span data-stu-id="1c227-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="1c227-111">Na koniec można zastąpić globalnej przestrzeni nazw w postaci literału ciągu XML.</span><span class="sxs-lookup"><span data-stu-id="1c227-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="1c227-112">Podczas korzystania z literały XML i właściwości XML, znajdujących się w zadeklarowany globalnie przestrzeni nazw, można zobaczyć rozwiniętą nazwą literały XML i właściwości, ustawiając kursor nad nimi w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c227-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="1c227-113">Zobaczysz rozwiniętą nazwą w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="1c227-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="1c227-114">Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada za pomocą globalnej przestrzeni nazw `GetXmlNamespace` metody.</span><span class="sxs-lookup"><span data-stu-id="1c227-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="1c227-115">Przykłady globalnej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="1c227-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="1c227-116">Poniższy przykład deklaruje globalne domyślnej przestrzeni nazw przy użyciu `Imports` instrukcji, a następnie używa literał XML zainicjować <xref:System.Xml.Linq.XElement> obiektu w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1c227-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1c227-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1c227-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="1c227-118">Poniższy przykład deklaruje globalnej przestrzeni nazw z prefiksem, a następnie używa literał XML można zainicjować elementu:</span><span class="sxs-lookup"><span data-stu-id="1c227-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1c227-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1c227-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="1c227-120">Globalne obszary nazw i wyrażenia osadzone</span><span class="sxs-lookup"><span data-stu-id="1c227-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="1c227-121">Przestrzenie nazw, które są zadeklarowane w literałach XML nie przenoszone do wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="1c227-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="1c227-122">Poniższy przykład deklaruje domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-122">The following example declares a default namespace.</span></span> <span data-ttu-id="1c227-123">Następnie używa wyrażenia osadzonego dla `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c227-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="1c227-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1c227-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="1c227-125">Jak widać, wynikowy kod XML zawiera deklarację domyślnej przestrzeni nazw, aby `Child` elementu jest bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="1c227-126">Można ponownie zadeklarować przestrzeni nazw w wyrażenia osadzonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1c227-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="1c227-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1c227-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="1c227-128">Jest to jednak bardziej skomplikowane niż korzystanie z domyślnej globalnej przestrzeni nazw, która jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="1c227-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="1c227-129">W domyślnej globalnej przestrzeni nazw możesz użyć literałów XML bez deklarowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="1c227-130">Wynikowy kod XML będzie mieć zadeklarowany globalnie domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="1c227-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1c227-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="1c227-132">Używanie przestrzeni nazw z właściwości XML</span><span class="sxs-lookup"><span data-stu-id="1c227-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="1c227-133">Jeśli pracujesz z drzewa XML, który znajduje się w przestrzeni nazw, a następnie użyj właściwości XML, konieczne jest użycie globalnej przestrzeni nazw, aby właściwości XML będzie również poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="1c227-134">Poniższy przykład deklaruje drzewo XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c227-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="1c227-135">Następnie drukuje liczbę `Child` elementów.</span><span class="sxs-lookup"><span data-stu-id="1c227-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="1c227-136">W tym przykładzie wskazuje, że nie istnieją żadne `Child` elementów.</span><span class="sxs-lookup"><span data-stu-id="1c227-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="1c227-137">Tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1c227-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="1c227-138">Jeśli jednak deklarowaniu globalne domyślnej przestrzeni nazw, następnie zarówno literał XML i właściwości XML znajdują się w domyślnej globalnej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1c227-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="1c227-139">W tym przykładzie oznacza, że istnieje jeden `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c227-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="1c227-140">Tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1c227-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="1c227-141">Przy deklarowaniu globalnej przestrzeni nazw z prefiksem można używać prefiksu literały XML i właściwości XML:</span><span class="sxs-lookup"><span data-stu-id="1c227-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="1c227-142">XNamespace i globalnej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="1c227-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="1c227-143">Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiektu przy użyciu `GetXmlNamespace` metody:</span><span class="sxs-lookup"><span data-stu-id="1c227-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="1c227-144">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1c227-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c227-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c227-145">See Also</span></span>  
 [<span data-ttu-id="1c227-146">Praca z przestrzeni nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c227-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
