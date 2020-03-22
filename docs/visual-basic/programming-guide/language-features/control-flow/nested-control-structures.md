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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="0354c-102">Zagnieżdżone struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0354c-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="0354c-103">Instrukcje kontroli można umieścić wewnątrz innych `If...Then...Else` instrukcji kontroli, na przykład bloku w `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="0354c-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="0354c-104">Instrukcja kontroli umieszczona wewnątrz innej instrukcji kontroli jest *uważana za zagnieżdżoną*.</span><span class="sxs-lookup"><span data-stu-id="0354c-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="0354c-105">Poziomy zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="0354c-105">Nesting Levels</span></span>  
 <span data-ttu-id="0354c-106">Struktury sterowania w języku Visual Basic mogą być zagnieżdżone do dowolną liczbę poziomów.</span><span class="sxs-lookup"><span data-stu-id="0354c-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="0354c-107">Powszechną praktyką jest uczynienie zagnieżdżonych struktur bardziej czytelnymi przez wcięcie ciała każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="0354c-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="0354c-108">Edytor zintegrowanego środowiska programistycznego (IDE) automatycznie to robi.</span><span class="sxs-lookup"><span data-stu-id="0354c-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="0354c-109">W poniższym przykładzie `sumRows` procedura dodaje razem dodatnie elementy każdego wiersza macierzy.</span><span class="sxs-lookup"><span data-stu-id="0354c-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="0354c-110">W poprzednim przykładzie pierwsza `Next` instrukcja zamyka `For` wewnętrzną `Next` pętlę, a `For` ostatnia instrukcja zamyka zewnętrzną pętlę.</span><span class="sxs-lookup"><span data-stu-id="0354c-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="0354c-111">Podobnie w zagnieżdżonych `If` instrukcji `End If` instrukcje są `If` automatycznie stosowane do najbliższej wcześniejszej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0354c-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="0354c-112">Pętle `Do` zagnieżdżone działają w `Loop` podobny sposób, `Do` z najbardziej wewnętrzną instrukcją pasującą do najbardziej wewnętrznej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0354c-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0354c-113">W przypadku wielu struktur kontrolnych po kliknięciu słowa kluczowego wszystkie słowa kluczowe w strukturze są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="0354c-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="0354c-114">Na przykład po `If` kliknięciu `If...Then...Else` w konstrukcji wszystkie `If` `Then`wystąpienia `ElseIf` `Else`, `End If` , , i w konstrukcji są podświetlone.</span><span class="sxs-lookup"><span data-stu-id="0354c-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="0354c-115">Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL+SHIFT+STRZAŁKA W DÓŁ lub CTRL+SHIFT+STRZAŁKA W GÓRĘ.</span><span class="sxs-lookup"><span data-stu-id="0354c-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="0354c-116">Zagnieżdżanie różnych rodzajów struktur kontrolnych</span><span class="sxs-lookup"><span data-stu-id="0354c-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="0354c-117">Można zagnieździć jeden rodzaj struktury kontroli w innym rodzaju.</span><span class="sxs-lookup"><span data-stu-id="0354c-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="0354c-118">W `With` poniższym przykładzie użyto bloku wewnątrz `For Each` pętli i zagnieżdżonych `If` bloków wewnątrz `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="0354c-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="0354c-119">Nakładające się struktury sterowania</span><span class="sxs-lookup"><span data-stu-id="0354c-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="0354c-120">Nie można nakładać struktur sterowania.</span><span class="sxs-lookup"><span data-stu-id="0354c-120">You cannot overlap control structures.</span></span> <span data-ttu-id="0354c-121">Oznacza to, że każda struktura zagnieżdżona musi być całkowicie zawarta w następnej najbardziej wewnętrznej strukturze.</span><span class="sxs-lookup"><span data-stu-id="0354c-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="0354c-122">Na przykład następujący układ jest `For` nieprawidłowy, ponieważ `With` pętla kończy się przed zakończeniem bloku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0354c-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram, który pokazuje przykład nieprawidłowego zagnieżdżania.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="0354c-124">Kompilator języka Visual Basic wykrywa takie nakładające się struktury kontroli i sygnalizuje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0354c-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0354c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0354c-125">See also</span></span>

- [<span data-ttu-id="0354c-126">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="0354c-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="0354c-127">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="0354c-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="0354c-128">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="0354c-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="0354c-129">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="0354c-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
