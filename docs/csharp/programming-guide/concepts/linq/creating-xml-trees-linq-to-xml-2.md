---
title: Tworzenie drzew XML w języku C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: a77171ebbc07e54f6988fb97aff197b4c6d31721
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594624"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="44cea-102">Tworzenie drzew XML w C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="44cea-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="44cea-103">Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w C#programie.</span><span class="sxs-lookup"><span data-stu-id="44cea-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="44cea-104">Aby uzyskać informacje o używaniu wyników zapytań LINQ jako zawartości dla elementu <xref:System.Xml.Linq.XElement>, zobacz [funkcjonalne konstruowanie (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="44cea-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="44cea-105">Konstruowanie elementów</span><span class="sxs-lookup"><span data-stu-id="44cea-105">Constructing elements</span></span>
 <span data-ttu-id="44cea-106">Sygnatury <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów umożliwiają przekazanie zawartości elementu lub atrybutu jako argumenty do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="44cea-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="44cea-107">Ponieważ jeden z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="44cea-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="44cea-108">Oczywiście każdy z tych elementów podrzędnych może zawierać własne elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="44cea-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="44cea-109">Dla dowolnego elementu można dodać dowolną liczbę atrybutów.</span><span class="sxs-lookup"><span data-stu-id="44cea-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="44cea-110">W przypadku <xref:System.Xml.Linq.XNode> dodawania ( <xref:System.Xml.Linq.XElement>w tym <xref:System.Xml.Linq.XAttribute> ) lub obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="44cea-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="44cea-111">Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, Nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="44cea-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="44cea-112">W ostatnim przykładzie w tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="44cea-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="44cea-113">Aby utworzyć obiekt `contacts` <xref:System.Xml.Linq.XElement>, można użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="44cea-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="44cea-114">W przypadku poprawnego wcięcia kod do konstruowania <xref:System.Xml.Linq.XElement> obiektów ściśle przypomina strukturę bazowego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="44cea-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="44cea-115">Konstruktory XElement</span><span class="sxs-lookup"><span data-stu-id="44cea-115">XElement constructors</span></span>  
 <span data-ttu-id="44cea-116"><xref:System.Xml.Linq.XElement> Klasa używa następujących konstruktorów dla konstrukcji funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="44cea-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="44cea-117">Należy zauważyć, że istnieją inne konstruktory <xref:System.Xml.Linq.XElement>dla, ale ponieważ nie są one używane do konstruowania funkcjonalnego, nie są wyświetlane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="44cea-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="44cea-118">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="44cea-118">Constructor</span></span>|<span data-ttu-id="44cea-119">Opis</span><span class="sxs-lookup"><span data-stu-id="44cea-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="44cea-120"><xref:System.Xml.Linq.XElement>Tworzy.</span><span class="sxs-lookup"><span data-stu-id="44cea-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="44cea-121">`name` Parametr określa nazwę elementu; `content` określa zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="44cea-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="44cea-122">Tworzy obiekt <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> z zainicjowanym do określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="44cea-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="44cea-123">Tworzy obiekt <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> z zainicjowanym do określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="44cea-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="44cea-124">Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="44cea-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="44cea-125">`content` Parametr jest niezwykle elastyczny.</span><span class="sxs-lookup"><span data-stu-id="44cea-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="44cea-126">Obsługuje wszystkie typy obiektów, które są prawidłowymi elementami podrzędnymi <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="44cea-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="44cea-127">Następujące reguły mają zastosowanie do różnych typów obiektów przekazaną w tym parametrze:</span><span class="sxs-lookup"><span data-stu-id="44cea-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="44cea-128">Ciąg jest dodawany jako zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="44cea-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="44cea-129"><xref:System.Xml.Linq.XElement> Jest dodawany jako element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="44cea-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="44cea-130">Element <xref:System.Xml.Linq.XAttribute> jest dodawany jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="44cea-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="44cea-131">Element <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, lub<xref:System.Xml.Linq.XText> jest dodawany jako zawartość podrzędna.</span><span class="sxs-lookup"><span data-stu-id="44cea-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="44cea-132">Wyliczenie <xref:System.Collections.IEnumerable> jest wyliczane i reguły są stosowane cyklicznie do wyników.</span><span class="sxs-lookup"><span data-stu-id="44cea-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="44cea-133">Dla każdego innego typu `ToString` Metoda jest wywoływana, a wynik jest dodawany jako zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="44cea-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="44cea-134">Tworzenie XElement z zawartością</span><span class="sxs-lookup"><span data-stu-id="44cea-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="44cea-135">Można utworzyć obiekt <xref:System.Xml.Linq.XElement> zawierający prostą zawartość z pojedynczym wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="44cea-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="44cea-136">W tym celu określ zawartość jako drugi parametr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="44cea-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="44cea-137">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="44cea-138">Każdy typ obiektu można przekazać jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="44cea-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="44cea-139">Na przykład poniższy kod tworzy element, który zawiera liczbę zmiennoprzecinkową jako zawartość:</span><span class="sxs-lookup"><span data-stu-id="44cea-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="44cea-140">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="44cea-141">Liczba zmiennoprzecinkowa jest opakowana i przenoszona do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="44cea-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="44cea-142">Numer opakowany jest konwertowany na ciąg i używany jako zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="44cea-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="44cea-143">Tworzenie XElement z elementem podrzędnym</span><span class="sxs-lookup"><span data-stu-id="44cea-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="44cea-144">Jeśli przekazujesz wystąpienie <xref:System.Xml.Linq.XElement> klasy dla argumentu Content, Konstruktor tworzy element z elementem podrzędnym:</span><span class="sxs-lookup"><span data-stu-id="44cea-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="44cea-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="44cea-146">Tworzenie XElement z wieloma elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="44cea-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="44cea-147">Można przekazać wiele <xref:System.Xml.Linq.XElement> obiektów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="44cea-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="44cea-148"><xref:System.Xml.Linq.XElement> Każdy obiekt jest dołączony jako element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="44cea-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="44cea-149">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="44cea-150">Rozszerzając powyższy przykład, można utworzyć całe drzewo XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="44cea-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="44cea-151">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-151">This example produces the following output:</span></span>  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="44cea-152">Tworzenie XElement przy użyciu XAttribute</span><span class="sxs-lookup"><span data-stu-id="44cea-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="44cea-153">Jeśli przekazujesz wystąpienie <xref:System.Xml.Linq.XAttribute> klasy dla argumentu Content, Konstruktor tworzy element z atrybutem:</span><span class="sxs-lookup"><span data-stu-id="44cea-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="44cea-154">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```   

### <a name="creating-an-empty-element"></a><span data-ttu-id="44cea-155">Tworzenie pustego elementu</span><span class="sxs-lookup"><span data-stu-id="44cea-155">Creating an empty element</span></span>  
 <span data-ttu-id="44cea-156">Aby utworzyć pustą <xref:System.Xml.Linq.XElement>, nie należy przekazywać żadnej zawartości do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="44cea-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="44cea-157">Poniższy przykład tworzy pusty element:</span><span class="sxs-lookup"><span data-stu-id="44cea-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="44cea-158">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="44cea-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="44cea-159">Dołączanie a klonowanie</span><span class="sxs-lookup"><span data-stu-id="44cea-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="44cea-160">Jak wspomniano wcześniej, podczas <xref:System.Xml.Linq.XNode> dodawania ( <xref:System.Xml.Linq.XElement>w tym <xref:System.Xml.Linq.XAttribute> ) lub obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="44cea-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="44cea-161">Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, Nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="44cea-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="44cea-162">Poniższy przykład ilustruje zachowanie po dodaniu elementu nadrzędnego do drzewa i po dodaniu elementu z elementem nadrzędnym do drzewa.</span><span class="sxs-lookup"><span data-stu-id="44cea-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

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

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a><span data-ttu-id="44cea-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44cea-163">See also</span></span>

- [<span data-ttu-id="44cea-164">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="44cea-164">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
