---
title: "Konstrukcja funkcjonalności (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a>Konstrukcja funkcjonalności (LINQ do XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]udostępnia zaawansowane metody do tworzenia elementów XML o nazwie *funkcjonalności konstrukcji*. Konstrukcja funkcjonalności jest możliwość tworzenia drzewo XML w jednej instrukcji.  
  
 Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, umożliwiające konstrukcji funkcjonalności:  
  
-   <xref:System.Xml.Linq.XElement> Konstruktor ma różne typy argumentów dla zawartości. Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiektu, który staje się elementu podrzędnego. Można przekazać <xref:System.Xml.Linq.XAttribute> obiektu, który staje się atrybutem elementu. Lub może przekazać inny rodzaj obiektu, który jest konwertowana na ciąg i staje się zawartości tekstowej elementu.  
  
-   <xref:System.Xml.Linq.XElement> Konstruktor pobiera `params` tablicy typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora. Dzięki temu można utworzyć element, który ma zawartość złożoną.  
  
-   Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>wyliczeniu kolekcji w obiekcie i zostaną dodane wszystkie elementy w kolekcji. Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty oddzielnie dodaniu każdego elementu w kolekcji. Jest to ważne, ponieważ dzięki temu można przekazać wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do konstruktora.  
  
 Te funkcje umożliwiają napisać kod, aby utworzyć drzewo XML. Oto przykład:  
  
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
  
 Te funkcje umożliwiają również napisać kod, który używa wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania podczas tworzenia drzewo XML w następujący sposób:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
