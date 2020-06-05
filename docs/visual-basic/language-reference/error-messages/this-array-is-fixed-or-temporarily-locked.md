---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 4a86460104b6c4d9d6791e60f6f377cec0030425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363036"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
Ten błąd ma następujące możliwe przyczyny:  
  
- Przy użyciu `ReDim` programu można zmienić liczbę elementów tablicy o stałym rozmiarze.  
  
- Przewymiarowanie dynamicznej tablicy na poziomie modułu, w którym jeden element został przekazano jako argument do procedury. Jeśli element jest zakończony, tablica jest zablokowana, aby zapobiec cofnięciu przydziału pamięci dla parametru Reference w ramach procedury.  
  
- Podjęto próbę przypisania wartości do `Variant` zmiennej zawierającej tablicę, ale `Variant` jest ona obecnie zablokowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Oznacz oryginalną tablicę zamiast naprawić, deklarując ją z `ReDim` (jeśli tablica jest zadeklarowana w ramach procedury) lub deklarując ją bez określania liczby elementów (jeśli tablica jest zadeklarowana na poziomie modułu.  
  
2. Ustal, czy naprawdę potrzebujesz przekazać element, ponieważ jest on widoczny we wszystkich procedurach w module.  
  
3. Określ, co blokuje `Variant` i zaradzenia.  
  
## <a name="see-also"></a>Zobacz też

- [Tablice](../../programming-guide/language-features/arrays/index.md)
