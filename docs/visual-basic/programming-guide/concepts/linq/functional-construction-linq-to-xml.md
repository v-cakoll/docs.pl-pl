---
title: Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: a942d4a0fa4c33cf4699c5825ea05403bdfce48f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618320"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia zaawansowany sposób tworzyć elementy XML o nazwie *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna jest możliwość tworzenia drzewa XML w pojedynczej instrukcji.  
  
 Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejs programowania, które umożliwiają konstrukcja funkcjonalna:  
  
- <xref:System.Xml.Linq.XElement> Konstruktor przyjmuje różne typy argumentów dla zawartości. Na przykład, można przekazać inny <xref:System.Xml.Linq.XElement> obiektu, który staje się nie zawiera elementu podrzędnego. Możesz przekazać <xref:System.Xml.Linq.XAttribute> obiektu, który staje się atrybut elementu. Lub możesz przekazać inny rodzaj obiektu, który jest konwertowany na ciąg i staje się zawartością tekstową elementu.  
  
- <xref:System.Xml.Linq.XElement> Konstruktor przyjmuje `params` tablicy typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora. Dzięki temu można utworzyć elementu, który ma zawartość złożoną.  
  
- Jeśli obiekt implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, są wyliczane kolekcji w obiekcie, a wszystkie elementy w kolekcji są dodawane. Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiektów, każdy element w kolekcji zostanie dodany osobno. Jest to ważne, ponieważ dzięki temu można przekazać wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do konstruktora.  
  
 Oto przykład:  
  
 Te funkcje umożliwiają pisanie kodu przy użyciu literałów XML, tworzenie drzewa XML, a także napisać kod, który używa wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania podczas tworzenia drzewa XML:  
  
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
