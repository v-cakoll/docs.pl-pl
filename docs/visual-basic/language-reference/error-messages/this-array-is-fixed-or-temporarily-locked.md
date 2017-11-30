---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
