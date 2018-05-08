---
title: 'Porady: przekazywanie argumentów do procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: f393f17f87c5920fb9bfa2a2097c09d48bebdc16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Porady: przekazywanie argumentów do procedury (Visual Basic)
Po wywołaniu procedury, możesz po nazwie procedury z listą argumentów w nawiasach. Poddaj argument odpowiadający każdego wymaganego parametru definiuje procedurę i opcjonalnie możesz podać argumenty `Optional` parametrów. Jeśli nie podasz `Optional` parametr w wywołaniu musi zawierać przecinka, aby oznaczyć jego miejsce na liście argumentów, jeśli są dostarczanie wszystkie pozostałe argumenty.  
  
 Jeśli chcesz przekazać argumentu typu danych w innym niż jego odpowiadającego mu parametru, takich jak `Byte` do `String`, można ustawić sprawdzanie typu przełącznika ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) do `Off`. Jeśli `Option Strict` jest `On`, należy użyć jednego rozszerzanie konwersji lub słowa kluczowe konwersji jawnej. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i [funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Aby przekazać co najmniej jeden z argumentów do procedury  
  
1.  W instrukcji wywoływania wykonaj nazwę procedury w nawiasach.  
  
2.  Wewnątrz nawiasów umieść listy argumentów. Argument dla wszystkich wymaganych parametrów definiuje procedurę obejmują i argumenty należy oddzielić przecinkami.  
  
3.  Upewnij się, że każdy argument jest prawidłowe wyrażenie, którego wynikiem jest typ danych można przekonwertować na typ procedury definicje odpowiadającego mu parametru.  
  
4.  Jeśli parametr jest zdefiniowany jako [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md), możesz dołączyć go na liście argumentów lub pominąć go. Jeśli ten parametr zostanie pominięty, procedura korzysta z wartości domyślnej zdefiniowanej dla tego parametru.  
  
5.  Jeśli zostanie pominięty argument `Optional` parametru i inny parametr po występuje on na liście parametrów, możesz oznaczyć miejsca pominięty argument przez dodatkowy przecinek na liście argumentów.  
  
     Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     Powyższy przykład dostarcza wymagane pierwszego argumentu, który jest ciągiem komunikat do wyświetlenia. Argument opcjonalny drugi parametr, który określa przyciski, który będzie wyświetlany w oknie komunikatu to ciąg. Ponieważ wywołania podano wartości, `MsgBox` domyślną wartość `MsgBoxStyle.OKOnly`, który zawiera tylko **OK** przycisku.  
  
     Drugi przecinek w liście argumentów oznacza miejsca pominięcia drugi argument, a ostatni ciąg jest przekazywana do opcjonalny trzeci parametr funkcji `MsgBox`, która jest tekst, który ma być wyświetlany w pasku tytułu.  
  
## <a name="see-also"></a>Zobacz także

 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Instrukcje: definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Procedury rekursywne](./recursive-procedures.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)  
