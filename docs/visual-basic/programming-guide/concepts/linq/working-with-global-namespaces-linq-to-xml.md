---
title: Praca z globalnymi przestrzeniami nazw (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 9aab6f7175c905fcb3e82829f131f52b3d9368ac
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710385"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="e5e3a-102">Praca z globalnymi przestrzeniami nazw (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e5e3a-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="e5e3a-103">Jedną z najważniejszych funkcji literałów XML w Visual Basic jest możliwość deklarowania przestrzeni nazw XML przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="e5e3a-104">Korzystając z tej funkcji, można zadeklarować przestrzeń nazw XML, która używa prefiksu lub można zadeklarować domyślną przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="e5e3a-105">Ta funkcja jest przydatna w dwóch sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-105">This capability is useful in two situations.</span></span> <span data-ttu-id="e5e3a-106">Po pierwsze obszary nazw zadeklarowane w literałach XML nie są przenoszone do wyrażeń osadzonych.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="e5e3a-107">Deklarowanie globalnych przestrzeni nazw zmniejsza ilość pracy, którą trzeba wykonać, aby korzystać z osadzonych wyrażeń z przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="e5e3a-108">Po drugie należy zadeklarować globalne przestrzenie nazw w celu używania przestrzeni nazw z właściwościami XML.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="e5e3a-109">Można zadeklarować globalne przestrzenie nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="e5e3a-110">Można również zadeklarować globalne przestrzenie nazw na poziomie modułu, który zastępuje globalne przestrzenie nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="e5e3a-111">Na koniec można przesłonić globalne przestrzenie nazw w literale XML.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="e5e3a-112">W przypadku używania literałów XML lub właściwości XML, które znajdują się w globalnie zadeklarowanych przestrzeniach nazw, można zobaczyć rozwinięte nazwy literałów XML lub właściwości przez umieszczenie ich w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="e5e3a-113">Rozwinięta nazwa zostanie wyświetlona w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="e5e3a-114">Można uzyskać <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do globalnej przestrzeni nazw `GetXmlNamespace` za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="e5e3a-115">Przykłady globalnych przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="e5e3a-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="e5e3a-116">Poniższy przykład deklaruje domyślną globalną przestrzeń nazw przy użyciu `Imports` instrukcji, a następnie używa literału XML do <xref:System.Xml.Linq.XElement> inicjowania obiektu w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e5e3a-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="e5e3a-118">Poniższy przykład deklaruje globalną przestrzeń nazw z prefiksem, a następnie używa literału XML do zainicjowania elementu:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e5e3a-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="e5e3a-120">Globalne przestrzenie nazw i wyrażenia osadzone</span><span class="sxs-lookup"><span data-stu-id="e5e3a-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="e5e3a-121">Przestrzenie nazw, które są zadeklarowane w literałach XML, nie są przenoszone do wyrażeń osadzonych.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="e5e3a-122">Poniższy przykład deklaruje domyślną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-122">The following example declares a default namespace.</span></span> <span data-ttu-id="e5e3a-123">Następnie używa osadzonego wyrażenia dla `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="e5e3a-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="e5e3a-125">Jak widać, otrzymany kod XML zawiera deklarację domyślnej przestrzeni nazw, tak aby `Child` element nie był w żadnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="e5e3a-126">Można ponownie zadeklarować przestrzeń nazw w wyrażeniu osadzonym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="e5e3a-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="e5e3a-128">Jednak jest to bardziej skomplikowany sposób użycia niż Globalna domyślna przestrzeń nazw, która jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="e5e3a-129">Przy użyciu globalnej domyślnej przestrzeni nazw można używać literałów XML bez deklarowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="e5e3a-130">Otrzymany kod XML będzie w globalnie zadeklarowanej przestrzeni nazw default.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="e5e3a-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="e5e3a-132">Używanie przestrzeni nazw z właściwościami XML</span><span class="sxs-lookup"><span data-stu-id="e5e3a-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="e5e3a-133">Jeśli pracujesz z drzewem XML, który znajduje się w przestrzeni nazw, i używasz właściwości XML, należy użyć globalnej przestrzeni nazw, aby właściwości XML również znajdować się w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="e5e3a-134">Poniższy przykład deklaruje drzewo XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="e5e3a-135">Następnie drukuje liczbę `Child` elementów.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="e5e3a-136">Ten przykład wskazuje, że nie ma `Child` żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="e5e3a-137">Generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="e5e3a-138">Jeśli jednak zostanie zadeklarowana Domyślna globalna przestrzeń nazw, wówczas zarówno literał XML, jak i Właściwość XML znajdują się w domyślnej globalnej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="e5e3a-139">Ten przykład wskazuje, że istnieje jeden `Child` element.</span><span class="sxs-lookup"><span data-stu-id="e5e3a-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="e5e3a-140">Generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="e5e3a-141">Jeśli zadeklarujesz globalną przestrzeń nazw, która ma prefiks, można użyć prefiksu dla obu literałów XML i właściwości XML:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="e5e3a-142">XNamespace i globalne przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="e5e3a-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="e5e3a-143">Można uzyskać <xref:System.Xml.Linq.XNamespace> obiekt za `GetXmlNamespace` pomocą metody:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="e5e3a-144">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e5e3a-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5e3a-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5e3a-145">See also</span></span>

- [<span data-ttu-id="e5e3a-146">Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5e3a-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
