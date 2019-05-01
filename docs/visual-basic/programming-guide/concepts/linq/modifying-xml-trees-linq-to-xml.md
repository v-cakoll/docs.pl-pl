---
title: Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: 4673902880822e6e4ed0bc144aedc2428faa5b69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031801"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest magazyn w pamięci dla drzewa XML. Po ładowania lub analizowania drzewa XML z źródła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia modyfikowanie tego drzewa w miejscu, a następnie serializacji drzewa, może być zapisanie go do pliku i wysyłaniu ich do serwera zdalnego.  
  
 Po zmodyfikowaniu drzewa w miejscu niektórych metod, takich jak używać <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Istnieje jednak inny podejście, które jest użycie konstrukcja funkcjonalna do generowania nowego drzewa za pomocą innego kształtu. W zależności od typów zmian, które należy wprowadzić swoje drzewa XML, a także w zależności od rozmiaru drzewa ta metoda może być bardziej niezawodne i łatwiejsze do opracowywania. Pierwszym temacie w tej sekcji przedstawiono porównanie tych dwóch metod.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Modyfikowanie drzewa XML w pamięci a Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Porównuje modyfikowanie drzewa XML w pamięci, aby konstrukcja funkcjonalna.|  
|[Dodawanie elementów, atrybutów i węzłów do drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Zawiera informacje dotyczące dodawania elementów, atrybutów i węzłów do drzewa XML.|  
|[Modyfikowanie elementów, atrybutów i węzłów w drzewie XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Zawiera informacje dotyczące modyfikowania istniejących elementów, atrybutów lub węzłów.|  
|[Usuwanie elementów, atrybutów i węzłów z drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Zawiera informacje dotyczące usuwania elementów, atrybutów i węzłów z drzewa XML.|  
|[Obsługa pary nazwa/wartość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|W tym artykule opisano, jak zachować informacje o aplikacji, który jest najlepiej pozostawić w postaci par nazwa/wartość, takie jak informacje o konfiguracji lub ustawień globalnych.|  
|[Instrukcje: Zmień Namespace dla całego drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Pokazuje sposób przenoszenia drzewa XML z jednego obszaru nazw do innego.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
