---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: f70b984fc493e79d7a83b33236615a3220405786
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516996"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
Ten błąd ma następujące możliwe przyczyny:  
  
-   Za pomocą `ReDim` Aby zmienić liczbę elementów tablicy o stałym rozmiarze.  
  
-   Redimensioning tablic dynamicznych poziom modułu, w którym jeden element został przekazany jako argument do procedury. Jeśli element jest przekazywany, tablica jest zablokowane, aby uniemożliwić cofanie przydziału pamięci dla parametru odwołania w ramach procedury.  
  
-   Próba przypisania wartości do `Variant` zmienną, która zawiera tablicę, ale `Variant` jest obecnie zablokowany.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Utworzyć tablicy oryginalnej dynamiczną, zamiast stałej deklarując ją za pomocą `ReDim` (Jeśli tablica jest zadeklarowana w obrębie procedury), lub deklarując ją bez określania liczby elementów (Jeśli tablica jest zadeklarowana na poziomie modułu.  
  
2.  Ustal, czy naprawdę potrzebujesz przekazać elementu, ponieważ jest ona widoczna w ramach wszystkich procedur w module.  
  
3.  Określić, co blokuje `Variant` i usunięcia go.  
  
## <a name="see-also"></a>Zobacz także
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
