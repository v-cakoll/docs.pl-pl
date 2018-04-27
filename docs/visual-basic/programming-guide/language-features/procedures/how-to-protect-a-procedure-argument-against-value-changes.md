---
title: 'Porady: chronienie argumentu procedury przed zmianami wartości (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59c0486bd9543167e4c17a3109c4b89b3502e80e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Porady: chronienie argumentu procedury przed zmianami wartości (Visual Basic)
Jeśli procedura deklaruje jako parametru [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic daje kodu procedury bezpośrednie odwołanie do elementu programistycznego bazowy argumentu w wywoływanym kodzie. Pozwala to na procedurę, aby zmienić wartość bazowy argumentu w wywoływanym kodzie. W niektórych przypadkach kod wywołujący może być przydatna ochrona przed tej zmiany.  
  
 Zawsze chronić argumentu z zmiany przez zadeklarowanie odpowiadającego mu parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) w procedurze. Jeśli chcesz mieć możliwość zmiany podany argument w niektórych przypadkach, ale nie można zadeklarować go `ByRef` i pozwolić, aby określić mechanizm przekazywania w każdym wywołaniu kodu wywołującego. Jest to możliwe dzięki otaczającej odpowiadającego mu argumentu w nawiasach przekazywany przez wartość lub nie należy ująć w nawias przekazywany przez odwołanie. Aby uzyskać więcej informacji, zobacz [porady: Wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwie procedury, które podejmują zmienną tablicową i które działają na swoich elementów. `increase` Procedury po prostu dodaje je do każdego elementu. `replace` Procedury przypisuje nową macierz do parametru `a()` , a następnie dodaje je do każdego elementu. Jednak ponowne przypisanie nie ma wpływu na podstawowe zmiennej tablicy w wywoływanym kodzie.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41". Ponieważ tablicy `n` jest typem referencyjnym `replace` można zmienić jej członków, nawet jeśli jest mechanizm przekazywania `ByVal`.  
  
 Drugi `MsgBox` wywołać Wyświetla "po replace(n): 11, 21, 31, 41". Ponieważ `n` jest przekazywany `ByVal`, `replace` nie można zmodyfikować zmienną `n` w wywoływanym kodzie przez przypisanie nowej tablicy. Gdy `replace` tworzy nowe wystąpienie tablicy `k` i przypisuje go do zmiennej lokalnej `a`, tym samym odwołanie do `n` przekazany przez wywołującego kodu. Podczas zmiany jego elementów członkowskich `a`, lokalnej tablicy `k` dotyczy. W związku z tym `replace` nie zwiększa się wartości w tablicy `n` w wywoływanym kodzie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości. Jednak jest dobre rozwiązanie to dołączenie albo programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr. Ułatwia to kodu do odczytu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Instrukcje: zmiana wartości argumentu procedury](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
