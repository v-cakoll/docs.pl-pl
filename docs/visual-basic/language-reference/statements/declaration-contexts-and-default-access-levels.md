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
ms.openlocfilehash: 05c2d6420526b660ead2f50eba7feb6b20524705
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623942"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)
W tym temacie opisano, które typy danych Visual Basic mogą być deklarowane w ramach których innych typów, a także jakie są ich domyślne poziomy dostępu, jeśli nie zostały określone.  
  
## <a name="declaration-context-levels"></a>Deklaracja kontekst poziomów  
 *Kontekst deklaracji* elementu programowania jest to region, kod, w którym jest zdeklarowana. Jest to często innego elementu programistycznego, który jest następnie wywoływana *zawierającego element*.  
  
 Poziomy kontekst deklaracji są następujące:  
  
- *Poziom Namespace* — w pliku źródłowym lub przestrzeni nazw, ale nie w obrębie klasy, struktury, modułu lub interfejsu  
  
- *Poziom modułu* — w ramach klasy, struktury, modułu lub interfejs, ale nie w obrębie procedurą lub blokiem  
  
- *Poziom procedury* — w ramach procedurą lub blokiem (takie jak `If` lub `For`)  
  
 W poniższej tabeli przedstawiono domyślne poziomy dostępu dla różnych zadeklarowany element programistyczny, w zależności od ich kontekst deklaracji.  
  
|Zadeklarowanych elementów|Poziom Namespace|Poziom modułu|Poziom procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Zmienna ([Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md))|Niedozwolone|`Private` (`Public` w `Structure`, jest to niedozwolone w `Interface`)|`Public`|  
|Stałe ([Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md))|Niedozwolone|`Private` (`Public` w `Structure`, jest to niedozwolone w `Interface`)|`Public`|  
|Wyliczenia ([Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Klasy ([Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Struktury ([struktury instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Moduł ([Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Niedozwolone|Niedozwolone|  
|Interfejs ([Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Procedura ([funkcji instrukcji](../../../visual-basic/language-reference/statements/function-statement.md), [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Odwołanie zewnętrzne ([instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Niedozwolone|`Public` (nie jest dozwolone w `Interface`)|Niedozwolone|  
|Operator ([operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md))|Niedozwolone|`Public` (nie jest dozwolone w `Interface` lub `Module`)|Niedozwolone|  
|Właściwości ([Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Właściwość domyślna ([domyślne](../../../visual-basic/language-reference/modifiers/default.md))|Niedozwolone|`Public` (nie jest dozwolone w `Module`)|Niedozwolone|  
|Zdarzenia ([Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Delegat ([Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Niedozwolone|  
  
 Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz także

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
