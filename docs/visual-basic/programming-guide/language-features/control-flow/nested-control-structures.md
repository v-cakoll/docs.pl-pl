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
ms.openlocfilehash: ec3d4d477290480cdfa0f5b1c88aa82c81040d11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nested-control-structures-visual-basic"></a>Zagnieżdżone struktury sterujące (Visual Basic)
Możesz na przykład umieścić instrukcji sterowania wewnątrz innych instrukcji sterowania `If...Then...Else` zablokować w `For...Next` pętli. Instrukcji sterowania umieszczony wewnątrz innego instrukcji sterowania jest określany jako *zagnieżdżonych*.  
  
## <a name="nesting-levels"></a>Poziomów zagnieżdżenia  
 Struktury sterujące w języku Visual Basic można zagnieżdżać dowolną liczbę poziomów. Jest powszechną praktyką było odczytywać struktury zagnieżdżone przez wcięcia treści każdego z nich. Edytor środowiska (IDE) zintegrowanego rozwoju automatycznie robi to.  
  
 W poniższym przykładzie procedura `sumRows` dodaje razem dodatnią elementy każdego wiersza w macierzy.  
  
```  
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
  
 W powyższym przykładzie pierwszy `Next` instrukcji zamyka wewnętrzny `For` pętli oraz za ostatni `Next` instrukcji zamyka zewnętrznego `For` pętli.  
  
 Podobnie, w zagnieżdżonych `If` instrukcji `End If` instrukcje dotyczą automatycznie najbliższej przed `If` instrukcji. Zagnieżdżone `Do` pętle działa w podobny sposób, z najbardziej wewnętrzną funkcją `Loop` instrukcji dopasowania najbardziej wewnętrzną funkcją `Do` instrukcji.  
  
> [!NOTE]
>  Dla wielu struktur kontroli po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze wyróżniono. Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji, wszystkie wystąpienia `If`, `Then`, `ElseIf`, `Else`, i `End If` są wyróżniane w konstrukcji. Aby przejść do następnej lub poprzedniej wyróżnione słowa kluczowego, naciśnij kombinację klawiszy CTRL + SHIFT + Strzałka w dół strzałkę lub CTRL + SHIFT + Strzałka w górę, strzałki.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Zagnieżdżania różnego rodzaju struktury sterujące  
 Można zagnieżdżać jednego rodzaju Struktura kontroli w ramach innego rodzaju. W poniższym przykładzie użyto `With` zablokować wewnątrz `For Each` pętli i zagnieżdżone `If` bloki wewnątrz `With` bloku.  
  
```  
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
 Struktury sterujące nie mogą się nakładać. Oznacza to, wszystkie zagnieżdżone struktury musi być całkowicie zawarty w strukturze najbardziej dalej. Na przykład następujące rozmieszczenia jest nieprawidłowy ponieważ `For` pętli kończy się przed wewnętrzny `With` kończy bloku.  
  
 ![Graficzny diagram nieprawidłowego zagnieżdżenia](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Nieprawidłowy zagnieżdżanie do i z struktury  
  
 Kompilator Visual Basic wykrywa takie nakładające się struktury sterujące i sygnalizuje błąd kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
