---
title: Dim — Instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: c051572e83b915346d48ec12fb5d97f77b47e4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="7c0a0-102">Dim — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c0a0-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="7c0a0-103">Deklaruje i alokuje magazyn przechowywania dla co najmniej jedną zmienną.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c0a0-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="7c0a0-105">Części</span><span class="sxs-lookup"><span data-stu-id="7c0a0-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="7c0a0-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-106">Optional.</span></span> <span data-ttu-id="7c0a0-107">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="7c0a0-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-108">Optional.</span></span> <span data-ttu-id="7c0a0-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="7c0a0-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="7c0a0-110">Public</span><span class="sxs-lookup"><span data-stu-id="7c0a0-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="7c0a0-111">Protected</span><span class="sxs-lookup"><span data-stu-id="7c0a0-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="7c0a0-112">Friend</span><span class="sxs-lookup"><span data-stu-id="7c0a0-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="7c0a0-113">Private</span><span class="sxs-lookup"><span data-stu-id="7c0a0-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="7c0a0-114">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="7c0a0-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-115">Optional.</span></span> <span data-ttu-id="7c0a0-116">Zobacz [udostępnionych](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="7c0a0-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-117">Optional.</span></span> <span data-ttu-id="7c0a0-118">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="7c0a0-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-119">Optional.</span></span> <span data-ttu-id="7c0a0-120">Zobacz [statycznych](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="7c0a0-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-121">Optional.</span></span> <span data-ttu-id="7c0a0-122">Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="7c0a0-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-123">Optional.</span></span> <span data-ttu-id="7c0a0-124">Określa, że są one zmienne obiektów, które odwołują się do wystąpienia klasy, które może wywoływać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="7c0a0-125">Zobacz [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="7c0a0-126">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-126">Required.</span></span> <span data-ttu-id="7c0a0-127">Lista zmiennych został zadeklarowany w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="7c0a0-128">Każdy `variable` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="7c0a0-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="7c0a0-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="7c0a0-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="7c0a0-130">Część</span><span class="sxs-lookup"><span data-stu-id="7c0a0-130">Part</span></span>|<span data-ttu-id="7c0a0-131">Opis</span><span class="sxs-lookup"><span data-stu-id="7c0a0-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="7c0a0-132">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-132">Required.</span></span> <span data-ttu-id="7c0a0-133">Nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-133">Name of the variable.</span></span> <span data-ttu-id="7c0a0-134">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="7c0a0-135">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-135">Optional.</span></span> <span data-ttu-id="7c0a0-136">Lista granic dla każdego wymiaru tablicy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="7c0a0-137">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-137">Optional.</span></span> <span data-ttu-id="7c0a0-138">Tworzy nowe wystąpienie klasy po `Dim` uruchamia instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="7c0a0-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-139">Optional.</span></span> <span data-ttu-id="7c0a0-140">Typ danych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="7c0a0-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-141">Optional.</span></span> <span data-ttu-id="7c0a0-142">Wprowadza na liście inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="7c0a0-143">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-143">Optional.</span></span> <span data-ttu-id="7c0a0-144">Nazwa właściwości w klasie tworzysz wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="7c0a0-145">Wymagany po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-145">Required after `propertyname` =.</span></span> <span data-ttu-id="7c0a0-146">Wyrażenie, które jest obliczane i ma przypisaną nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="7c0a0-147">Opcjonalny w przypadku `New` nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="7c0a0-148">Wyrażenie, które jest obliczane i przypisaną do zmiennej podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c0a0-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c0a0-149">Remarks</span></span>  
 <span data-ttu-id="7c0a0-150">Kompilator Visual Basic używa `Dim` instrukcji do określenia typu danych i inne informacje, takie jak kodu, jakie mają dostęp do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="7c0a0-151">Poniższy przykład deklaruje zmienną do przechowywania `Integer` wartość.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="7c0a0-152">Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="7c0a0-153">Dla typu odwołania, możesz użyć `New` — słowo kluczowe, aby utworzyć nowe wystąpienie klasy lub struktury, który jest określony przez typ danych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="7c0a0-154">Jeśli używasz `New`, nie należy używać wyrażenia inicjatora.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="7c0a0-155">Zamiast tego należy podać argumenty, jeśli są wymagane do konstruktora klasy, z którego tworzysz zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="7c0a0-156">Można zadeklarować zmiennej w procedurze, blok, klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="7c0a0-157">Nie można zadeklarować zmiennej w pliku źródłowym, przestrzeni nazw lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="7c0a0-158">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="7c0a0-159">Zmienna, która jest zadeklarowana na poziomie modułu, poza każda procedura jest *zmiennej członkowskiej* lub *pola*.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="7c0a0-160">Zmienne Członkowskie znajdują się w zakresie w całym ich klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="7c0a0-161">Zmienna, która jest zadeklarowana na poziomie procedura jest *zmiennej lokalnej*.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="7c0a0-162">Zmienne lokalne są w zakresie tylko w ramach ich procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="7c0a0-163">Następujące modyfikatory dostępu są używane do deklarowania zmiennych poza procedurą: `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="7c0a0-164">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-164">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="7c0a0-165">`Dim` — Słowo kluczowe jest opcjonalna i zwykle pominąć, jeśli określono żadnego z następujących modyfikatorów: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, lub `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="7c0a0-166">Jeśli `Option Explicit` jest na (ustawienie domyślne), kompilator wymaga deklaracji dla każdej zmiennej można użyć.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="7c0a0-167">Aby uzyskać więcej informacji, zobacz [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="7c0a0-168">Określanie wartości początkowej</span><span class="sxs-lookup"><span data-stu-id="7c0a0-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="7c0a0-169">Można przypisać wartości do zmiennej podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="7c0a0-170">Dla typu wartości, możesz użyć *inicjatora* umożliwiają określanie wartości wyrażenia do przypisania do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="7c0a0-171">Wyrażenia musi być stała, który może zostać obliczona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="7c0a0-172">Jeśli określono inicjatora i typu danych nie została określona w `As` klauzuli *wnioskowanie* służy do wnioskować o typie danych z inicjatora.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="7c0a0-173">W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="7c0a0-174">W drugim deklaracji wnioskowanie o typie wnioskuje typ z wartość 3.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="7c0a0-175">Wnioskowanie o typie stosowana na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="7c0a0-176">Nie ma zastosowania poza procedury w klasy, struktury, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="7c0a0-177">Aby uzyskać więcej informacji na temat wnioskowanie o typie, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="7c0a0-178">Aby dowiedzieć, co się stanie, jeśli nie określono typu danych lub inicjatora, zobacz [domyślne typy danych i wartości](../../../visual-basic/language-reference/statements/dim-statement.md#default) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="7c0a0-179">Można użyć *obiekt inicjatora* Aby zadeklarować wystąpień typy nazwane i anonimowe.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="7c0a0-180">Poniższy kod tworzy wystąpienie `Student` klasy i używa inicjatora obiektów, aby zainicjować właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="7c0a0-181">Aby uzyskać więcej informacji na temat inicjatory obiektów, zobacz [porady: deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), i [typy anonimowe ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="7c0a0-182">Deklarowanie zmiennych wielu</span><span class="sxs-lookup"><span data-stu-id="7c0a0-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="7c0a0-183">Można zadeklarować kilku zmiennych w jednej deklaracji instrukcji, określając nazwę zmiennej, dla każdej z nich, a następnie po każdej nazwy tablicy w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="7c0a0-184">Wiele zmiennych są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="7c0a0-185">W przypadku więcej niż jedną zmienną z jednym `As` klauzuli, nie można podać inicjatora dla tej grupy zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="7c0a0-186">Można określić różne typy danych dla różnych zmiennych, przy użyciu oddzielnej `As` klauzula dla każdej zmiennej można zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="7c0a0-187">Każda zmienna ma typ danych określony w pierwszym `As` klauzuli napotkano po jego `variablename` części.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="7c0a0-188">Tablice</span><span class="sxs-lookup"><span data-stu-id="7c0a0-188">Arrays</span></span>  
 <span data-ttu-id="7c0a0-189">Należy zadeklarować zmienną do przechowywania *tablicy*, która zawiera wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="7c0a0-190">Aby określić, że zmienna posiada tablicy, wykonaj jego `variablename` natychmiast w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="7c0a0-191">Aby uzyskać więcej informacji dotyczących tablic, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="7c0a0-192">Można określić dolną i górną granicę każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="7c0a0-193">Aby to zrobić, należy uwzględnić `boundslist` wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="7c0a0-194">Dla każdego wymiaru `boundslist` określa górną granicę i opcjonalnie dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="7c0a0-195">Dolna granica jest zawsze zero, czy została ona określona lub nie.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="7c0a0-196">Każdy indeks może różnić się od zera za pośrednictwem jego górna granica wartości.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="7c0a0-197">Dwa poniższe instrukcje są równoważne.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-197">The following two statements are equivalent.</span></span> <span data-ttu-id="7c0a0-198">Każda instrukcja deklaruje tablicę 21 `Integer` elementów.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="7c0a0-199">Gdy uzyskujesz dostęp do tablicy, indeks może się różnić od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="7c0a0-200">Następująca instrukcja deklaruje jest tablicą dwuwymiarową typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="7c0a0-201">Tablica ma 4 wiersze (3 + 1) 6 kolumn (5 + 1) każdego.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="7c0a0-202">Należy pamiętać, że górna granica reprezentuje najwyższą możliwą wartość indeksu nie długość wymiaru.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="7c0a0-203">Wymiar jest górna granica plus jeden.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="7c0a0-204">Tablica może mieć od 1 do 32 wymiarów.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="7c0a0-205">Wszystkie granice może pozostać puste deklaracji tablicy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="7c0a0-206">Jeśli to zrobisz, tablica ma liczbę wymiarów, które określisz, ale jest niezainicjowany.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="7c0a0-207">Ma ona wartość `Nothing` do momentu zainicjowania w co najmniej niektóre z jego elementów.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="7c0a0-208">`Dim` Instrukcja musi określać granice wszystkie wymiary lub nie wymiarów.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="7c0a0-209">Jeśli tablica ma więcej niż jednym wymiarze, musi zawierać przecinków między nawiasy, aby wskazać liczbę wymiarów.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="7c0a0-210">Można zadeklarować *o zerowej długości tablicy* przez zadeklarowanie jedną wymiary tablicy jako wartość -1.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="7c0a0-211">Zmienna, która przechowuje tablicą o zerowej długości nie ma wartości `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="7c0a0-212">Tablice o zerowej długości są wymagane przez niektóre typowe funkcje środowiska uruchomieniowego języka.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="7c0a0-213">Próba dostępu do tych tablicy wystąpi wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="7c0a0-214">Aby uzyskać więcej informacji, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="7c0a0-215">Wartości w tablicy można zainicjować za pomocą literału tablicy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="7c0a0-216">Aby to zrobić, należy ująć inicjowania wartości ujęte w nawiasy klamrowe (`{}`).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="7c0a0-217">Dla wielowymiarowych tablic inicjowania dla każdego wymiaru oddzielne jest ujęta w nawiasy klamrowe w wymiarze zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="7c0a0-218">Elementy są określone w kolejności wierszy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="7c0a0-219">Aby uzyskać więcej informacji na temat Literały tablicy, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a> <span data-ttu-id="7c0a0-220">Dane domyślne typy i wartości</span><span class="sxs-lookup"><span data-stu-id="7c0a0-220">Default Data Types and Values</span></span>  
 <span data-ttu-id="7c0a0-221">W poniższej tabeli przedstawiono wyniki określający typ danych oraz inicjator w różnych kombinacji `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="7c0a0-222">Określony typ danych?</span><span class="sxs-lookup"><span data-stu-id="7c0a0-222">Data type specified?</span></span>|<span data-ttu-id="7c0a0-223">Inicjator określona?</span><span class="sxs-lookup"><span data-stu-id="7c0a0-223">Initializer specified?</span></span>|<span data-ttu-id="7c0a0-224">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0a0-224">Example</span></span>|<span data-ttu-id="7c0a0-225">Wynik</span><span class="sxs-lookup"><span data-stu-id="7c0a0-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="7c0a0-226">Nie</span><span class="sxs-lookup"><span data-stu-id="7c0a0-226">No</span></span>|<span data-ttu-id="7c0a0-227">Nie</span><span class="sxs-lookup"><span data-stu-id="7c0a0-227">No</span></span>|`Dim qty`|<span data-ttu-id="7c0a0-228">Jeśli [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="7c0a0-229">Jeśli `Option Strict` jest włączone, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="7c0a0-230">Nie</span><span class="sxs-lookup"><span data-stu-id="7c0a0-230">No</span></span>|<span data-ttu-id="7c0a0-231">Tak</span><span class="sxs-lookup"><span data-stu-id="7c0a0-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="7c0a0-232">Jeśli [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) znajduje się na (ustawienie domyślne), typ zmiennej przyjmuje dane inicjatora.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="7c0a0-233">Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="7c0a0-234">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączony, zmienna ma typ danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="7c0a0-235">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="7c0a0-236">Tak</span><span class="sxs-lookup"><span data-stu-id="7c0a0-236">Yes</span></span>|<span data-ttu-id="7c0a0-237">Nie</span><span class="sxs-lookup"><span data-stu-id="7c0a0-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="7c0a0-238">Zmienna jest ustawiana na wartość domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="7c0a0-239">Zobacz tabelę w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="7c0a0-240">Tak</span><span class="sxs-lookup"><span data-stu-id="7c0a0-240">Yes</span></span>|<span data-ttu-id="7c0a0-241">Tak</span><span class="sxs-lookup"><span data-stu-id="7c0a0-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="7c0a0-242">Jeśli typ danych Inicjator nie jest możliwe do przekonwertowania na określony typ danych, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="7c0a0-243">Jeśli można określić typu danych, ale nie należy określać inicjatora, Visual Basic inicjuje zmiennej na wartość domyślną dla tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-243">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="7c0a0-244">W poniższej tabeli przedstawiono domyślne wartości inicjowania.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="7c0a0-245">Typ danych</span><span class="sxs-lookup"><span data-stu-id="7c0a0-245">Data type</span></span>|<span data-ttu-id="7c0a0-246">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="7c0a0-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="7c0a0-247">Wszystkie typy liczbowe (łącznie z `Byte` i `SByte`)</span><span class="sxs-lookup"><span data-stu-id="7c0a0-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="7c0a0-248">0</span><span class="sxs-lookup"><span data-stu-id="7c0a0-248">0</span></span>|  
|`Char`|<span data-ttu-id="7c0a0-249">Binarny 0</span><span class="sxs-lookup"><span data-stu-id="7c0a0-249">Binary 0</span></span>|  
|<span data-ttu-id="7c0a0-250">Wszystkie typy odwołań (łącznie z `Object`, `String`, a wszystkie tablice)</span><span class="sxs-lookup"><span data-stu-id="7c0a0-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="7c0a0-251">00:00:00 1 stycznia 1 roku (0001-01/01 00:00:00: 00)</span><span class="sxs-lookup"><span data-stu-id="7c0a0-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="7c0a0-252">Każdy element struktury został zainicjowany, tak jakby był on osobnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="7c0a0-253">Czy zadeklarować długość tablicy, ale nie zainicjować swoich elementów, każdy element została zainicjowana, tak jakby był on osobnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="7c0a0-254">Statyczne okres istnienia zmiennej lokalnej</span><span class="sxs-lookup"><span data-stu-id="7c0a0-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="7c0a0-255">A `Static` zmiennej lokalnej ma dłuższy okres istnienia niż procedury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="7c0a0-256">Granice istnienia zmiennej zależą od którym jest zadeklarowany jako procedura oraz czy jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="7c0a0-257">Deklaracja procedury</span><span class="sxs-lookup"><span data-stu-id="7c0a0-257">Procedure declaration</span></span>|<span data-ttu-id="7c0a0-258">Zmienna została zainicjowana</span><span class="sxs-lookup"><span data-stu-id="7c0a0-258">Variable initialized</span></span>|<span data-ttu-id="7c0a0-259">Zmienna zatrzymuje istniejących</span><span class="sxs-lookup"><span data-stu-id="7c0a0-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="7c0a0-260">W module</span><span class="sxs-lookup"><span data-stu-id="7c0a0-260">In a module</span></span>|<span data-ttu-id="7c0a0-261">Procedura jest wywoływana po raz pierwszy</span><span class="sxs-lookup"><span data-stu-id="7c0a0-261">The first time the procedure is called</span></span>|<span data-ttu-id="7c0a0-262">Gdy program zatrzymuje wykonywanie</span><span class="sxs-lookup"><span data-stu-id="7c0a0-262">When your program stops execution</span></span>|  
|<span data-ttu-id="7c0a0-263">W klasie lub strukturze jest procedury `Shared`</span><span class="sxs-lookup"><span data-stu-id="7c0a0-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="7c0a0-264">Po raz pierwszy procedura jest wywoływana na określonym wystąpieniu lub dla klasy lub struktury, sama</span><span class="sxs-lookup"><span data-stu-id="7c0a0-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="7c0a0-265">Gdy program zatrzymuje wykonywanie</span><span class="sxs-lookup"><span data-stu-id="7c0a0-265">When your program stops execution</span></span>|  
|<span data-ttu-id="7c0a0-266">W klasie lub strukturze nie jest procedurą `Shared`</span><span class="sxs-lookup"><span data-stu-id="7c0a0-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="7c0a0-267">Procedura jest wywoływana na określonym wystąpieniu po raz pierwszy</span><span class="sxs-lookup"><span data-stu-id="7c0a0-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="7c0a0-268">Po zwolnieniu wystąpienie dla wyrzucanie elementów bezużytecznych (GC)</span><span class="sxs-lookup"><span data-stu-id="7c0a0-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="7c0a0-269">Atrybuty i Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="7c0a0-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="7c0a0-270">Atrybuty można stosować tylko do zmiennych Członkowskich, a nie do zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="7c0a0-271">Atrybut przyczynia się informacji metadanych zestawu, która nie jest zrozumiały dla tymczasowego magazynu, takich jak zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="7c0a0-272">Na poziomie modułu, nie można użyć `Static` modyfikator do deklarowania zmiennych Członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="7c0a0-273">Na poziomie procedury nie można użyć `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, lub dowolnego dostępu Modyfikatory do deklarowania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="7c0a0-274">Można określić, jaki kod uzyskać dostęp do zmiennej, podając `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="7c0a0-275">Klasy i moduł domyślny zmienne (poza dowolnej procedury) elementu członkowskiego o dostępie prywatnym i domyślnie zmienne Członkowskie struktury dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="7c0a0-276">Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="7c0a0-277">Nie można używać modyfikatorów dostępu na zmienne lokalne (wewnątrz procedury).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="7c0a0-278">Można określić `WithEvents` tylko dla zmiennych Członkowskich, a nie na zmiennych lokalnych wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="7c0a0-279">Jeśli określisz `WithEvents`, typ danych zmiennej musi być typem określonej klasy nie `Object`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="7c0a0-280">Nie można zadeklarować tablicy o `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="7c0a0-281">Aby uzyskać więcej informacji o zdarzeniach, zobacz [zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c0a0-282">Kod poza klasą, strukturą lub modułu muszą nazwy zmiennej członkowskiej z nazwą tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="7c0a0-283">Kod poza procedurę lub blok nie może odwoływać się do żadnych zmiennych lokalnych w ramach tej procedury lub bloku.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="7c0a0-284">Zwolnienie zasobów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="7c0a0-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="7c0a0-285">Moduł zbierający elementy bezużyteczne .NET Framework usuwa zasoby zarządzane bez żadnych dodatkowych kodowania ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="7c0a0-286">Można jednak wymusić usuwania zarządzanych zasobów, zamiast czekać na moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="7c0a0-287">Jeśli klasa jest przechowywana na szczególnie cenne i ograniczonych zasobów (takich jak dojścia połączenia lub pliku bazy danych), może nie chcesz czekać do następnego wyrzucanie elementów bezużytecznych wyczyścić wystąpienia klasy, która nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="7c0a0-288">Klasa może zawierać implementację <xref:System.IDisposable> interfejsu sposób, aby zwolnić zasoby przed wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="7c0a0-289">Udostępnia klasy, która implementuje ten interfejs `Dispose` metody, który można wywołać, aby wymusić cenne zasoby pozostają dostępne do zwolnienia natychmiast.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="7c0a0-290">`Using` Instrukcji automatyzuje proces pobierania zasobu, wykonywania zbiór instrukcji i następnie Usuwanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="7c0a0-291">Jednak zasobu musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="7c0a0-292">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a0-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c0a0-293">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0a0-293">Example</span></span>  
 <span data-ttu-id="7c0a0-294">Poniższy przykład deklaruje zmienne przy użyciu `Dim` instrukcji z różnymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0a0-295">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0a0-295">Example</span></span>  
 <span data-ttu-id="7c0a0-296">Poniższy przykład zawiera listę liczb pierwszych od 1 do 30.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-296">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="7c0a0-297">Zakres zmiennych lokalnych jest opisany w komentarze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-297">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0a0-298">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0a0-298">Example</span></span>  
 <span data-ttu-id="7c0a0-299">W poniższym przykładzie `speedValue` deklaracji zmiennej na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-299">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="7c0a0-300">`Private` Słowo kluczowe jest używane w celu zadeklarowania zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-300">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="7c0a0-301">Procedury w programie można można uzyskać dostępu do zmiennej `Car` klasy.</span><span class="sxs-lookup"><span data-stu-id="7c0a0-301">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7c0a0-302">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c0a0-302">See Also</span></span>  
 [<span data-ttu-id="7c0a0-303">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0a0-303">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="7c0a0-304">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0a0-304">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="7c0a0-305">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0a0-305">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="7c0a0-306">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0a0-306">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="7c0a0-307">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0a0-307">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="7c0a0-308">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c0a0-308">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="7c0a0-309">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="7c0a0-309">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="7c0a0-310">Tablice</span><span class="sxs-lookup"><span data-stu-id="7c0a0-310">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="7c0a0-311">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="7c0a0-311">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="7c0a0-312">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7c0a0-312">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="7c0a0-313">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="7c0a0-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="7c0a0-314">Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="7c0a0-314">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="7c0a0-315">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="7c0a0-315">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
