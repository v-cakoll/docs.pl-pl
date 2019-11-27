---
title: 'Porady: tworzenie procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344909"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Porady: tworzenie procedury (Visual Basic)

Należy ująć procedurę między początkową instrukcją deklaracji (`Sub` lub `Function`) i kończącą się instrukcją deklaracji (`End Sub` lub `End Function`). Cały kod procedury należy do tych instrukcji.

 Procedura nie może zawierać innej procedury, dlatego jej instrukcje początkowe i końcowe muszą znajdować się poza inną procedurą.

 Jeśli masz kod, który wykonuje to samo zadanie w różnych miejscach, możesz napisać zadanie jeden raz jako procedurę, a następnie wywołać ją z różnych miejsc w kodzie.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Aby utworzyć procedurę, która nie zwraca wartości

1. Poza każdą inną procedurę Użyj instrukcji `Sub`, a po niej instrukcji `End Sub`.

2. W instrukcji `Sub` postępuj według słowa kluczowego `Sub` z nazwą procedury, a następnie listę parametrów w nawiasach.

3. Umieść instrukcje kodu procedury między instrukcjami `Sub` i `End Sub`.

### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedurę zwracającą wartość

1. Poza każdą inną procedurę Użyj instrukcji `Function`, a po niej instrukcji `End Function`.

2. W instrukcji `Function` postępuj zgodnie ze słowem kluczowym `Function` z nazwą procedury, następnie listą parametrów w nawiasach, a następnie klauzulą `As` określającą typ danych wartości zwracanej.

3. Umieść instrukcje kodu procedury między instrukcjami `Function` i `End Function`.

4. Użyj instrukcji `Return`, aby zwrócić wartość do kodu wywołującego.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Aby połączyć swoją nową procedurę z starymi powtarzalnymi blokami kodu

1. Upewnij się, że definiujesz nową procedurę w miejscu, do którego stary kod ma do niego dostęp.

2. W starym, powtarzającym się bloku kodu Zastąp instrukcje, które wykonują powtarzające się zadanie z pojedynczą instrukcją wywołującą procedurę `Sub` lub `Function`.

3. Jeśli procedura jest `Function`, która zwraca wartość, upewnij się, że instrukcja wywołująca wykonuje akcję z zwracaną wartością, taką jak przechowywanie jej w zmiennej lub wartość zostanie utracona.

## <a name="example"></a>Przykład

 Poniższa procedura `Function` oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, z uwzględnieniem wartości pozostałych dwóch stron:

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Procedury](index.md)
- [Sub, procedury](sub-procedures.md)
- [Procedury funkcji](function-procedures.md)
- [Procedury właściwości](property-procedures.md)
- [Procedury operatorów](operator-procedures.md)
- [Parametry i argumenty procedur](procedure-parameters-and-arguments.md)
- [Procedury rekursywne](recursive-procedures.md)
- [Przeciążanie procedury](procedure-overloading.md)
- [Obiekty i klasy](../objects-and-classes/index.md)
- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
