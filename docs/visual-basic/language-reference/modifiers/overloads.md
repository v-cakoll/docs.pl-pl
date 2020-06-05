---
title: Przeciążenia
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392109"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="f89ce-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f89ce-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="f89ce-103">Określa, że właściwość lub procedura ponownie deklaruje jedną lub więcej istniejących właściwości lub procedur o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f89ce-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f89ce-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f89ce-104">Remarks</span></span>

<span data-ttu-id="f89ce-105">*Przeciążanie* jest sposobem dostarczenia więcej niż jednej definicji dla danej właściwości lub nazwy procedury w tym samym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f89ce-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="f89ce-106">Redeklaruj właściwość lub procedurę z innym podpisem jest czasami nazywana *ukrywaniem przez podpis*.</span><span class="sxs-lookup"><span data-stu-id="f89ce-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="f89ce-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="f89ce-107">Rules</span></span>

- <span data-ttu-id="f89ce-108">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="f89ce-108">**Declaration Context.**</span></span> <span data-ttu-id="f89ce-109">Można użyć `Overloads` tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="f89ce-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="f89ce-110">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="f89ce-110">**Combined Modifiers.**</span></span> <span data-ttu-id="f89ce-111">Nie można określić `Overloads` razem z [cieniami](shadows.md) w tej samej deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="f89ce-111">You cannot specify `Overloads` together with [Shadows](shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="f89ce-112">**Wymagane różnice.**</span><span class="sxs-lookup"><span data-stu-id="f89ce-112">**Required Differences.**</span></span> <span data-ttu-id="f89ce-113">*Sygnatura* w tej deklaracji musi być różna od sygnatury każdej właściwości lub procedury, która została przeciążać.</span><span class="sxs-lookup"><span data-stu-id="f89ce-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="f89ce-114">Podpis składa się z nazwy właściwości lub procedury wraz z następującymi:</span><span class="sxs-lookup"><span data-stu-id="f89ce-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="f89ce-115">liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="f89ce-115">the number of parameters</span></span>

  - <span data-ttu-id="f89ce-116">kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="f89ce-116">the order of the parameters</span></span>

  - <span data-ttu-id="f89ce-117">typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="f89ce-117">the data types of the parameters</span></span>

  - <span data-ttu-id="f89ce-118">liczba parametrów typu (dla procedury ogólnej)</span><span class="sxs-lookup"><span data-stu-id="f89ce-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="f89ce-119">zwracany typ (tylko dla procedury operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="f89ce-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="f89ce-120">Wszystkie przeciążenia muszą mieć taką samą nazwę, ale każdy z nich musi się różnić od wszystkich innych w jednym lub więcej z powyższych kwestii.</span><span class="sxs-lookup"><span data-stu-id="f89ce-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="f89ce-121">Dzięki temu kompilator może odróżnić, która wersja, która ma zostać użyta, gdy kod wywołuje właściwość lub procedurę.</span><span class="sxs-lookup"><span data-stu-id="f89ce-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="f89ce-122">**Niedozwolone różnice.**</span><span class="sxs-lookup"><span data-stu-id="f89ce-122">**Disallowed Differences.**</span></span> <span data-ttu-id="f89ce-123">Zmiana co najmniej jednego z następujących elementów nie jest prawidłowa w celu przeładowania właściwości lub procedury, ponieważ nie są one częścią podpisu:</span><span class="sxs-lookup"><span data-stu-id="f89ce-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="f89ce-124">Czy zwraca wartość (dla procedury)</span><span class="sxs-lookup"><span data-stu-id="f89ce-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="f89ce-125">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="f89ce-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="f89ce-126">nazwy parametrów lub parametrów typu</span><span class="sxs-lookup"><span data-stu-id="f89ce-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="f89ce-127">ograniczenia dotyczące parametrów typu (dla procedury ogólnej)</span><span class="sxs-lookup"><span data-stu-id="f89ce-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="f89ce-128">Słowa kluczowe modyfikatora parametru (takie jak `ByRef` lub `Optional` )</span><span class="sxs-lookup"><span data-stu-id="f89ce-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="f89ce-129">Słowa kluczowe modyfikatora właściwości lub procedury (takie jak `Public` lub `Shared` )</span><span class="sxs-lookup"><span data-stu-id="f89ce-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="f89ce-130">**Modyfikator opcjonalny.**</span><span class="sxs-lookup"><span data-stu-id="f89ce-130">**Optional Modifier.**</span></span> <span data-ttu-id="f89ce-131">Nie trzeba używać `Overloads` modyfikatora podczas definiowania wielu przeciążonych właściwości lub procedur w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="f89ce-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="f89ce-132">Jeśli jednak używasz `Overloads` w jednej z deklaracji, musisz użyć go we wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="f89ce-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="f89ce-133">**Obserwowanie i Przeciążenie.**</span><span class="sxs-lookup"><span data-stu-id="f89ce-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="f89ce-134">`Overloads`może również służyć do cieniowania istniejącego elementu członkowskiego lub zestawu przeciążonych elementów członkowskich w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="f89ce-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="f89ce-135">Gdy używasz `Overloads` w ten sposób, deklarujesz właściwość lub metodę o tej samej nazwie i tej samej liście parametrów co element członkowski klasy bazowej i nie podasz `Shadows` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="f89ce-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="f89ce-136">W przypadku korzystania `Overrides` z programu kompilator niejawnie dodaje w `Overloads` taki sposób, aby interfejsy API biblioteki działały w łatwiejszy sposób.</span><span class="sxs-lookup"><span data-stu-id="f89ce-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="f89ce-137">`Overloads`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="f89ce-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="f89ce-138">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f89ce-138">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="f89ce-139">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="f89ce-139">Operator Statement</span></span>](../statements/operator-statement.md)

- [<span data-ttu-id="f89ce-140">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="f89ce-140">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="f89ce-141">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f89ce-141">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="f89ce-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f89ce-142">See also</span></span>

- [<span data-ttu-id="f89ce-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="f89ce-143">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="f89ce-144">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="f89ce-144">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="f89ce-145">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f89ce-145">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="f89ce-146">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="f89ce-146">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="f89ce-147">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="f89ce-147">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
