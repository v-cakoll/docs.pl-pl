---
title: "Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b89b74a6c0393f6a52a0b5c1ddf6f66c505564ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)
W tym temacie opisano typy danych Visual Basic mogą być deklarowane w ramach których innych typów, a co ich poziomy dostępu domyślnie Jeśli nie zostanie określony.  
  
## <a name="declaration-context-levels"></a>Poziomy kontekście deklaracji  
 *Kontekście deklaracji* elementu programowania to region kodu, w którym jest zadeklarowany. Jest to często innego elementu programistycznego, która jest następnie wywoływana *zawierającego element*.  
  
 Poziomy konteksty deklaracji są następujące:  
  
-   *Poziom Namespace* — w pliku źródłowym lub przestrzeni nazw, ale nie w obrębie klasy, struktury, modułu lub interfejsu  
  
-   *Poziom modułu* — w ramach klasy, struktury, modułu lub interfejsu, ale nie w procedurze lub bloku  
  
-   *Poziom procedury* — w ramach procedury lub bloku (takich jak `If` lub `For`)  
  
 W poniższej tabeli przedstawiono domyślne poziomy dostępu dla różnych zadeklarowany element programistyczny, w zależności od ich konteksty deklaracji.  
  
|Zadeklarowany element|Poziom Namespace|Poziom modułu|Poziom procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Zmienna ([Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md))|Niedozwolone|`Private`(`Public` w `Structure`, nie jest dozwolone w `Interface`)|`Public`|  
|Stałe ([Const — instrukcja](../../../visual-basic/language-reference/statements/const-statement.md))|Niedozwolone|`Private`(`Public` w `Structure`, nie jest dozwolone w `Interface`)|`Public`|  
|Wyliczanie ([Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Klasy ([Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Struktury ([struktury instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Moduł ([Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Niedozwolone|Niedozwolone|  
|Interfejs ([Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Procedura ([funkcji instrukcji](../../../visual-basic/language-reference/statements/function-statement.md), [Sub instrukcji](../../../visual-basic/language-reference/statements/sub-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Odwołanie zewnętrzne ([instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Niedozwolone|`Public`(nie są dozwolone w `Interface`)|Niedozwolone|  
|Operator ([operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md))|Niedozwolone|`Public`(nie są dozwolone w `Interface` lub `Module`)|Niedozwolone|  
|Właściwość ([Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Właściwość domyślna ([domyślne](../../../visual-basic/language-reference/modifiers/default.md))|Niedozwolone|`Public`(nie są dozwolone w `Module`)|Niedozwolone|  
|Zdarzenia ([Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Delegat ([Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Niedozwolone|  
  
 Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)  
 [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)
