---
title: Kontrola dostępu
description: Dowiedz się, jak kontrolować dostęp do elementów programowania, takich jak typy, metody i funkcje, w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 8db178b26f3beb6ce95bff84ccad9ac9e8c40ce7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612813"
---
# <a name="access-control"></a><span data-ttu-id="946bc-103">Kontrola dostępu</span><span class="sxs-lookup"><span data-stu-id="946bc-103">Access Control</span></span>

<span data-ttu-id="946bc-104">*Kontrola dostępu* odwołuje się do deklarowania, której klienci mogą używać niektórych elementów programów, takich jak typy, metody i funkcje.</span><span class="sxs-lookup"><span data-stu-id="946bc-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="946bc-105">Podstawowe informacje o kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="946bc-105">Basics of Access Control</span></span>

<span data-ttu-id="946bc-106">W F#, specyfikatory dostępu `public`, `internal`, i `private` można zastosować do modułów, typów, metod, definicje wartości, funkcje, właściwości i pola jawne.</span><span class="sxs-lookup"><span data-stu-id="946bc-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="946bc-107">`public` Wskazuje, czy jednostki są dostępne dla wszystkich obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="946bc-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="946bc-108">`internal` Wskazuje, że jednostki są dostępne tylko z tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="946bc-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="946bc-109">`private` Wskazuje, że jednostki są dostępne tylko z otaczającej typu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="946bc-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="946bc-110">Specyfikator dostępu `protected` nie jest używany w F#, mimo że jest dopuszczalne, jeśli używasz typów, utworzone w językach, które obsługują `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="946bc-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="946bc-111">Dlatego Jeśli zastąpisz Metoda chroniona metoda pozostaje dostępny tylko w klasie i jego elementów potomnych.</span><span class="sxs-lookup"><span data-stu-id="946bc-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="946bc-112">Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą jednostki, chyba że `mutable` lub `inline` specyfikator jest używany, które występują po specyfikatorze kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="946bc-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="946bc-113">Jeśli jest używany nie specyfikatora dostępu, wartość domyślna to `public`, z wyjątkiem `let` powiązania w typie, które są zawsze `private` do typu.</span><span class="sxs-lookup"><span data-stu-id="946bc-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="946bc-114">Podpisy w F# Podaj inny mechanizm do kontrolowania dostępu do F# program elementów.</span><span class="sxs-lookup"><span data-stu-id="946bc-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="946bc-115">Podpisy nie są wymagane dla kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="946bc-115">Signatures are not required for access control.</span></span> <span data-ttu-id="946bc-116">Aby uzyskać więcej informacji, zobacz [podpisy](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="946bc-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="946bc-117">Zasady kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="946bc-117">Rules for Access Control</span></span>

<span data-ttu-id="946bc-118">Kontrola dostępu jest się następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="946bc-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="946bc-119">Dziedziczenie, deklaracje (oznacza to, że użycie `inherit` określić klasę bazową dla klasy), interfejs deklaracje, (które określając, że klasa implementuje interfejs) i wydobyć członków zawsze mieć identyczną dostępność co typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="946bc-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="946bc-120">W związku z tym specyfikatora dostępu nie można używać na te konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="946bc-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="946bc-121">Ułatwienia dostępu dla poszczególnych przypadków w złożenia dyskryminowanego jest określany przez dostępność złożenia dyskryminowanego, sam.</span><span class="sxs-lookup"><span data-stu-id="946bc-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="946bc-122">Określonego case złożenia jest nie jest mniej dostępny niż samo połączenie.</span><span class="sxs-lookup"><span data-stu-id="946bc-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="946bc-123">Ułatwienia dostępu dla poszczególnych pól typu rekordu nie zależy od dostępności samego rekordu.</span><span class="sxs-lookup"><span data-stu-id="946bc-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="946bc-124">Etykieta określonego rekordu jest nie jest mniej dostępny niż samego rekordu.</span><span class="sxs-lookup"><span data-stu-id="946bc-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="946bc-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="946bc-125">Example</span></span>

<span data-ttu-id="946bc-126">Poniższy kod ilustruje użycie specyfikatory dostępu.</span><span class="sxs-lookup"><span data-stu-id="946bc-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="946bc-127">Istnieją dwa pliki w projekcie `Module1.fs` i `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="946bc-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="946bc-128">Każdy plik jest niejawnie modułu.</span><span class="sxs-lookup"><span data-stu-id="946bc-128">Each file is implicitly a module.</span></span> <span data-ttu-id="946bc-129">Dlatego istnieją dwa moduły `Module1` i `Module2`.</span><span class="sxs-lookup"><span data-stu-id="946bc-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="946bc-130">Prywatny typ i wewnętrzny typ są zdefiniowane w `Module1`.</span><span class="sxs-lookup"><span data-stu-id="946bc-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="946bc-131">Prywatny typ nie jest dostępny z `Module2`, ale wewnętrzny typ można.</span><span class="sxs-lookup"><span data-stu-id="946bc-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="946bc-132">Poniższy kod sprawdza dostępność typów, utworzone w `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="946bc-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="946bc-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="946bc-133">See also</span></span>

- [<span data-ttu-id="946bc-134">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="946bc-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="946bc-135">Podpisy</span><span class="sxs-lookup"><span data-stu-id="946bc-135">Signatures</span></span>](signatures.md)