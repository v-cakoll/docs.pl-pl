---
title: do — Powiązania w klasach
description: Dowiedz się, jak F# używać powiązania "do" w definicji klasy, która wykonuje akcje, gdy obiekt jest konstruowany lub gdy typ jest używany jako pierwszy.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627588"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="be7d7-103">do — Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="be7d7-103">do Bindings in Classes</span></span>

<span data-ttu-id="be7d7-104">Powiązanie w definicji klasy wykonuje akcje, gdy obiekt jest konstruowany lub dla powiązania statycznego `do` , gdy typ jest używany jako pierwszy. `do`</span><span class="sxs-lookup"><span data-stu-id="be7d7-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="be7d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="be7d7-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="be7d7-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be7d7-106">Remarks</span></span>

<span data-ttu-id="be7d7-107">Powiązanie występuje razem z lub po `let` powiązaniach, ale przed definicjami elementów członkowskich w definicji klasy. `do`</span><span class="sxs-lookup"><span data-stu-id="be7d7-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="be7d7-108">Chociaż słowo kluczowe jest opcjonalne dla `do` powiązań na poziomie modułu, nie jest opcjonalne dla `do` powiązań w definicji klasy. `do`</span><span class="sxs-lookup"><span data-stu-id="be7d7-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="be7d7-109">Dla konstrukcji każdego obiektu dowolnego danego typu, niestatyczne `do` powiązania i niestatyczne `let` powiązania są wykonywane w kolejności, w jakiej występują w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="be7d7-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="be7d7-110">W `do` jednym typie może wystąpić wiele powiązań.</span><span class="sxs-lookup"><span data-stu-id="be7d7-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="be7d7-111">Powiązania niestatyczne `let` i powiązania niestatyczne `do` stają się treścią głównego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="be7d7-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="be7d7-112">Kod w sekcji powiązania niestatyczne `do` może odwoływać się do parametrów konstruktora podstawowego i wszelkich wartości lub funkcji, które są zdefiniowane `let` w sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="be7d7-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="be7d7-113">Niestatyczne `do` powiązania mogą uzyskać dostęp do elementów członkowskich klasy, o ile Klasa ma własny identyfikator, który jest zdefiniowany `as` przez słowo kluczowe w nagłówku klasy, i tak długo, jak wszystkie zastosowania tych elementów są kwalifikowane przy użyciu samodzielnego identyfikatora dla klasy.</span><span class="sxs-lookup"><span data-stu-id="be7d7-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="be7d7-114">Ze `let` względu na to, że powiązania inicjują pola prywatne klasy, co jest często niezbędne do zagwarantowania `do` , że elementy członkowskie zachowują się zgodnie z oczekiwaniami, `do` powiązania są zwykle umieszczane po `let` powiązaniach, aby kod w powiązaniu mógł Wykonaj z w pełni zainicjowanym obiektem.</span><span class="sxs-lookup"><span data-stu-id="be7d7-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="be7d7-115">Jeśli kod próbuje użyć elementu członkowskiego przed ukończeniem inicjowania, zostanie zgłoszony InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="be7d7-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="be7d7-116">Powiązania `do` statyczne mogą odwoływać się do statycznych elementów członkowskich lub pól z otaczającej klasy, ale nie elementów członkowskich lub pól wystąpień.</span><span class="sxs-lookup"><span data-stu-id="be7d7-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="be7d7-117">Powiązania `do` statyczne stają się częścią inicjatora statycznego dla klasy, która jest gwarantowana do wykonania przed pierwszym użyciem klasy.</span><span class="sxs-lookup"><span data-stu-id="be7d7-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="be7d7-118">Atrybuty są ignorowane dla `do` powiązań w typach.</span><span class="sxs-lookup"><span data-stu-id="be7d7-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="be7d7-119">Jeśli atrybut jest wymagany dla kodu, który jest wykonywany w `do` powiązaniu, musi zostać zastosowany do głównego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="be7d7-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="be7d7-120">W poniższym kodzie Klasa ma powiązanie statyczne `do` i powiązanie niestatyczne. `do`</span><span class="sxs-lookup"><span data-stu-id="be7d7-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="be7d7-121">Obiekt ma Konstruktor, który ma dwa parametry, `a` i `b`i dwa prywatne `let` pola są zdefiniowane w powiązaniach dla klasy.</span><span class="sxs-lookup"><span data-stu-id="be7d7-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="be7d7-122">Zdefiniowano również dwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="be7d7-122">Two properties are also defined.</span></span> <span data-ttu-id="be7d7-123">Wszystkie te elementy znajdują się w zakresie w sekcji powiązania `do` niestatyczne, jak pokazano w wierszu, który drukuje wszystkie wartości.</span><span class="sxs-lookup"><span data-stu-id="be7d7-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="be7d7-124">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="be7d7-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="be7d7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be7d7-125">See also</span></span>

- [<span data-ttu-id="be7d7-126">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="be7d7-126">Members</span></span>](index.md)
- [<span data-ttu-id="be7d7-127">Klasy</span><span class="sxs-lookup"><span data-stu-id="be7d7-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="be7d7-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="be7d7-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="be7d7-129">`let`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="be7d7-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="be7d7-130">`do`Powiązań</span><span class="sxs-lookup"><span data-stu-id="be7d7-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
