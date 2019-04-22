---
title: Praca z globalnymi przestrzeniami nazw (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: d8e74e949815d36f06f522460cc31ca6c3ccabb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827383"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="7754a-102">Praca z globalnymi przestrzeniami nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7754a-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="7754a-103">Jedną z kluczowych funkcji literałów XML w Visual Basic jest możliwość zadeklarować przestrzeni nazw XML przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7754a-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="7754a-104">Dzięki tej funkcji można zadeklarować przestrzeni nazw XML, który używa prefiksu lub można zadeklarować domyślnej przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="7754a-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="7754a-105">Ta możliwość jest przydatna w dwóch sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="7754a-105">This capability is useful in two situations.</span></span> <span data-ttu-id="7754a-106">Po pierwsze przestrzenie nazw zadeklarowanych w literałach XML nie jest przenoszone do wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="7754a-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="7754a-107">Deklarowanie globalnymi przestrzeniami nazw zmniejsza ilość pracy, które należy wykonać wyrażenia osadzone za pomocą przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="7754a-108">Po drugie należy zadeklarować globalnymi przestrzeniami nazw, aby można było używać przestrzeni nazw za pomocą właściwości XML.</span><span class="sxs-lookup"><span data-stu-id="7754a-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="7754a-109">Można zadeklarować globalnymi przestrzeniami nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="7754a-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="7754a-110">Można również zadeklarować globalnej przestrzeni nazw na poziom modułu, który zastępuje globalnymi przestrzeniami nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="7754a-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="7754a-111">Na koniec można zastąpić globalnej przestrzeni nazw w literał XML.</span><span class="sxs-lookup"><span data-stu-id="7754a-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="7754a-112">Korzystając z literały XML i właściwości XML, które znajdują się w przestrzeni nazw z globalnie zadeklarowane, widać rozwiniętej nazwy w literałach XML i właściwości, umieszczając kursor myszy nad nimi w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7754a-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="7754a-113">Zobaczysz rozwiniętą nazwę w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="7754a-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="7754a-114">Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do globalnej przestrzeni nazw za pomocą `GetXmlNamespace` metody.</span><span class="sxs-lookup"><span data-stu-id="7754a-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="7754a-115">Przykłady globalnymi przestrzeniami nazw</span><span class="sxs-lookup"><span data-stu-id="7754a-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="7754a-116">Poniższy przykład deklaruje globalnej domyślnej przestrzeni nazw za pomocą `Imports` instrukcji, a następnie używa literał XML można zainicjować <xref:System.Xml.Linq.XElement> obiektów w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="7754a-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7754a-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="7754a-118">Poniższy przykład deklaruje globalnej przestrzeni nazw z prefiksem, a następnie używa literał XML, aby zainicjować element:</span><span class="sxs-lookup"><span data-stu-id="7754a-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7754a-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="7754a-120">Globalne przestrzenie nazw i wyrażenia osadzone</span><span class="sxs-lookup"><span data-stu-id="7754a-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="7754a-121">Przestrzenie nazw, które są zadeklarowane w literałach XML nie przeniosą się do wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="7754a-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="7754a-122">Poniższy przykład deklaruje domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-122">The following example declares a default namespace.</span></span> <span data-ttu-id="7754a-123">Następnie używa wyrażenia osadzone dla `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="7754a-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="7754a-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="7754a-125">Jak widać, wynikowy kod XML zawiera deklarację domyślnej przestrzeni nazw, aby `Child` element znajduje się w żadnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="7754a-126">Można ponownie zadeklarować przestrzeni nazw w wyrażeniu osadzonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7754a-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="7754a-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="7754a-128">To bardziej skomplikowane niż korzystanie z domyślnej globalnej przestrzeni nazw, który jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="7754a-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="7754a-129">Przy użyciu domyślnej globalnej przestrzeni nazw możesz użyć literałów XML bez deklarowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="7754a-130">Wynikowy kod XML będzie mieć globalnie zadeklarowane domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="7754a-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="7754a-132">Używanie przestrzeni nazw za pomocą właściwości XML</span><span class="sxs-lookup"><span data-stu-id="7754a-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="7754a-133">Jeśli pracujesz z drzewa XML, który znajduje się w przestrzeni nazw i korzystać z właściwości XML, następnie należy użyć globalnej przestrzeni nazw, aby właściwości XML będzie również poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="7754a-134">Poniższy przykład deklaruje drzewa XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7754a-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="7754a-135">Następnie wyświetla liczbę `Child` elementów.</span><span class="sxs-lookup"><span data-stu-id="7754a-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="7754a-136">W tym przykładzie wskazuje, że nie istnieją żadne `Child` elementów.</span><span class="sxs-lookup"><span data-stu-id="7754a-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="7754a-137">Generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="7754a-138">Jeśli jednak zadeklarować globalnych domyślny obszar nazw, następnie literał XML i właściwości XML znajdują się w globalnej przestrzeni nazw z domyślnej:</span><span class="sxs-lookup"><span data-stu-id="7754a-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="7754a-139">W tym przykładzie wskazuje, że istnieje jeden `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="7754a-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="7754a-140">Generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="7754a-141">Jeśli zadeklarujesz globalnej przestrzeni nazw, który zawiera prefiks służy prefiks dla literały XML i właściwości XML:</span><span class="sxs-lookup"><span data-stu-id="7754a-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="7754a-142">XNamespace i globalnej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="7754a-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="7754a-143">Możesz uzyskać <xref:System.Xml.Linq.XNamespace> obiektu za pomocą `GetXmlNamespace` metody:</span><span class="sxs-lookup"><span data-stu-id="7754a-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="7754a-144">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7754a-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="7754a-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7754a-145">See also</span></span>

- [<span data-ttu-id="7754a-146">Praca z przestrzeniami nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7754a-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
