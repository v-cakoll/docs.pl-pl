---
title: "Kontrola dostępu (F#)"
description: "Informacje o sposobie kontrolowania dostępu do elementów programowania, takich jak typy, metod i funkcje w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 955b06fe-d1cd-431d-8db6-93e83b697453
ms.openlocfilehash: a02e20a585a0456577901f2762a0eeb0e3ecd2f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="access-control"></a><span data-ttu-id="95c57-104">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="95c57-104">Access Control</span></span>

<span data-ttu-id="95c57-105">*Kontrola dostępu* odwołuje się do deklarowania, których klienci mogą używać niektórych elementów programów, takich jak typy, metod i funkcje.</span><span class="sxs-lookup"><span data-stu-id="95c57-105">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>


## <a name="basics-of-access-control"></a><span data-ttu-id="95c57-106">Podstawowe informacje dotyczące kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="95c57-106">Basics of Access Control</span></span>
<span data-ttu-id="95c57-107">W języku F #, kontroli dostępu w specyfikatory `public`, `internal`, i `private` można zastosować do modułów, typy metod, definicje wartości, funkcji, właściwości i pola jawne.</span><span class="sxs-lookup"><span data-stu-id="95c57-107">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>


- <span data-ttu-id="95c57-108">`public`Wskazuje, czy jednostka jest dostępna przez wszystkie obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="95c57-108">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="95c57-109">`internal`Wskazuje, że jednostka jest możliwy tylko z tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="95c57-109">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="95c57-110">`private`Wskazuje, że jednostka jest możliwy tylko z otaczającym typu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="95c57-110">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>


>[!NOTE] 
<span data-ttu-id="95c57-111">Specyfikator dostępu `protected` nie jest używana w języku F #, chociaż jest dopuszczalne, jeśli używasz typy utworzone w językach, które obsługują `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="95c57-111">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="95c57-112">W związku z tym w przypadku przesłonięcia Metoda chroniona metodę pozostaje dostępna tylko w klasie i jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="95c57-112">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="95c57-113">Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą podmiotu, chyba że `mutable` lub `inline` specyfikator jest używana, które występują po specyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="95c57-113">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="95c57-114">Jeśli nie specyfikatora dostępu jest używana, wartością domyślną jest `public`, z wyjątkiem `let` powiązania w typie, które są zawsze `private` do typu.</span><span class="sxs-lookup"><span data-stu-id="95c57-114">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="95c57-115">Podpisy w języku F # Podaj inny mechanizm kontroli dostępu do elementów programu F #.</span><span class="sxs-lookup"><span data-stu-id="95c57-115">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="95c57-116">Podpisy nie są wymagane do kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="95c57-116">Signatures are not required for access control.</span></span> <span data-ttu-id="95c57-117">Aby uzyskać więcej informacji, zobacz [podpisy](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="95c57-117">For more information, see [Signatures](signatures.md).</span></span>


## <a name="rules-for-access-control"></a><span data-ttu-id="95c57-118">Zasady kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="95c57-118">Rules for Access Control</span></span>
<span data-ttu-id="95c57-119">Kontrola dostępu podlega następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="95c57-119">Access control is subject to the following rules:</span></span>


- <span data-ttu-id="95c57-120">Deklaracje dziedziczenia (oznacza to, że korzystanie z `inherit` określić klasę podstawową dla klasy) interfejsu deklaracje (które określając, że klasa implementuje interfejs) i abstrakcyjne elementy członkowskie zawsze mieć tą samą dostępnością, typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="95c57-120">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="95c57-121">W związku z tym specyfikatora dostępu nie można używać w tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="95c57-121">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="95c57-122">Poszczególnych przypadków Unii rozłącznych nie może mieć własne niezależnie od typu union Modyfikatory kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="95c57-122">Individual cases in a discriminated union cannot have their own access control modifiers separate from the union type.</span></span>

- <span data-ttu-id="95c57-123">Poszczególne pola typu rekordu nie może mieć własne niezależnie od typu rekordu Modyfikatory kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="95c57-123">Individual fields of a record type cannot have their own access control modifiers separate from the record type.</span></span>


## <a name="example"></a><span data-ttu-id="95c57-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="95c57-124">Example</span></span>
<span data-ttu-id="95c57-125">Poniższy kod przedstawia użycie specyfikatorów kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="95c57-125">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="95c57-126">Istnieją dwa pliki w projekcie `Module1.fs` i `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="95c57-126">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="95c57-127">Każdy plik jest niejawnie modułu.</span><span class="sxs-lookup"><span data-stu-id="95c57-127">Each file is implicitly a module.</span></span> <span data-ttu-id="95c57-128">Dlatego istnieją dwa moduły `Module1` i `Module2`.</span><span class="sxs-lookup"><span data-stu-id="95c57-128">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="95c57-129">Prywatny typ i wewnętrzny typ są zdefiniowane w `Module1`.</span><span class="sxs-lookup"><span data-stu-id="95c57-129">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="95c57-130">Prywatny typ nie ma dostępu z `Module2`, ale wewnętrzny typ można.</span><span class="sxs-lookup"><span data-stu-id="95c57-130">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="95c57-131">Poniższy kod sprawdza dostępność typy utworzone w `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="95c57-131">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="95c57-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95c57-132">See Also</span></span>
[<span data-ttu-id="95c57-133">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="95c57-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="95c57-134">Podpisy</span><span class="sxs-lookup"><span data-stu-id="95c57-134">Signatures</span></span>](signatures.md)
