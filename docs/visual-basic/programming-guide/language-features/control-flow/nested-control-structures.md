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
ms.openlocfilehash: c016722332dafa3d3be91a1e9e98cc0ce9a49717
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835196"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="4aa59-102">Zagnieżdżone struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4aa59-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="4aa59-103">Instrukcje kontroli wewnątrz innych instrukcji sterowania można umieścić na przykład `If...Then...Else` blokowania w ramach `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="4aa59-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="4aa59-104">Instrukcją sterowania, umieszczone wewnątrz innej instrukcji sterowania jest nazywany *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="4aa59-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="4aa59-105">Poziomów zagnieżdżenia</span><span class="sxs-lookup"><span data-stu-id="4aa59-105">Nesting Levels</span></span>  
 <span data-ttu-id="4aa59-106">Mogą być zagnieżdżone struktury sterujące w języku Visual Basic na dowolną liczbę poziomów.</span><span class="sxs-lookup"><span data-stu-id="4aa59-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="4aa59-107">Jest to powszechną praktyką, aby zagnieżdżone struktury przez wcięcia treść każdej z nich był bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="4aa59-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="4aa59-108">Edytor środowiska (IDE) zintegrowanego rozwoju wykonuje to automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4aa59-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="4aa59-109">W poniższym przykładzie procedury `sumRows` dodaje razem dodatnią elementy każdy wiersz macierzy.</span><span class="sxs-lookup"><span data-stu-id="4aa59-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="4aa59-110">W powyższym przykładzie pierwsze `Next` instrukcji zamyka wewnętrzny `For` pętli, a ostatni `Next` instrukcji zamyka zewnętrzny `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="4aa59-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="4aa59-111">Podobnie, w zagnieżdżonych `If` instrukcji `End If` instrukcji automatyczne stosowanie do najbliższej przed `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4aa59-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="4aa59-112">Zagnieżdżone `Do` pętli działają w podobny sposób, przy użyciu najbardziej wewnętrzną funkcją `Loop` instrukcji dopasowania najbardziej wewnętrzną funkcją `Do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4aa59-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aa59-113">Dla wielu struktur sterowania po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze, zostały wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="4aa59-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="4aa59-114">Na przykład po kliknięciu `If` w `If...Then...Else` budowy, wszystkie wystąpienia elementu `If`, `Then`, `ElseIf`, `Else`, i `End If` w konstrukcji są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="4aa59-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="4aa59-115">Aby przejść do następnego lub poprzedniego wyróżnionego słów kluczowych, naciśnij klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka.</span><span class="sxs-lookup"><span data-stu-id="4aa59-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="4aa59-116">Różne rodzaje struktur sterujących zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="4aa59-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="4aa59-117">Można zagnieżdżać jednego rodzaju strukturze kontroli w ramach innego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="4aa59-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="4aa59-118">W poniższym przykładzie użyto `With` block wewnątrz `For Each` pętli i zagnieżdżone `If` blokuje wewnątrz `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="4aa59-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="4aa59-119">Nakładające się struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="4aa59-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="4aa59-120">Nie może nakładać się struktur sterujących.</span><span class="sxs-lookup"><span data-stu-id="4aa59-120">You cannot overlap control structures.</span></span> <span data-ttu-id="4aa59-121">Oznacza to, dowolnej struktury zagnieżdżonej musi być całkowicie zawarty w ramach następnego najbardziej wewnętrznej struktury.</span><span class="sxs-lookup"><span data-stu-id="4aa59-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="4aa59-122">Na przykład, poniższy rozmieszczenie jest nieprawidłowy ponieważ `For` pętli kończy się przed wewnętrzny `With` kończy blok.</span><span class="sxs-lookup"><span data-stu-id="4aa59-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram przedstawia przykład nieprawidłowego zagnieżdżenia.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 <span data-ttu-id="4aa59-124">Kompilator Visual Basic wykrywa takie nakładających się struktury sterujące i sygnalizuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4aa59-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa59-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4aa59-125">See also</span></span>

- [<span data-ttu-id="4aa59-126">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="4aa59-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="4aa59-127">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="4aa59-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="4aa59-128">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="4aa59-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="4aa59-129">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="4aa59-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
