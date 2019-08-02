---
title: Zakres w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512849"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="272c8-102">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="272c8-102">Scope in Visual Basic</span></span>

<span data-ttu-id="272c8-103">*Zakres* zadeklarowanego elementu jest zestawem wszystkich kodów, które mogą odwoływać się do niego bez zakwalifikowania jego nazwy lub udostępniania za pomocą [instrukcji Imports (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="272c8-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="272c8-104">Element może mieć zakres na jednym z następujących poziomów:</span><span class="sxs-lookup"><span data-stu-id="272c8-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="272c8-105">Poziom</span><span class="sxs-lookup"><span data-stu-id="272c8-105">Level</span></span>|<span data-ttu-id="272c8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="272c8-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="272c8-107">Zakres bloku</span><span class="sxs-lookup"><span data-stu-id="272c8-107">Block scope</span></span>|<span data-ttu-id="272c8-108">Dostępne tylko w bloku kodu, w którym jest zadeklarowany</span><span class="sxs-lookup"><span data-stu-id="272c8-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="272c8-109">Zakres procedury</span><span class="sxs-lookup"><span data-stu-id="272c8-109">Procedure scope</span></span>|<span data-ttu-id="272c8-110">Dostępne dla całego kodu w ramach procedury, w której jest zadeklarowany</span><span class="sxs-lookup"><span data-stu-id="272c8-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="272c8-111">Zakres modułu</span><span class="sxs-lookup"><span data-stu-id="272c8-111">Module scope</span></span>|<span data-ttu-id="272c8-112">Dostępne dla wszystkich kodów w module, klasie lub strukturze, w których jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="272c8-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="272c8-113">Zakres przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="272c8-113">Namespace scope</span></span>|<span data-ttu-id="272c8-114">Dostępne dla całego kodu w przestrzeni nazw, w którym jest zadeklarowany</span><span class="sxs-lookup"><span data-stu-id="272c8-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="272c8-115">Poziomy postęp zakresu od najwęższego (bloku) do najszerszego (przestrzeni nazw), gdzie najwęższy *zakres* oznacza najmniejszy zestaw kodu, który może odwoływać się do elementu bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="272c8-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="272c8-116">Aby uzyskać więcej informacji, zobacz sekcję "poziomy zakresu" na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="272c8-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="272c8-117">Określanie zakresu i Definiowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="272c8-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="272c8-118">Należy określić zakres elementu podczas jego deklarowania.</span><span class="sxs-lookup"><span data-stu-id="272c8-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="272c8-119">Zakres może zależeć od następujących czynników:</span><span class="sxs-lookup"><span data-stu-id="272c8-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="272c8-120">Region (blok, procedura, moduł, Klasa lub struktura), w którym deklarujesz element</span><span class="sxs-lookup"><span data-stu-id="272c8-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="272c8-121">Przestrzeń nazw zawierająca deklarację elementu</span><span class="sxs-lookup"><span data-stu-id="272c8-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="272c8-122">Poziom dostępu zadeklarowany dla elementu</span><span class="sxs-lookup"><span data-stu-id="272c8-122">The access level you declare for the element</span></span>

<span data-ttu-id="272c8-123">Należy zachować ostrożność podczas definiowania zmiennych o tej samej nazwie, ale innym zakresie, ponieważ takie działanie może prowadzić do nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="272c8-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="272c8-124">Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="272c8-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="272c8-125">Poziomy zakresu</span><span class="sxs-lookup"><span data-stu-id="272c8-125">Levels of Scope</span></span>

<span data-ttu-id="272c8-126">Element programistyczny jest dostępny w całym regionie, w którym jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="272c8-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="272c8-127">Cały kod w tym samym regionie może odwoływać się do elementu bez kwalifikowania jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="272c8-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="272c8-128">Zakres bloku</span><span class="sxs-lookup"><span data-stu-id="272c8-128">Block Scope</span></span>

<span data-ttu-id="272c8-129">Blok to zestaw instrukcji ujętych w instrukcji inicjujących i kończących deklaracje, takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="272c8-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="272c8-130">`Do` i `Loop`</span><span class="sxs-lookup"><span data-stu-id="272c8-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="272c8-131">`For`[`Each`] i`Next`</span><span class="sxs-lookup"><span data-stu-id="272c8-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="272c8-132">`If` i `End If`</span><span class="sxs-lookup"><span data-stu-id="272c8-132">`If` and `End If`</span></span>

- <span data-ttu-id="272c8-133">`Select` i `End Select`</span><span class="sxs-lookup"><span data-stu-id="272c8-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="272c8-134">`SyncLock` i `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="272c8-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="272c8-135">`Try` i `End Try`</span><span class="sxs-lookup"><span data-stu-id="272c8-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="272c8-136">`While` i `End While`</span><span class="sxs-lookup"><span data-stu-id="272c8-136">`While` and `End While`</span></span>

- <span data-ttu-id="272c8-137">`With` i `End With`</span><span class="sxs-lookup"><span data-stu-id="272c8-137">`With` and `End With`</span></span>

<span data-ttu-id="272c8-138">Jeśli zadeklarujesz zmienną w bloku, można jej używać tylko w obrębie tego bloku.</span><span class="sxs-lookup"><span data-stu-id="272c8-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="272c8-139">W poniższym przykładzie zakres `cube` zmiennej całkowitej jest blokiem między `If` i `End If`i nie można już się odwoływać `cube` , gdy wykonywanie kończy się z bloku.</span><span class="sxs-lookup"><span data-stu-id="272c8-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="272c8-140">Nawet jeśli zakres zmiennej jest ograniczony do bloku, jego okres istnienia jest nadal w całej procedurze.</span><span class="sxs-lookup"><span data-stu-id="272c8-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="272c8-141">W przypadku wprowadzenia bloku więcej niż raz podczas procedury Każda zmienna bloku zachowuje poprzednią wartość.</span><span class="sxs-lookup"><span data-stu-id="272c8-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="272c8-142">Aby uniknąć nieoczekiwanych wyników w taki sposób, należy inicjować zmienne blokowe na początku bloku.</span><span class="sxs-lookup"><span data-stu-id="272c8-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="272c8-143">Zakres procedury</span><span class="sxs-lookup"><span data-stu-id="272c8-143">Procedure Scope</span></span>

<span data-ttu-id="272c8-144">Element zadeklarowany w ramach procedury nie jest dostępny poza tą procedurą.</span><span class="sxs-lookup"><span data-stu-id="272c8-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="272c8-145">Tylko procedura, która zawiera deklarację, może jej używać.</span><span class="sxs-lookup"><span data-stu-id="272c8-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="272c8-146">Zmienne na tym poziomie są również nazywane *zmiennymi lokalnymi*.</span><span class="sxs-lookup"><span data-stu-id="272c8-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="272c8-147">Deklaruje je za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)z lub bez słowa kluczowego [static](../../../../visual-basic/language-reference/modifiers/static.md) .</span><span class="sxs-lookup"><span data-stu-id="272c8-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="272c8-148">Procedura i zakres bloku są ściśle powiązane.</span><span class="sxs-lookup"><span data-stu-id="272c8-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="272c8-149">Jeśli zadeklarujesz zmienną wewnątrz procedury, ale poza jakimkolwiek blokiem w ramach tej procedury, można myśleć o zmiennej jako zakresu bloku, gdzie blok jest całą procedurą.</span><span class="sxs-lookup"><span data-stu-id="272c8-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="272c8-150">Wszystkie elementy lokalne, nawet jeśli są `Static` zmiennymi, są prywatne do procedury, w której się znajdują.</span><span class="sxs-lookup"><span data-stu-id="272c8-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="272c8-151">Nie można zadeklarować żadnego elementu za pomocą [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) słowa kluczowego w ramach procedury.</span><span class="sxs-lookup"><span data-stu-id="272c8-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="272c8-152">Zakres modułu</span><span class="sxs-lookup"><span data-stu-id="272c8-152">Module Scope</span></span>

<span data-ttu-id="272c8-153">Dla wygody poziom jednoterminowego *modułu* jest stosowany równomiernie dla modułów, klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="272c8-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="272c8-154">Można zadeklarować elementy na tym poziomie poprzez umieszczenie instrukcji deklaracji poza procedurą lub blokiem, ale w module, klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="272c8-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="272c8-155">Po wprowadzeniu deklaracji na poziomie modułu wybrany poziom dostępu określa zakres.</span><span class="sxs-lookup"><span data-stu-id="272c8-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="272c8-156">Przestrzeń nazw, która zawiera moduł, klasę lub strukturę, ma także wpływ na zakres.</span><span class="sxs-lookup"><span data-stu-id="272c8-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="272c8-157">Elementy, dla których deklarujesz [prywatny](../../../../visual-basic/language-reference/modifiers/private.md) poziom dostępu, są dostępne dla każdej procedury w tym module, ale nie do żadnego kodu w innym module.</span><span class="sxs-lookup"><span data-stu-id="272c8-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="272c8-158">W przypadku, `Dim`gdynie sąużywaneżadnesłowakluczowepoziomudostępu.`Private`</span><span class="sxs-lookup"><span data-stu-id="272c8-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="272c8-159">Jednak zakres i poziom dostępu można uczynić bardziej oczywistymi przy użyciu `Private` słowa kluczowego `Dim` w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="272c8-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="272c8-160">W poniższym przykładzie wszystkie procedury zdefiniowane w module mogą odwoływać się do zmiennej `strMsg`ciągu.</span><span class="sxs-lookup"><span data-stu-id="272c8-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="272c8-161">Gdy druga procedura jest wywoływana, wyświetla zawartość zmiennej `strMsg` String w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="272c8-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="272c8-162">Zakres przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="272c8-162">Namespace Scope</span></span>

<span data-ttu-id="272c8-163">Jeśli zadeklarujesz element na poziomie modułu przy użyciu [](../../../../visual-basic/language-reference/modifiers/friend.md) słowa kluczowego zaprzyjaźnione lub [publiczne](../../../../visual-basic/language-reference/modifiers/public.md) , będzie on dostępny dla wszystkich procedur w całym obszarze nazw, w którym jest zadeklarowany element.</span><span class="sxs-lookup"><span data-stu-id="272c8-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="272c8-164">Przy następujących zmianach do powyższego przykładu zmienna `strMsg` String może być określana przez kod w dowolnym miejscu w przestrzeni nazw swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="272c8-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="272c8-165">Zakres przestrzeni nazw zawiera zagnieżdżone przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="272c8-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="272c8-166">Element dostępny w przestrzeni nazw jest również dostępny z poziomu dowolnej przestrzeni nazw zagnieżdżonej w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="272c8-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="272c8-167">Jeśli projekt nie zawiera żadnych [instrukcji Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), wszystko w projekcie znajduje się w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="272c8-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="272c8-168">W takim przypadku zakres przestrzeni nazw może być uważany za zakres projektu.</span><span class="sxs-lookup"><span data-stu-id="272c8-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="272c8-169">`Public`elementy w module, klasie lub strukturze są również dostępne dla każdego projektu, który odwołuje się do projektu.</span><span class="sxs-lookup"><span data-stu-id="272c8-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="272c8-170">Wybór zakresu</span><span class="sxs-lookup"><span data-stu-id="272c8-170">Choice of Scope</span></span>

<span data-ttu-id="272c8-171">Podczas deklarowania zmiennej należy pamiętać o następujących kwestiach podczas wybierania jej zakresu.</span><span class="sxs-lookup"><span data-stu-id="272c8-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="272c8-172">Zalety zmiennych lokalnych</span><span class="sxs-lookup"><span data-stu-id="272c8-172">Advantages of Local Variables</span></span>

<span data-ttu-id="272c8-173">Zmienne lokalne są dobrym wyborem dla dowolnego rodzaju obliczeń tymczasowych, z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="272c8-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="272c8-174">**Unikanie konfliktu nazw.**</span><span class="sxs-lookup"><span data-stu-id="272c8-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="272c8-175">Nazwy zmiennych lokalnych nie są podatne na konflikt.</span><span class="sxs-lookup"><span data-stu-id="272c8-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="272c8-176">Na przykład można utworzyć kilka różnych procedur zawierających zmienną o nazwie `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="272c8-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="272c8-177">O ile każda z `intTemp` nich jest zadeklarowana jako zmienna lokalna, każda procedura rozpoznaje tylko własną wersję programu `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="272c8-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="272c8-178">Każda procedura może zmienić wartość w jej lokalnej `intTemp` bez `intTemp` wpływu na zmienne w innych procedurach.</span><span class="sxs-lookup"><span data-stu-id="272c8-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="272c8-179">**Użycie pamięci.**</span><span class="sxs-lookup"><span data-stu-id="272c8-179">**Memory Consumption.**</span></span> <span data-ttu-id="272c8-180">Zmienne lokalne zużywają pamięć tylko wtedy, gdy ich procedura jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="272c8-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="272c8-181">Pamięć jest wydawana, gdy procedura wraca do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="272c8-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="272c8-182">Z kolei zmienne [udostępnione](../../../../visual-basic/language-reference/modifiers/shared.md) i [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) zużywają zasoby pamięci do momentu zatrzymania działania aplikacji, dlatego należy używać ich tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="272c8-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="272c8-183">*Zmienne wystąpień* zużywają pamięć, gdy ich wystąpienie nadal istnieje, co sprawia, że są mniej wydajne niż zmienne lokalne, ale potencjalnie `Shared` bardziej `Static` wydajne niż lub zmienne.</span><span class="sxs-lookup"><span data-stu-id="272c8-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="272c8-184">Minimalizacja zakresu</span><span class="sxs-lookup"><span data-stu-id="272c8-184">Minimizing Scope</span></span>

<span data-ttu-id="272c8-185">Ogólnie rzecz biorąc, w przypadku deklarowania dowolnej zmiennej lub stałej jest dobrym sposobem programowania, aby zakres był możliwie wąski (zakres blokowy jest najwęższy).</span><span class="sxs-lookup"><span data-stu-id="272c8-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="272c8-186">Pozwala to zaoszczędzić pamięć i zminimalizować prawdopodobieństwo błędnego kodu do niewłaściwej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="272c8-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="272c8-187">Podobnie należy zadeklarować zmienną, która ma być [statyczna](../../../../visual-basic/language-reference/modifiers/static.md) tylko wtedy, gdy jest to konieczne, aby zachować jej wartość między wywołaniami procedur.</span><span class="sxs-lookup"><span data-stu-id="272c8-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="272c8-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="272c8-188">See also</span></span>

- [<span data-ttu-id="272c8-189">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="272c8-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="272c8-190">Instrukcje: Kontrolowanie zakresu zmiennej</span><span class="sxs-lookup"><span data-stu-id="272c8-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="272c8-191">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="272c8-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="272c8-192">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="272c8-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="272c8-193">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="272c8-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="272c8-194">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="272c8-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
