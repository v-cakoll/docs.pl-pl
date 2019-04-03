---
title: 'Instrukcje: Zmień wartość argumentu procedury (Visual Basic)'
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
ms.openlocfilehash: 6aee795fefe36c2ad19390c0ac6d1613b2199415
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837504"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Instrukcje: Zmień wartość argumentu procedury (Visual Basic)
Po wywołaniu procedury, każdy argument, który podasz odnosi się do jednego z parametrów zdefiniowanych w procedurze. W niektórych przypadkach kod procedury można zmienić wartości bazowe argumentu w wywoływanym kodzie. W innych przypadkach procedura może zmienić tylko w swojej lokalnej kopii argumentu.  
  
 Po wywołaniu procedury, Visual Basic sprawia, że lokalna kopia każdego argumentu, który jest przekazywany [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Każdy argument przekazany [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic, zawiera kod procedury bezpośrednie odwołanie do elementu programistycznego, bazowy argumentu w wywoływanym kodzie.  
  
 Jeśli element podstawowy kod wywołujący jest elementem można modyfikować, a argument jest przekazywany `ByRef`, kod procedury użyć odwołanie bezpośrednie tak, aby zmienić wartości elementu w wywoływanym kodzie.  
  
## <a name="changing-the-underlying-value"></a>Zmiana wartości podstawowej  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Aby zmienić podstawowej wartości argumentu w wywoływanym kodzie procedury  
  
1.  W deklaracji procedury, należy określić [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametru odpowiadającego atrybutowi argument.  
  
2.  W wywoływanym kodzie należy przekazać można modyfikować elementu programistycznego jako argument.  
  
3.  W wywoływanym kodzie nie należy umieszczać argument w nawiasach na liście argumentów.  
  
4.  W kodzie procedury należy użyć nazwy parametru do przypisania wartości do elementu bazowego w wywoływanym kodzie.  
  
 Zobacz przykład dalej na dół demonstracyjne.  
  
## <a name="changing-local-copies"></a>Zmiana kopiami lokalnymi  
 Jeśli element podstawowy kod wywołujący jest elementem niemodyfikowalnymi lub jeśli argument jest przekazywany `ByVal`, procedury nie można zmienić jego wartość w wywoływanym kodzie. Procedurę można zmieniać swojej lokalnej kopii takich argumentu.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Aby zmienić kopię argumentu procedury w kodzie procedury  
  
1.  W deklaracji procedury, należy określić [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) parametru odpowiadającego atrybutowi argument.  
  
     —lub—  
  
     W wywoływanym kodzie należy ująć argument w nawiasach na liście argumentów. Zmusza to Visual Basic do przekazywania argumentu przez wartość, nawet wtedy, gdy odpowiedni parametr określa `ByRef`.  
  
2.  W kodzie procedury należy użyć nazwy parametru do przypisania wartości do lokalnej kopi argumentu. Podstawową wartość w kod wywołujący nie jest zmieniany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwie procedury używające zmiennej tablicy i działać na jego elementach. `increase` Procedura dodaje po prostu jednym do każdego elementu. `replace` Procedury przypisuje nową tablicę z parametrem `a()` , a następnie dodaje je do każdego elementu.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41". Ponieważ tablicy `n` jest typem referencyjnym `replace` można zmienić jej członków, nawet jeśli jest mechanizm przekazywania `ByVal`.  
  
 Drugi `MsgBox` wywołać Wyświetla "po replace(n): 101, 201, 301". Ponieważ `n` jest przekazywany `ByRef`, `replace` można zmodyfikować zmienną `n` w wywoływanym kodzie i przypisać nową tablicę do niego. Ponieważ `n` jest typem referencyjnym `replace` można również zmienić jej członków.  
  
 Aby uniemożliwić procedurę modyfikowania zmiennej w wywoływanym kodzie. Zobacz [jak: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jeśli zmienna jest przekazywane przez odwołanie, musisz użyć `ByRef` — słowo kluczowe, aby określić, ten mechanizm.  
  
 Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości. Jednak dobrą praktyką, aby uwzględnić albo programowania jest [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr. Dzięki temu można łatwiej odczytać kodu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Z zezwoleniem na procedury zmienić wartość argumentu w wywoływanym kodzie bazowego zawsze to potencjalne zagrożenie. Upewnij się, że oczekiwane tę wartość można zmienić i przygotowywane do sprawdzania poprawności, przed jego użyciem.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Różnice między przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Instrukcje: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Instrukcje: Wymuszanie być przekazywany przez wartość argumentu](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
