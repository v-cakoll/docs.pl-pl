---
title: 'Instrukcje: Utwórz procedurę (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216718"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Porady: Utwórz procedurę (Visual Basic)

Należy`Sub` ująć procedurę między początkową instrukcją deklaracji (lub `Function`) i kończącą się instrukcją deklaracji`End Sub` ( `End Function`lub). Cały kod procedury należy do tych instrukcji.

 Procedura nie może zawierać innej procedury, dlatego jej instrukcje początkowe i końcowe muszą znajdować się poza inną procedurą.

 Jeśli masz kod, który wykonuje to samo zadanie w różnych miejscach, możesz napisać zadanie jeden raz jako procedurę, a następnie wywołać ją z różnych miejsc w kodzie.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Aby utworzyć procedurę, która nie zwraca wartości

1. Poza inną procedurą Użyj `Sub` instrukcji, a po niej `End Sub` instrukcji.

2. W instrukcji należy `Sub` przestrzegać słowa kluczowego o nazwie procedury, a następnie listy parametrów w nawiasach. `Sub`

3. Umieść instrukcje kodu procedury między `Sub` instrukcjami i. `End Sub`

### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedurę zwracającą wartość

1. Poza inną procedurą Użyj `Function` instrukcji, a po niej `End Function` instrukcji.

2. W instrukcji wykonaj słowo kluczowe z nazwą procedury, następnie listę parametrów w nawiasach, a następnie `As` klauzulę określającą typ danych zwracanej wartości. `Function` `Function`

3. Umieść instrukcje kodu procedury między `Function` instrukcjami i. `End Function`

4. `Return` Użyj instrukcji, aby zwrócić wartość do kodu wywołującego.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Aby połączyć swoją nową procedurę z starymi powtarzalnymi blokami kodu

1. Upewnij się, że definiujesz nową procedurę w miejscu, do którego stary kod ma do niego dostęp.

2. W starym, powtarzającym się bloku kodu Zastąp instrukcje, które wykonują powtarzające się zadanie z pojedynczą `Sub` instrukcją, która wywołuje procedurę lub. `Function`

3. Jeśli procedura jest `Function` zwracająca wartość, upewnij się, że instrukcja wywołująca wykonuje akcję z zwracaną wartością, taką jak przechowywanie jej w zmiennej, lub w przeciwnym razie wartość zostanie utracona.

## <a name="example"></a>Przykład

 Poniższa `Function` procedura oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, z uwzględnieniem wartości pozostałych dwóch stron:

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
