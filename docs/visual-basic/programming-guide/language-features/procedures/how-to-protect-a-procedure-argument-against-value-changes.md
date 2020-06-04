---
title: 'Porady: chronienie argumentu procedury przed zmianami wartości'
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
ms.openlocfilehash: b0504d9f7a8862274d5d71dc6a9c1570551629a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414366"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Porady: chronienie argumentu procedury przed zmianami wartości (Visual Basic)
Jeśli procedura deklaruje parametr jako [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic daje kod procedury bezpośrednio odwołanie do elementu programowania, który jest powiązany z argumentem w kodzie wywołującym. Pozwala to na procedurę zmiany wartości bazowej argumentu w wywoływanym kodzie. W niektórych przypadkach kod wywołujący może chcieć chronić przed takimi zmianami.  
  
 Można zawsze chronić argument przed zmianami, deklarując odpowiedni parametr [ByVal](../../../language-reference/modifiers/byval.md) w procedurze. Jeśli chcesz mieć możliwość zmiany danego argumentu w niektórych przypadkach, ale nie do innych, można zadeklarować go `ByRef` i pozwolić, aby kod wywołujący mógł określić mechanizm przekazywania w każdym wywołaniu. W tym celu należy ująć w nawiasy odpowiedni argument, aby przekazać go przez wartość, lub nie umieścić go w nawiasie, aby przekazać go przez odwołanie. Aby uzyskać więcej informacji, zobacz [jak: Wymuś przekazywanie argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwie procedury, które pobierają zmienną tablicową i działają na jej elementach. `increase`Procedura po prostu dodaje jeden do każdego elementu. `replace`Procedura przypisuje nową tablicę do parametru `a()` , a następnie dodaje ją do każdego elementu. Jednak ponowne przypisanie nie ma wpływu na podstawową zmienną tablicową w kodzie wywołującym.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Pierwsze `MsgBox` wywołanie wyświetla "po zwiększeniu (n): 11, 21, 31, 41". Ponieważ tablica `n` jest typem referencyjnym, `increase` może zmienić jej składowe, nawet jeśli mechanizm przekazywania jest `ByVal` .  
  
 Drugie `MsgBox` wywołanie wyświetla "po zastąpieniu (n): 11, 21, 31, 41". Ponieważ `n` jest zakończony `ByVal` , `replace` nie można zmodyfikować zmiennej `n` w wywoływanym kodzie, przypisując do niej nową tablicę. Gdy program `replace` tworzy nowe wystąpienie tablicy `k` i przypisuje je do zmiennej lokalnej `a` , traci odwołanie do `n` przekazywania przez kod wywołujący. Gdy zmienia elementy członkowskie `a` , dotyczy tylko tablicy lokalnej `k` . W związku z tym program nie `replace` zwiększa wartości tablicy `n` w kodzie wywołującym.  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości. Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../language-reference/modifiers/byval.md) lub [ByRef](../../../language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem. Ułatwia to odczytywanie kodu.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../data-types/value-types-and-reference-types.md)
