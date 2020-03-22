---
title: Zagnieżdżone struktury sterujące
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
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266927"
---
# <a name="nested-control-structures-visual-basic"></a>Zagnieżdżone struktury sterujące (Visual Basic)
Instrukcje kontroli można umieścić wewnątrz innych `If...Then...Else` instrukcji kontroli, na przykład bloku w `For...Next` pętli. Instrukcja kontroli umieszczona wewnątrz innej instrukcji kontroli jest *uważana za zagnieżdżoną*.  
  
## <a name="nesting-levels"></a>Poziomy zagnieżdżania  
 Struktury sterowania w języku Visual Basic mogą być zagnieżdżone do dowolną liczbę poziomów. Powszechną praktyką jest uczynienie zagnieżdżonych struktur bardziej czytelnymi przez wcięcie ciała każdego z nich. Edytor zintegrowanego środowiska programistycznego (IDE) automatycznie to robi.  
  
 W poniższym przykładzie `sumRows` procedura dodaje razem dodatnie elementy każdego wiersza macierzy.  
  
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
  
 W poprzednim przykładzie pierwsza `Next` instrukcja zamyka `For` wewnętrzną `Next` pętlę, a `For` ostatnia instrukcja zamyka zewnętrzną pętlę.  
  
 Podobnie w zagnieżdżonych `If` instrukcji `End If` instrukcje są `If` automatycznie stosowane do najbliższej wcześniejszej instrukcji. Pętle `Do` zagnieżdżone działają w `Loop` podobny sposób, `Do` z najbardziej wewnętrzną instrukcją pasującą do najbardziej wewnętrznej instrukcji.  
  
> [!NOTE]
> W przypadku wielu struktur kontrolnych po kliknięciu słowa kluczowego wszystkie słowa kluczowe w strukturze są wyróżnione. Na przykład po `If` kliknięciu `If...Then...Else` w konstrukcji wszystkie `If` `Then`wystąpienia `ElseIf` `Else`, `End If` , , i w konstrukcji są podświetlone. Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL+SHIFT+STRZAŁKA W DÓŁ lub CTRL+SHIFT+STRZAŁKA W GÓRĘ.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Zagnieżdżanie różnych rodzajów struktur kontrolnych  
 Można zagnieździć jeden rodzaj struktury kontroli w innym rodzaju. W `With` poniższym przykładzie użyto bloku wewnątrz `For Each` pętli i zagnieżdżonych `If` bloków wewnątrz `With` bloku.  
  
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
  
## <a name="overlapping-control-structures"></a>Nakładające się struktury sterowania  
 Nie można nakładać struktur sterowania. Oznacza to, że każda struktura zagnieżdżona musi być całkowicie zawarta w następnej najbardziej wewnętrznej strukturze. Na przykład następujący układ jest `For` nieprawidłowy, ponieważ `With` pętla kończy się przed zakończeniem bloku wewnętrznego.  
  
 ![Diagram, który pokazuje przykład nieprawidłowego zagnieżdżania.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Kompilator języka Visual Basic wykrywa takie nakładające się struktury kontroli i sygnalizuje błąd w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
