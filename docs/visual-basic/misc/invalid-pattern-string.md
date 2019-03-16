---
title: Nieprawidłowy ciąg wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: bc2e91060ca1b0e21ea28b0f08febc3e0c54f4f1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027318"
---
# <a name="invalid-pattern-string"></a>Nieprawidłowy ciąg wzorca
Ciągu wzorca określonego w `Like` operacji wyszukiwania jest nieprawidłowy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź prawidłowe znaki listy wyrażeń.  
  
2.  W zakresie wzorzec, upewnij się, że znaku zakresu początkowego jest mniejszy niż końcowy znak zakresu, podobnie jak w `[a-z]`.  
  
3.  W zakresie wzorzec, upewnij się, że nie wielu łączników obok siebie, podobnie jak w `[a--z]`.  
  
4.  Końcowa wzorzec zakresów nawias zamykający.  
  
## <a name="see-also"></a>Zobacz także

- [Like, operator](../../visual-basic/language-reference/operators/like-operator.md)
