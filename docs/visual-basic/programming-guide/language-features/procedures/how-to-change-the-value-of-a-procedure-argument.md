---
title: 'Porady: zmienianie wartości argumentu procedury (Visual Basic)'
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
ms.openlocfilehash: 118dd3389804794801d39e7d67b68ab195bbad3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Porady: zmienianie wartości argumentu procedury (Visual Basic)
Po wywołaniu procedury, każdy argument, który podasz odnosi się do jednego z parametrów zdefiniowanych w procedurze. W niektórych przypadkach kodu procedury można zmienić wartości podstawowej argumentu w wywoływanym kodzie. W pozostałych przypadkach procedura można zmienić tylko w swojej lokalnej kopii argumentu.  
  
 Po wywołaniu procedury, Visual Basic tworzy kopię lokalnych każdy argument, który jest przekazywany [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Dla każdego argumentu przekazany [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic daje kodu procedury bezpośrednie odwołanie do elementu programistycznego bazowy argumentu w wywoływanym kodzie.  
  
 Jeśli odpowiedniego elementu kodu wywołującego jest elementem można modyfikować, a argument jest przekazywany `ByRef`, kod procedury użyć odwołanie bezpośrednie tak, aby zmienić wartości elementu w wywoływanym kodzie.  
  
## <a name="changing-the-underlying-value"></a>Zmiana wartości podstawowej  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Aby zmienić podstawowej wartości argumentu w wywoływanym kodzie procedury  
  
1.  W deklaracji procedury określ [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) dla parametru odpowiadającego atrybutowi argument.  
  
2.  Kod wywołujący dokonują można modyfikować elementu programistycznego jako argument.  
  
3.  W wywoływanym kodzie nie należy umieszczać argument w nawiasach na liście argumentów.  
  
4.  W kodzie procedura umożliwia przypisywanie wartości do odpowiedniego elementu kodu wywołującego nazwę parametru.  
  
 Zapoznaj się z przykładem już pokaz w dół.  
  
## <a name="changing-local-copies"></a>Zmiana kopiami lokalnymi  
 Jeśli odpowiedniego elementu kodu wywołującego jest elementem niemodyfikowalnymi lub argument jest przekazywany `ByVal`, procedury nie można zmienić jego wartości w wywoływanym kodzie. Jednak procedura może zmienić swojej lokalnej kopii tych argumentów.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Aby zmienić kopię argumentu procedury w kodzie procedury  
  
1.  W deklaracji procedury określ [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dla parametru odpowiadającego atrybutowi argument.  
  
     —lub—  
  
     W wywoływanym kodzie ujmij argument w nawiasach na liście argumentów. To zmusza Visual Basic do przekazywania argumentu przez wartość, nawet jeśli określa odpowiadającego mu parametru `ByRef`.  
  
2.  W kodzie procedury umożliwia przypisywanie wartości do lokalnej kopii argument nazwę parametru. Odpowiednia wartość w wywoływanym kodzie nie ulega zmianie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwie procedury, które podejmują zmienną tablicową i które działają na swoich elementów. `increase` Procedury po prostu dodaje je do każdego elementu. `replace` Procedury przypisuje nową macierz do parametru `a()` , a następnie dodaje je do każdego elementu.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41". Ponieważ tablicy `n` jest typem referencyjnym `replace` można zmienić jej członków, nawet jeśli jest mechanizm przekazywania `ByVal`.  
  
 Drugi `MsgBox` wywołać Wyświetla "po replace(n): 101, 201, 301". Ponieważ `n` jest przekazywany `ByRef`, `replace` można zmodyfikować zmienną `n` w wywoływanym kodzie i przypisać do niej nowej tablicy. Ponieważ `n` jest typem referencyjnym `replace` można również zmienić jej elementów członkowskich.  
  
 Aby uniemożliwić procedurze zmodyfikowanie zmiennej w wywoływanym kodzie. Zobacz [porady: chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jeśli zmienna przez odwołanie, należy użyć `ByRef` — słowo kluczowe, aby określić, ten mechanizm.  
  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości. Jednak jest dobre rozwiązanie to dołączenie albo programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr. Ułatwia to kodu do odczytu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieje potencjalne ryzyko z umożliwieniem procedury zmienić wartość argumentu w wywoływanym kodzie podstawowy. Upewnij się, że oczekiwane tę wartość można zmienić, i jest gotowy do Sprawdź poprawność, przed jego użyciem.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Instrukcje: ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Instrukcje: wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
