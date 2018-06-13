---
title: User-Defined Data Type
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
ms.openlocfilehash: 07f04fb111863ca18d4966a7f0f967f11719aeec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590678"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="9f975-102">User-Defined Data Type</span><span class="sxs-lookup"><span data-stu-id="9f975-102">User-Defined Data Type</span></span>
<span data-ttu-id="9f975-103">Przechowuje dane w formacie, który należy zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="9f975-103">Holds data in a format you define.</span></span> <span data-ttu-id="9f975-104">`Structure` Instrukcji definiuje format.</span><span class="sxs-lookup"><span data-stu-id="9f975-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="9f975-105">Poprzednie wersje programu Visual Basic obsługuje typ zdefiniowany przez użytkownika (UDT).</span><span class="sxs-lookup"><span data-stu-id="9f975-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="9f975-106">Bieżąca wersja rozszerza UDT do *struktury*.</span><span class="sxs-lookup"><span data-stu-id="9f975-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="9f975-107">Struktura jest złączeniem co najmniej jeden *członków* różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="9f975-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="9f975-108">Visual Basic traktuje jako pojedynczą jednostkę, struktury, chociaż można także przejść do jego elementów członkowskich indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="9f975-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f975-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f975-109">Remarks</span></span>  
 <span data-ttu-id="9f975-110">Definiowanie i używać typu danych struktury, gdy trzeba połączyć różnych typów danych w pojedynczą jednostkę, lub żaden z typów podstawowych danych z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="9f975-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="9f975-111">Wartość domyślna typu danych struktury składa się z kombinacji wartości domyślne wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="9f975-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="9f975-112">Format deklaracji</span><span class="sxs-lookup"><span data-stu-id="9f975-112">Declaration Format</span></span>  
 <span data-ttu-id="9f975-113">Rozpoczyna się od deklaracji struktury [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md) i kończy `End``Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9f975-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End``Structure` statement.</span></span> <span data-ttu-id="9f975-114">`Structure` Instrukcja zawiera nazwę struktury, która jest również identyfikator typu danych, jest zdefiniowanie struktury.</span><span class="sxs-lookup"><span data-stu-id="9f975-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="9f975-115">Inne części kodu, można użyć tego identyfikatora do deklarowania zmiennych, parametry i funkcja zwracają wartości typu danych tej struktury.</span><span class="sxs-lookup"><span data-stu-id="9f975-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="9f975-116">Deklaracje między `Structure` i `End``Structure` instrukcje zdefiniować elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="9f975-116">The declarations between the `Structure` and `End``Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="9f975-117">Poziomy dostępu elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="9f975-117">Member Access Levels</span></span>  
 <span data-ttu-id="9f975-118">Musisz zadeklarować każdego elementu członkowskiego przy użyciu [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md) lub instrukcję, która określa poziom dostępu, takich jak [publicznego](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnego](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="9f975-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="9f975-119">Jeśli używasz `Dim` instrukcji, wartości domyślnych poziomu dostępu do publicznej.</span><span class="sxs-lookup"><span data-stu-id="9f975-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="9f975-120">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="9f975-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="9f975-121">**Zużycie pamięci.**</span><span class="sxs-lookup"><span data-stu-id="9f975-121">**Memory Consumption.**</span></span> <span data-ttu-id="9f975-122">Podobnie jak w przypadku wszystkich złożone typy danych, nie można bezpiecznie obliczania zużycia całkowitej ilości pamięci struktury przez dodanie alokacji magazynu nominalnego jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9f975-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="9f975-123">Ponadto nie można bezpiecznie zakładać, że kolejność magazynu w pamięci jest taka sama jak zamówienia deklaracji.</span><span class="sxs-lookup"><span data-stu-id="9f975-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="9f975-124">Jeśli potrzebujesz do sterowania układem magazynu struktury, możesz zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9f975-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="9f975-125">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="9f975-125">**Interop Considerations.**</span></span> <span data-ttu-id="9f975-126">Jeśli użytkownik są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy danych zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z programem Visual Basic struktury typów.</span><span class="sxs-lookup"><span data-stu-id="9f975-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="9f975-127">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="9f975-127">**Widening.**</span></span> <span data-ttu-id="9f975-128">Nie jest automatyczna konwersja do lub z dowolnego typu danych struktury.</span><span class="sxs-lookup"><span data-stu-id="9f975-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="9f975-129">Operatory konwersji można zdefiniować na przy użyciu struktury [operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md), a każdy operatora konwersji można zadeklarować `Widening` lub `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="9f975-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="9f975-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="9f975-130">**Type Characters.**</span></span> <span data-ttu-id="9f975-131">Typy danych struktury mieć znak literalny typu lub znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="9f975-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="9f975-132">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="9f975-132">**Framework Type.**</span></span> <span data-ttu-id="9f975-133">Nie ma odpowiedniego typu w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f975-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="9f975-134">Wszystkie struktury dziedziczyć po klasie .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale nie poszczególnych struktura odpowiada <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9f975-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f975-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f975-135">Example</span></span>  
 <span data-ttu-id="9f975-136">Następujące modelu zawiera konturu deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="9f975-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f975-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f975-137">See Also</span></span>  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [<span data-ttu-id="9f975-138">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9f975-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="9f975-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="9f975-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="9f975-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9f975-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="9f975-141">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9f975-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="9f975-142">Widening</span><span class="sxs-lookup"><span data-stu-id="9f975-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="9f975-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="9f975-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="9f975-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="9f975-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="9f975-145">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="9f975-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
