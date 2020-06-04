---
title: Nieprawidłowy ciąg wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402216"
---
# <a name="invalid-pattern-string"></a>Nieprawidłowy ciąg wzorca
Ciąg wzorca określony w `Like` operacji wyszukiwania jest nieprawidłowy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Przejrzyj prawidłowe znaki dla wyrażeń listy.  
  
2. W zakresie wzorców upewnij się, że znak zakresu początkowego jest mniejszy niż znak zakresu końcowego, jak w `[a-z]` .  
  
3. W zakresie wzorców upewnij się, że nie ma kilku łączników obok siebie, jak w `[a--z]` .  
  
4. Końcowe zakresy wzorców z nawiasem zamykającym.  
  
## <a name="see-also"></a>Zobacz też

- [Like — Operator](../language-reference/operators/like-operator.md)
