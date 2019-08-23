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
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941684"
---
# <a name="nested-control-structures-visual-basic"></a>Zagnieżdżone struktury sterujące (Visual Basic)
Można umieścić instrukcje sterujące wewnątrz innych instrukcji sterowania, na przykład `If...Then...Else` blok `For...Next` w pętli. Instrukcja sterująca umieszczona wewnątrz innej instrukcji sterującej jest określana jako *zagnieżdżona*.  
  
## <a name="nesting-levels"></a>Poziomy zagnieżdżania  
 Struktury formantów w Visual Basic mogą być zagnieżdżane do tylu poziomów. Powszechną zaletą jest bardziej czytelność zagnieżdżonych struktur przez wcięcie treści każdej z nich. Edytor zintegrowanego środowiska programistycznego (IDE) automatycznie robi to.  
  
 W poniższym przykładzie procedura `sumRows` dodaje razem elementy dodatnie każdego wiersza macierzy.  
  
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
  
 W poprzednim przykładzie `Next` Pierwsza instrukcja zamyka pętlę wewnętrzną `For` , a Ostatnia `Next` instrukcja zamyka pętlę zewnętrzną `For` .  
  
 Podobnie, w instrukcjach `If` zagnieżdżonych `End If` instrukcje są automatycznie stosowane do najbliższej `If` wcześniejszej instrukcji. Pętle zagnieżdżone `Do` działają w podobny sposób, przy użyciu najbardziej `Loop` wewnętrznej instrukcji pasującej `Do` do najbardziej wewnętrznej instrukcji.  
  
> [!NOTE]
> W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze. `If` Na przykład po kliknięciu `If...Then...Else` w konstrukcji `Then` `End If` wszystkie wystąpienia elementów `If`, ,,iwkonstrukcjisąwyróżnione.`Else` `ElseIf` Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Zagnieżdżanie różnych rodzajów struktur kontroli  
 Można zagnieżdżać jeden rodzaj struktury kontroli w innym rodzaju. Poniższy przykład używa `With` bloku `For Each` wewnątrz `If` pętli`With` i zagnieżdżonych bloków wewnątrz bloku.  
  
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
  
## <a name="overlapping-control-structures"></a>Nakładające się struktury kontroli  
 Nie można nakładać się na struktury formantów. Oznacza to, że jakakolwiek struktura zagnieżdżona musi być całkowicie zawarta w obrębie następnej wewnętrznej struktury. Na przykład następujące rozmieszczenie jest nieprawidłowe, `For` ponieważ pętla kończy się przed zakończeniem wewnętrznego `With` bloku.  
  
 ![Diagram przedstawiający przykład nieprawidłowego zagnieżdżania.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Kompilator Visual Basic wykrywa te nakładające się struktury kontroli i sygnalizuje błąd czasu kompilacji.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
