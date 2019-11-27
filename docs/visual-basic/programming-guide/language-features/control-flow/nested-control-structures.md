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
ms.openlocfilehash: 5818b13661fb4415c6f531b741b8a963a80bd2b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348148"
---
# <a name="nested-control-structures-visual-basic"></a>Zagnieżdżone struktury sterujące (Visual Basic)
Można umieścić instrukcje sterujące wewnątrz innych instrukcji sterowania, na przykład blok `If...Then...Else` w pętli `For...Next`. Instrukcja sterująca umieszczona wewnątrz innej instrukcji sterującej jest określana jako *zagnieżdżona*.  
  
## <a name="nesting-levels"></a>Poziomy zagnieżdżania  
 Struktury formantów w Visual Basic mogą być zagnieżdżane do tylu poziomów. Powszechną zaletą jest bardziej czytelność zagnieżdżonych struktur przez wcięcie treści każdej z nich. Edytor zintegrowanego środowiska programistycznego (IDE) automatycznie robi to.  
  
 W poniższym przykładzie procedura `sumRows` dodaje wszystkie elementy dodatnie każdego wiersza macierzy.  
  
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
  
 W powyższym przykładzie pierwsza instrukcja `Next` zamyka wewnętrzną pętlę `For` i ostatnią `Next` instrukcję zamyka pętlę `For` zewnętrznego.  
  
 Podobnie, w zagnieżdżonych instrukcjach `If`, instrukcje `End If` automatycznie stosują się do najbliższej wcześniejszej instrukcji `If`. Zagnieżdżone pętle `Do` działają w podobny sposób, z najbardziej wewnętrznym instrukcją `Loop` pasującą do najbardziej wewnętrznej instrukcji `Do`.  
  
> [!NOTE]
> W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze. Na przykład po kliknięciu `If` w konstrukcji `If...Then...Else` wszystkie wystąpienia `If`, `Then`, `ElseIf`, `Else`i `End If` w konstrukcji są wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Zagnieżdżanie różnych rodzajów struktur kontroli  
 Można zagnieżdżać jeden rodzaj struktury kontroli w innym rodzaju. Poniższy przykład używa bloku `With` wewnątrz pętli `For Each` i zagnieżdżonych bloków `If` wewnątrz bloku `With`.  
  
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
 Nie można nakładać się na struktury formantów. Oznacza to, że jakakolwiek struktura zagnieżdżona musi być całkowicie zawarta w obrębie następnej wewnętrznej struktury. Na przykład następujące rozmieszczenie jest nieprawidłowe, ponieważ pętla `For` kończy się przed przerwaniem wewnętrznego `With` bloku.  
  
 ![Diagram przedstawiający przykład nieprawidłowego zagnieżdżania.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Kompilator Visual Basic wykrywa te nakładające się struktury kontroli i sygnalizuje błąd czasu kompilacji.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
