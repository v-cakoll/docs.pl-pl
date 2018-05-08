---
title: Procedura lub funkcja nie jest zdefiniowana
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 58e90d769d5a7f2d88b5c27d1ec7d0d28c8d7b03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Procedura lub funkcja nie jest zdefiniowana
A `Sub` lub `Function` musi być zdefiniowana, aby można było można wywołać. Możliwe przyczyny tego błędu:  
  
-   Błąd pisowni Nazwa procedury.  
  
-   Próba wywołania procedury z innego projektu bez jawnie dodać odwołanie do tego projektu w **odwołania** okno dialogowe.  
  
-   Określanie procedury, która jest niewidoczna dla procedury wywołującej.  
  
-   Deklarowanie procedury biblioteki dołączanej (dynamicznie DLL) systemu Windows lub procedury zasobu kodu Macintosh, który nie jest określony zasób biblioteki lub kodu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że nazwa procedury została wpisana poprawnie.  
  
2.  Znajdź nazwę projektu zawierającego procedury, która ma wywołać w **odwołania** okno dialogowe. Jeśli nie ma, kliknij przycisk **Przeglądaj** przycisk, aby wyszukać. Zaznacz pole wyboru po lewej nazwę projektu, a następnie kliknij przycisk **OK**.  
  
3.  Sprawdź nazwę procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
