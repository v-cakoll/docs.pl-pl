---
title: Tworzenie drzew XML w języku C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4794e4fe019b30d8f2acb3eb255bb77ba2f7f290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169548"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="f87e4-102">Tworzenie drzew XML w języku C# (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="f87e4-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="f87e4-103">Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w języku C#.</span><span class="sxs-lookup"><span data-stu-id="f87e4-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="f87e4-104">Aby uzyskać informacje na temat używania wyników <xref:System.Xml.Linq.XElement>zapytań LINQ jako zawartości , zobacz [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f87e4-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="f87e4-105">Konstruowanie elementów</span><span class="sxs-lookup"><span data-stu-id="f87e4-105">Constructing elements</span></span>
 <span data-ttu-id="f87e4-106">Podpisy <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów pozwalają przekazać zawartość elementu lub atrybutu jako argumenty do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f87e4-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="f87e4-107">Ponieważ jeden z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f87e4-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="f87e4-108">Oczywiście każdy z tych elementów podrzędnych może zawierać własne elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f87e4-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="f87e4-109">Dla dowolnego elementu można dodać dowolną liczbę atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f87e4-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="f87e4-110">Podczas <xref:System.Xml.Linq.XNode> dodawania <xref:System.Xml.Linq.XElement>(w tym ) lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma nadrzędnego, obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f87e4-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="f87e4-111">Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f87e4-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="f87e4-112">Ostatni przykład w tym temacie pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="f87e4-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="f87e4-113">Aby utworzyć `contacts` <xref:System.Xml.Linq.XElement>, można użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="f87e4-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="f87e4-114">Jeśli wcięte poprawnie, kod do <xref:System.Xml.Linq.XElement> konstruowania obiektów ściśle przypomina strukturę podstawowego XML.</span><span class="sxs-lookup"><span data-stu-id="f87e4-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="f87e4-115">Konstruktory XElement</span><span class="sxs-lookup"><span data-stu-id="f87e4-115">XElement constructors</span></span>  
 <span data-ttu-id="f87e4-116">Klasa <xref:System.Xml.Linq.XElement> używa następujących konstruktorów do konstrukcji funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="f87e4-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="f87e4-117">Należy pamiętać, że istnieją inne <xref:System.Xml.Linq.XElement>konstruktory dla , ale ponieważ nie są one wykorzystywane do konstrukcji funkcjonalnej nie są wymienione tutaj.</span><span class="sxs-lookup"><span data-stu-id="f87e4-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="f87e4-118">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="f87e4-118">Constructor</span></span>|<span data-ttu-id="f87e4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f87e4-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="f87e4-120">Tworzy <xref:System.Xml.Linq.XElement>plik .</span><span class="sxs-lookup"><span data-stu-id="f87e4-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f87e4-121">Parametr `name` określa nazwę elementu; `content` określa zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="f87e4-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="f87e4-122">Tworzy <xref:System.Xml.Linq.XElement> z <xref:System.Xml.Linq.XName> jego zainicjowane do określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f87e4-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="f87e4-123">Tworzy <xref:System.Xml.Linq.XElement> z <xref:System.Xml.Linq.XName> jego zainicjowane do określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f87e4-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="f87e4-124">Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f87e4-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="f87e4-125">Parametr `content` jest niezwykle elastyczny.</span><span class="sxs-lookup"><span data-stu-id="f87e4-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="f87e4-126">Obsługuje dowolny typ obiektu, który jest <xref:System.Xml.Linq.XElement>prawidłowym elementem podrzędnym pliku .</span><span class="sxs-lookup"><span data-stu-id="f87e4-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f87e4-127">Następujące reguły mają zastosowanie do różnych typów obiektów przekazanych w tym parametrze:</span><span class="sxs-lookup"><span data-stu-id="f87e4-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="f87e4-128">Ciąg jest dodawany jako zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="f87e4-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="f87e4-129">An <xref:System.Xml.Linq.XElement> jest dodawany jako element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="f87e4-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="f87e4-130">An <xref:System.Xml.Linq.XAttribute> jest dodawany jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="f87e4-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="f87e4-131">An <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>, <xref:System.Xml.Linq.XText> lub jest dodawany jako zawartość podrzędna.</span><span class="sxs-lookup"><span data-stu-id="f87e4-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="f87e4-132">An <xref:System.Collections.IEnumerable> jest wyliczany, a te reguły są stosowane cyklicznie do wyników.</span><span class="sxs-lookup"><span data-stu-id="f87e4-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="f87e4-133">Dla każdego innego `ToString` typu jego metoda jest wywoływana, a wynik jest dodawany jako zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="f87e4-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="f87e4-134">Tworzenie elementu XElement z zawartością</span><span class="sxs-lookup"><span data-stu-id="f87e4-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="f87e4-135">Można utworzyć, <xref:System.Xml.Linq.XElement> który zawiera prostą zawartość z wywołaniem jednej metody.</span><span class="sxs-lookup"><span data-stu-id="f87e4-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="f87e4-136">Aby to zrobić, należy określić zawartość jako drugi parametr, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f87e4-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="f87e4-137">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="f87e4-138">Można przekazać dowolny typ obiektu jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="f87e4-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="f87e4-139">Na przykład poniższy kod tworzy element, który zawiera numer zmiennoprzecinkowy jako zawartość:</span><span class="sxs-lookup"><span data-stu-id="f87e4-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="f87e4-140">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="f87e4-141">Numer zmiennoprzecinkowego jest zapakowany i przekazany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f87e4-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="f87e4-142">Numer w pudełku jest konwertowany na ciąg i używany jako zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="f87e4-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="f87e4-143">Tworzenie elementu XElement z elementem podrzędnym</span><span class="sxs-lookup"><span data-stu-id="f87e4-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="f87e4-144">Jeśli przekażesz wystąpienie <xref:System.Xml.Linq.XElement> klasy dla argumentu zawartości, konstruktor tworzy element z elementem podrzędnym:</span><span class="sxs-lookup"><span data-stu-id="f87e4-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="f87e4-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="f87e4-146">Tworzenie elementu XElement z wieloma elementami podrzędowymi</span><span class="sxs-lookup"><span data-stu-id="f87e4-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="f87e4-147">Można przekazać w <xref:System.Xml.Linq.XElement> wielu obiektów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="f87e4-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="f87e4-148">Każdy z <xref:System.Xml.Linq.XElement> obiektów jest dołączony jako element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="f87e4-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="f87e4-149">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="f87e4-150">Rozszerzając powyższy przykład, można utworzyć całe drzewo XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f87e4-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f87e4-151">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-151">This example produces the following output:</span></span>  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="f87e4-152">Tworzenie Elementu XElement za pomocą atrybutu XAttribute</span><span class="sxs-lookup"><span data-stu-id="f87e4-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="f87e4-153">Jeśli przekażesz wystąpienie <xref:System.Xml.Linq.XAttribute> klasy dla argumentu zawartości, konstruktor tworzy element z atrybutem:</span><span class="sxs-lookup"><span data-stu-id="f87e4-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="f87e4-154">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="f87e4-155">Tworzenie pustego elementu</span><span class="sxs-lookup"><span data-stu-id="f87e4-155">Creating an empty element</span></span>  
 <span data-ttu-id="f87e4-156">Aby utworzyć <xref:System.Xml.Linq.XElement>pustą, nie przekazuje się żadnej zawartości do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f87e4-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="f87e4-157">Poniższy przykład tworzy pusty element:</span><span class="sxs-lookup"><span data-stu-id="f87e4-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="f87e4-158">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f87e4-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="f87e4-159">Dołączanie a klonowanie</span><span class="sxs-lookup"><span data-stu-id="f87e4-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="f87e4-160">Jak wspomniano wcześniej, <xref:System.Xml.Linq.XNode> podczas <xref:System.Xml.Linq.XElement>dodawania (w tym ) lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma nadrzędnego, obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f87e4-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="f87e4-161">Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f87e4-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="f87e4-162">W poniższym przykładzie przedstawiono zachowanie podczas dodawania elementu nadrzędnego do drzewa i po dodaniu elementu bez elementu nadrzędnego do drzewa.</span><span class="sxs-lookup"><span data-stu-id="f87e4-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f87e4-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f87e4-163">See also</span></span>

- [<span data-ttu-id="f87e4-164">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f87e4-164">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
