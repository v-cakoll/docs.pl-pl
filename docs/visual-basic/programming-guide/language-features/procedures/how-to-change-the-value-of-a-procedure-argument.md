---
title: 'Porady: zmienianie wartości argumentu procedury'
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: deac87ca4690990a4d00f63d0ea9b843c3f9a9c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344476"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Porady: zmienianie wartości argumentu procedury (Visual Basic)
Po wywołaniu procedury każdy pożądany argument odpowiada jednemu z parametrów zdefiniowanych w procedurze. W niektórych przypadkach kod procedury może zmienić wartość odpowiadającą argumentowi w kodzie wywołującym. W innych przypadkach procedura może zmienić tylko jego lokalną kopię argumentu.  
  
 Po wywołaniu procedury Visual Basic wykonuje kopię lokalną każdego argumentu, który został przekazaną przez [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Dla każdego argumentu, który przeszedł metodę [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic daje kod procedury bezpośrednio odwołanie do elementu programowania, który jest powiązany z argumentem w kodzie wywołującym.  
  
 Jeśli element źródłowy w kodzie wywołującym jest elementem modyfikowalnym, a argument jest przenoszona `ByRef`, kod procedury może użyć odwołania bezpośredniego do zmiany wartości elementu w kodzie wywołującym.  
  
## <a name="changing-the-underlying-value"></a>Zmiana podstawowej wartości  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Aby zmienić podstawową wartość argumentu procedury w kodzie wywołującym  
  
1. W deklaracji procedury Określ wartość [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) dla parametru odpowiadającego argumentowi.  
  
2. W kodzie wywołującym Przekaż modyfikowalny element programistyczny jako argument.  
  
3. W kodzie wywołującym nie należy ujmować argumentu w nawiasach na liście argumentów.  
  
4. W kodzie procedury Użyj nazwy parametru, aby przypisać wartość do podstawowego elementu w kodzie wywołującym.  
  
 Zapoznaj się z przykładem.  
  
## <a name="changing-local-copies"></a>Zmienianie kopii lokalnych  
 Jeśli element źródłowy w kodzie wywołującym jest niemodyfikowalnym elementem lub jeśli argument jest przenoszona `ByVal`, procedura nie może zmienić jego wartości w kodzie wywołującym. Jednakże procedura może zmienić swoją lokalną kopię takiego argumentu.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Aby zmienić kopię argumentu procedury w kodzie procedury  
  
1. W deklaracji procedury Określ [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dla parametru odpowiadającego argumentowi.  
  
     lub  
  
     W kodzie wywołującym Umieść argument w nawiasach na liście argumentów. Wymusza to Visual Basic przekazanie argumentu według wartości, nawet jeśli odpowiedni parametr określa `ByRef`.  
  
2. W kodzie procedury Użyj nazwy parametru, aby przypisać wartość do lokalnej kopii argumentu. Wartość bazowa w wywołaniu kodu nie jest zmieniana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwie procedury, które pobierają zmienną tablicową i działają na jej elementach. Procedura `increase` po prostu dodaje jeden do każdego elementu. Procedura `replace` przypisuje nową tablicę do parametru `a()` a następnie dodaje ją do każdego elementu.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Pierwsze wywołanie `MsgBox` wyświetla "po zwiększeniu (n): 11, 21, 31, 41". Ponieważ tablica `n` jest typem referencyjnym, `replace` może zmienić jego składowe, nawet gdy mechanizm przekazywania jest `ByVal`.  
  
 Drugie wywołanie `MsgBox` wyświetla "po zastąpieniu (n): 101, 201, 301". Ponieważ `n` jest przenoszona `ByRef`, `replace` może zmodyfikować zmienną `n` w kodzie wywołującym i przypisać do niej nową tablicę. Ponieważ `n` jest typem referencyjnym, `replace` może również zmienić jego składowe.  
  
 Można zapobiec modyfikowaniu przez procedurę samej zmiennej w kodzie wywołującym. Zobacz [jak: Ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Gdy przekazujesz zmienną według odwołania, musisz użyć słowa kluczowego `ByRef`, aby określić ten mechanizm.  
  
 Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości. Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem. Ułatwia to odczytywanie kodu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Zawsze istnieje potencjalne ryzyko w umożliwieniu procedury zmiany wartości bazowej argumentu w wywoływanym kodzie. Upewnij się, że ta wartość jest zmieniana, i przygotuj się do sprawdzenia jej pod kątem poprawności przed jej użyciem.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
