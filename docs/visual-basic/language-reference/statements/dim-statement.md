---
title: Dim — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: 7bee6bffcfe0660d1661cd2c8e2ddf0528e98620
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360267"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="1a731-102">Dim — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a731-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="1a731-103">Deklaruje i alokuje magazyn przechowywania dla co najmniej jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a731-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a731-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="1a731-105">Części</span><span class="sxs-lookup"><span data-stu-id="1a731-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="1a731-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-106">Optional.</span></span> <span data-ttu-id="1a731-107">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="1a731-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-108">Optional.</span></span> <span data-ttu-id="1a731-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="1a731-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="1a731-110">Public</span><span class="sxs-lookup"><span data-stu-id="1a731-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="1a731-111">Protected</span><span class="sxs-lookup"><span data-stu-id="1a731-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="1a731-112">Friend</span><span class="sxs-lookup"><span data-stu-id="1a731-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="1a731-113">Private</span><span class="sxs-lookup"><span data-stu-id="1a731-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="1a731-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="1a731-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="1a731-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="1a731-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

     <span data-ttu-id="1a731-116">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="1a731-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-117">Optional.</span></span> <span data-ttu-id="1a731-118">Zobacz [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="1a731-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-119">Optional.</span></span> <span data-ttu-id="1a731-120">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="1a731-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-121">Optional.</span></span> <span data-ttu-id="1a731-122">Zobacz [statyczne](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="1a731-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-123">Optional.</span></span> <span data-ttu-id="1a731-124">Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="1a731-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-125">Optional.</span></span> <span data-ttu-id="1a731-126">Określa, że są one zmienne obiektów, które odwołują się do wystąpienia klasy, które może wywoływać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1a731-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="1a731-127">Zobacz [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="1a731-128">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1a731-128">Required.</span></span> <span data-ttu-id="1a731-129">Lista zmiennych został zadeklarowany w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a731-129">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="1a731-130">Każdy `variable` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="1a731-130">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="1a731-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="1a731-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="1a731-132">Część</span><span class="sxs-lookup"><span data-stu-id="1a731-132">Part</span></span>|<span data-ttu-id="1a731-133">Opis</span><span class="sxs-lookup"><span data-stu-id="1a731-133">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="1a731-134">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1a731-134">Required.</span></span> <span data-ttu-id="1a731-135">Nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-135">Name of the variable.</span></span> <span data-ttu-id="1a731-136">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="1a731-137">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-137">Optional.</span></span> <span data-ttu-id="1a731-138">Lista granic dla każdego wymiaru zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="1a731-138">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="1a731-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-139">Optional.</span></span> <span data-ttu-id="1a731-140">Tworzy nowe wystąpienie klasy po `Dim` uruchomienia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a731-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="1a731-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-141">Optional.</span></span> <span data-ttu-id="1a731-142">Typ danych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-142">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="1a731-143">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-143">Optional.</span></span> <span data-ttu-id="1a731-144">Wprowadza na liście inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a731-144">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="1a731-145">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1a731-145">Optional.</span></span> <span data-ttu-id="1a731-146">Nazwa właściwości w klasie wykonujesz wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1a731-146">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="1a731-147">Wymagany po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="1a731-147">Required after `propertyname` =.</span></span> <span data-ttu-id="1a731-148">Wyrażenie, które jest obliczane i ma przypisaną nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a731-148">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="1a731-149">Opcjonalny Jeśli `New` nie zostanie określony.</span><span class="sxs-lookup"><span data-stu-id="1a731-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="1a731-150">Wyrażenie jest obliczane i przypisana do zmiennej podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="1a731-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a731-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a731-151">Remarks</span></span>  
 <span data-ttu-id="1a731-152">Kompilator języka Visual Basic używa `Dim` instrukcię, aby określić typ danych zmiennej i inne informacje, takie jak jaki kod mają dostęp do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="1a731-153">Poniższy przykład deklaruje zmienną do przechowywania `Integer` wartość.</span><span class="sxs-lookup"><span data-stu-id="1a731-153">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="1a731-154">Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1a731-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="1a731-155">Typ odwołania, możesz użyć `New` — słowo kluczowe, aby utworzyć nowe wystąpienie klasy lub struktury, która jest określona przez typ danych.</span><span class="sxs-lookup"><span data-stu-id="1a731-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="1a731-156">Jeśli używasz `New`, wyrażenie inicjatora nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="1a731-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="1a731-157">Zamiast tego podajesz argumentów, jeśli są wymagane, do konstruktora klasy, w którym tworzysz zmienną.</span><span class="sxs-lookup"><span data-stu-id="1a731-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="1a731-158">Można zadeklarować zmienną w procedurze, blok, klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="1a731-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="1a731-159">Nie można zadeklarować zmiennej w pliku źródłowym, przestrzeń nazw lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1a731-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="1a731-160">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="1a731-161">Zmienna, które są zadeklarowane na poziomie modułu, poza każda procedura jest *zmiennej składowej* lub *pola*.</span><span class="sxs-lookup"><span data-stu-id="1a731-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="1a731-162">Zmienne Członkowskie znajdują się w zakresie ich klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="1a731-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="1a731-163">Zmienna, która jest zadeklarowana na poziomie procedura jest *zmienna lokalna*.</span><span class="sxs-lookup"><span data-stu-id="1a731-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="1a731-164">Zmienne lokalne są w zakresie tylko w ramach ich procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="1a731-164">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="1a731-165">Następujące modyfikatory dostępu są używane do deklarowania zmiennych na zewnątrz procedury: `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private`.</span><span class="sxs-lookup"><span data-stu-id="1a731-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="1a731-166">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="1a731-167">`Dim` — Słowo kluczowe jest opcjonalna i zazwyczaj pominąć, jeśli określisz dowolną z następujących modyfikatorów: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, lub `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="1a731-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="1a731-168">Jeśli `Option Explicit` jest włączone (ustawienie domyślne), kompilator wymaga deklaracji dla każdej zmiennej, możesz użyć.</span><span class="sxs-lookup"><span data-stu-id="1a731-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="1a731-169">Aby uzyskać więcej informacji, zobacz [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="1a731-170">Określając wartość początkową</span><span class="sxs-lookup"><span data-stu-id="1a731-170">Specifying an Initial Value</span></span>  
 <span data-ttu-id="1a731-171">Można przypisać wartość do zmiennej, podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="1a731-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="1a731-172">Typ wartości, możesz użyć *inicjatora* umożliwiają określanie wartości wyrażenia można przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="1a731-173">Wyrażenia musi być stałą, która może być obliczona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1a731-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="1a731-174">Jeśli określono inicjatora i typu danych nie jest określony w `As` klauzuli *wnioskowanie o typie* można wywnioskować typu danych z inicjatora.</span><span class="sxs-lookup"><span data-stu-id="1a731-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="1a731-175">W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="1a731-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="1a731-176">W drugim deklaracji wnioskowanie o typie wnioskuje typ z znajduje się wartość 3.</span><span class="sxs-lookup"><span data-stu-id="1a731-176">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="1a731-177">Wnioskowanie o typie ma zastosowanie na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="1a731-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="1a731-178">Nie ma zastosowania poza procedury w klasie, strukturze, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="1a731-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="1a731-179">Aby uzyskać więcej informacji na temat wnioskowanie o typie, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="1a731-180">Aby dowiedzieć się, jak co się stanie, jeśli nie określono typu danych lub inicjatora, zobacz [domyślne typy danych i wartości](../../../visual-basic/language-reference/statements/dim-statement.md#default) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1a731-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="1a731-181">Możesz użyć *inicjatora obiektu* do deklarowania wystąpień nazwanych i anonimowych typów.</span><span class="sxs-lookup"><span data-stu-id="1a731-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="1a731-182">Poniższy kod tworzy wystąpienie `Student` klasy i używa inicjatora obiektu można zainicjować właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a731-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="1a731-183">Aby uzyskać więcej informacji na temat inicjatorów obiektów zobacz [jak: Deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicjatorach obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), i [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="1a731-184">Deklarowanie wiele zmiennych</span><span class="sxs-lookup"><span data-stu-id="1a731-184">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="1a731-185">Można zadeklarować wiele zmiennych w jednej deklaracji instrukcji, określając nazwę zmiennej dla każdego z nich, a także następujące nazwy tablicy za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="1a731-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="1a731-186">Wiele zmiennych rozdziela się przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1a731-186">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="1a731-187">Jeśli zadeklarujesz więcej niż jedną zmienną z jednym `As` klauzuli nie może dostarczyć inicjatora dla tej grupy zmiennych.</span><span class="sxs-lookup"><span data-stu-id="1a731-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="1a731-188">Można określić różne typy danych dla różnych zmiennych, przy użyciu oddzielnego `As` klauzula dla każdej zmiennej można zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="1a731-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="1a731-189">Każda zmienna ma typ danych określonego w pierwszym `As` klauzuli napotkały po jego `variablename` części.</span><span class="sxs-lookup"><span data-stu-id="1a731-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="1a731-190">Tablice</span><span class="sxs-lookup"><span data-stu-id="1a731-190">Arrays</span></span>  
 <span data-ttu-id="1a731-191">Można zadeklarować zmienną do przechowywania *tablicy*, który może zawierać wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="1a731-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="1a731-192">Aby określić, że zmienna zawiera tablicę, postępuj zgodnie z jego `variablename` natychmiast za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="1a731-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="1a731-193">Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="1a731-194">Można określić dolną i górną granicę każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="1a731-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="1a731-195">Aby to zrobić, należy dołączyć `boundslist` wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="1a731-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="1a731-196">Dla każdego wymiaru `boundslist` określa górną granicę i opcjonalnie dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="1a731-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="1a731-197">Dolna granica zawsze wynosi zero, czy została ona określona lub nie.</span><span class="sxs-lookup"><span data-stu-id="1a731-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="1a731-198">Każdy indeks może się różnić od zera za pośrednictwem jego wartość górnej granicy.</span><span class="sxs-lookup"><span data-stu-id="1a731-198">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="1a731-199">Następujące dwie instrukcje są równoważne.</span><span class="sxs-lookup"><span data-stu-id="1a731-199">The following two statements are equivalent.</span></span> <span data-ttu-id="1a731-200">Każda instrukcja deklaruje tablicę 21 `Integer` elementów.</span><span class="sxs-lookup"><span data-stu-id="1a731-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="1a731-201">Gdy uzyskujesz dostęp do tablicy, indeks może się różnić od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="1a731-201">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="1a731-202">Poniższa instrukcja deklaruje tablicę dwuwymiarową typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="1a731-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="1a731-203">Tablica ma 4 wiersze (3 + 1) 6 kolumn (5 + 1) każdego.</span><span class="sxs-lookup"><span data-stu-id="1a731-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="1a731-204">Należy pamiętać, że górna granica reprezentuje najwyższą możliwą wartość indeksu nie długość drugiego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="1a731-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="1a731-205">Długość drugiego wymiaru jest górną granicę plus jeden.</span><span class="sxs-lookup"><span data-stu-id="1a731-205">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="1a731-206">Tablica może mieć od 1 do 32 wymiarów.</span><span class="sxs-lookup"><span data-stu-id="1a731-206">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="1a731-207">Wszystkie granice można pozostawić puste deklaracji tablicy.</span><span class="sxs-lookup"><span data-stu-id="1a731-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="1a731-208">Jeśli to zrobisz, tablica ma liczbę wymiarów, które określisz, ale jest niezainicjowany.</span><span class="sxs-lookup"><span data-stu-id="1a731-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="1a731-209">Ma ona wartość `Nothing` do momentu zainicjowania w co najmniej niektóre z jego elementów.</span><span class="sxs-lookup"><span data-stu-id="1a731-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="1a731-210">`Dim` Instrukcja musi określać granice dla wszystkich wymiarów lub żadnych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="1a731-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="1a731-211">Jeśli tablica zawiera więcej niż jednym wymiarze, musi zawierać przecinków w nawiasach, aby wskazać liczbę wymiarów.</span><span class="sxs-lookup"><span data-stu-id="1a731-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="1a731-212">Można zadeklarować *tablicę o zerowej długości* deklarując jedną z wymiarów tablicy na-1.</span><span class="sxs-lookup"><span data-stu-id="1a731-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="1a731-213">Zmienna, która zawiera tablicę o zerowej długości nie ma wartości `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1a731-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="1a731-214">Tablice o zerowej długości są wymagane przez niektóre typowe funkcje środowiska uruchomieniowego języka.</span><span class="sxs-lookup"><span data-stu-id="1a731-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="1a731-215">Jeśli próbujesz uzyskać dostęp z takiej tablicy, wystąpi wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a731-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="1a731-216">Aby uzyskać więcej informacji, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="1a731-217">Wartości w tablicy można zainicjować za pomocą literału tablicowego.</span><span class="sxs-lookup"><span data-stu-id="1a731-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="1a731-218">Aby to zrobić, należy otoczyć Inicjowanie wartości ujęte w nawiasy klamrowe (`{}`).</span><span class="sxs-lookup"><span data-stu-id="1a731-218">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="1a731-219">Dla tablic wielowymiarowych inicjowania dla każdego wymiaru oddzielne jest ujęte w nawiasy klamrowe w wymiarze zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="1a731-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="1a731-220">Elementy są określone w kolejności wierszy.</span><span class="sxs-lookup"><span data-stu-id="1a731-220">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="1a731-221">Aby uzyskać więcej informacji na temat literały tablicowe, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="default"></a> <span data-ttu-id="1a731-222">Dane domyślne typy i wartości</span><span class="sxs-lookup"><span data-stu-id="1a731-222">Default Data Types and Values</span></span>  
 <span data-ttu-id="1a731-223">W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a731-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="1a731-224">Określony typ danych?</span><span class="sxs-lookup"><span data-stu-id="1a731-224">Data type specified?</span></span>|<span data-ttu-id="1a731-225">Inicjatora określona?</span><span class="sxs-lookup"><span data-stu-id="1a731-225">Initializer specified?</span></span>|<span data-ttu-id="1a731-226">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a731-226">Example</span></span>|<span data-ttu-id="1a731-227">Wynik</span><span class="sxs-lookup"><span data-stu-id="1a731-227">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="1a731-228">Nie</span><span class="sxs-lookup"><span data-stu-id="1a731-228">No</span></span>|<span data-ttu-id="1a731-229">Nie</span><span class="sxs-lookup"><span data-stu-id="1a731-229">No</span></span>|`Dim qty`|<span data-ttu-id="1a731-230">Jeśli [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1a731-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="1a731-231">Jeśli `Option Strict` jest włączona, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1a731-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="1a731-232">Nie</span><span class="sxs-lookup"><span data-stu-id="1a731-232">No</span></span>|<span data-ttu-id="1a731-233">Tak</span><span class="sxs-lookup"><span data-stu-id="1a731-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="1a731-234">Jeśli [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) znajduje się na (ustawienie domyślne), zmienna przyjmuje dane typu inicjatora.</span><span class="sxs-lookup"><span data-stu-id="1a731-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="1a731-235">Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="1a731-236">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączone, zmienna ma typ danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="1a731-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="1a731-237">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1a731-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="1a731-238">Tak</span><span class="sxs-lookup"><span data-stu-id="1a731-238">Yes</span></span>|<span data-ttu-id="1a731-239">Nie</span><span class="sxs-lookup"><span data-stu-id="1a731-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="1a731-240">Zmienna jest ustawiana na wartość domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="1a731-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="1a731-241">Zobacz tabelę w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1a731-241">See the table later in this section.</span></span>|  
|<span data-ttu-id="1a731-242">Tak</span><span class="sxs-lookup"><span data-stu-id="1a731-242">Yes</span></span>|<span data-ttu-id="1a731-243">Tak</span><span class="sxs-lookup"><span data-stu-id="1a731-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="1a731-244">Jeśli typ danych Inicjator nie jest konwertowany na określony typ danych, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1a731-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="1a731-245">W przypadku określenia typu danych, ale nie należy określać inicjatora, Visual Basic inicjuje zmienną wartością domyślną dla jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="1a731-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="1a731-246">W poniższej tabeli przedstawiono domyślne wartości inicjowania.</span><span class="sxs-lookup"><span data-stu-id="1a731-246">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="1a731-247">Typ danych</span><span class="sxs-lookup"><span data-stu-id="1a731-247">Data type</span></span>|<span data-ttu-id="1a731-248">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="1a731-248">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="1a731-249">Wszystkie typy liczbowe (w tym `Byte` i `SByte`)</span><span class="sxs-lookup"><span data-stu-id="1a731-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="1a731-250">0</span><span class="sxs-lookup"><span data-stu-id="1a731-250">0</span></span>|  
|`Char`|<span data-ttu-id="1a731-251">Binarny 0</span><span class="sxs-lookup"><span data-stu-id="1a731-251">Binary 0</span></span>|  
|<span data-ttu-id="1a731-252">Wszystkie typy odwołań (w tym `Object`, `String`i wszystkie tablice)</span><span class="sxs-lookup"><span data-stu-id="1a731-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="1a731-253">12:00:00 1 stycznia 1 rok (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="1a731-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="1a731-254">Każdy element struktury jest inicjowany, tak jakby osobnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="1a731-255">Jeśli zadeklarować długość tablicy, ale nie zainicjować jej elementy, każdy element jest inicjowany, tak jakby osobnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="1a731-256">Statyczny okres istnienia zmiennych lokalnych</span><span class="sxs-lookup"><span data-stu-id="1a731-256">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="1a731-257">A `Static` zmienna lokalna ma dłuższy okres istnienia niż procedury, w którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="1a731-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="1a731-258">Granice okresu istnienia zmiennej są zależne od której jest zadeklarowana procedury i czy jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="1a731-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="1a731-259">Deklaracja procedury</span><span class="sxs-lookup"><span data-stu-id="1a731-259">Procedure declaration</span></span>|<span data-ttu-id="1a731-260">Zmienna została zainicjowana</span><span class="sxs-lookup"><span data-stu-id="1a731-260">Variable initialized</span></span>|<span data-ttu-id="1a731-261">Zmienna zatrzymuje istniejące</span><span class="sxs-lookup"><span data-stu-id="1a731-261">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="1a731-262">W module</span><span class="sxs-lookup"><span data-stu-id="1a731-262">In a module</span></span>|<span data-ttu-id="1a731-263">Procedura jest wywoływana po raz pierwszy</span><span class="sxs-lookup"><span data-stu-id="1a731-263">The first time the procedure is called</span></span>|<span data-ttu-id="1a731-264">Gdy program zatrzymuje wykonywanie</span><span class="sxs-lookup"><span data-stu-id="1a731-264">When your program stops execution</span></span>|  
|<span data-ttu-id="1a731-265">W klasie lub strukturze procedura jest `Shared`</span><span class="sxs-lookup"><span data-stu-id="1a731-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="1a731-266">Po raz pierwszy procedura jest wywoływana na konkretne wystąpienie lub klasa lub struktura</span><span class="sxs-lookup"><span data-stu-id="1a731-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="1a731-267">Gdy program zatrzymuje wykonywanie</span><span class="sxs-lookup"><span data-stu-id="1a731-267">When your program stops execution</span></span>|  
|<span data-ttu-id="1a731-268">W klasie lub strukturze nie jest procedurą `Shared`</span><span class="sxs-lookup"><span data-stu-id="1a731-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="1a731-269">Po raz pierwszy procedura jest wywoływana na określonym wystąpieniu</span><span class="sxs-lookup"><span data-stu-id="1a731-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="1a731-270">Po zwolnieniu wystąpienie do wyrzucania elementów bezużytecznych (GC)</span><span class="sxs-lookup"><span data-stu-id="1a731-270">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="1a731-271">Atrybuty i modyfikatorów</span><span class="sxs-lookup"><span data-stu-id="1a731-271">Attributes and Modifiers</span></span>  
 <span data-ttu-id="1a731-272">Atrybuty można zastosować tylko do zmiennych składowych, a nie do zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1a731-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="1a731-273">Atrybut przyczynia się informacji metadanych zestawu, który nie jest zrozumiały dla magazynu tymczasowego, takie jak zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="1a731-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="1a731-274">Na poziomie modułu, nie można użyć `Static` modyfikator, aby zadeklarować zmienne elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1a731-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="1a731-275">Na poziomie procedury nie można użyć `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, lub dostępu dowolną Modyfikatory do deklarowania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1a731-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="1a731-276">Można określić, jaki kod może dostęp do zmiennej, podając `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="1a731-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="1a731-277">Klasy i moduł domyślny zmienne (poza dowolnej procedury) elementu członkowskiego o dostępie prywatnym i domyślnie zmienne elementu członkowskiego struktury dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="1a731-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="1a731-278">Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="1a731-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="1a731-279">Nie można używać modyfikatorów dostępu w zmiennych lokalnych (wewnątrz procedury).</span><span class="sxs-lookup"><span data-stu-id="1a731-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="1a731-280">Można określić `WithEvents` tylko w zmiennych elementu członkowskiego, a nie na zmiennych lokalnych wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="1a731-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="1a731-281">Jeśli określisz `WithEvents`, typ danych zmiennej musi być typu określonej klasy nie `Object`.</span><span class="sxs-lookup"><span data-stu-id="1a731-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="1a731-282">Nie można zadeklarować tablicy o liczbie `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="1a731-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="1a731-283">Aby uzyskać więcej informacji o zdarzeniach zobacz [zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a731-284">Kod poza klasą, struktury lub modułu musi kwalifikować nazwy zmiennej członkowskiej z nazwą tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="1a731-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="1a731-285">Kod poza terenem procedurą lub blokiem nie może odwoływać się do żadnych zmiennych lokalnych, w tym procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="1a731-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="1a731-286">Przy zwalnianiu zasobów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="1a731-286">Releasing Managed Resources</span></span>  
 <span data-ttu-id="1a731-287">Moduł zbierający elementy bezużyteczne .NET Framework usuwa zasoby zarządzane bez żadnych dodatkowych kodowania ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1a731-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="1a731-288">Możesz jednak wymusić likwidacji zasobów zarządzanych, zamiast czekać, aż moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="1a731-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="1a731-289">Jeśli klasa przechowuje na szczególnie cenne i ograniczonych zasobów (takich jak połączenie lub plik dojście do bazy danych), może nie chcesz czekać aż do następnego wyrzucania elementów bezużytecznych aby wyczyścić wystąpienie klasy, która nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="1a731-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="1a731-290">Klasa może implementować <xref:System.IDisposable> interfejs zapewnia metodę, aby zwolnić zasoby przed wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1a731-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="1a731-291">Udostępnia klasę, która implementuje ten interfejs `Dispose` metodę, która może być wywoływana w celu wymuszenia cenne zasoby mogą być wprowadzane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="1a731-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="1a731-292">`Using` Instrukcji automatyzuje proces pobierania zasobu, wykonywanie zbiór instrukcji i następnie Usuwanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="1a731-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="1a731-293">Jednak zasobu musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1a731-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="1a731-294">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1a731-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a731-295">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a731-295">Example</span></span>  
 <span data-ttu-id="1a731-296">Poniższy przykład deklaruje zmienne przy użyciu `Dim` instrukcji z różnymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="1a731-296">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]  
  
## <a name="example"></a><span data-ttu-id="1a731-297">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a731-297">Example</span></span>  
 <span data-ttu-id="1a731-298">Poniższy przykład wyświetla listę liczb pierwszych, od 1 do 30.</span><span class="sxs-lookup"><span data-stu-id="1a731-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="1a731-299">Zakres zmiennych lokalnych jest opisane w komentarzach do kodu.</span><span class="sxs-lookup"><span data-stu-id="1a731-299">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]  
  
## <a name="example"></a><span data-ttu-id="1a731-300">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a731-300">Example</span></span>  
 <span data-ttu-id="1a731-301">W poniższym przykładzie `speedValue` zmienna została zgłoszona na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="1a731-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="1a731-302">`Private` — Słowo kluczowe jest używane do deklarowania zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1a731-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="1a731-303">Zmienna może zostać oceniony przez każda procedura w `Car` klasy.</span><span class="sxs-lookup"><span data-stu-id="1a731-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]  
  
 [!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]  
  
## <a name="see-also"></a><span data-ttu-id="1a731-304">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a731-304">See also</span></span>
- [<span data-ttu-id="1a731-305">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a731-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="1a731-306">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a731-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="1a731-307">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a731-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="1a731-308">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a731-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="1a731-309">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a731-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="1a731-310">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a731-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="1a731-311">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="1a731-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="1a731-312">Tablice</span><span class="sxs-lookup"><span data-stu-id="1a731-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="1a731-313">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="1a731-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="1a731-314">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="1a731-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="1a731-315">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="1a731-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="1a731-316">Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="1a731-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="1a731-317">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="1a731-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
