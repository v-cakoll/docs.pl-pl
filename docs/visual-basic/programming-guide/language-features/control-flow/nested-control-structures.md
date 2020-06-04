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
ms.openlocfilehash: 539ad639320615c1e53176fe47e5468864aa21d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414392"
---
# <a name="nested-control-structures-visual-basic"></a>Zagnieżdżone struktury sterujące (Visual Basic)
Można umieścić instrukcje sterujące wewnątrz innych instrukcji sterowania, na przykład `If...Then...Else` blok w `For...Next` pętli. Instrukcja sterująca umieszczona wewnątrz innej instrukcji sterującej jest określana jako *zagnieżdżona*.  
  
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
  
 W poprzednim przykładzie pierwsza `Next` instrukcja zamyka pętlę wewnętrzną, `For` a Ostatnia `Next` instrukcja zamyka pętlę zewnętrzną `For` .  
  
 Podobnie, w `If` instrukcjach zagnieżdżonych `End If` instrukcje są automatycznie stosowane do najbliższej wcześniejszej `If` instrukcji. `Do`Pętle zagnieżdżone działają w podobny sposób, przy użyciu najbardziej wewnętrznej `Loop` instrukcji pasującej do najbardziej wewnętrznej `Do` instrukcji.  
  
> [!NOTE]
> W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze. Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji wszystkie wystąpienia elementów,,, `If` `Then` `ElseIf` `Else` i `End If` w konstrukcji są wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Zagnieżdżanie różnych rodzajów struktur kontroli  
 Można zagnieżdżać jeden rodzaj struktury kontroli w innym rodzaju. Poniższy przykład używa `With` bloku wewnątrz `For Each` pętli i zagnieżdżonych `If` bloków wewnątrz `With` bloku.  
  
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
 Nie można nakładać się na struktury formantów. Oznacza to, że jakakolwiek struktura zagnieżdżona musi być całkowicie zawarta w obrębie następnej wewnętrznej struktury. Na przykład następujące rozmieszczenie jest nieprawidłowe, ponieważ `For` Pętla kończy się przed `With` zakończeniem wewnętrznego bloku.  
  
 ![Diagram przedstawiający przykład nieprawidłowego zagnieżdżania.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Kompilator Visual Basic wykrywa te nakładające się struktury kontroli i sygnalizuje błąd czasu kompilacji.  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](index.md)
- [Struktury decyzji](decision-structures.md)
- [Struktury pętli](loop-structures.md)
- [Inne struktury sterujące](other-control-structures.md)
