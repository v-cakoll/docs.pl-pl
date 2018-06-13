---
title: Set — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: dbc48d14bac54809e4ddd12c87429bf407169950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604838"
---
# <a name="set-statement-visual-basic"></a>Set — Instrukcja (Visual Basic)
Deklaruje `Set` procedury właściwości używane do przypisania wartości dla właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Części  
 `attributelist`  
 Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcjonalnie na maksymalnie jeden `Get` i `Set` instrukcje w tej właściwości. Może to być jeden z następujących elementów:  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Wymagana. Parametr zawierający nową wartość dla właściwości.  
  
 `datatype`  
 Jeśli wymagane `Option Strict` jest `On`. Typ danych `value` parametru. Określony typ danych musi być taki sam jak typ danych właściwości gdzie to `Set` zadeklarowano instrukcji.  
  
 `statements`  
 Opcjonalna. Co najmniej jeden instrukcji, które podczas uruchamiania `Set` właściwości procedura jest wywoływana.  
  
 `End Set`  
 Wymagana. Kończy definicję `Set` procedury właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Dla każdej właściwości musi mieć `Set` procedury właściwości, chyba że właściwość jest oznaczona jako `ReadOnly`. `Set` Procedura służy do ustawiania wartości właściwości.  
  
 Visual Basic automatycznie wywołuje właściwość `Set` procedury w przypadku instrukcji przypisania udostępnia wartość jest przechowywana we właściwości.  
  
 Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości. Jeśli nie podasz parametru `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`. Parametr zawiera wartość do przypisania do właściwości. Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatnych i przywrócić go przy każdym `Get` procedura jest wywoływana.  
  
 Treść deklaracja właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji. Nie można zapisać żadnych innych niż te procedury. W szczególności go nie można zapisać bieżącą wartość właściwości. Ta wartość poza właściwości, muszą być przechowywane, ponieważ Jeśli przechowujesz wewnątrz jednej z właściwości procedur procedurę właściwości nie można do niego dostęp. Jest zwykle podejście do przechowywania wartości [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarować zmiennej na tym samym poziomie jako wartość właściwości. Należy zdefiniować `Set` procedurę wewnątrz właściwości, której dotyczy.  
  
 `Set` Procedury Domyślnie poziom dostępu do jego właściwości zawierającego tylko w przypadku `accessmodifier` w `Set` instrukcji.  
  
## <a name="rules"></a>Reguły  
  
-   **Mieszanymi poziomami dostępu.** Jeśli definiujesz właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu różnych jednego `Get` lub `Set` procedura, ale nie oba. Jeśli to zrobisz, poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowany jako `Friend`, mogą zadeklarować `Set` procedury `Private`, ale nie `Public`.  
  
     Jeśli definiujesz `WriteOnly` właściwość `Set` procedury reprezentuje cały właściwość. Nie można zadeklarować poziom dostępu różnych `Set`, ponieważ który ustawiał dwa poziomy dostępu dla właściwości.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zwracanie z procedury właściwości.** Gdy `Set` procedura zwraca do kodu wywołującego, wykonanie jest kontynuowane po instrukcji, która podane wartości, które mają być przechowywane.  
  
     `Set` procedury własności może zwrócić przy użyciu [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) lub [instrukcji Zakończ](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     `Exit Property` i `Return` instrukcje spowodować natychmiastowe wyjścia z procedury właściwości. Dowolną liczbę `Exit Property` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Property` i `Return` instrukcje.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Set` instrukcji można ustawić wartości właściwości.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
