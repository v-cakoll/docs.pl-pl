---
title: Konstrukcja funkcjonalna (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635759"
---
# <a name="functional-construction-linq-to-xml-c"></a>Konstrukcja funkcjonalna (LINQ to XML)C#()
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia zaawansowany sposób tworzenia elementów XML o nazwie *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna to możliwość tworzenia drzewa XML w pojedynczej instrukcji.  
  
 Istnieje kilka najważniejszych funkcji interfejsu programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], które umożliwiają konstruowanie funkcjonalne:  
  
- Konstruktor <xref:System.Xml.Linq.XElement> ma różne typy argumentów dla zawartości. Na przykład można przekazać inny obiekt <xref:System.Xml.Linq.XElement>, który stanie się elementem podrzędnym. Można przekazać obiekt <xref:System.Xml.Linq.XAttribute>, który stanie się atrybutem elementu. Lub można przekazać każdy inny typ obiektu, który jest konwertowany na ciąg i stanie się zawartością tekstową elementu.  
  
- Konstruktor <xref:System.Xml.Linq.XElement> pobiera tablicę `params` typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora. Dzięki temu można utworzyć element, który ma złożoną zawartość.  
  
- Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie zostanie wyliczona i wszystkie elementy w kolekcji zostaną dodane. Jeśli kolekcja zawiera obiekty <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, każdy element w kolekcji zostanie dodany osobno. Jest to ważne, ponieważ umożliwia przekazywanie wyników zapytania LINQ do konstruktora.  
  
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
  
 Te funkcje umożliwiają również pisanie kodu, który używa wyników zapytań LINQ podczas tworzenia drzewa XML w następujący sposób:  
  
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
  