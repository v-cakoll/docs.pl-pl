---
title: Deklaracja zmiennej w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8edd0b65b08efd437cc35e8f58ed7ed423736920
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="25115-102">Deklaracja zmiennej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25115-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="25115-103">Można zadeklarować zmiennej do określenia nazwy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="25115-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="25115-104">Instrukcja deklaracji zmiennych jest [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25115-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="25115-105">Jej lokalizacja i zawartość należy określić charakterystyki zmiennej.</span><span class="sxs-lookup"><span data-stu-id="25115-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="25115-106">Reguły nazewnictwa zmiennych i zagadnienia, zobacz [zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="25115-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="25115-107">Poziomy deklaracji</span><span class="sxs-lookup"><span data-stu-id="25115-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="25115-108">Lokalne i zmienne Członkowskie</span><span class="sxs-lookup"><span data-stu-id="25115-108">Local and Member Variables</span></span>  
 <span data-ttu-id="25115-109">A *zmiennej lokalnej* to taki, który jest zadeklarowana w obrębie procedury.</span><span class="sxs-lookup"><span data-stu-id="25115-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="25115-110">A *zmiennej członkowskiej* jest elementem członkowskim typu Visual Basic; jest zadeklarowany na poziomie modułu, wewnątrz klasy, struktury lub moduł, ale nie w dowolnej procedury wewnętrzne dla tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="25115-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="25115-111">Udostępnione i wystąpienie zmiennych</span><span class="sxs-lookup"><span data-stu-id="25115-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="25115-112">W klasie lub strukturze kategorii zmiennej członkowskiej zależy od tego, czy są one udostępniane.</span><span class="sxs-lookup"><span data-stu-id="25115-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="25115-113">Jeśli jest ona zadeklarowana z [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) — słowo kluczowe, jest *współdzielonej zmiennej*, i istnieje on w pojedynczej kopii współdzielona przez wszystkie wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="25115-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="25115-114">W przeciwnym razie jest *zmienna wystąpienia*, i osobną kopię jest tworzony dla każdego wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="25115-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="25115-115">Kopię danego zmienna wystąpienia jest dostępna tylko dla wystąpienia klasy lub struktury, w której został utworzony.</span><span class="sxs-lookup"><span data-stu-id="25115-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="25115-116">Jest niezależna od kopię zmienna wystąpienia w wszystkie inne wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="25115-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="25115-117">Deklarowanie typu danych</span><span class="sxs-lookup"><span data-stu-id="25115-117">Declaring Data Type</span></span>  
 <span data-ttu-id="25115-118">[Jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli w instrukcji deklaracji można zdefiniować typu danych lub typ obiektu są deklarowanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="25115-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="25115-119">Można określić jedną z następujących typów dla zmiennej:</span><span class="sxs-lookup"><span data-stu-id="25115-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="25115-120">Typ danych podstawowych, takich jak `Boolean`, `Long`, lub `Decimal`</span><span class="sxs-lookup"><span data-stu-id="25115-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="25115-121">Złożonego typu danych, takich jak tablica lub struktury</span><span class="sxs-lookup"><span data-stu-id="25115-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="25115-122">Typ obiektu lub klasa zdefiniowana w aplikacji lub w innej aplikacji</span><span class="sxs-lookup"><span data-stu-id="25115-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="25115-123">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy, takie jak <xref:System.Windows.Forms.Label> lub <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="25115-123">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="25115-124">Typ interfejsu, takich jak <xref:System.IComparable> lub <xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="25115-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="25115-125">Kilku zmiennych w jednej instrukcji można zadeklarować bez konieczności powtarzania typu danych.</span><span class="sxs-lookup"><span data-stu-id="25115-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="25115-126">W poniższych instrukcjach, zmienne `i`, `j`, i `k` został zadeklarowany jako typ `Integer`, `l` i `m` jako `Long`, i `x` i `y` jako `Single`:</span><span class="sxs-lookup"><span data-stu-id="25115-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="25115-127">Aby uzyskać więcej informacji o typach danych, zobacz [typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="25115-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="25115-128">Aby uzyskać więcej informacji dotyczących obiektów, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [programowania ze składnikami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="25115-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="25115-129">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="25115-129">Local Type Inference</span></span>  
 <span data-ttu-id="25115-130">*Wnioskowanie o typie* służy do określania typów danych zmienna lokalna zadeklarowana bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="25115-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="25115-131">Kompilator wnioskuje typ zmiennej typu wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="25115-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="25115-132">Dzięki temu można zadeklarować zmienne bez jawne określenie typu.</span><span class="sxs-lookup"><span data-stu-id="25115-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="25115-133">W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="25115-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 <span data-ttu-id="25115-134">Jeśli chcesz użyć wnioskowanie o typie lokalnym, `Option Infer` musi mieć ustawioną `On`.</span><span class="sxs-lookup"><span data-stu-id="25115-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="25115-135">Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25115-135">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="25115-136">Właściwości zadeklarowane zmienne</span><span class="sxs-lookup"><span data-stu-id="25115-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="25115-137">*Okres istnienia* zmiennej jest okres, w którym jest dostępny do użytku.</span><span class="sxs-lookup"><span data-stu-id="25115-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="25115-138">Ogólnie rzecz biorąc istnieje zmienna, jak długo element, który deklaruje on (np. procedury lub klasy) nadal istnieje.</span><span class="sxs-lookup"><span data-stu-id="25115-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="25115-139">Zmienna nie trzeba kontynuować istniejące poza okres istnienia jego zawierający element, nie trzeba wykonywać żadnych czynności specjalne w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="25115-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="25115-140">Jeśli zmienna musi nadal istnieje dłużej niż jego zawierający element, należą `Static` lub `Shared` — słowo kluczowe w jego `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="25115-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="25115-141">Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="25115-141">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="25115-142">*Zakres* zmiennej to zbiór wszystkich kod, który może odwoływać się do niego bez kwalifikujących się jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="25115-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="25115-143">Zakres zmiennej jest określana przez którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="25115-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="25115-144">Kod znajdujący się w danym regionie można używać zmiennych zdefiniowanych w tym regionie bez konieczności kwalifikują się ich nazw.</span><span class="sxs-lookup"><span data-stu-id="25115-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="25115-145">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="25115-145">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="25115-146">Zmienna *poziom dostępu* jest zakres kodu, który ma uprawnienia dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="25115-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="25115-147">Jest to określane przez modyfikator dostępu (takich jak [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md)) używanego w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="25115-147">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="25115-148">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="25115-148">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25115-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25115-149">See Also</span></span>  
 [<span data-ttu-id="25115-150">Instrukcje: tworzenie nowej zmiennej</span><span class="sxs-lookup"><span data-stu-id="25115-150">How to: Create a New Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [<span data-ttu-id="25115-151">Instrukcje: przenoszenie danych do zmiennej i z niej</span><span class="sxs-lookup"><span data-stu-id="25115-151">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="25115-152">Typy danych</span><span class="sxs-lookup"><span data-stu-id="25115-152">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="25115-153">Protected</span><span class="sxs-lookup"><span data-stu-id="25115-153">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="25115-154">Friend</span><span class="sxs-lookup"><span data-stu-id="25115-154">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="25115-155">Static</span><span class="sxs-lookup"><span data-stu-id="25115-155">Static</span></span>](../../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="25115-156">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="25115-156">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="25115-157">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="25115-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="25115-158">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="25115-158">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
