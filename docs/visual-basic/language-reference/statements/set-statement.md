---
title: Set, instrukcja
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
ms.openlocfilehash: 75ad6d87f1785fea13a282d953f117c9c234e203
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349567"
---
# <a name="set-statement-visual-basic"></a>Set — Instrukcja (Visual Basic)
Deklaruje procedurę właściwości `Set` służącą do przypisywania wartości do właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Części  
 `attributelist`  
 Opcjonalna. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcjonalne dla co najwyżej jednej instrukcji `Get` i `Set` w tej właściwości. Może to być jeden z następujących modyfikatorów dostępu:  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Wymagana. Parametr zawierający nową wartość właściwości.  
  
 `datatype`  
 Wymagane, jeśli `Option Strict` jest `On`. Typ danych parametru `value`. Określony typ danych musi być taki sam jak typ danych właściwości, w której jest zadeklarowana ta instrukcja `Set`.  
  
 `statements`  
 Opcjonalna. Jedna lub więcej instrukcji, które są uruchamiane po wywołaniu procedury `Set` właściwości.  
  
 `End Set`  
 Wymagana. Kończy definicję procedury `Set` właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Każda właściwość musi mieć procedurę właściwości `Set`, chyba że właściwość jest oznaczona `ReadOnly`. Procedura `Set` służy do ustawiania wartości właściwości.  
  
 Visual Basic automatycznie wywołuje procedurę `Set` właściwości, gdy instrukcja przypisania dostarcza wartość, która ma być przechowywana we właściwości.  
  
 Visual Basic przekazuje parametr do procedury `Set` podczas przypisywania właściwości. Jeśli nie podasz parametru dla `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`. Parametr zawiera wartość, która ma zostać przypisana do właściwości. Zwykle ta wartość jest przechowywana w prywatnej zmiennej lokalnej i zwracana przy każdym wywołaniu procedury `Get`.  
  
 Treść deklaracji właściwości może zawierać tylko `Get` i `Set` procedur między [instrukcją właściwości](../../../visual-basic/language-reference/statements/property-statement.md) i instrukcją `End Property`. Nie może on przechowywać żadnych elementów innych niż te procedury. W szczególności nie można zapisać bieżącej wartości właściwości. Ta wartość musi być przechowywana poza właściwością, ponieważ w przypadku przechowywania jej w ramach jednej z procedur dotyczących właściwości inna procedura właściwości nie będzie mogła uzyskać do niej dostępu. Typowym podejściem jest przechowywanie wartości w zmiennej [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarowanej na tym samym poziomie co właściwość. Należy zdefiniować `Set` procedury wewnątrz właściwości, do której ma zastosowanie.  
  
 Procedura `Set` domyślnie jest poziomem dostępu właściwości zawierającego, chyba że w instrukcji `Set` użyto `accessmodifier`.  
  
## <a name="rules"></a>Reguły  
  
- **Mieszane poziomy dostępu.** W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub procedury `Set`, ale nie dla obu tych opcji. W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować procedurę `Set` `Private`, ale nie `Public`.  
  
     Jeśli definiujesz Właściwość `WriteOnly`, procedura `Set` reprezentuje całą właściwość. Nie można zadeklarować innego poziomu dostępu dla `Set`, ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Powrót z procedury właściwości.** Gdy procedura `Set` zwraca kod wywołujący, wykonanie kontynuuje się po instrukcji, która dostarczyła wartość do zapisania.  
  
     procedury właściwości `Set` mogą być zwracane przy użyciu [instrukcji return](../../../visual-basic/language-reference/statements/return-statement.md) lub [instrukcji Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     Instrukcje `Exit Property` i `Return` powodują natychmiastowe wyjście z procedury właściwości. Dowolna liczba instrukcji `Exit Property` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Property` i `Return`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Set`, aby ustawić wartość właściwości.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Zobacz także

- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
