---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350789"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
Ten błąd ma następujące możliwe przyczyny:  
  
- Przy użyciu `ReDim` zmienić liczbę elementów tablicy o stałym rozmiarze.  
  
- Przewymiarowanie dynamicznej tablicy na poziomie modułu, w którym jeden element został przekazano jako argument do procedury. Jeśli element jest zakończony, tablica jest zablokowana, aby zapobiec cofnięciu przydziału pamięci dla parametru Reference w ramach procedury.  
  
- Podjęto próbę przypisania wartości do zmiennej `Variant` zawierającej tablicę, ale `Variant` jest obecnie zablokowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zamiast naprawiać oryginalną tablicę, należy ją zadeklarować przy użyciu `ReDim` (jeśli tablica jest zadeklarowana w ramach procedury) lub przez zadeklarowanie jej bez określenia liczby elementów (jeśli tablica jest zadeklarowana na poziomie modułu.  
  
2. Ustal, czy naprawdę potrzebujesz przekazać element, ponieważ jest on widoczny we wszystkich procedurach w module.  
  
3. Określ, co blokuje `Variant` i je naprawić.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
