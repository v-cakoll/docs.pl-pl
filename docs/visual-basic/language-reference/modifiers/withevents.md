---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 50d5a768393e90d28d150b451405e35e6f4c7953
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583038"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="bbc82-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbc82-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="bbc82-103">Określa, że co najmniej jedna zadeklarowana zmienna składowej odnosi się do wystąpienia klasy, która może zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bbc82-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbc82-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbc82-104">Remarks</span></span>

<span data-ttu-id="bbc82-105">Gdy zmienna jest definiowana przy użyciu `WithEvents`, można deklaratywnie określić, że metoda obsługuje zdarzenia zmiennej przy użyciu słowa kluczowego `Handles`.</span><span class="sxs-lookup"><span data-stu-id="bbc82-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="bbc82-106">@No__t_0 można używać tylko na poziomie klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="bbc82-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="bbc82-107">Oznacza to, że kontekst deklaracji dla zmiennej `WithEvents` musi być klasą lub modułem i nie może być plikiem źródłowym, przestrzenią nazw, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="bbc82-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="bbc82-108">Nie można użyć `WithEvents` w składowej struktury.</span><span class="sxs-lookup"><span data-stu-id="bbc82-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="bbc82-109">Można zadeklarować tylko pojedyncze zmienne — nie tablice — z `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="bbc82-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="bbc82-110">Przepisy</span><span class="sxs-lookup"><span data-stu-id="bbc82-110">Rules</span></span>

<span data-ttu-id="bbc82-111">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="bbc82-111">**Element Types.**</span></span> <span data-ttu-id="bbc82-112">Należy zadeklarować zmienne `WithEvents` jako zmienne obiektów, aby mogły akceptować wystąpienia klas.</span><span class="sxs-lookup"><span data-stu-id="bbc82-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="bbc82-113">Nie można jednak zadeklarować ich jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="bbc82-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="bbc82-114">Należy zadeklarować je jako konkretną klasę, która może zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bbc82-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="bbc82-115">Modyfikator `WithEvents` może być używany w tym kontekście: [Dim — Instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bbc82-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="bbc82-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbc82-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="bbc82-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbc82-117">See also</span></span>

- [<span data-ttu-id="bbc82-118">Realizuj</span><span class="sxs-lookup"><span data-stu-id="bbc82-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="bbc82-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="bbc82-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="bbc82-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="bbc82-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
