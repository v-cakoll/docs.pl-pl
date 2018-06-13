---
title: Kontrola dostępu (F#)
description: 'Informacje o sposobie kontrolowania dostępu do elementów programowania, takich jak typy, metod i funkcje w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 0a5cc1faa1aef343aaca0abb0c42a0dd9a52fcbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566525"
---
# <a name="access-control"></a><span data-ttu-id="afe6a-103">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="afe6a-103">Access Control</span></span>

<span data-ttu-id="afe6a-104">*Kontrola dostępu* odwołuje się do deklarowania, których klienci mogą używać niektórych elementów programów, takich jak typy, metod i funkcje.</span><span class="sxs-lookup"><span data-stu-id="afe6a-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>


## <a name="basics-of-access-control"></a><span data-ttu-id="afe6a-105">Podstawowe informacje dotyczące kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="afe6a-105">Basics of Access Control</span></span>
<span data-ttu-id="afe6a-106">W języku F #, kontroli dostępu w specyfikatory `public`, `internal`, i `private` można zastosować do modułów, typy metod, definicje wartości, funkcji, właściwości i pola jawne.</span><span class="sxs-lookup"><span data-stu-id="afe6a-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>


- <span data-ttu-id="afe6a-107">`public` Wskazuje, czy jednostka jest dostępna przez wszystkie obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="afe6a-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="afe6a-108">`internal` Wskazuje, że jednostka jest możliwy tylko z tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="afe6a-109">`private` Wskazuje, że jednostka jest możliwy tylko z otaczającym typu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>


>[!NOTE] 
<span data-ttu-id="afe6a-110">Specyfikator dostępu `protected` nie jest używana w języku F #, chociaż jest dopuszczalne, jeśli używasz typy utworzone w językach, które obsługują `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="afe6a-111">W związku z tym w przypadku przesłonięcia Metoda chroniona metodę pozostaje dostępna tylko w klasie i jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="afe6a-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="afe6a-112">Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą podmiotu, chyba że `mutable` lub `inline` specyfikator jest używana, które występują po specyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="afe6a-113">Jeśli nie specyfikatora dostępu jest używana, wartością domyślną jest `public`, z wyjątkiem `let` powiązania w typie, które są zawsze `private` do typu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="afe6a-114">Podpisy w języku F # Podaj inny mechanizm kontroli dostępu do elementów programu F #.</span><span class="sxs-lookup"><span data-stu-id="afe6a-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="afe6a-115">Podpisy nie są wymagane do kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-115">Signatures are not required for access control.</span></span> <span data-ttu-id="afe6a-116">Aby uzyskać więcej informacji, zobacz [podpisy](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="afe6a-116">For more information, see [Signatures](signatures.md).</span></span>


## <a name="rules-for-access-control"></a><span data-ttu-id="afe6a-117">Zasady kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="afe6a-117">Rules for Access Control</span></span>
<span data-ttu-id="afe6a-118">Kontrola dostępu podlega następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="afe6a-118">Access control is subject to the following rules:</span></span>


- <span data-ttu-id="afe6a-119">Deklaracje dziedziczenia (oznacza to, że korzystanie z `inherit` określić klasę podstawową dla klasy) interfejsu deklaracje (które określając, że klasa implementuje interfejs) i abstrakcyjne elementy członkowskie zawsze mieć tą samą dostępnością, typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="afe6a-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="afe6a-120">W związku z tym specyfikatora dostępu nie można używać w tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="afe6a-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="afe6a-121">Poszczególnych przypadków Unii rozłącznych nie może mieć własne niezależnie od typu union Modyfikatory kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-121">Individual cases in a discriminated union cannot have their own access control modifiers separate from the union type.</span></span>

- <span data-ttu-id="afe6a-122">Poszczególne pola typu rekordu nie może mieć własne niezależnie od typu rekordu Modyfikatory kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-122">Individual fields of a record type cannot have their own access control modifiers separate from the record type.</span></span>


## <a name="example"></a><span data-ttu-id="afe6a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe6a-123">Example</span></span>
<span data-ttu-id="afe6a-124">Poniższy kod przedstawia użycie specyfikatorów kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-124">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="afe6a-125">Istnieją dwa pliki w projekcie `Module1.fs` i `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="afe6a-125">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="afe6a-126">Każdy plik jest niejawnie modułu.</span><span class="sxs-lookup"><span data-stu-id="afe6a-126">Each file is implicitly a module.</span></span> <span data-ttu-id="afe6a-127">Dlatego istnieją dwa moduły `Module1` i `Module2`.</span><span class="sxs-lookup"><span data-stu-id="afe6a-127">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="afe6a-128">Prywatny typ i wewnętrzny typ są zdefiniowane w `Module1`.</span><span class="sxs-lookup"><span data-stu-id="afe6a-128">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="afe6a-129">Prywatny typ nie ma dostępu z `Module2`, ale wewnętrzny typ można.</span><span class="sxs-lookup"><span data-stu-id="afe6a-129">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="afe6a-130">Poniższy kod sprawdza dostępność typy utworzone w `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="afe6a-130">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="afe6a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afe6a-131">See Also</span></span>
[<span data-ttu-id="afe6a-132">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="afe6a-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="afe6a-133">Podpisy</span><span class="sxs-lookup"><span data-stu-id="afe6a-133">Signatures</span></span>](signatures.md)
