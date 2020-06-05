---
title: Modyfikowanie drzew XML (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: 3402188c4e34ef81bad41ed49f9236b4fb7c47ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406888"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest magazynem w pamięci dla drzewa XML. Po załadowaniu lub przeanalizowaniu drzewa XML ze źródła program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pozwala modyfikować to drzewo w miejscu, a następnie serializować drzewo, co może spowodować zapisanie go do pliku lub wysłanie go do zdalnego serwera.  
  
 W przypadku zmodyfikowania drzewa na miejscu należy użyć pewnych metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A> .  
  
 Istnieje jednak inne podejście, które służy do generowania nowych drzew z innym kształtem. W zależności od typów zmian, które należy wprowadzić w drzewie XML, i w zależności od rozmiaru drzewa takie podejście może być bardziej niezawodne i prostsze. W pierwszym temacie w tej sekcji porównano te dwa podejścia.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md)|Porównuje modyfikowanie drzewa XML w pamięci z konstrukcją funkcjonalną.|  
|[Dodawanie elementów, atrybutów i węzłów do drzewa XML (Visual Basic)](adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Zawiera informacje na temat dodawania elementów, atrybutów lub węzłów do drzewa XML.|  
|[Modyfikowanie elementów, atrybutów i węzłów w drzewie XML](modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Zawiera informacje o modyfikowaniu istniejących elementów, atrybutów lub węzłów.|  
|[Usuwanie elementów, atrybutów i węzłów z drzewa XML (Visual Basic)](removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Zawiera informacje dotyczące usuwania elementów, atrybutów lub węzłów z drzewa XML.|  
|[Obsługa par nazwa/wartość (Visual Basic)](maintaining-name-value-pairs.md)|Opisuje, jak utrzymywać informacje o aplikacji najlepiej przechowywane jako pary nazwa/wartość, takie jak informacje o konfiguracji lub ustawienia globalne.|  
|[Instrukcje: zmienianie przestrzeni nazw dla całego drzewa XML (Visual Basic)](how-to-change-the-namespace-for-an-entire-xml-tree.md)|Pokazuje, jak przenieść drzewo XML z jednej przestrzeni nazw do innej.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)
