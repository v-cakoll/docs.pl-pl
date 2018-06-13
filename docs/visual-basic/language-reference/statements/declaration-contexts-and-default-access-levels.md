---
title: Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: b30b1068fe662d5f0318a1712dc4690b79bd739d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605449"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)
W tym temacie opisano, które typy danych Visual Basic mogą być deklarowane w ramach których innych typów, a także jakie są ich domyślne poziomy dostępu, jeśli nie zostały określone.  
  
## <a name="declaration-context-levels"></a>Poziomy kontekście deklaracji  
 *Kontekście deklaracji* elementu programowania to region kodu, w którym jest zadeklarowany. Jest to często innego elementu programistycznego, która jest następnie wywoływana *zawierającego element*.  
  
 Poziomy konteksty deklaracji są następujące:  
  
-   *Poziom Namespace* — w pliku źródłowym lub przestrzeni nazw, ale nie w obrębie klasy, struktury, modułu lub interfejsu  
  
-   *Poziom modułu* — w ramach klasy, struktury, modułu lub interfejsu, ale nie w procedurze lub bloku  
  
-   *Poziom procedury* — w ramach procedury lub bloku (takich jak `If` lub `For`)  
  
 W poniższej tabeli przedstawiono domyślne poziomy dostępu dla różnych zadeklarowany element programistyczny, w zależności od ich konteksty deklaracji.  
  
|Zadeklarowany element|Poziom Namespace|Poziom modułu|Poziom procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Zmienna ([Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md))|Niedozwolone|`Private` (`Public` w `Structure`, nie jest dozwolone w `Interface`)|`Public`|  
|Stałe ([Const — instrukcja](../../../visual-basic/language-reference/statements/const-statement.md))|Niedozwolone|`Private` (`Public` w `Structure`, nie jest dozwolone w `Interface`)|`Public`|  
|Wyliczanie ([Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Klasy ([Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Struktury ([struktury instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Moduł ([Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Niedozwolone|Niedozwolone|  
|Interfejs ([Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Procedura ([funkcji instrukcji](../../../visual-basic/language-reference/statements/function-statement.md), [Sub instrukcji](../../../visual-basic/language-reference/statements/sub-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Odwołanie zewnętrzne ([instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Niedozwolone|`Public` (nie są dozwolone w `Interface`)|Niedozwolone|  
|Operator ([operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md))|Niedozwolone|`Public` (nie są dozwolone w `Interface` lub `Module`)|Niedozwolone|  
|Właściwość ([Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Właściwość domyślna ([domyślne](../../../visual-basic/language-reference/modifiers/default.md))|Niedozwolone|`Public` (nie są dozwolone w `Module`)|Niedozwolone|  
|Zdarzenia ([Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Delegat ([Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Niedozwolone|  
  
 Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)
