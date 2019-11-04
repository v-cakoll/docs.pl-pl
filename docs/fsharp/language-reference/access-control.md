---
title: Kontrola dostępu
description: Dowiedz się, jak kontrolować dostęp do elementów programistycznych, takich jak typy, metody i funkcje, F# w języku programowania.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425110"
---
# <a name="access-control"></a><span data-ttu-id="351ff-103">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="351ff-103">Access Control</span></span>

<span data-ttu-id="351ff-104">*Kontrola dostępu* odwołuje się do deklarowania, którzy klienci mogą używać niektórych elementów programu, takich jak typy, metody i funkcje.</span><span class="sxs-lookup"><span data-stu-id="351ff-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="351ff-105">Podstawy Access Control</span><span class="sxs-lookup"><span data-stu-id="351ff-105">Basics of Access Control</span></span>

<span data-ttu-id="351ff-106">W F#programie specyfikatory kontroli dostępu `public`, `internal`i `private` mogą być stosowane do modułów, typów, metod, definicji wartości, funkcji, właściwości i pól jawnych.</span><span class="sxs-lookup"><span data-stu-id="351ff-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="351ff-107">`public` wskazuje, że można uzyskać dostęp do jednostki przez wszystkie obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="351ff-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="351ff-108">`internal` wskazuje, że można uzyskać dostęp do jednostki tylko z tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="351ff-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="351ff-109">`private` wskazuje, że można uzyskać dostęp do jednostki tylko z otaczającego typu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="351ff-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="351ff-110">`protected` specyfikatora dostępu nie jest używany w programie F#, chociaż jest akceptowalny, jeśli używasz typów utworzonych w językach, które obsługują `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="351ff-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="351ff-111">W związku z tym, jeśli zastąpisz metodę chronioną, Metoda pozostanie dostępna tylko w obrębie klasy i jej elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="351ff-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="351ff-112">Ogólnie rzecz biorąc, specyfikator jest umieszczony przed nazwą jednostki, z wyjątkiem sytuacji, gdy jest używany specyfikator `mutable` lub `inline`, który pojawia się Po specyfikatorze kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="351ff-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="351ff-113">Jeśli nie jest używany żaden specyfikator dostępu, wartość domyślna to `public`, z wyjątkiem powiązań `let` w typie, które są zawsze `private` do typu.</span><span class="sxs-lookup"><span data-stu-id="351ff-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="351ff-114">Podpisy F# w programie zapewniają inny mechanizm kontroli dostępu F# do elementów programu.</span><span class="sxs-lookup"><span data-stu-id="351ff-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="351ff-115">Podpisy nie są wymagane do kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="351ff-115">Signatures are not required for access control.</span></span> <span data-ttu-id="351ff-116">Aby uzyskać więcej informacji, zobacz [podpisy](signature-files.md).</span><span class="sxs-lookup"><span data-stu-id="351ff-116">For more information, see [Signatures](signature-files.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="351ff-117">Reguły dla Access Control</span><span class="sxs-lookup"><span data-stu-id="351ff-117">Rules for Access Control</span></span>

<span data-ttu-id="351ff-118">Kontrola dostępu podlega następującym zasadom:</span><span class="sxs-lookup"><span data-stu-id="351ff-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="351ff-119">Deklaracje dziedziczenia (czyli użycie `inherit`, aby określić klasę bazową dla klasy), deklaracje interfejsu (oznacza to, że klasa implementuje interfejs), a abstrakcyjne składowe zawsze mają takie same ułatwienia dostępu jak typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="351ff-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="351ff-120">W związku z tym nie można użyć specyfikatora kontroli dostępu dla tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="351ff-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="351ff-121">Dostępność indywidualnych przypadków w Unii rozłącznych jest określana na podstawie dostępności samego związku rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="351ff-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="351ff-122">Oznacza to, że konkretny przypadek Unii nie jest mniej dostępny niż sam związek.</span><span class="sxs-lookup"><span data-stu-id="351ff-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="351ff-123">Dostępność dla poszczególnych pól typu rekordu jest określana na podstawie dostępności samego rekordu.</span><span class="sxs-lookup"><span data-stu-id="351ff-123">Accessibility for individual fields of a record type is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="351ff-124">Oznacza to, że określona etykieta rekordu nie jest mniej dostępna od samego rekordu.</span><span class="sxs-lookup"><span data-stu-id="351ff-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="351ff-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="351ff-125">Example</span></span>

<span data-ttu-id="351ff-126">Poniższy kod ilustruje użycie specyfikatorów kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="351ff-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="351ff-127">W projekcie znajdują się dwa pliki, `Module1.fs` i `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="351ff-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="351ff-128">Każdy plik jest niejawnie modułem.</span><span class="sxs-lookup"><span data-stu-id="351ff-128">Each file is implicitly a module.</span></span> <span data-ttu-id="351ff-129">W związku z tym istnieją dwa moduły `Module1` i `Module2`.</span><span class="sxs-lookup"><span data-stu-id="351ff-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="351ff-130">Typ prywatny i wewnętrzny są zdefiniowane w `Module1`.</span><span class="sxs-lookup"><span data-stu-id="351ff-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="351ff-131">Nie można uzyskać dostępu do typu prywatnego z `Module2`, ale wewnętrzny typ może.</span><span class="sxs-lookup"><span data-stu-id="351ff-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="351ff-132">Poniższy kod testuje dostępność typów utworzonych w `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="351ff-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="351ff-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="351ff-133">See also</span></span>

- [<span data-ttu-id="351ff-134">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="351ff-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="351ff-135">Podpisy</span><span class="sxs-lookup"><span data-stu-id="351ff-135">Signatures</span></span>](signature-files.md)
