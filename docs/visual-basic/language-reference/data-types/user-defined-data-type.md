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
ms.openlocfilehash: 99eeb4b619f6bb23d00f8e449de953d41843f714
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343866"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="811c9-102">User-Defined Data Type</span><span class="sxs-lookup"><span data-stu-id="811c9-102">User-Defined Data Type</span></span>

<span data-ttu-id="811c9-103">Przechowuje dane w formacie zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="811c9-103">Holds data in a format you define.</span></span> <span data-ttu-id="811c9-104">Instrukcja `Structure` definiuje format.</span><span class="sxs-lookup"><span data-stu-id="811c9-104">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="811c9-105">Poprzednie wersje Visual Basic obsługują typ zdefiniowany przez użytkownika (UDT).</span><span class="sxs-lookup"><span data-stu-id="811c9-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="811c9-106">Bieżąca wersja rozszerza UDT do *struktury*.</span><span class="sxs-lookup"><span data-stu-id="811c9-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="811c9-107">Struktura jest połączeniem jednego lub większej liczby *elementów członkowskich* różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="811c9-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="811c9-108">Visual Basic traktuje strukturę jako pojedynczą jednostkę, chociaż można także uzyskać dostęp do jej elementów członkowskich pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="811c9-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="811c9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="811c9-109">Remarks</span></span>

<span data-ttu-id="811c9-110">Zdefiniuj typ danych struktury i użyj go, jeśli chcesz połączyć różne typy danych w pojedynczą jednostkę lub gdy żaden z podstawowych typów danych nie odpowiada Twoim potrzebom.</span><span class="sxs-lookup"><span data-stu-id="811c9-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="811c9-111">Wartość domyślna struktury typu danych składa się z kombinacji wartości domyślnych każdego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="811c9-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="811c9-112">Format deklaracji</span><span class="sxs-lookup"><span data-stu-id="811c9-112">Declaration Format</span></span>

<span data-ttu-id="811c9-113">Deklaracja struktury rozpoczyna się od [instrukcji Structure](../../../visual-basic/language-reference/statements/structure-statement.md) i kończyć się instrukcją `End Structure`.</span><span class="sxs-lookup"><span data-stu-id="811c9-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="811c9-114">Instrukcja `Structure` dostarcza nazwę struktury, która jest również identyfikatorem typu danych definiującego strukturę.</span><span class="sxs-lookup"><span data-stu-id="811c9-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="811c9-115">Inne części kodu mogą używać tego identyfikatora do deklarowania zmiennych, parametrów i wartości zwracanych funkcji jako typu danych tej struktury.</span><span class="sxs-lookup"><span data-stu-id="811c9-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="811c9-116">Deklaracje między instrukcjami `Structure` i `End Structure` definiują elementy członkowskie struktury.</span><span class="sxs-lookup"><span data-stu-id="811c9-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="811c9-117">Poziomy dostępu członków</span><span class="sxs-lookup"><span data-stu-id="811c9-117">Member Access Levels</span></span>

<span data-ttu-id="811c9-118">Należy zadeklarować każdy element członkowski przy użyciu [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md) lub instrukcji, która określa poziom dostępu, na przykład [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)lub [Private](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="811c9-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="811c9-119">Jeśli używasz instrukcji `Dim`, poziom dostępu jest domyślnie publiczny.</span><span class="sxs-lookup"><span data-stu-id="811c9-119">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="811c9-120">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="811c9-120">Programming Tips</span></span>

- <span data-ttu-id="811c9-121">**Użycie pamięci.**</span><span class="sxs-lookup"><span data-stu-id="811c9-121">**Memory Consumption.**</span></span> <span data-ttu-id="811c9-122">Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć łącznego zużycia pamięci przez strukturę, dodając do siebie nominalne alokacje magazynu jej składowych.</span><span class="sxs-lookup"><span data-stu-id="811c9-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="811c9-123">Ponadto nie można bezpiecznie założyć, że kolejność magazynowania w pamięci jest taka sama jak kolejność deklaracji.</span><span class="sxs-lookup"><span data-stu-id="811c9-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="811c9-124">Jeśli konieczne jest kontrolowanie układu pamięci masowej struktury, można zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> do instrukcji `Structure`.</span><span class="sxs-lookup"><span data-stu-id="811c9-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="811c9-125">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="811c9-125">**Interop Considerations.**</span></span> <span data-ttu-id="811c9-126">Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy zdefiniowane przez użytkownika w innych środowiskach nie są zgodne z typami struktur Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="811c9-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="811c9-127">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="811c9-127">**Widening.**</span></span> <span data-ttu-id="811c9-128">Nie istnieje Automatyczna konwersja do lub z dowolnego typu danych struktury.</span><span class="sxs-lookup"><span data-stu-id="811c9-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="811c9-129">Operatory konwersji można definiować w strukturze przy użyciu [instrukcji operatora](../../../visual-basic/language-reference/statements/operator-statement.md)i można zadeklarować każdy operator konwersji do `Widening` lub `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="811c9-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="811c9-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="811c9-130">**Type Characters.**</span></span> <span data-ttu-id="811c9-131">Typy danych struktury nie mają znaku typu literału lub znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="811c9-131">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="811c9-132">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="811c9-132">**Framework Type.**</span></span> <span data-ttu-id="811c9-133">Brak odpowiedniego typu w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="811c9-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="811c9-134">Wszystkie struktury dziedziczą z klasy .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale żadna konkretna struktura nie odnosi się do <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="811c9-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="811c9-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="811c9-135">Example</span></span>

<span data-ttu-id="811c9-136">Poniższy model przedstawia kontur deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="811c9-136">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="811c9-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="811c9-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="811c9-138">Typy danych</span><span class="sxs-lookup"><span data-stu-id="811c9-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="811c9-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="811c9-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="811c9-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="811c9-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="811c9-141">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="811c9-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="811c9-142">Widening</span><span class="sxs-lookup"><span data-stu-id="811c9-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="811c9-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="811c9-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="811c9-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="811c9-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="811c9-145">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="811c9-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
