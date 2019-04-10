---
title: 'Instrukcje: Przekazywanie argumentów do procedury (Visual Basic)'
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
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333915"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Instrukcje: Przekazywanie argumentów do procedury (Visual Basic)
Po wywołaniu procedury, należy wykonać Nazwa procedury z listą argumentów w nawiasach. Należy podać argument odpowiadający każdego wymaganego parametru definiuje procedurę i opcjonalnie można podać argumenty do `Optional` parametrów. Jeśli nie podasz `Optional` parametr w wywołaniu musi zawierać przecinek, aby oznaczyć jego miejsce na liście argumentów, jeśli są podawania wszystkie pozostałe argumenty.  
  
 Jeśli zamierzasz przekazać argumentu o typie danych innym niż odpowiadającego mu parametru takich jak `Byte` do `String`, można ustawić przełącznik kontrola typów ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) do `Off`. Jeśli `Option Strict` jest `On`, należy użyć poszerzenia konwersje lub słowa kluczowe konwersji jawnej. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i [funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Aby przekazać jeden lub więcej argumentów do procedury  
  
1. W instrukcji wywołujące postępuj zgodnie z nazwy procedury za pomocą nawiasów.  
  
2. Wewnątrz nawiasów umieść listy argumentów. Obejmują argument dla każdego wymaganego parametru definiuje procedurę i należy je oddzielić przecinkami.  
  
3. Upewnij się, że każdy argument jest prawidłowe wyrażenie obliczane do typu danych można przekonwertować na typ procedury definiuje odpowiadającego mu parametru.  
  
4. Jeśli parametr jest zdefiniowany jako [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md), możesz włączyć ją na liście argumentów lub Pomiń ją. Jeśli ten parametr zostanie pominięty, w procedurze użyto wartości domyślnej zdefiniowanej dla tego parametru.  
  
5. Jeżeli pominięto argument `Optional` parametru i ma inny parametr po liście parametrów, można oznaczyć miejsce pominięty argument przez dodatkowy przecinek na liście argumentów.  
  
     Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     Poprzedni przykład dostarcza wymagane pierwszego argumentu, czyli ciąg komunikatu, które mają być wyświetlane. Pomija argument opcjonalny drugi parametr, który określa przyciski, które mają być wyświetlane w oknie komunikatu. Ponieważ to wywołanie nie dostarcza wartość `MsgBox` użyje wartości domyślnej `MsgBoxStyle.OKOnly`, powoduje wyświetlenie tylko **OK** przycisku.  
  
     Drugi przecinek w liście argumentów oznacza miejsce pominięty drugi argument, a ostatni ciąg jest przekazywany do opcjonalny trzeci parametr `MsgBox`, który jest tekst, który ma być wyświetlany na pasku tytułu.  
  
## <a name="see-also"></a>Zobacz także

- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
