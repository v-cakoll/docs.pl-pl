---
title: Zagnieżdżone struktury sterujące (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: 13e2c5c8d818a09ec5e77ec47fe8a2c83b675d82
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409799"
---
# <a name="nested-control-structures-visual-basic"></a>Zagnieżdżone struktury sterujące (Visual Basic)
Instrukcje kontroli wewnątrz innych instrukcji sterowania można umieścić na przykład `If...Then...Else` blokowania w ramach `For...Next` pętli. Instrukcją sterowania, umieszczone wewnątrz innej instrukcji sterowania jest nazywany *zagnieżdżonych*.  
  
## <a name="nesting-levels"></a>Poziomów zagnieżdżenia  
 Mogą być zagnieżdżone struktury sterujące w języku Visual Basic na dowolną liczbę poziomów. Jest to powszechną praktyką, aby zagnieżdżone struktury przez wcięcia treść każdej z nich był bardziej czytelny. Edytor środowiska (IDE) zintegrowanego rozwoju wykonuje to automatycznie.  
  
 W poniższym przykładzie procedury `sumRows` dodaje razem dodatnią elementy każdy wiersz macierzy.  
  
```vb
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 W powyższym przykładzie pierwsze `Next` instrukcji zamyka wewnętrzny `For` pętli, a ostatni `Next` instrukcji zamyka zewnętrzny `For` pętli.  
  
 Podobnie, w zagnieżdżonych `If` instrukcji `End If` instrukcji automatyczne stosowanie do najbliższej przed `If` instrukcji. Zagnieżdżone `Do` pętli działają w podobny sposób, przy użyciu najbardziej wewnętrzną funkcją `Loop` instrukcji dopasowania najbardziej wewnętrzną funkcją `Do` instrukcji.  
  
> [!NOTE]
>  Dla wielu struktur sterowania po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze, zostały wyróżnione. Na przykład po kliknięciu `If` w `If...Then...Else` budowy, wszystkie wystąpienia elementu `If`, `Then`, `ElseIf`, `Else`, i `End If` w konstrukcji są wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego słów kluczowych, naciśnij klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Różne rodzaje struktur sterujących zagnieżdżania  
 Można zagnieżdżać jednego rodzaju strukturze kontroli w ramach innego rodzaju. W poniższym przykładzie użyto `With` block wewnątrz `For Each` pętli i zagnieżdżone `If` blokuje wewnątrz `With` bloku.  
  
```vb
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>Nakładające się struktury sterujące  
 Nie może nakładać się struktur sterujących. Oznacza to, dowolnej struktury zagnieżdżonej musi być całkowicie zawarty w ramach następnego najbardziej wewnętrznej struktury. Na przykład, poniższy rozmieszczenie jest nieprawidłowy ponieważ `For` pętli kończy się przed wewnętrzny `With` kończy blok.  
  
 ![Diagram przedstawia przykład nieprawidłowego zagnieżdżenia.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Kompilator Visual Basic wykrywa takie nakładających się struktury sterujące i sygnalizuje błąd kompilacji.  
  
## <a name="see-also"></a>Zobacz także
- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
