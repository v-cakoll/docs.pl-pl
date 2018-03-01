---
title: Procedura lub funkcja nie jest zdefiniowana
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Error — typy](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
