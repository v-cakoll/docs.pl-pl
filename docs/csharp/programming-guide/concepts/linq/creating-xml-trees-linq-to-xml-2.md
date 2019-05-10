---
title: Tworzenie drzew XML w języku C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 00f528bca00b2c2316d949ceb3b6c4bba2499146
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597664"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Tworzenie drzew XML w języku C# (LINQ to XML)
Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w języku C#.  
  
 Informacji o używaniu wyników zapytania LINQ jako zawartość dla <xref:System.Xml.Linq.XElement>, zobacz [konstrukcja funkcjonalna (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Konstruowanie elementów
 Podpisy <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktory pozwalają przekazać zawartość elementu lub atrybutu jako argumenty do konstruktora. Ponieważ w jednym z konstruktorów przyjmuje zmienną liczbę argumentów, można przekazać dowolną liczbę elementów podrzędnych. Oczywiście każda z tych elementów podrzędnych może zawierać własne elementy podrzędne. Dla każdego elementu możesz dodać dowolną liczbę atrybutów.  
  
 Podczas dodawania <xref:System.Xml.Linq.XNode> (w tym <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty, po prostu są dołączone do drzewa XML. Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, nowej zawartości został sklonowany, a nowo sklonowanego zawartości jest dołączony do drzewa XML. Przykład ostatniego, w tym temacie przedstawia to.  
  
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
  
 Jeśli poprawnie, wcięcia kodu do konstruowania <xref:System.Xml.Linq.XElement> obiektów przypomina strukturę podstawowy kod XML.  
  
## <a name="xelement-constructors"></a>Konstruktory klasy XElement  
 <xref:System.Xml.Linq.XElement> Klasa używa następujących konstruktorów konstrukcja funkcjonalna. Należy pamiętać, że niektóre inne konstruktory <xref:System.Xml.Linq.XElement>, ale ponieważ nie są one używane do konstrukcja funkcjonalna są niewymienione w tym miejscu.  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XElement>. `name` Parametr określa nazwę elementu; `content` określa zawartości elementu.|  
|`XElement(XName name)`|Tworzy <xref:System.Xml.Linq.XElement> z jego <xref:System.Xml.Linq.XName> zainicjowany do określonej nazwy.|  
|`XElement(XName name, params object[] content)`|Tworzy <xref:System.Xml.Linq.XElement> z jego <xref:System.Xml.Linq.XName> zainicjowany do określonej nazwy. Atrybuty i/lub elementy podrzędne są tworzone na podstawie zawartości listy parametrów.|  
  
 `content` Parametru jest niezwykle elastyczny. Obsługuje ona dowolnego typu obiektu, który jest prawidłowy element podrzędny <xref:System.Xml.Linq.XElement>. Następujące reguły stosuje się do różnych typów obiektów tego parametru:  
  
- Ciąg jest dodawany jako zawartości tekstowej.  
  
- <xref:System.Xml.Linq.XElement> Jest dodawany jako element podrzędny.  
  
- <xref:System.Xml.Linq.XAttribute> Jest dodawany jako atrybut.  
  
- <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Lub <xref:System.Xml.Linq.XText> jest dodawany jako zawartość elementu podrzędnego.  
  
- <xref:System.Collections.IEnumerable> Są wyliczane, a te zasady są stosowane cyklicznie z wynikami.  
  
- Dla dowolnego typu jego `ToString` wywoływana jest metoda, a wynik jest dodawany jako zawartości tekstowej.  
  
### <a name="creating-an-xelement-with-content"></a>Tworzenie XElement z zawartością  
 Możesz utworzyć <xref:System.Xml.Linq.XElement> zawierający prostej zawartości z pojedynczym wywołaniu metody. Aby to zrobić, należy określić zawartość jako drugi parametr w następujący sposób:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Można przekazać obiekty dowolnego typu jako zawartości. Na przykład, poniższy kod tworzy element, który zawiera zmiennoprzecinkowy numer jako zawartość punktu:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Zmiennoprzecinkowa numer jest zapakowany i przekazany do konstruktora. Spakowany liczba jest konwertowana na ciąg i używany jako zawartość elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Tworzenie XElement za pomocą elementu podrzędnego  
 W przypadku przekazania wystąpienia <xref:System.Xml.Linq.XElement> klasy dla zawartości argumentu konstruktora tworzy element z element podrzędny:  
  
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
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Tworzenie XElement za pomocą wielu podrzędnych elementów  
 Można przekazać wiele <xref:System.Xml.Linq.XElement> obiektów dla zawartości. Każdy z <xref:System.Xml.Linq.XElement> obiektów jest dołączony jako element podrzędny.  
  
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
  
 Rozszerzając powyższego przykładu, można utworzyć całego drzewa XML w następujący sposób:  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>Tworzenie XElement za pomocą XAttribute
 W przypadku przekazania wystąpienia <xref:System.Xml.Linq.XAttribute> klasy dla zawartości argumentu konstruktora tworzy element z atrybutem:

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
 Aby utworzyć pustą <xref:System.Xml.Linq.XElement>, żadnej zawartości nie są przekazywane do konstruktora. Poniższy przykład tworzy pustego elementu:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Dołączanie a klonowania  
 Jak wspomniano wcześniej, podczas dodawania <xref:System.Xml.Linq.XNode> (w tym <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty, po prostu są dołączone do drzewa XML. Jeśli nowa zawartość jest elementem nadrzędnym, a jest częścią innego drzewa XML, Nowa zawartość zostanie sklonowany, a nowo sklonowanego zawartości jest dołączony do drzewa XML.  

Poniższy przykład pokazuje zachowanie podczas dodawania elementu nadrzędnego w drzewie, a podczas dodawania elementu z elementu nadrzędnego na drzewo.

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

- [Tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
