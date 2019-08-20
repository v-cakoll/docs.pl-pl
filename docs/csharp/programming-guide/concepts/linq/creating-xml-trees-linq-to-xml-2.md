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
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Tworzenie drzew XML w C# (LINQ to XML)
Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w C#programie.  
  
 Aby uzyskać informacje o używaniu wyników zapytań LINQ jako zawartości dla elementu <xref:System.Xml.Linq.XElement>, zobacz [funkcjonalne konstruowanie (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Konstruowanie elementów
 Sygnatury <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów umożliwiają przekazanie zawartości elementu lub atrybutu jako argumenty do konstruktora. Ponieważ jeden z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych. Oczywiście każdy z tych elementów podrzędnych może zawierać własne elementy podrzędne. Dla dowolnego elementu można dodać dowolną liczbę atrybutów.  
  
 W przypadku <xref:System.Xml.Linq.XNode> dodawania ( <xref:System.Xml.Linq.XElement>w tym <xref:System.Xml.Linq.XAttribute> ) lub obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, Nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML. W ostatnim przykładzie w tym temacie pokazano, jak to zrobić.  
  
 Aby utworzyć obiekt `contacts` <xref:System.Xml.Linq.XElement>, można użyć następującego kodu:  
  
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
  
 W przypadku poprawnego wcięcia kod do konstruowania <xref:System.Xml.Linq.XElement> obiektów ściśle przypomina strukturę bazowego kodu XML.  
  
## <a name="xelement-constructors"></a>Konstruktory XElement  
 <xref:System.Xml.Linq.XElement> Klasa używa następujących konstruktorów dla konstrukcji funkcjonalnej. Należy zauważyć, że istnieją inne konstruktory <xref:System.Xml.Linq.XElement>dla, ale ponieważ nie są one używane do konstruowania funkcjonalnego, nie są wyświetlane w tym miejscu.  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<xref:System.Xml.Linq.XElement>Tworzy. `name` Parametr określa nazwę elementu; `content` określa zawartość elementu.|  
|`XElement(XName name)`|Tworzy obiekt <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> z zainicjowanym do określonej nazwy.|  
|`XElement(XName name, params object[] content)`|Tworzy obiekt <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> z zainicjowanym do określonej nazwy. Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.|  
  
 `content` Parametr jest niezwykle elastyczny. Obsługuje wszystkie typy obiektów, które są prawidłowymi elementami podrzędnymi <xref:System.Xml.Linq.XElement>. Następujące reguły mają zastosowanie do różnych typów obiektów przekazaną w tym parametrze:  
  
- Ciąg jest dodawany jako zawartość tekstowa.  
  
- <xref:System.Xml.Linq.XElement> Jest dodawany jako element podrzędny.  
  
- Element <xref:System.Xml.Linq.XAttribute> jest dodawany jako atrybut.  
  
- Element <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, lub<xref:System.Xml.Linq.XText> jest dodawany jako zawartość podrzędna.  
  
- Wyliczenie <xref:System.Collections.IEnumerable> jest wyliczane i reguły są stosowane cyklicznie do wyników.  
  
- Dla każdego innego typu `ToString` Metoda jest wywoływana, a wynik jest dodawany jako zawartość tekstowa.  
  
### <a name="creating-an-xelement-with-content"></a>Tworzenie XElement z zawartością  
 Można utworzyć obiekt <xref:System.Xml.Linq.XElement> zawierający prostą zawartość z pojedynczym wywołaniem metody. W tym celu określ zawartość jako drugi parametr w następujący sposób:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Każdy typ obiektu można przekazać jako zawartość. Na przykład poniższy kod tworzy element, który zawiera liczbę zmiennoprzecinkową jako zawartość:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Liczba zmiennoprzecinkowa jest opakowana i przenoszona do konstruktora. Numer opakowany jest konwertowany na ciąg i używany jako zawartość elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Tworzenie XElement z elementem podrzędnym  
 Jeśli przekazujesz wystąpienie <xref:System.Xml.Linq.XElement> klasy dla argumentu Content, Konstruktor tworzy element z elementem podrzędnym:  
  
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
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Tworzenie XElement z wieloma elementami podrzędnymi  
 Można przekazać wiele <xref:System.Xml.Linq.XElement> obiektów dla zawartości. <xref:System.Xml.Linq.XElement> Każdy obiekt jest dołączony jako element podrzędny.  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>Tworzenie XElement przy użyciu XAttribute
 Jeśli przekazujesz wystąpienie <xref:System.Xml.Linq.XAttribute> klasy dla argumentu Content, Konstruktor tworzy element z atrybutem:

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
 Aby utworzyć pustą <xref:System.Xml.Linq.XElement>, nie należy przekazywać żadnej zawartości do konstruktora. Poniższy przykład tworzy pusty element:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Dołączanie a klonowanie  
 Jak wspomniano wcześniej, podczas <xref:System.Xml.Linq.XNode> dodawania ( <xref:System.Xml.Linq.XElement>w tym <xref:System.Xml.Linq.XAttribute> ) lub obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, Nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.  

Poniższy przykład ilustruje zachowanie po dodaniu elementu nadrzędnego do drzewa i po dodaniu elementu z elementem nadrzędnym do drzewa.

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

## <a name="see-also"></a>Zobacz także

- [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md)
