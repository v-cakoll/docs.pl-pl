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
ms.openlocfilehash: b5bb943a062ac648f88645fb6de1acb42213071c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404800"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontekst deklaracji i domyślne poziomy dostępu (Visual Basic)
W tym temacie opisano, które typy Visual Basic mogą być deklarowane w ramach których inne typy i do których poziomów dostępu domyślnie nie są określone.  
  
## <a name="declaration-context-levels"></a>Poziomy kontekstu deklaracji  
 *Kontekst deklaracji* elementu programowania to region kodu, w którym jest zadeklarowany. Jest to często inny element programistyczny, który jest następnie nazywany *elementem zawierającym*.  
  
 Poziomy kontekstu deklaracji są następujące:  
  
- *Poziom przestrzeni nazw* — w pliku źródłowym lub przestrzeni nazw, ale nie w obrębie klasy, struktury, modułu lub interfejsu  
  
- *Poziom modułu* — w obrębie klasy, struktury, modułu lub interfejsu, ale nie w ramach procedury lub bloku  
  
- *Poziom procedury* — w ramach procedury lub bloku (na przykład `If` lub `For` )  
  
 W poniższej tabeli przedstawiono domyślne poziomy dostępu dla różnych zadeklarowanych elementów programowania, w zależności od ich kontekstów deklaracji.  
  
|Zadeklarowany element|Poziom przestrzeni nazw|Poziom modułu|Poziom procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([Dim — Instrukcja](dim-statement.md))|Niedozwolone|`Private`( `Public` w `Structure` , niedozwolone w `Interface` )|`Public`|  
|Stała ([instrukcja const](const-statement.md))|Niedozwolone|`Private`( `Public` w `Structure` , niedozwolone w `Interface` )|`Public`|  
|Wyliczenie ([instrukcja enum](enum-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Class ([instrukcja klasy](class-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Structure ([instrukcja struktury](structure-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Module ([instrukcja modułu](module-statement.md))|`Friend`|Niedozwolone|Niedozwolone|  
|Interfejs ([instrukcja interfejsu](interface-statement.md))|`Friend`|`Public`|Niedozwolone|  
|Procedura ([Instrukcja function](function-statement.md), [instrukcja sub](sub-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Odwołanie zewnętrzne ([instrukcja DECLARE](declare-statement.md))|Niedozwolone|`Public`(niedozwolone w `Interface` )|Niedozwolone|  
|Operator ([instrukcja operatora](operator-statement.md))|Niedozwolone|`Public`(niedozwolone w `Interface` lub `Module` )|Niedozwolone|  
|Property ([instrukcja właściwości](property-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Default — właściwość ([wartość domyślna](../modifiers/default.md))|Niedozwolone|`Public`(niedozwolone w `Module` )|Niedozwolone|  
|Zdarzenie ([instrukcja zdarzenia](event-statement.md))|Niedozwolone|`Public`|Niedozwolone|  
|Delegate ([delegowanie instrukcji](delegate-statement.md))|`Friend`|`Public`|Niedozwolone|  
  
 Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz też

- [Osoby](../modifiers/friend.md)
- [Użytek](../modifiers/private.md)
- [Społeczeństwo](../modifiers/public.md)
