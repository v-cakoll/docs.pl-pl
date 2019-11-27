---
title: Konstrukcja funkcjonalna (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 6366c7781372d34e15d62f81a5ceae8ff4ccda2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353466"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia zaawansowany sposób tworzenia elementów XML o nazwie *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna to możliwość tworzenia drzewa XML w pojedynczej instrukcji.  
  
 Istnieje kilka najważniejszych funkcji interfejsu programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], które umożliwiają konstruowanie funkcjonalne:  
  
- Konstruktor <xref:System.Xml.Linq.XElement> ma różne typy argumentów dla zawartości. Na przykład można przekazać inny obiekt <xref:System.Xml.Linq.XElement>, który stanie się elementem podrzędnym. Można przekazać obiekt <xref:System.Xml.Linq.XAttribute>, który stanie się atrybutem elementu. Lub można przekazać każdy inny typ obiektu, który jest konwertowany na ciąg i stanie się zawartością tekstową elementu.  
  
- Konstruktor <xref:System.Xml.Linq.XElement> pobiera tablicę `params` typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora. Dzięki temu można utworzyć element, który ma złożoną zawartość.  
  
- Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie zostanie wyliczona i wszystkie elementy w kolekcji zostaną dodane. Jeśli kolekcja zawiera obiekty <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, każdy element w kolekcji zostanie dodany osobno. Jest to ważne, ponieważ umożliwia przekazywanie wyników zapytania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do konstruktora.  
  
 Oto przykład:  
  
 Te funkcje umożliwiają pisanie kodu przy użyciu literałów XML w celu utworzenia drzewa XML, a także do pisania kodu, który używa wyników zapytań [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] podczas tworzenia drzewa XML:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
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
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
