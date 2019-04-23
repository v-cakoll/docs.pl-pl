---
title: Nieprawidłowy ciąg wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298685"
---
# <a name="invalid-pattern-string"></a>Nieprawidłowy ciąg wzorca
Ciągu wzorca określonego w `Like` operacji wyszukiwania jest nieprawidłowy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź prawidłowe znaki listy wyrażeń.  
  
2. W zakresie wzorzec, upewnij się, że znaku zakresu początkowego jest mniejszy niż końcowy znak zakresu, podobnie jak w `[a-z]`.  
  
3. W zakresie wzorzec, upewnij się, że nie wielu łączników obok siebie, podobnie jak w `[a--z]`.  
  
4. Końcowa wzorzec zakresów nawias zamykający.  
  
## <a name="see-also"></a>Zobacz także

- [Like, operator](../../visual-basic/language-reference/operators/like-operator.md)
