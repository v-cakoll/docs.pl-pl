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
ms.openlocfilehash: 46cf9062d01e248b6e90882a923a48210780f7f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388507"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Porady: zmienianie wartości argumentu procedury (Visual Basic)
Po wywołaniu procedury każdy pożądany argument odpowiada jednemu z parametrów zdefiniowanych w procedurze. W niektórych przypadkach kod procedury może zmienić wartość odpowiadającą argumentowi w kodzie wywołującym. W innych przypadkach procedura może zmienić tylko jego lokalną kopię argumentu.  
  
 Po wywołaniu procedury Visual Basic wykonuje kopię lokalną każdego argumentu, który został przekazaną przez [ByVal](../../../language-reference/modifiers/byval.md). Dla każdego argumentu, który przeszedł metodę [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic daje kod procedury bezpośrednio odwołanie do elementu programowania, który jest powiązany z argumentem w kodzie wywołującym.  
  
 Jeśli element podstawowy w kodzie wywołującym jest elementem modyfikowalnym, a argument jest przenoszona `ByRef` , kod procedury może użyć odwołania bezpośredniego do zmiany wartości elementu w kodzie wywołującym.  
  
## <a name="changing-the-underlying-value"></a>Zmiana podstawowej wartości  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Aby zmienić podstawową wartość argumentu procedury w kodzie wywołującym  
  
1. W deklaracji procedury Określ wartość [ByRef](../../../language-reference/modifiers/byref.md) dla parametru odpowiadającego argumentowi.  
  
2. W kodzie wywołującym Przekaż modyfikowalny element programistyczny jako argument.  
  
3. W kodzie wywołującym nie należy ujmować argumentu w nawiasach na liście argumentów.  
  
4. W kodzie procedury Użyj nazwy parametru, aby przypisać wartość do podstawowego elementu w kodzie wywołującym.  
  
 Zapoznaj się z przykładem.  
  
## <a name="changing-local-copies"></a>Zmienianie kopii lokalnych  
 Jeśli element podstawowy w kodzie wywołującym jest niemodyfikowalnym elementem lub jeśli argument jest przenoszona `ByVal` , procedura nie może zmienić jego wartości w kodzie wywołującym. Jednakże procedura może zmienić swoją lokalną kopię takiego argumentu.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Aby zmienić kopię argumentu procedury w kodzie procedury  
  
1. W deklaracji procedury Określ [ByVal](../../../language-reference/modifiers/byval.md) dla parametru odpowiadającego argumentowi.  
  
     -lub-  
  
     W kodzie wywołującym Umieść argument w nawiasach na liście argumentów. Wymusza to Visual Basic do przekazania argumentu przez wartość, nawet jeśli odpowiedni parametr określa `ByRef` .  
  
2. W kodzie procedury Użyj nazwy parametru, aby przypisać wartość do lokalnej kopii argumentu. Wartość bazowa w wywołaniu kodu nie jest zmieniana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwie procedury, które pobierają zmienną tablicową i działają na jej elementach. `increase`Procedura po prostu dodaje jeden do każdego elementu. `replace`Procedura przypisuje nową tablicę do parametru `a()` , a następnie dodaje ją do każdego elementu.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Pierwsze `MsgBox` wywołanie wyświetla "po zwiększeniu (n): 11, 21, 31, 41". Ponieważ tablica `n` jest typem referencyjnym, `replace` może zmienić jej składowe, nawet jeśli mechanizm przekazywania jest `ByVal` .  
  
 Drugie `MsgBox` wywołanie wyświetla "po zastąpieniu (n): 101, 201, 301". Ponieważ `n` jest zakończony `ByRef` , `replace` można zmodyfikować zmienną `n` w wywoływanym kodzie i przypisać do niej nową tablicę. Ponieważ `n` jest typem referencyjnym, `replace` można także zmienić jego składowe.  
  
 Można zapobiec modyfikowaniu przez procedurę samej zmiennej w kodzie wywołującym. Zobacz [jak: Ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Gdy przekazujesz zmienną według odwołania, musisz użyć `ByRef` słowa kluczowego, aby określić ten mechanizm.  
  
 Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości. Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../language-reference/modifiers/byval.md) lub [ByRef](../../../language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem. Ułatwia to odczytywanie kodu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze istnieje potencjalne ryzyko w umożliwieniu procedury zmiany wartości bazowej argumentu w wywoływanym kodzie. Upewnij się, że ta wartość jest zmieniana, i przygotuj się do sprawdzenia jej pod kątem poprawności przed jej użyciem.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../data-types/value-types-and-reference-types.md)
