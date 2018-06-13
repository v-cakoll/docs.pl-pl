---
title: Modyfikowanie drzew XML (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: e524088ac6ccde3a46de7547379eb82f9760fd57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645619"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modyfikowanie drzew XML (LINQ do XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest magazynu w pamięci dla drzewa XML. Po załadować lub przeanalizować drzewo XML ze źródła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia modyfikowanie tego drzewa w miejscu, a następnie serializować drzewa, być może zapisać go do pliku lub wysłanie ich do serwera zdalnego.  
  
 Po zmodyfikowaniu drzewa w miejscu niektórych metod, takich jak używać <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Istnieje jednak innym rozwiązaniem, który jest używany konstrukcji funkcjonalności do generowania nowego drzewa z innego kształtu. W zależności od typów zmian, które należy wprowadzić swoje drzewo XML, a w zależności od wielkości drzewa ta metoda może być bardziej niezawodne i łatwiejsze do opracowywania. Pierwszym temacie w tej sekcji porównanie tych dwóch metod.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Modyfikowanie drzewa XML w pamięci a Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Porównuje modyfikowanie drzewo XML w pamięci do budowy funkcjonalności.|  
|[Dodawanie elementy, atrybuty i węzłów do drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Zawiera informacje o dodawaniu elementy, atrybuty lub węzłów do drzewa XML.|  
|[Modyfikowanie elementów, atrybutów i węzłów w drzewie XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Zawiera informacje dotyczące modyfikowania istniejące elementy, atrybuty lub węzłów.|  
|[Usuwanie elementy, atrybuty i węzły z drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Zawiera informacje o usuwaniu elementy, atrybuty lub węzłów w drzewie XML.|  
|[Obsługa pary nazwa/wartość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Zawiera opis sposobu obsługi informacji o aplikacji, która najlepiej jest przechowywane jako pary nazwa/wartość, takie jak informacje o konfiguracji lub ustawień globalnych.|  
|[Porady: Zmienianie Namespace drzewo całego XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Przedstawia sposób przenoszenia drzewa XML z jednej przestrzeni nazw do innego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
