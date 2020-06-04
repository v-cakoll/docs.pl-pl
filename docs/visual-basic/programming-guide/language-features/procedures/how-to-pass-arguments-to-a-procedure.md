---
title: 'Porady: przekazywanie argumentów do procedury'
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
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387780"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Porady: przekazywanie argumentów do procedury (Visual Basic)
Po wywołaniu procedury należy użyć nazwy procedury z listą argumentów w nawiasach. Należy podać argument odpowiadający każdemu wymaganemu parametrowi zdefiniowanej przez procedurę i opcjonalnie dostarczyć argumentów do `Optional` parametrów. Jeśli nie podasz `Optional` parametru w wywołaniu, musisz dołączyć przecinek, aby oznaczyć jego miejsce na liście argumentów, jeśli podasz kolejne argumenty.  
  
 Jeśli zamierzasz przekazać argument typu danych innego niż odpowiadający mu parametr, na przykład `Byte` do `String` , można ustawić przełącznik kontroli typu ([Option Strict](../../../language-reference/statements/option-strict-statement.md)) na `Off` . Jeśli `Option Strict` jest `On` , musisz użyć rozszerzonych słów kluczowych lub konwersji. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md) oraz [funkcji konwersji typów](../../../language-reference/functions/type-conversion-functions.md).  
  
 Aby uzyskać więcej informacji, zobacz [parametry procedury i argumenty](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Aby przekazać jeden lub więcej argumentów do procedury  
  
1. W instrukcji wywołującej postępuj według nazwy procedury z nawiasami.  
  
2. Umieść listę argumentów wewnątrz nawiasów. Należy dołączyć argument dla każdego wymaganego parametru, który definiuje procedura, i oddzielić argumenty przecinkami.  
  
3. Upewnij się, że każdy argument jest prawidłowym wyrażeniem, które oblicza typ danych do przekonwertowania na typ, który procedura definiuje dla odpowiadającego parametru.  
  
4. Jeśli parametr jest zdefiniowany jako [opcjonalny](../../../language-reference/modifiers/optional.md), można go umieścić na liście argumentów lub pominąć. Jeśli zostanie pominięty, procedura używa wartości domyślnej zdefiniowanej dla tego parametru.  
  
5. W przypadku pominięcia argumentu dla `Optional` parametru, gdy na liście parametrów istnieje inny parametr, można oznaczyć pominięty argument przez dodatkowy przecinek na liście argumentów.  
  
     Poniższy przykład wywołuje <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcję Visual Basic.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     Powyższy przykład zawiera wymagany pierwszy argument, który jest ciągiem komunikatów do wyświetlenia. Pomija argument dla opcjonalnego drugiego parametru, który określa przyciski, które mają być wyświetlane w oknie komunikatu. Ponieważ wywołanie nie dostarcza wartości, `MsgBox` używa wartości domyślnej, `MsgBoxStyle.OKOnly` która wyświetla tylko przycisk **OK** .  
  
     Drugi przecinek na liście argumentów oznacza miejsce pominiętego drugiego argumentu, a ostatni ciąg jest przenoszona do opcjonalnego trzeciego parametru `MsgBox` , który jest tekstem, który ma być wyświetlany na pasku tytułu.  
  
## <a name="see-also"></a>Zobacz też

- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury własności](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Obiekty i klasy](../objects-and-classes/index.md)
- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
