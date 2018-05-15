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
ms.openlocfilehash: b4a7e2b63b930b98ee082c0104c24f6857b5b35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="a0f87-102">Stałe zdefiniowane przez użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0f87-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="a0f87-103">Stała jest znaczącą nazwę, która ma miejsce, liczby lub ciąg, który nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="a0f87-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="a0f87-104">Stałe przechowywać wartości, które, jak nazwa wskazuje, pozostają stałe w trakcie wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0f87-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="a0f87-105">Można użyć stałe zdefiniowane przez formanty lub składników, którymi współpracujesz lub Utwórz swój własny.</span><span class="sxs-lookup"><span data-stu-id="a0f87-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="a0f87-106">Stałe samodzielnie utworzyć są nazywane *użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="a0f87-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="a0f87-107">Deklarowanie stałej z `Const` instrukcji, korzystając z tego samego wskazówek, jak do tworzenia nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a0f87-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="a0f87-108">Jeśli `Option Strict` jest `On`, musisz jawnie zadeklarować typu stałej.</span><span class="sxs-lookup"><span data-stu-id="a0f87-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="a0f87-109">Użycie instrukcji const</span><span class="sxs-lookup"><span data-stu-id="a0f87-109">Const Statement Usage</span></span>  
 <span data-ttu-id="a0f87-110">A `Const` instrukcji można reprezentować matematyczne lub ilość daty/godziny:</span><span class="sxs-lookup"><span data-stu-id="a0f87-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 <span data-ttu-id="a0f87-111">On również zdefiniować `String` stałe:</span><span class="sxs-lookup"><span data-stu-id="a0f87-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 <span data-ttu-id="a0f87-112">Wyrażenie po prawej stronie znaku równości ( `=` ) jest często liczba lub ciąg literału, ale również może być wyrażeniem, które powoduje liczbę lub ciąg (chociaż tego wyrażenia nie może zawierać wywołania funkcji).</span><span class="sxs-lookup"><span data-stu-id="a0f87-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="a0f87-113">Można nawet Definiowanie stałych pod względem wcześniej zdefiniowanego stałe:</span><span class="sxs-lookup"><span data-stu-id="a0f87-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="a0f87-114">Zakres stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="a0f87-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="a0f87-115">A `Const` instrukcji w zakresie jest taka sama jak zmiennej zadeklarowanej w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a0f87-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="a0f87-116">Można określić zakres, w żadnym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="a0f87-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="a0f87-117">Aby utworzyć stałą, że istnieje tylko w obrębie procedury, należy zadeklarować w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="a0f87-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="a0f87-118">Aby utworzyć stałą dostępne do wszystkich procedur w obrębie klasy, ale nie do kodu poza ten moduł, należy zadeklarować w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="a0f87-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="a0f87-119">Aby utworzyć stałą jest dostępny do wszystkich elementów członkowskich zestawu, ale nie do zewnętrznej klientów zestawu, Zadeklaruj ją przy użyciu `Friend` — słowo kluczowe w sekcji deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="a0f87-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="a0f87-120">Aby utworzyć stałą dostępne w całej aplikacji, Zadeklaruj ją przy użyciu `Public` — słowo kluczowe w deklaracjach sekcji klasy.</span><span class="sxs-lookup"><span data-stu-id="a0f87-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="a0f87-121">Aby uzyskać więcej informacji, zobacz [porady: deklarowanie stałej A](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="a0f87-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="a0f87-122">Unikanie odwołania cykliczne</span><span class="sxs-lookup"><span data-stu-id="a0f87-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="a0f87-123">Ponieważ stałe można zdefiniować pod względem innych stałe, istnieje możliwość tworzenia przypadkowo *cykl*, lub odwołanie cykliczne między co najmniej dwie stałe.</span><span class="sxs-lookup"><span data-stu-id="a0f87-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="a0f87-124">Cykl występuje, gdy masz co najmniej dwie stałe publicznych, z których każdy jest określana w kontekście innych, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a0f87-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 <span data-ttu-id="a0f87-125">Jeśli występuje cykl, Visual Basic generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a0f87-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f87-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0f87-126">See Also</span></span>  
 [<span data-ttu-id="a0f87-127">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a0f87-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="a0f87-128">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="a0f87-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="a0f87-129">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a0f87-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [<span data-ttu-id="a0f87-130">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a0f87-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="a0f87-131">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="a0f87-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="a0f87-132">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="a0f87-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="a0f87-133">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="a0f87-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="a0f87-134">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="a0f87-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="a0f87-135">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a0f87-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
