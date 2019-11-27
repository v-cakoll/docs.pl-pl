---
title: Exit, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345938"
---
# <a name="exit-statement-visual-basic"></a>Exit — Instrukcja (Visual Basic)

Zamyka procedurę lub blok i natychmiast przenosi kontrolę do instrukcji następującej po wywołaniu procedury lub definicji bloku.

## <a name="syntax"></a>Składnia

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Instrukcje

 `Exit Do`  
 Natychmiast zamyka pętlę `Do`, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `Loop`. `Exit Do` można używać tylko wewnątrz pętli `Do`. W przypadku użycia w zagnieżdżonych pętlach `Do` `Exit Do` opuszcza najbardziej zachodzącą pętlę i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.

 `Exit For`  
 Natychmiast zamyka pętlę `For`, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `Next`. `Exit For` można używać tylko wewnątrz pętli `For`...`Next` lub `For Each`...`Next`. W przypadku użycia w zagnieżdżonych pętlach `For` `Exit For` opuszcza najbardziej zachodzącą pętlę i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.

 `Exit Function`  
 Natychmiast opuszcza procedurę `Function`, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała procedurę `Function`. `Exit Function` można używać tylko wewnątrz procedury `Function`.

 Aby określić wartość zwracaną, można przypisać wartość do nazwy funkcji w wierszu przed instrukcją `Exit Function`. Aby przypisać wartość zwracaną i zamknąć funkcję w jednej instrukcji, zamiast tego można użyć [instrukcji return](return-statement.md).

 `Exit Property`  
 Natychmiast opuszcza procedurę `Property`, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołała procedurę `Property`, czyli z instrukcją żądającą lub ustawieniem wartości właściwości. `Exit Property` można używać tylko wewnątrz procedury `Get` lub `Set`j właściwości.

 Aby określić wartość zwracaną w procedurze `Get`, można przypisać wartość do nazwy funkcji w wierszu przed instrukcją `Exit Property`. Aby przypisać wartość zwracaną i zamknąć procedurę `Get` w jednej instrukcji, można zamiast tego użyć instrukcji `Return`.

 W procedurze `Set` instrukcja `Exit Property` jest równoważna instrukcji `Return`.

 `Exit Select`  
 Natychmiast zamyka blok `Select Case`, w którym występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `End Select`. `Exit Select` można używać tylko wewnątrz instrukcji `Select Case`.

 `Exit Sub`  
 Natychmiast opuszcza procedurę `Sub`, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała procedurę `Sub`. `Exit Sub` można używać tylko wewnątrz procedury `Sub`.

 W procedurze `Sub` instrukcja `Exit Sub` jest równoważna instrukcji `Return`.

 `Exit Try`  
 Natychmiast zamyka blok `Try` lub `Catch`, w którym występuje. Wykonywanie jest kontynuowane z blokiem `Finally`, jeśli istnieje, lub instrukcji po instrukcji `End Try` w przeciwnym razie. `Exit Try` można używać tylko wewnątrz bloku `Try` lub `Catch`, a nie wewnątrz bloku `Finally`.

 `Exit While`  
 Natychmiast zamyka pętlę `While`, w której występuje. Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `End While`. `Exit While` można używać tylko wewnątrz pętli `While`. Gdy jest używany w zagnieżdżonych pętlach `While`, `Exit While` przenosi kontrolkę do pętli, która jest jednym zagnieżdżonym poziomem powyżej pętli, w której występuje `Exit While`.

## <a name="remarks"></a>Uwagi

Nie należy mylić instrukcji `Exit` z instrukcjami `End`. `Exit` nie definiuje końca instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie warunek pętli przerywa pętlę, gdy zmienna `index` jest większa niż 100. Instrukcja `If` w pętli, jednak powoduje, że instrukcja `Exit Do` przerywa pętlę, gdy zmienna indeksu jest większa niż 10.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Przykład

Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction`, a następnie używa `Exit Function` do powrotu z funkcji:

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>Przykład

Poniższy przykład używa [instrukcji return](return-statement.md) do przypisania wartości zwracanej i opuszczenia funkcji:

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>Zobacz także

- [Continue, instrukcja](continue-statement.md)
- [Do...Loop, instrukcja](do-loop-statement.md)
- [End, instrukcja](end-statement.md)
- [For Each...Next, instrukcja](for-each-next-statement.md)
- [For...Next, instrukcja](for-next-statement.md)
- [Function, instrukcja](function-statement.md)
- [Return, instrukcja](return-statement.md)
- [Stop, instrukcja](stop-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
