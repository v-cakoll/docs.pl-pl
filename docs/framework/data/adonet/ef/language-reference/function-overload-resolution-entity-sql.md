---
title: Rozpoznanie przeciążenia funkcji (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 517bdb682213deff90a37eafcf32946fef63921f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="function-overload-resolution-entity-sql"></a>Rozpoznanie przeciążenia funkcji (jednostka SQL)
W tym temacie opisano sposób [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje zostaną rozwiązane.  
  
 Tak długo, jak długo mają unikatowe sygnatury można zdefiniować więcej niż jedna funkcja o tej samej nazwie.  
  
 W przypadku, należy zastosować następujące kryteria ustalenie funkcji odwołuje się do niego danego wyrażenia. Te kryteria są stosowane w kolejności. Pierwsze kryterium, która ma zastosowanie tylko do jednej funkcji jest funkcją rozwiązane.  
  
1.  **Liczba parametrów**. Funkcja ma taką samą liczbę parametrów w wyrażeniu.  
  
2.  **Dokładnego dopasowania w typie**. Każdy typ argumentu funkcji dokładnie zgodny z typem parametru lub jest pusty literał.  
  
3.  **Dopasować podtypu**. Każdy typ argumentu funkcji dokładnie odpowiada i jest podtypem typu parametru lub argument jest pusty literał. W przypadku, gdy kilka funkcji różnią się tylko w wymagana liczba podtyp konwersji, funkcja o najmniejszej Liczba konwersji podtyp jest rozwiązany funkcji.  
  
4.  **Odpowiednik typu lub podtypu podwyższania poziomu**. Każdy typ argumentu funkcji dokładnie odpowiada, jest podtyp o lub może być podwyższony do typu parametru lub argument jest pusty literał. Ponownie w zdarzeniu kilka funkcji różnią się jedynie liczby konwersje podtypem i promocjach, funkcja o najmniejszej liczby konwersje podtypem i promocji jest rozwiązany funkcji.  
  
 Jeśli żaden z tych kryteriów spowodować jednej funkcji wybierane wyrażenie wywołania funkcji jest niejednoznaczny.  
  
 Nawet jeśli stosowanie tych reguł można wyodrębnić jednej funkcji, argumenty nadal mogą być niezgodne parametry. Błąd w tym przypadku.  
  
 Funkcje zdefiniowane przez użytkownika definicji wbudowanej funkcji zapytania ma pierwszeństwo, nawet wtedy, gdy istnieje funkcję zdefiniowaną w modelu przy użyciu podpisu lepsze dopasowanie dla funkcji zdefiniowanej przez użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
