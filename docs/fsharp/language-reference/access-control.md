---
title: Kontrola dostępu
description: Dowiedz się, jak kontrolować dostęp do elementów programistycznych, takich jak typy, metody i funkcje, F# w języku programowania.
ms.date: 05/16/2016
ms.openlocfilehash: ed77a09cf87aabf9a4134276e89e84aa42abd3c3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629959"
---
# <a name="access-control"></a><span data-ttu-id="68d13-103">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="68d13-103">Access Control</span></span>

<span data-ttu-id="68d13-104">*Kontrola dostępu* odwołuje się do deklarowania, którzy klienci mogą używać niektórych elementów programu, takich jak typy, metody i funkcje.</span><span class="sxs-lookup"><span data-stu-id="68d13-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="68d13-105">Podstawy Access Control</span><span class="sxs-lookup"><span data-stu-id="68d13-105">Basics of Access Control</span></span>

<span data-ttu-id="68d13-106">W F#programie specyfikatory `public` `internal`kontroli dostępu, i `private` mogą być stosowane do modułów, typów, metod, definicji wartości, funkcji, właściwości i pól jawnych.</span><span class="sxs-lookup"><span data-stu-id="68d13-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="68d13-107">`public`wskazuje, że można uzyskać dostęp do jednostki przez wszystkie obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="68d13-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="68d13-108">`internal`wskazuje, że można uzyskać dostęp do jednostki tylko z tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="68d13-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="68d13-109">`private`wskazuje, że można uzyskać dostęp do jednostki tylko z otaczającego typu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="68d13-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="68d13-110">Specyfikator `protected` dostępu nie jest używany w programie F#, chociaż jest akceptowalny, jeśli używasz typów utworzonych w językach, które obsługują `protected` dostęp.</span><span class="sxs-lookup"><span data-stu-id="68d13-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="68d13-111">W związku z tym, jeśli zastąpisz metodę chronioną, Metoda pozostanie dostępna tylko w obrębie klasy i jej elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="68d13-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="68d13-112">Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą jednostki, z wyjątkiem sytuacji, gdy `mutable` jest używany lub `inline` specyfikator kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="68d13-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="68d13-113">Jeśli nie jest używany żaden specyfikator dostępu, wartość domyślna to `public`, `let` z wyjątkiem powiązań w typie, który jest zawsze `private` typem.</span><span class="sxs-lookup"><span data-stu-id="68d13-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="68d13-114">Podpisy F# w programie zapewniają inny mechanizm kontroli dostępu F# do elementów programu.</span><span class="sxs-lookup"><span data-stu-id="68d13-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="68d13-115">Podpisy nie są wymagane do kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="68d13-115">Signatures are not required for access control.</span></span> <span data-ttu-id="68d13-116">Aby uzyskać więcej informacji, [](signatures.md)Zobacz podpisy.</span><span class="sxs-lookup"><span data-stu-id="68d13-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="68d13-117">Reguły dla Access Control</span><span class="sxs-lookup"><span data-stu-id="68d13-117">Rules for Access Control</span></span>

<span data-ttu-id="68d13-118">Kontrola dostępu podlega następującym zasadom:</span><span class="sxs-lookup"><span data-stu-id="68d13-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="68d13-119">Deklaracje dziedziczenia (czyli użycie `inherit` , aby określić klasę bazową dla klasy), deklaracje interfejsu (to oznacza, że klasa implementuje interfejs), a abstrakcyjne składowe zawsze mają taką samą dostępność jak typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="68d13-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="68d13-120">W związku z tym nie można użyć specyfikatora kontroli dostępu dla tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="68d13-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="68d13-121">Dostępność indywidualnych przypadków w Unii rozłącznych jest określana na podstawie dostępności samego związku rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="68d13-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="68d13-122">Oznacza to, że konkretny przypadek Unii nie jest mniej dostępny niż sam związek.</span><span class="sxs-lookup"><span data-stu-id="68d13-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="68d13-123">Ułatwienia dostępu dla poszczególnych pól typu rekordu nie mogą być określane przez dostępność samego rekordu.</span><span class="sxs-lookup"><span data-stu-id="68d13-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="68d13-124">Oznacza to, że określona etykieta rekordu nie jest mniej dostępna od samego rekordu.</span><span class="sxs-lookup"><span data-stu-id="68d13-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="68d13-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="68d13-125">Example</span></span>

<span data-ttu-id="68d13-126">Poniższy kod ilustruje użycie specyfikatorów kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="68d13-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="68d13-127">Istnieją dwa pliki w projekcie `Module1.fs` i. `Module2.fs`</span><span class="sxs-lookup"><span data-stu-id="68d13-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="68d13-128">Każdy plik jest niejawnie modułem.</span><span class="sxs-lookup"><span data-stu-id="68d13-128">Each file is implicitly a module.</span></span> <span data-ttu-id="68d13-129">W związku z tym istnieją dwa moduły `Module1` i `Module2`.</span><span class="sxs-lookup"><span data-stu-id="68d13-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="68d13-130">Typ prywatny i wewnętrzny są zdefiniowane w `Module1`.</span><span class="sxs-lookup"><span data-stu-id="68d13-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="68d13-131">Nie można uzyskać dostępu do typu prywatnego `Module2`z, ale wewnętrzny typ może.</span><span class="sxs-lookup"><span data-stu-id="68d13-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="68d13-132">Poniższy kod testuje dostępność typów utworzonych w `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="68d13-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="68d13-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68d13-133">See also</span></span>

- [<span data-ttu-id="68d13-134">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="68d13-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="68d13-135">Podpisy</span><span class="sxs-lookup"><span data-stu-id="68d13-135">Signatures</span></span>](signatures.md)
