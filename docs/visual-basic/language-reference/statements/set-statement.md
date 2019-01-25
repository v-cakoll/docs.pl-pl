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
ms.openlocfilehash: d77c7d3f2e70edcc1028c207150944c5394afbe0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685376"
---
# <a name="set-statement-visual-basic"></a>Set — Instrukcja (Visual Basic)
Deklaruje `Set` procedury właściwości używane do przypisywania wartości do właściwości.  
  
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
 Opcjonalnie na co najwyżej jeden z `Get` i `Set` instrukcje w tej właściwości. Może to być jeden z następujących elementów:  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Wymagana. Parametr zawierający nową wartość dla właściwości.  
  
 `datatype`  
 Jeśli wymagane `Option Strict` jest `On`. Typ danych `value` parametru. Określony typ danych musi być taki sam jak typ danych właściwości gdzie to `Set` instrukcji jest zadeklarowana.  
  
 `statements`  
 Opcjonalna. Jedna lub więcej instrukcji, które są uruchamiane podczas `Set` nosi nazwę procedury właściwości.  
  
 `End Set`  
 Wymagana. Kończy definicję `Set` procedury właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Dla każdej właściwości musi mieć `Set` procedury właściwości, chyba że właściwość jest oznaczona `ReadOnly`. `Set` Procedura służy do ustawiania wartości właściwości.  
  
 Visual Basic automatycznie wywołuje właściwość `Set` procedury w przypadku instrukcji przypisania udostępnia wartość jest przechowywana we właściwości.  
  
 Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości. Jeśli parametr nie zostanie podana `Set`, zintegrowanego środowiska programistycznego (IDE) korzysta z niejawny parametr o nazwie `value`. Parametr przechowuje wartość do przypisania do właściwości. Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatne i przywrócić go zawsze wtedy, gdy `Get` procedura jest wywoływana.  
  
 Treść deklaracja właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji. Nie można zapisać coś innego niż te procedury. W szczególności go nie można zapisać bieżącą wartość właściwości. Ta wartość poza właściwości, muszą być przechowywane, ponieważ jeśli będą przechowywane w jednej z procedur właściwość, inne procedury właściwości nie można uzyskać do niego dostęp. Zwykle rozwiązaniem jest wartość jest przechowywana w [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) Zmienna zadeklarowana na tym samym poziomie jak właściwość. Należy zdefiniować `Set` procedury właściwości, której dotyczy.  
  
 `Set` Procedury wartość domyślna to poziom dostępu do jego zawierającą je właściwość, chyba że używasz `accessmodifier` w `Set` instrukcji.  
  
## <a name="rules"></a>reguły  
  
-   **Mieszanymi poziomami dostępu.** Jeśli zamierzasz zdefiniować właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu do różnych dla dowolnego `Get` lub `Set` procedury, ale nie oba. Jeśli to zrobisz, procedura poziom dostępu musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować `Set` procedury `Private`, ale nie `Public`.  
  
     Jeśli definiujesz `WriteOnly` właściwości `Set` procedury reprezentuje cały właściwość. Nie można zadeklarować dostęp inny poziom `Set`, ponieważ, ustawić dwa poziomy dostępu dla właściwości.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zwracanie z procedury właściwości.** Gdy `Set` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane po instrukcji, która podano wartość, która ma być przechowywany.  
  
     `Set` procedury własności może zwrócić przy użyciu [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md) lub [instrukcji zakończenia](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     `Exit Property` i `Return` instrukcji powodują natychmiastowego wyjścia z procedury właściwości. Dowolną liczbę `Exit Property` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Property` i `Return` instrukcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Set` instrukcję, aby ustawić wartość właściwości.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
