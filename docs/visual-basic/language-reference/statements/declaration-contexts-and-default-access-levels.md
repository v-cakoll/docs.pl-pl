---
title: Kontekst deklaracji i domyślne poziomy dostępu
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354102"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)
W tym temacie opisano, które typy danych Visual Basic mogą być deklarowane w ramach których innych typów, a także jakie są ich domyślne poziomy dostępu, jeśli nie zostały określone.  
  
## <a name="declaration-context-levels"></a>Poziomy kontekstu deklaracji  
 *Kontekst deklaracji* elementu programowania to region kodu, w którym jest zadeklarowany. Jest to często inny element programistyczny, który jest następnie nazywany *elementem zawierającym*.  
  
 Poziomy kontekstu deklaracji są następujące:  
  
- *Poziom przestrzeni nazw* — w pliku źródłowym lub przestrzeni nazw, ale nie w obrębie klasy, struktury, modułu lub interfejsu  
  
- *Poziom modułu* — w obrębie klasy, struktury, modułu lub interfejsu, ale nie w ramach procedury lub bloku  
  
- *Poziom procedury* — w obrębie procedury lub bloku (na przykład `If` lub `For`)  
  
 W poniższej tabeli przedstawiono domyślne poziomy dostępu dla różnych zadeklarowanych elementów programowania, w zależności od ich kontekstów deklaracji.  
  
|Zadeklarowany element|Poziom przestrzeni nazw|Poziom modułu|Poziom procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([Dim — Instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md))|Niedozwolone|`Private` (`Public` w `Structure`, niedozwolone w `Interface`)|`Public`|  
|Stała ([instrukcja const](../../../visual-basic/language-reference/statements/const-statement.md))|Niedozwolone|`Private` (`Public` w `Structure`, niedozwolone w `Interface`)|`Public`|  
|Wyliczenie ([instrukcja enum](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Class ([instrukcja klasy](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Structure ([instrukcja struktury](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Module ([instrukcja modułu](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Niedozwolone|Niedozwolone|  
|Interfejs ([instrukcja interfejsu](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Procedura ([Instrukcja function](../../../visual-basic/language-reference/statements/function-statement.md), [instrukcja sub](../../../visual-basic/language-reference/statements/sub-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Odwołanie zewnętrzne ([instrukcja DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md))|Niedozwolone|`Public` (niedozwolone w `Interface`)|Niedozwolone|  
|Operator ([instrukcja operatora](../../../visual-basic/language-reference/statements/operator-statement.md))|Niedozwolone|`Public` (niedozwolone w `Interface` lub `Module`)|Niedozwolone|  
|Property ([instrukcja właściwości](../../../visual-basic/language-reference/statements/property-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Default — właściwość ([wartość domyślna](../../../visual-basic/language-reference/modifiers/default.md))|Niedozwolone|`Public` (niedozwolone w `Module`)|Niedozwolone|  
|Zdarzenie ([instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Delegate ([delegowanie instrukcji](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Niedozwolone|  
  
 Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz także

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
