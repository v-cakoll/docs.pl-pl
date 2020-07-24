---
title: Konstrukcja funkcjonalna (LINQ to XML) (C#)
description: Dowiedz się, w jaki sposób interfejs programowania LINQ to XML umożliwia konstruowanie funkcjonalne, możliwość tworzenia drzewa XML w pojedynczej instrukcji w języku C#.
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103774"
---
# <a name="functional-construction-linq-to-xml-c"></a>Konstrukcja funkcjonalna (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia zaawansowany sposób tworzenia elementów XML o nazwie *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna to możliwość tworzenia drzewa XML w pojedynczej instrukcji.  
  
 Istnieje kilka najważniejszych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, które umożliwiają konstruowanie funkcjonalne:  
  
- <xref:System.Xml.Linq.XElement>Konstruktor ma różne typy argumentów dla zawartości. Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiekt, który stanie się elementem podrzędnym. Można przekazać <xref:System.Xml.Linq.XAttribute> obiekt, który stanie się atrybutem elementu. Lub można przekazać każdy inny typ obiektu, który jest konwertowany na ciąg i stanie się zawartością tekstową elementu.  
  
- <xref:System.Xml.Linq.XElement>Konstruktor pobiera `params` tablicę typu <xref:System.Object> , dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora. Dzięki temu można utworzyć element, który ma złożoną zawartość.  
  
- Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601> , kolekcja w obiekcie jest wyliczana i dodawane są wszystkie elementy w kolekcji. Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> obiekty lub <xref:System.Xml.Linq.XAttribute> , każdy element w kolekcji zostanie dodany osobno. Jest to ważne, ponieważ umożliwia przekazywanie wyników zapytania LINQ do konstruktora.  
  
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
  