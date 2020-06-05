---
title: Przeciążanie procedury
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363879"
---
# <a name="procedure-overloading-visual-basic"></a>Przeciążanie procedury (Visual Basic)

*Przeciążanie* procedury oznacza zdefiniowanie jej w wielu wersjach przy użyciu takiej samej nazwy, ale innych list parametrów. Przeciążanie polega na zdefiniowaniu kilku ściśle powiązanych wersji procedury bez konieczności odróżnienia ich według nazwy. Można to zrobić, zmieniając listę parametrów.

## <a name="overloading-rules"></a>Reguły przeciążania

W przypadku przeciążenia procedury stosowane są następujące reguły:

- **Ta sama nazwa**. Każda przeciążona wersja musi używać tej samej nazwy procedury.

- **Inny podpis**. Każda przeciążona wersja musi różnić się od wszystkich innych przeciążonych wersji w co najmniej jednej z następujących kwestii:

  - Liczba parametrów

  - Kolejność parametrów

  - Typy danych parametrów

  - Liczba parametrów typu (dla procedury ogólnej)

  - Zwracany typ (tylko dla operatora konwersji)

  Wraz z nazwą procedury, poprzednie elementy są zbiorczo nazywane *podpisem* procedury. Gdy wywołujesz przeciążoną procedurę, kompilator używa podpisu, aby sprawdzić, czy wywołanie jest prawidłowo zgodne z definicją.

- **Elementy nie są częścią podpisu**. Nie można przeciążać procedury bez różnicowania podpisu. W szczególności nie można przeciążać procedury, zmieniając tylko jeden lub więcej z następujących elementów:

  - Słowa kluczowe modyfikatora procedury, takie jak `Public` , `Shared` , i`Static`

  - Nazwy parametrów lub parametrów typu

  - Ograniczenia parametru typu (dla procedury ogólnej)

  - Słowa kluczowe modyfikatora parametru, takie jak `ByRef` i`Optional`

  - Czy zwraca wartość

  - Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)

  Elementy z powyższej listy nie są częścią podpisu. Chociaż nie można ich używać do rozróżniania przeciążonych wersji, można różnicować je między przeciążonymi wersjami, które są poprawnie różnicowane według ich sygnatur.

- **Argumenty z późnym wiązaniem**. Jeśli zamierzasz przekazać zmienną obiektu z późnym wiązaniem do przeciążonej wersji, musisz zadeklarować odpowiedni parametr jako <xref:System.Object> .

## <a name="multiple-versions-of-a-procedure"></a>Wiele wersji procedury

Załóżmy, że piszesz `Sub` procedurę w celu opublikowania transakcji w oparciu o saldo klienta i chcesz mieć możliwość odwoływania się do klienta według nazwy lub numeru konta. Aby to umożliwić, można zdefiniować dwie różne `Sub` procedury, jak w poniższym przykładzie:

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>Przeciążone wersje

Alternatywą jest przeciążanie pojedynczej nazwy procedury. Możesz użyć słowa kluczowego [overloads](../../../language-reference/modifiers/overloads.md) , aby zdefiniować wersję procedury dla każdej listy parametrów w następujący sposób:

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>Dodatkowe przeciążenia

Jeśli chcesz również zaakceptować kwotę transakcji w `Decimal` lub `Single` , możesz dodatkowo przeciążyć, `post` Aby zezwolić na tę odmianę. Jeśli przeciążenia zostały wykonane w poprzednim przykładzie, będziesz mieć cztery `Sub` procedury, wszystkie o tej samej nazwie, ale z czterema różnymi podpisami.

## <a name="advantages-of-overloading"></a>Zalety przeciążenia

Zaletą przeładowania procedury jest elastyczność wywołania. Aby użyć `post` procedury zadeklarowanej w poprzednim przykładzie, kod wywołujący może uzyskać identyfikację klienta jako `String` albo a `Integer` , a następnie wywołać tę samą procedurę w obu przypadkach. Zostało to przedstawione w poniższym przykładzie:

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
- [Przeciążenia](../../../language-reference/modifiers/overloads.md)
- [Typy ogólne w Visual Basic](../data-types/generic-types.md)
