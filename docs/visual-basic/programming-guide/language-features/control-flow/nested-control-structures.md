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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="8314b-102">Zagnieżdżone struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8314b-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="8314b-103">Można umieścić instrukcje sterujące wewnątrz innych instrukcji sterowania, na przykład `If...Then...Else` blok w `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="8314b-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="8314b-104">Instrukcja sterująca umieszczona wewnątrz innej instrukcji sterującej jest określana jako *zagnieżdżona*.</span><span class="sxs-lookup"><span data-stu-id="8314b-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="8314b-105">Poziomy zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="8314b-105">Nesting Levels</span></span>  
 <span data-ttu-id="8314b-106">Struktury formantów w Visual Basic mogą być zagnieżdżane do tylu poziomów.</span><span class="sxs-lookup"><span data-stu-id="8314b-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="8314b-107">Powszechną zaletą jest bardziej czytelność zagnieżdżonych struktur przez wcięcie treści każdej z nich.</span><span class="sxs-lookup"><span data-stu-id="8314b-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="8314b-108">Edytor zintegrowanego środowiska programistycznego (IDE) automatycznie robi to.</span><span class="sxs-lookup"><span data-stu-id="8314b-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="8314b-109">W poniższym przykładzie procedura `sumRows` dodaje razem elementy dodatnie każdego wiersza macierzy.</span><span class="sxs-lookup"><span data-stu-id="8314b-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="8314b-110">W poprzednim przykładzie pierwsza `Next` instrukcja zamyka pętlę wewnętrzną, `For` a Ostatnia `Next` instrukcja zamyka pętlę zewnętrzną `For` .</span><span class="sxs-lookup"><span data-stu-id="8314b-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="8314b-111">Podobnie, w `If` instrukcjach zagnieżdżonych `End If` instrukcje są automatycznie stosowane do najbliższej wcześniejszej `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8314b-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="8314b-112">`Do`Pętle zagnieżdżone działają w podobny sposób, przy użyciu najbardziej wewnętrznej `Loop` instrukcji pasującej do najbardziej wewnętrznej `Do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8314b-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8314b-113">W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze.</span><span class="sxs-lookup"><span data-stu-id="8314b-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="8314b-114">Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji wszystkie wystąpienia elementów,,, `If` `Then` `ElseIf` `Else` i `End If` w konstrukcji są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="8314b-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="8314b-115">Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.</span><span class="sxs-lookup"><span data-stu-id="8314b-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="8314b-116">Zagnieżdżanie różnych rodzajów struktur kontroli</span><span class="sxs-lookup"><span data-stu-id="8314b-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="8314b-117">Można zagnieżdżać jeden rodzaj struktury kontroli w innym rodzaju.</span><span class="sxs-lookup"><span data-stu-id="8314b-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="8314b-118">Poniższy przykład używa `With` bloku wewnątrz `For Each` pętli i zagnieżdżonych `If` bloków wewnątrz `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="8314b-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="8314b-119">Nakładające się struktury kontroli</span><span class="sxs-lookup"><span data-stu-id="8314b-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="8314b-120">Nie można nakładać się na struktury formantów.</span><span class="sxs-lookup"><span data-stu-id="8314b-120">You cannot overlap control structures.</span></span> <span data-ttu-id="8314b-121">Oznacza to, że jakakolwiek struktura zagnieżdżona musi być całkowicie zawarta w obrębie następnej wewnętrznej struktury.</span><span class="sxs-lookup"><span data-stu-id="8314b-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="8314b-122">Na przykład następujące rozmieszczenie jest nieprawidłowe, ponieważ `For` Pętla kończy się przed `With` zakończeniem wewnętrznego bloku.</span><span class="sxs-lookup"><span data-stu-id="8314b-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram przedstawiający przykład nieprawidłowego zagnieżdżania.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="8314b-124">Kompilator Visual Basic wykrywa te nakładające się struktury kontroli i sygnalizuje błąd czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8314b-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8314b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8314b-125">See also</span></span>

- [<span data-ttu-id="8314b-126">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="8314b-126">Control Flow</span></span>](index.md)
- [<span data-ttu-id="8314b-127">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="8314b-127">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="8314b-128">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="8314b-128">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="8314b-129">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="8314b-129">Other Control Structures</span></span>](other-control-structures.md)
