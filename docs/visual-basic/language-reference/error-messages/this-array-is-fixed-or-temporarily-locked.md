---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
Ten błąd ma następujące możliwe przyczyny:  
  
-   Przy użyciu `ReDim` Aby zmienić liczbę elementów w tablicy o ustalonym rozmiarze.  
  
-   Redimensioning poziom modułu dynamicznego tablicy, w której jeden element został przekazany jako argument do procedury. Jeśli element zostanie przekazany, tablicy jest zablokowany w celu uniemożliwienia cofanie przydziału pamięci dla parametru odwołania w ramach procedury.  
  
-   Przypisanie wartości do prób `Variant` zmienną, która zawiera tablicę, ale `Variant` jest obecnie zablokowany.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Ustawić dynamiczny, zamiast stałej ona z tablicy oryginalnej `ReDim` (Jeśli tablica jest zadeklarowany w procedurze,) lub przez zadeklarowanie go bez określania liczby elementów (Jeśli tablica jest zadeklarowane na poziomie modułu.  
  
2.  Ustal, czy naprawdę musisz przekazać elementu, ponieważ nie jest widoczna w ramach wszystkich procedur w module.  
  
3.  Określić, co jest blokowanie `Variant` i naprawienia go.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
