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
ms.openlocfilehash: 9b10363e2273a22ac7ee3d9a943a1bec4616d232
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185730"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="f9438-102">Zagnieżdżone struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9438-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="f9438-103">Instrukcje kontroli wewnątrz innych instrukcji sterowania można umieścić na przykład `If...Then...Else` blokowania w ramach `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="f9438-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="f9438-104">Instrukcją sterowania, umieszczone wewnątrz innej instrukcji sterowania jest nazywany *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="f9438-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="f9438-105">Poziomów zagnieżdżenia</span><span class="sxs-lookup"><span data-stu-id="f9438-105">Nesting Levels</span></span>  
 <span data-ttu-id="f9438-106">Mogą być zagnieżdżone struktury sterujące w języku Visual Basic na dowolną liczbę poziomów.</span><span class="sxs-lookup"><span data-stu-id="f9438-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="f9438-107">Jest to powszechną praktyką, aby zagnieżdżone struktury przez wcięcia treść każdej z nich był bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="f9438-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="f9438-108">Edytor środowiska (IDE) zintegrowanego rozwoju wykonuje to automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f9438-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="f9438-109">W poniższym przykładzie procedury `sumRows` dodaje razem dodatnią elementy każdy wiersz macierzy.</span><span class="sxs-lookup"><span data-stu-id="f9438-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="f9438-110">W powyższym przykładzie pierwsze `Next` instrukcji zamyka wewnętrzny `For` pętli, a ostatni `Next` instrukcji zamyka zewnętrzny `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="f9438-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="f9438-111">Podobnie, w zagnieżdżonych `If` instrukcji `End If` instrukcji automatyczne stosowanie do najbliższej przed `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9438-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="f9438-112">Zagnieżdżone `Do` pętli działają w podobny sposób, przy użyciu najbardziej wewnętrzną funkcją `Loop` instrukcji dopasowania najbardziej wewnętrzną funkcją `Do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9438-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9438-113">Dla wielu struktur sterowania po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze, zostały wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="f9438-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="f9438-114">Na przykład po kliknięciu `If` w `If...Then...Else` budowy, wszystkie wystąpienia elementu `If`, `Then`, `ElseIf`, `Else`, i `End If` w konstrukcji są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="f9438-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="f9438-115">Aby przejść do następnego lub poprzedniego wyróżnionego słów kluczowych, naciśnij klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka.</span><span class="sxs-lookup"><span data-stu-id="f9438-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="f9438-116">Różne rodzaje struktur sterujących zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="f9438-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="f9438-117">Można zagnieżdżać jednego rodzaju strukturze kontroli w ramach innego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="f9438-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="f9438-118">W poniższym przykładzie użyto `With` block wewnątrz `For Each` pętli i zagnieżdżone `If` blokuje wewnątrz `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="f9438-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="f9438-119">Nakładające się struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="f9438-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="f9438-120">Nie może nakładać się struktur sterujących.</span><span class="sxs-lookup"><span data-stu-id="f9438-120">You cannot overlap control structures.</span></span> <span data-ttu-id="f9438-121">Oznacza to, dowolnej struktury zagnieżdżonej musi być całkowicie zawarty w ramach następnego najbardziej wewnętrznej struktury.</span><span class="sxs-lookup"><span data-stu-id="f9438-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="f9438-122">Na przykład, poniższy rozmieszczenie jest nieprawidłowy ponieważ `For` pętli kończy się przed wewnętrzny `With` kończy blok.</span><span class="sxs-lookup"><span data-stu-id="f9438-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="f9438-123">![Graficzny diagram nieprawidłowe zagnieżdżanie](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="f9438-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="f9438-124">Nieprawidłowe zagnieżdżanie i z struktury</span><span class="sxs-lookup"><span data-stu-id="f9438-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="f9438-125">Kompilator Visual Basic wykrywa takie nakładających się struktury sterujące i sygnalizuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f9438-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9438-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9438-126">See also</span></span>
- [<span data-ttu-id="f9438-127">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="f9438-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="f9438-128">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="f9438-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="f9438-129">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="f9438-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="f9438-130">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="f9438-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
