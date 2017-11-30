---
title: Modyfikowanie drzew XML (LINQ do XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8cf3ffabeb7c3caa5f0e3e38fb6f69551ce791b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a>Modyfikowanie drzew XML (LINQ do XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest magazynu w pamięci dla drzewa XML. Po załadować lub przeanalizować drzewo XML ze źródła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia modyfikowanie tego drzewa w miejscu, a następnie serializować drzewa, być może zapisać go do pliku lub wysłanie ich do serwera zdalnego.  
  
 Po zmodyfikowaniu drzewa w miejscu niektórych metod, takich jak używać <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Istnieje jednak innym rozwiązaniem, który jest używany konstrukcji funkcjonalności do generowania nowego drzewa z innego kształtu. W zależności od typów zmian, które należy wprowadzić swoje drzewo XML, a w zależności od wielkości drzewa ta metoda może być bardziej niezawodne i łatwiejsze do opracowywania. Pierwszym temacie w tej sekcji porównanie tych dwóch metod.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|Porównuje modyfikowanie drzewo XML w pamięci do budowy funkcjonalności.|  
|[Dodawanie elementy, atrybuty i węzłów do drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Zawiera informacje o dodawaniu elementy, atrybuty lub węzłów do drzewa XML.|  
|[Modyfikowanie elementy, atrybuty i węzłów w drzewie XML](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Zawiera informacje dotyczące modyfikowania istniejące elementy, atrybuty lub węzłów.|  
|[Usuwanie elementy, atrybuty i węzły z drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Zawiera informacje o usuwaniu elementy, atrybuty lub węzłów w drzewie XML.|  
|[Obsługa pary nazwa/wartość (C#)](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Zawiera opis sposobu obsługi informacji o aplikacji, która najlepiej jest przechowywane jako pary nazwa/wartość, takie jak informacje o konfiguracji lub ustawień globalnych.|  
|[Porady: Zmienianie Namespace drzewo całego XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Przedstawia sposób przenoszenia drzewa XML z jednej przestrzeni nazw do innego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
