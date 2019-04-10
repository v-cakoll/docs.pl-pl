---
title: Rozpoznanie przeciążenia funkcji (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302520"
---
# <a name="function-overload-resolution-entity-sql"></a>Rozpoznanie przeciążenia funkcji (jednostka SQL)
W tym temacie opisano sposób [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje zostaną rozwiązane.  
  
 Tak długo, jak funkcje mają unikatowe podpisy, można zdefiniować więcej niż jednej funkcji o takiej samej nazwie.  
  
 W przypadku następujących kryteriów musi można zastosować w taki sposób, aby ustalić, funkcja, która odwołuje się do podanego wyrażenia. Te kryteria są stosowane w kolejności. Kryterium, która dotyczy tylko jednej funkcji jest funkcją rozwiązania.  
  
1. **Liczba parametrów**. Funkcja ma taką samą liczbę parametrów określonych w wyrażeniu.  
  
2. **Dokładne dopasowanie typu**. Każdy typ argumentu funkcji dokładnie zgodny z typem parametru lub jest literałem o wartości null.  
  
3. **Dopasować wybrany parametr podtypu**. Każdy typ argumentu funkcji dokładnie pasuje do lub jest podtyp typu parametru lub argument jest literał o wartości null. W przypadku, gdy kilka funkcji różnią się tylko w wymagana liczba podtyp konwersji, funkcja o najmniejszej liczby konwersje podtyp jest funkcją rozwiązania.  
  
4. **Dopasowanie w promocji typu lub podtypu**. Typ każdego argumentu funkcji dokładnie odpowiada, jest typem podrzędne lub może być podwyższony do typu parametru lub argument jest literał o wartości null. Ponownie w zdarzeniu, które kilka funkcji różnią się jedynie liczby konwersje podtyp i promocje, funkcja o najmniejszej liczby konwersje podtyp i promocji jest funkcją rozwiązania.  
  
 Jeśli żadne z tych kryteriów wynik w jednej funkcji jest zaznaczone, wyrażenie wywołania funkcji jest niejednoznaczny.  
  
 Nawet wtedy, gdy przy użyciu tych reguł można wyodrębnić jednej funkcji, argumenty nadal mogą być niezgodne parametry. Błąd w tym przypadku.  
  
 Funkcje zdefiniowane przez użytkownika definicji wbudowanej funkcji zapytanie ma pierwszeństwo, nawet wtedy, gdy istnieje funkcji definiowanych przez model, za pomocą podpisu, który lepiej pasuje do funkcji zdefiniowanej przez użytkownika.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Przegląd języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
