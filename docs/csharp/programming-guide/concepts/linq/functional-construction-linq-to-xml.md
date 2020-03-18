---
title: Konstrukcja funkcjonalna (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635759"
---
# <a name="functional-construction-linq-to-xml-c"></a>Konstrukcja funkcjonalna (LINQ do XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia potężny sposób tworzenia elementów XML zwanych *konstrukcją funkcjonalną.* Funkcjonalna konstrukcja to możliwość tworzenia drzewa XML w jednej instrukcji.  
  
 Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, które umożliwiają funkcjonalną konstrukcję:  
  
- Konstruktor <xref:System.Xml.Linq.XElement> przyjmuje różne typy argumentów dla zawartości. Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiekt, który staje się elementem podrzędnym. Można przekazać <xref:System.Xml.Linq.XAttribute> obiekt, który staje się atrybutem elementu. Lub można przekazać dowolny inny typ obiektu, który jest konwertowany na ciąg i staje się zawartość tekstową elementu.  
  
- Konstruktor <xref:System.Xml.Linq.XElement> `params` przyjmuje tablicę typu, <xref:System.Object>dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora. Dzięki temu można utworzyć element, który ma złożoną zawartość.  
  
- Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie jest wyliczana, a wszystkie elementy w kolekcji są dodawane. Jeśli kolekcja <xref:System.Xml.Linq.XElement> zawiera <xref:System.Xml.Linq.XAttribute> lub obiektów, każdy element w kolekcji jest dodawany oddzielnie. Jest to ważne, ponieważ umożliwia przekazywanie wyników kwerendy LINQ do konstruktora.  
  
 Te funkcje umożliwiają pisanie kodu w celu utworzenia drzewa XML. Poniżej przedstawiono przykład:  
  
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
  
 Funkcje te umożliwiają również pisanie kodu, który używa wyników kwerend LINQ podczas tworzenia drzewa XML, w następujący sposób:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  