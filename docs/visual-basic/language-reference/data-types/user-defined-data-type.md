---
title: Typ danych zdefiniowany przez użytkownika (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 1dac93145b6e11a0d149f03b43e1e0b28b770925
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276904"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="210c3-102">User-Defined Data Type</span><span class="sxs-lookup"><span data-stu-id="210c3-102">User-Defined Data Type</span></span>
<span data-ttu-id="210c3-103">Przechowuje dane w postaci, jaką zdefiniujesz.</span><span class="sxs-lookup"><span data-stu-id="210c3-103">Holds data in a format you define.</span></span> <span data-ttu-id="210c3-104">`Structure` Instrukcja definiuje format.</span><span class="sxs-lookup"><span data-stu-id="210c3-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="210c3-105">Poprzednie wersje języka Visual Basic obsługuje typ zdefiniowany przez użytkownika (UDT).</span><span class="sxs-lookup"><span data-stu-id="210c3-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="210c3-106">Bieżąca wersja rozwija UDT do *struktury*.</span><span class="sxs-lookup"><span data-stu-id="210c3-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="210c3-107">Struktura jest łączenia jednej lub więcej *członków* różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="210c3-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="210c3-108">Visual Basic traktuje struktury jako pojedynczą jednostkę, chociaż można także przejść do jego członków indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="210c3-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="210c3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="210c3-109">Remarks</span></span>  
 <span data-ttu-id="210c3-110">Definiowanie i korzystanie z typem struktury danych, gdy trzeba połączyć różne typy danych w pojedynczą jednostkę, lub gdy żaden z typów podstawowych danych spełniały Twoje potrzeby.</span><span class="sxs-lookup"><span data-stu-id="210c3-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="210c3-111">Wartość domyślna typu danych struktury składa się z kombinacji wartości domyślne wszystkich członków.</span><span class="sxs-lookup"><span data-stu-id="210c3-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="210c3-112">Format deklaracji</span><span class="sxs-lookup"><span data-stu-id="210c3-112">Declaration Format</span></span>  
 <span data-ttu-id="210c3-113">Deklaracji struktury zaczyna się od [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md) i kończy `End Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="210c3-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="210c3-114">`Structure` Instrukcji dostarcza nazwę struktury, która jest również identyfikator typu danych jest zdefiniowanie struktury.</span><span class="sxs-lookup"><span data-stu-id="210c3-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="210c3-115">Inne części kodu można użyć tego identyfikatora do deklarowania zmiennych, parametrów i funkcja zwraca wartości o typie danych tej struktury.</span><span class="sxs-lookup"><span data-stu-id="210c3-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="210c3-116">Deklaracje między `Structure` i `End Structure` instrukcji Definiowanie elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="210c3-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="210c3-117">Poziomy dostępu elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="210c3-117">Member Access Levels</span></span>  
 <span data-ttu-id="210c3-118">Należy zadeklarować każdego członka za pomocą [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md) lub instrukcję, która określa poziom dostępu, takich jak [publicznych](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatne](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="210c3-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="210c3-119">Jeśli używasz `Dim` instrukcja, wartości domyślnych poziomu dostępu na wartość publiczne.</span><span class="sxs-lookup"><span data-stu-id="210c3-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="210c3-120">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="210c3-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="210c3-121">**Zużycie pamięci.**</span><span class="sxs-lookup"><span data-stu-id="210c3-121">**Memory Consumption.**</span></span> <span data-ttu-id="210c3-122">Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć łącznego zużycia pamięci przez strukturę, dodając do siebie nominalne alokacje magazynu jej składowych.</span><span class="sxs-lookup"><span data-stu-id="210c3-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="210c3-123">Ponadto nie można bezpiecznie założyć, że kolejność magazynowania w pamięci jest taka sama jak kolejność deklaracji.</span><span class="sxs-lookup"><span data-stu-id="210c3-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="210c3-124">Jeśli musisz kontrolować układ magazynu struktury, możesz zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> w instrukcji `Structure`.</span><span class="sxs-lookup"><span data-stu-id="210c3-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="210c3-125">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="210c3-125">**Interop Considerations.**</span></span> <span data-ttu-id="210c3-126">Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, że typy danych zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z języka Visual Basic strukturę typów.</span><span class="sxs-lookup"><span data-stu-id="210c3-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="210c3-127">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="210c3-127">**Widening.**</span></span> <span data-ttu-id="210c3-128">Nie jest automatyczna konwersja do / z dowolnego typu danych struktury.</span><span class="sxs-lookup"><span data-stu-id="210c3-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="210c3-129">Operatory konwersji można zdefiniować w sieci za pomocą struktury [operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md), i można zadeklarować każdego operatora konwersji `Widening` lub `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="210c3-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="210c3-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="210c3-130">**Type Characters.**</span></span> <span data-ttu-id="210c3-131">Typy danych struktury mieć znak literalny typu lub znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="210c3-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="210c3-132">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="210c3-132">**Framework Type.**</span></span> <span data-ttu-id="210c3-133">W .NET Framework, nie ma żadnego odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="210c3-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="210c3-134">Wszystkie struktury dziedziczą z klasy .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale nie struktury poszczególnych odnosi się do <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="210c3-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="210c3-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="210c3-135">Example</span></span>  
 <span data-ttu-id="210c3-136">Następujące paradygmat przedstawia zarys deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="210c3-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="210c3-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="210c3-137">See Also</span></span>  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [<span data-ttu-id="210c3-138">Typy danych</span><span class="sxs-lookup"><span data-stu-id="210c3-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="210c3-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="210c3-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="210c3-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="210c3-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="210c3-141">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="210c3-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="210c3-142">Widening</span><span class="sxs-lookup"><span data-stu-id="210c3-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="210c3-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="210c3-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="210c3-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="210c3-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="210c3-145">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="210c3-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
