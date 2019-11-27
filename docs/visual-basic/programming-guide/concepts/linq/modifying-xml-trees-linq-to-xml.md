---
title: Modyfikowanie drzew XML (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: c946052beb612c087d26e312875b7f7950ceadf5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353171"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to magazyn w pamięci dla drzewa XML. Po załadowaniu lub przeanalizowaniu drzewa XML ze źródła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pozwala modyfikować to drzewo w miejscu, a następnie serializować drzewo, być może zapisać je do pliku lub wysłać do zdalnego serwera.  
  
 W przypadku zmodyfikowania drzewa w miejscu należy użyć niektórych metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Istnieje jednak inne podejście, które służy do generowania nowych drzew z innym kształtem. W zależności od typów zmian, które należy wprowadzić w drzewie XML, i w zależności od rozmiaru drzewa takie podejście może być bardziej niezawodne i prostsze. W pierwszym temacie w tej sekcji porównano te dwa podejścia.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Porównuje modyfikowanie drzewa XML w pamięci z konstrukcją funkcjonalną.|  
|[Dodawanie elementów, atrybutów i węzłów do drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Zawiera informacje na temat dodawania elementów, atrybutów lub węzłów do drzewa XML.|  
|[Modyfikowanie elementów, atrybutów i węzłów w drzewie XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Zawiera informacje o modyfikowaniu istniejących elementów, atrybutów lub węzłów.|  
|[Usuwanie elementów, atrybutów i węzłów z drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Zawiera informacje dotyczące usuwania elementów, atrybutów lub węzłów z drzewa XML.|  
|[Obsługa par nazwa/wartość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Opisuje, jak utrzymywać informacje o aplikacji najlepiej przechowywane jako pary nazwa/wartość, takie jak informacje o konfiguracji lub ustawienia globalne.|  
|[Instrukcje: zmienianie przestrzeni nazw dla całego drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Pokazuje, jak przenieść drzewo XML z jednej przestrzeni nazw do innej.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
