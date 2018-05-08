---
title: Nieprawidłowy numer rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 400879ba37c6b3215d9570ca6eb8eaa06edea03b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bad-record-number"></a>Nieprawidłowy numer rekordu
Liczba rekordów w `a FileGet`, `FilePut`, `FileGetObject`, lub `FilePutObject` instrukcja jest mniejsza niż lub równa zero.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź obliczeń używane do generowania numer. Sprawdź pisownię zmiennych, zawierającą numer rekordu lub używana do obliczania liczby rekordów. Nieprawidłowo zapisana nazwa zmiennej jest niejawnie zadeklarowany i zainicjowana na wartość 0, chyba że użyto `Option Explicit On` w module.  
  
## <a name="see-also"></a>Zobacz też  
 [Option Explicit, instrukcja](../../visual-basic/language-reference/statements/option-explicit-statement.md)
