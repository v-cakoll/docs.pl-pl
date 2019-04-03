---
title: Stałe zdefiniowane przez użytkownika (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: f0196457235ad77df545a367573f62b43209269d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813915"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="be643-102">Stałe zdefiniowane przez użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be643-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="be643-103">Stałe są znaczącą nazwę, która zajmuje miejsce liczbą lub ciągiem, który nie jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="be643-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="be643-104">Stałe przechowywać wartości, które jak wskazuje nazwa, pozostają stałe w trakcie wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="be643-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="be643-105">Można użyć stałe, które są definiowane przez formanty lub składników, którymi pracujesz, lub możesz utworzyć swój własny.</span><span class="sxs-lookup"><span data-stu-id="be643-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="be643-106">Stałe utworzone samodzielnie są określane jako *zdefiniowanych przez użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="be643-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="be643-107">Deklarowanie stałej z `Const` instrukcję, używając te same wytyczne, jak w przypadku tworzenia nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="be643-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="be643-108">Jeśli `Option Strict` jest `On`, należy jawnie deklarować typ stałej.</span><span class="sxs-lookup"><span data-stu-id="be643-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="be643-109">Const — instrukcja użycia</span><span class="sxs-lookup"><span data-stu-id="be643-109">Const Statement Usage</span></span>  
 <span data-ttu-id="be643-110">A `Const` instrukcji może reprezentować matematyczne lub daty/godziny ilość:</span><span class="sxs-lookup"><span data-stu-id="be643-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="be643-111">On również zdefiniować `String` stałe:</span><span class="sxs-lookup"><span data-stu-id="be643-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="be643-112">Wyrażenie po prawej stronie znaku równości ( `=` ) jest często liczbą lub ciągiem literału, ale również może być wyrażeniem, które powoduje liczbą lub ciągiem (mimo że to wyrażenie nie może zawierać wywołania funkcji).</span><span class="sxs-lookup"><span data-stu-id="be643-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="be643-113">Możesz nawet określić stałe pod względem wcześniej zdefiniowanego stałe:</span><span class="sxs-lookup"><span data-stu-id="be643-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="be643-114">Zakres stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="be643-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="be643-115">A `Const` zakres instrukcji jest taka sama, jak Zmienna zadeklarowana w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="be643-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="be643-116">Należy określić zakres, w dowolnym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="be643-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="be643-117">Aby utworzyć stałą, że istnieje tylko w obrębie procedury, należy zadeklarować ją w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="be643-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="be643-118">Aby utworzyć stałej dostępności, do wszystkich procedur w obrębie klasy, ale nie do kodu poza ten moduł, należy zadeklarować ją w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="be643-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="be643-119">Aby utworzyć stałą, która jest dostępna, do wszystkich elementów członkowskich zestawu, ale nie do klientów poza zestawu, Zadeklaruj go przy użyciu `Friend` — słowo kluczowe w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="be643-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="be643-120">Aby utworzyć stałą dostępne w całej aplikacji, Zadeklaruj go przy użyciu `Public` — słowo kluczowe w deklaracjach sekcji klasy.</span><span class="sxs-lookup"><span data-stu-id="be643-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="be643-121">Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="be643-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="be643-122">Unikanie odwołań cyklicznych</span><span class="sxs-lookup"><span data-stu-id="be643-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="be643-123">Ponieważ stałe można zdefiniować pod względem inne stałe, jest możliwe utworzenie przypadkowo *cyklu*, lub odwołanie cykliczne, między co najmniej dwóch stałych.</span><span class="sxs-lookup"><span data-stu-id="be643-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="be643-124">Cykl występuje, gdy masz co najmniej dwa publiczne stałe, z których każdy jest określana zgodnie z drugiej strony, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="be643-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="be643-125">W przypadku cyklu Visual Basic generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="be643-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be643-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be643-126">See also</span></span>

- [<span data-ttu-id="be643-127">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="be643-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="be643-128">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="be643-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="be643-129">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="be643-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="be643-130">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="be643-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="be643-131">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="be643-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="be643-132">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="be643-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="be643-133">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="be643-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="be643-134">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="be643-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="be643-135">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="be643-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
