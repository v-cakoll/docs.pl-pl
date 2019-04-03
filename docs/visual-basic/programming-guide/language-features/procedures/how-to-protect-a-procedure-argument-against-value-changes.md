---
title: 'Instrukcje: Chronienie argumentu procedury przed zmianami wartości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 70378b57c6d3af5a98e0ba9c6e3aebc319561b1b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837783"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Instrukcje: Chronienie argumentu procedury przed zmianami wartości (Visual Basic)
Jeśli procedura deklaruje jako parametru [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic, zawiera kod procedury bezpośrednie odwołanie do elementu programistycznego, bazowy argumentu w wywoływanym kodzie. Pozwala to na procedurę, aby zmienić wartość bazowego argumentu w wywoływanym kodzie. W niektórych przypadkach kod wywołujący może mają być chronione przed takich zmian.  
  
 Argument może zawsze chronić zmiana, deklarując z odpowiadającym mu parametrem [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) w procedurze. Jeśli chcesz można było zmienić w niektórych przypadkach, ale nie inne podany argument, trzeba je zadeklarować `ByRef` i pozwolić określić mechanizm przekazywania w każdym wywołaniu kodu wywołującego. Dzieje się tak, otaczający odnośnego argumentu w nawiasach przekazywany przez wartość lub nie otaczający w nawiasach przekazywany przez odwołanie. Aby uzyskać więcej informacji, zobacz [jak: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwie procedury używające zmiennej tablicy i działać na jego elementach. `increase` Procedura dodaje po prostu jednym do każdego elementu. `replace` Procedury przypisuje nową tablicę z parametrem `a()` , a następnie dodaje je do każdego elementu. Jednak ponowne przypisanie nie ma wpływu na podstawowe zmienną tablicy w wywoływanym kodzie.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41". Ponieważ tablicy `n` jest typem referencyjnym `increase` można zmienić jej członków, nawet jeśli jest mechanizm przekazywania `ByVal`.  
  
 Drugi `MsgBox` wywołać Wyświetla "po replace(n): 11, 21, 31, 41". Ponieważ `n` jest przekazywany `ByVal`, `replace` nie można zmodyfikować zmienną `n` w wywoływanym kodzie, przez przypisanie nowej tablicy. Gdy `replace` tworzy nowe wystąpienie tablicy `k` i przypisuje go do zmiennej lokalnej `a`, utracie odwołanie do `n` przekazany kod wywołujący. Kiedy zmienia członkowie `a`, tylko lokalnej tablicy `k` dotyczy. W związku z tym `replace` nie zwiększa się wartości tablicy `n` w wywoływanym kodzie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości. Jednak dobrą praktyką, aby uwzględnić albo programowania jest [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr. Dzięki temu można łatwiej odczytać kodu.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: Zmień wartość argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
