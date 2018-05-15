---
title: Tworzenie XML drzewa w języku C# (LINQ do XML)
ms.date: 07/20/2015
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4fcd0c14970dd4aabe4d51335f9a0a0a991ef019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="c4fe6-102">Tworzenie XML drzewa w języku C# (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="c4fe6-102">Creating XML Trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="c4fe6-103">Ta sekcja zawiera informacje o tworzeniu drzew XML w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="c4fe6-104">Informacje o korzystaniu z wyników zapytania LINQ jako zawartość <xref:System.Xml.Linq.XElement>, zobacz [funkcjonalności konstrukcji (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c4fe6-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="c4fe6-105">Konstruowanie elementów</span><span class="sxs-lookup"><span data-stu-id="c4fe6-105">Constructing Elements</span></span>  
 <span data-ttu-id="c4fe6-106">Podpisy <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów umożliwiają przekazywanie zawartości elementu lub atrybutu jako argumenty konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="c4fe6-107">Ponieważ jeden z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="c4fe6-108">Każdy z tych elementów podrzędnych, zawierają własne elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="c4fe6-109">Dla każdego elementu można dodać dowolną liczbę atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="c4fe6-110">Podczas dodawania <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączyć do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="c4fe6-111">Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, nowej zawartości został sklonowany, a zawartość nowo sklonowanego jest dołączony do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="c4fe6-112">W ostatnim przykładzie w tym temacie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="c4fe6-113">Aby utworzyć `contacts` <xref:System.Xml.Linq.XElement>, można użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="c4fe6-114">Jeśli poprawnie, wcięcia kodu do skonstruowania <xref:System.Xml.Linq.XElement> obiektów przypomina strukturę podstawowej XML.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="c4fe6-115">Konstruktory klasy XElement</span><span class="sxs-lookup"><span data-stu-id="c4fe6-115">XElement Constructors</span></span>  
 <span data-ttu-id="c4fe6-116"><xref:System.Xml.Linq.XElement> Klasa korzysta z następujących konstruktorów dla konstrukcji funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="c4fe6-117">Należy pamiętać, że niektóre inne konstruktory <xref:System.Xml.Linq.XElement>, ale ponieważ nie są używane do tworzenia funkcjonalności nie są wyświetlane tutaj.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="c4fe6-118">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="c4fe6-118">Constructor</span></span>|<span data-ttu-id="c4fe6-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c4fe6-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="c4fe6-120">Tworzy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c4fe6-121">`name` Parametr określa nazwę elementu; `content` określa zawartości elementu.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="c4fe6-122">Tworzy <xref:System.Xml.Linq.XElement> z jego <xref:System.Xml.Linq.XName> został zainicjowany w określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="c4fe6-123">Tworzy <xref:System.Xml.Linq.XElement> z jego <xref:System.Xml.Linq.XName> został zainicjowany w określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="c4fe6-124">Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="c4fe6-125">`content` Parametr jest bardzo elastyczny.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="c4fe6-126">Obsługuje ona dowolnego typu obiektu, który jest nieprawidłowym elementem podrzędnym elementu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c4fe6-127">Różne typy obiektów tego parametru mają zastosowanie następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
-   <span data-ttu-id="c4fe6-128">Ciąg jest dodawana jako zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-128">A string is added as text content.</span></span>  
  
-   <span data-ttu-id="c4fe6-129"><xref:System.Xml.Linq.XElement> Zostanie dodany jako element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
-   <span data-ttu-id="c4fe6-130"><xref:System.Xml.Linq.XAttribute> Jest dodawana jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
-   <span data-ttu-id="c4fe6-131"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Lub <xref:System.Xml.Linq.XText> jest dodawana jako zawartość elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
-   <span data-ttu-id="c4fe6-132"><xref:System.Collections.IEnumerable> Wyliczeniu, a te zasady są stosowane rekursywnie do wyników.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
-   <span data-ttu-id="c4fe6-133">Dla każdego typu jego `ToString` wywołania metody, wynik zostanie dodany jako zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="c4fe6-134">Tworzenie XElement z zawartością</span><span class="sxs-lookup"><span data-stu-id="c4fe6-134">Creating an XElement with Content</span></span>  
 <span data-ttu-id="c4fe6-135">Można utworzyć <xref:System.Xml.Linq.XElement> zawierający prostej zawartości przy użyciu wywołania pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="c4fe6-136">Aby to zrobić, należy określić zawartość jako drugiego parametru w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="c4fe6-137">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="c4fe6-138">Obiekty dowolnego typu można przekazać jako zawartości.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="c4fe6-139">Na przykład poniższy kod tworzy element zawierający zmiennoprzecinkową liczby jako zawartość:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="c4fe6-140">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="c4fe6-141">Liczba zmiennoprzecinkowa numer jest opakowany i przekazany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="c4fe6-142">Opakowany liczba jest konwertowana na ciąg i używać jako zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="c4fe6-143">Tworzenie XElement z elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="c4fe6-143">Creating an XElement with a Child Element</span></span>  
 <span data-ttu-id="c4fe6-144">W przypadku przekazania instancji <xref:System.Xml.Linq.XElement> klasy dla zawartości argumentu konstruktora tworzy element z elementu podrzędnego:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="c4fe6-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="c4fe6-146">Tworzenie XElement z wielu elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="c4fe6-146">Creating an XElement with Multiple Child Elements</span></span>  
 <span data-ttu-id="c4fe6-147">Można przekazać w liczbie <xref:System.Xml.Linq.XElement> obiektów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="c4fe6-148">Każdy z <xref:System.Xml.Linq.XElement> obiektów jest uwzględniona jako element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="c4fe6-149">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="c4fe6-150">Rozszerzając w powyższym przykładzie, można utworzyć całe drzewo XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="c4fe6-151">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-151">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="c4fe6-152">Tworzenie pustego elementu</span><span class="sxs-lookup"><span data-stu-id="c4fe6-152">Creating an Empty Element</span></span>  
 <span data-ttu-id="c4fe6-153">Aby utworzyć pustą <xref:System.Xml.Linq.XElement>, żadnej zawartości nie są przekazywane do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-153">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="c4fe6-154">Poniższy przykład tworzy pustego elementu:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-154">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="c4fe6-155">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-155">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="c4fe6-156">Dołączanie programu vs. Klonowania</span><span class="sxs-lookup"><span data-stu-id="c4fe6-156">Attaching vs. Cloning</span></span>  
 <span data-ttu-id="c4fe6-157">Jak wspomniano wcześniej, podczas dodawania <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączyć do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-157">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="c4fe6-158">Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, nowej zawartości został sklonowany, a zawartość nowo sklonowanego jest dołączony do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c4fe6-158">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="c4fe6-159">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4fe6-159">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4fe6-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4fe6-160">See Also</span></span>  
 [<span data-ttu-id="c4fe6-161">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c4fe6-161">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
