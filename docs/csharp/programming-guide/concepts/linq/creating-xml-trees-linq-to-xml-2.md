---
title: "Tworzenie XML drzewa w języku C# (LINQ do XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2e37ee7cd61058157b9c6c7d37784e215faf900a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Tworzenie XML drzewa w języku C# (LINQ do XML)
Ta sekcja zawiera informacje o tworzeniu drzew XML w języku C#.  
  
 Informacje o korzystaniu z wyników zapytania LINQ jako zawartość <xref:System.Xml.Linq.XElement>, zobacz [funkcjonalności konstrukcji (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Konstruowanie elementów  
 Podpisy <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów umożliwiają przekazywanie zawartości elementu lub atrybutu jako argumenty konstruktora. Ponieważ jeden z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych. Każdy z tych elementów podrzędnych, zawierają własne elementy podrzędne. Dla każdego elementu można dodać dowolną liczbę atrybutów.  
  
 Podczas dodawania <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączyć do drzewa XML. Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, nowej zawartości został sklonowany, a zawartość nowo sklonowanego jest dołączony do drzewa XML. W ostatnim przykładzie w tym temacie pokazano to.  
  
 Aby utworzyć `contacts` <xref:System.Xml.Linq.XElement>, można użyć poniższego kodu:  
  
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
  
 Jeśli poprawnie, wcięcia kodu do skonstruowania <xref:System.Xml.Linq.XElement> obiektów przypomina strukturę podstawowej XML.  
  
## <a name="xelement-constructors"></a>Konstruktory klasy XElement  
 <xref:System.Xml.Linq.XElement> Klasa korzysta z następujących konstruktorów dla konstrukcji funkcjonalności. Należy pamiętać, że niektóre inne konstruktory <xref:System.Xml.Linq.XElement>, ale ponieważ nie są używane do tworzenia funkcjonalności nie są wyświetlane tutaj.  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XElement>. `name` Parametr określa nazwę elementu; `content` określa zawartości elementu.|  
|`XElement(XName name)`|Tworzy <xref:System.Xml.Linq.XElement> z jego <xref:System.Xml.Linq.XName> został zainicjowany w określonej nazwie.|  
|`XElement(XName name, params object[] content)`|Tworzy <xref:System.Xml.Linq.XElement> z jego <xref:System.Xml.Linq.XName> został zainicjowany w określonej nazwie. Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.|  
  
 `content` Parametr jest bardzo elastyczny. Obsługuje ona dowolnego typu obiektu, który jest nieprawidłowym elementem podrzędnym elementu <xref:System.Xml.Linq.XElement>. Różne typy obiektów tego parametru mają zastosowanie następujące reguły:  
  
-   Ciąg jest dodawana jako zawartości tekstowej.  
  
-   <xref:System.Xml.Linq.XElement> Zostanie dodany jako element podrzędny.  
  
-   <xref:System.Xml.Linq.XAttribute> Jest dodawana jako atrybut.  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Lub <xref:System.Xml.Linq.XText> jest dodawana jako zawartość elementu podrzędnego.  
  
-   <xref:System.Collections.IEnumerable> Wyliczeniu, a te zasady są stosowane rekursywnie do wyników.  
  
-   Dla każdego typu jego `ToString` wywołania metody, wynik zostanie dodany jako zawartości tekstowej.  
  
### <a name="creating-an-xelement-with-content"></a>Tworzenie XElement z zawartością  
 Można utworzyć <xref:System.Xml.Linq.XElement> zawierający prostej zawartości przy użyciu wywołania pojedynczej metody. Aby to zrobić, należy określić zawartość jako drugiego parametru w następujący sposób:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Obiekty dowolnego typu można przekazać jako zawartości. Na przykład poniższy kod tworzy element zawierający zmiennoprzecinkową liczby jako zawartość:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Liczba zmiennoprzecinkowa numer jest opakowany i przekazany do konstruktora. Opakowany liczba jest konwertowana na ciąg i używać jako zawartość elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Tworzenie XElement z elementu podrzędnego  
 W przypadku przekazania instancji <xref:System.Xml.Linq.XElement> klasy dla zawartości argumentu konstruktora tworzy element z elementu podrzędnego:  
  
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
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Tworzenie XElement z wielu elementów podrzędnych  
 Można przekazać w liczbie <xref:System.Xml.Linq.XElement> obiektów dla zawartości. Każdy z <xref:System.Xml.Linq.XElement> obiektów jest uwzględniona jako element podrzędny.  
  
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
  
 Rozszerzając w powyższym przykładzie, można utworzyć całe drzewo XML w następujący sposób:  
  
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
  
### <a name="creating-an-empty-element"></a>Tworzenie pustego elementu  
 Aby utworzyć pustą <xref:System.Xml.Linq.XElement>, żadnej zawartości nie są przekazywane do konstruktora. Poniższy przykład tworzy pustego elementu:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Dołączanie programu vs. Klonowania  
 Jak wspomniano wcześniej, podczas dodawania <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączyć do drzewa XML. Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, nowej zawartości został sklonowany, a zawartość nowo sklonowanego jest dołączony do drzewa XML.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
