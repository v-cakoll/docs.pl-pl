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
ms.openlocfilehash: 49d4c36805b64d7232a94e818256723a0437b6ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404190"
---
# <a name="set-statement-visual-basic"></a>Set — Instrukcja (Visual Basic)
Deklaruje `Set` procedurę właściwości używaną do przypisywania wartości do właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Części  
 `attributelist`  
 Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).  
  
 `accessmodifier`  
 Opcjonalne dla co najwyżej jednej `Get` instrukcji i `Set` w tej właściwości. Może być jedną z następujących czynności:  
  
- [Chronione](../modifiers/protected.md)  
  
- [Osoby](../modifiers/friend.md)  
  
- [Użytek](../modifiers/private.md)  
  
- `Protected Friend`  
  
 Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Wymagany. Parametr zawierający nową wartość właściwości.  
  
 `datatype`  
 Wymagane, jeśli `Option Strict` jest `On` . Typ danych `value` parametru. Określony typ danych musi być taki sam jak typ danych właściwości, w której ta `Set` instrukcja jest zadeklarowana.  
  
 `statements`  
 Opcjonalny. Jedna lub więcej instrukcji, które są uruchamiane, gdy `Set` wywoływana jest procedura właściwości.  
  
 `End Set`  
 Wymagany. Kończy definicję `Set` procedury właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Każda właściwość musi mieć `Set` procedurę właściwości, chyba że właściwość jest oznaczona `ReadOnly` . `Set`Procedura służy do ustawiania wartości właściwości.  
  
 Visual Basic automatycznie wywołuje procedurę właściwości, `Set` gdy instrukcja przypisania dostarcza wartość, która ma być przechowywana we właściwości.  
  
 Visual Basic przekazuje parametr do `Set` procedury podczas przypisywania właściwości. Jeśli nie podasz parametru dla `Set` , zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value` . Parametr zawiera wartość, która ma zostać przypisana do właściwości. Zwykle ta wartość jest przechowywana w prywatnej zmiennej lokalnej i zwracana przy każdym `Get` wywołaniu procedury.  
  
 Treść deklaracji właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [instrukcją właściwości](property-statement.md) a `End Property` instrukcją. Nie może on przechowywać żadnych elementów innych niż te procedury. W szczególności nie można zapisać bieżącej wartości właściwości. Ta wartość musi być przechowywana poza właściwością, ponieważ w przypadku przechowywania jej w ramach jednej z procedur dotyczących właściwości inna procedura właściwości nie będzie mogła uzyskać do niej dostępu. Typowym podejściem jest przechowywanie wartości w zmiennej [prywatnej](../modifiers/private.md) zadeklarowanej na tym samym poziomie co właściwość. Należy zdefiniować `Set` procedurę wewnątrz właściwości, do której ma zastosowanie.  
  
 `Set`Procedura jest domyślnie ustawiona na poziom dostępu właściwości zawierającej, chyba że zostanie użyta `accessmodifier` `Set` instrukcja w instrukcji.  
  
## <a name="rules"></a>Reguły  
  
- **Mieszane poziomy dostępu.** W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub `Set` procedury, ale nie oba. W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend` , można zadeklarować `Set` procedurę `Private` , ale nie `Public` .  
  
     W przypadku definiowania `WriteOnly` właściwości `Set` procedura reprezentuje całą właściwość. Nie można zadeklarować innego poziomu dostępu dla `Set` , ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Powrót z procedury właściwości.** Gdy `Set` procedura wraca do kodu wywołującego, wykonanie jest kontynuowane po instrukcji, która dostarczyła wartość do zapisania.  
  
     `Set`procedury właściwości mogą być zwracane przy użyciu [instrukcji return](return-statement.md) lub [instrukcji Exit](exit-statement.md).  
  
     `Exit Property`Instrukcje i `Return` powodują natychmiastowe wyjście z procedury właściwości. Dowolna liczba `Exit Property` `Return` instrukcji i może występować w dowolnym miejscu procedury i można mieszać i wypełniać `Exit Property` `Return` instrukcje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Set` Aby ustawić wartość właściwości.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Zobacz też

- [Get — Instrukcja](get-statement.md)
- [Property — Instrukcja](property-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Procedury własności](../../programming-guide/language-features/procedures/property-procedures.md)
