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
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Tworzenie drzew XML w języku C# (LINQ do XML)
Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w języku C#.  
  
 Aby uzyskać informacje na temat używania wyników <xref:System.Xml.Linq.XElement>zapytań LINQ jako zawartości , zobacz [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Konstruowanie elementów
 Podpisy <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów pozwalają przekazać zawartość elementu lub atrybutu jako argumenty do konstruktora. Ponieważ jeden z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych. Oczywiście każdy z tych elementów podrzędnych może zawierać własne elementy podrzędne. Dla dowolnego elementu można dodać dowolną liczbę atrybutów.  
  
 Podczas <xref:System.Xml.Linq.XNode> dodawania <xref:System.Xml.Linq.XElement>(w tym ) lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma nadrzędnego, obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML. Ostatni przykład w tym temacie pokazuje to.  
  
 Aby utworzyć `contacts` <xref:System.Xml.Linq.XElement>, można użyć następującego kodu:  
  
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
  
 Jeśli wcięte poprawnie, kod do <xref:System.Xml.Linq.XElement> konstruowania obiektów ściśle przypomina strukturę podstawowego XML.  
  
## <a name="xelement-constructors"></a>Konstruktory XElement  
 Klasa <xref:System.Xml.Linq.XElement> używa następujących konstruktorów do konstrukcji funkcjonalnej. Należy pamiętać, że istnieją inne <xref:System.Xml.Linq.XElement>konstruktory dla , ale ponieważ nie są one wykorzystywane do konstrukcji funkcjonalnej nie są wymienione tutaj.  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XElement>plik . Parametr `name` określa nazwę elementu; `content` określa zawartość elementu.|  
|`XElement(XName name)`|Tworzy <xref:System.Xml.Linq.XElement> z <xref:System.Xml.Linq.XName> jego zainicjowane do określonej nazwy.|  
|`XElement(XName name, params object[] content)`|Tworzy <xref:System.Xml.Linq.XElement> z <xref:System.Xml.Linq.XName> jego zainicjowane do określonej nazwy. Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.|  
  
 Parametr `content` jest niezwykle elastyczny. Obsługuje dowolny typ obiektu, który jest <xref:System.Xml.Linq.XElement>prawidłowym elementem podrzędnym pliku . Następujące reguły mają zastosowanie do różnych typów obiektów przekazanych w tym parametrze:  
  
- Ciąg jest dodawany jako zawartość tekstowa.  
  
- An <xref:System.Xml.Linq.XElement> jest dodawany jako element podrzędny.  
  
- An <xref:System.Xml.Linq.XAttribute> jest dodawany jako atrybut.  
  
- An <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>, <xref:System.Xml.Linq.XText> lub jest dodawany jako zawartość podrzędna.  
  
- An <xref:System.Collections.IEnumerable> jest wyliczany, a te reguły są stosowane cyklicznie do wyników.  
  
- Dla każdego innego `ToString` typu jego metoda jest wywoływana, a wynik jest dodawany jako zawartość tekstowa.  
  
### <a name="creating-an-xelement-with-content"></a>Tworzenie elementu XElement z zawartością  
 Można utworzyć, <xref:System.Xml.Linq.XElement> który zawiera prostą zawartość z wywołaniem jednej metody. Aby to zrobić, należy określić zawartość jako drugi parametr, w następujący sposób:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Można przekazać dowolny typ obiektu jako zawartość. Na przykład poniższy kod tworzy element, który zawiera numer zmiennoprzecinkowy jako zawartość:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Numer zmiennoprzecinkowego jest zapakowany i przekazany do konstruktora. Numer w pudełku jest konwertowany na ciąg i używany jako zawartość elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Tworzenie elementu XElement z elementem podrzędnym  
 Jeśli przekażesz wystąpienie <xref:System.Xml.Linq.XElement> klasy dla argumentu zawartości, konstruktor tworzy element z elementem podrzędnym:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Tworzenie elementu XElement z wieloma elementami podrzędowymi  
 Można przekazać w <xref:System.Xml.Linq.XElement> wielu obiektów dla zawartości. Każdy z <xref:System.Xml.Linq.XElement> obiektów jest dołączony jako element podrzędny.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Rozszerzając powyższy przykład, można utworzyć całe drzewo XML w następujący sposób:  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>Tworzenie Elementu XElement za pomocą atrybutu XAttribute
 Jeśli przekażesz wystąpienie <xref:System.Xml.Linq.XAttribute> klasy dla argumentu zawartości, konstruktor tworzy element z atrybutem:

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a>Tworzenie pustego elementu  
 Aby utworzyć <xref:System.Xml.Linq.XElement>pustą, nie przekazuje się żadnej zawartości do konstruktora. Poniższy przykład tworzy pusty element:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Dołączanie a klonowanie  
 Jak wspomniano wcześniej, <xref:System.Xml.Linq.XNode> podczas <xref:System.Xml.Linq.XElement>dodawania (w tym ) lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma nadrzędnego, obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.  

W poniższym przykładzie przedstawiono zachowanie podczas dodawania elementu nadrzędnego do drzewa i po dodaniu elementu bez elementu nadrzędnego do drzewa.

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

## <a name="see-also"></a>Zobacz też

- [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md)
