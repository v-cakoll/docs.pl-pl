---
title: do — Powiązania w klasach (F#)
description: 'Dowiedz się, jak używać języka F # są powiązania w definicji klasy, która wykonuje akcje w przypadku, gdy obiekt jest konstruowany lub przy pierwszym użyciu typu.'
ms.date: 05/16/2016
ms.openlocfilehash: e54a5bde52bf6973cc338c929ba99e6fd5b53127
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801542"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="59b30-103">do — Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="59b30-103">do Bindings in Classes</span></span>

<span data-ttu-id="59b30-104">A `do` powiązania w definicji klasy wykonuje akcje, gdy obiekt jest konstruowany lub, w przypadku statycznego `do` powiązania, gdy typ pierwszego.</span><span class="sxs-lookup"><span data-stu-id="59b30-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="59b30-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59b30-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="59b30-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59b30-106">Remarks</span></span>

<span data-ttu-id="59b30-107">A `do` powiązania pojawi się wraz z lub po `let` powiązania, ale przed definicje elementów członkowskich w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="59b30-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="59b30-108">Mimo że `do` — słowo kluczowe jest opcjonalny w przypadku `do` powiązania na poziomie modułu nie jest opcjonalny w przypadku `do` powiązania w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="59b30-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="59b30-109">Do tworzenia wszystkich obiektów dowolnego danego typu, niestatycznej `do` powiązania i niestatycznych `let` powiązania są wykonywane w kolejności, w jakiej są wyświetlane w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="59b30-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="59b30-110">Wiele `do` powiązania mogą wystąpić w jednym typie.</span><span class="sxs-lookup"><span data-stu-id="59b30-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="59b30-111">Niestatyczna `let` powiązania i niestatycznych `do` powiązania stają się treść konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="59b30-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="59b30-112">Kod w niestatycznej `do` może odwoływać się w sekcji wiązania podstawowy Konstruktor parametrów i wartości lub funkcje, które są zdefiniowane w `let` sekcję wiązania.</span><span class="sxs-lookup"><span data-stu-id="59b30-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="59b30-113">Niestatycznych `do` powiązania mogą uzyskiwać dostęp do elementów członkowskich klasy tak długo, jak klasa ma własny identyfikator, który jest definiowany przez `as` — słowo kluczowe w klasie, nagłówek i tak długo, jak wszystkie przypadki użycia tych elementów członkowskich są kwalifikowany za pomocą własny identyfikator dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="59b30-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="59b30-114">Ponieważ `let` powiązania zainicjować pól prywatnych klasy, która często jest to niezbędne zagwarantować, że elementy Członkowskie zachowują się zgodnie z oczekiwaniami, `do` powiązania są zazwyczaj umieszczane po `let` powiązania tak, możesz pisać kod w `do` może powiązania są wykonywane z w pełni zainicjowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="59b30-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="59b30-115">Jeśli kod próbuje przed zakończeniem inicjowania, należy użyć członka, zgłaszany jest InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="59b30-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="59b30-116">Statyczne `do` powiązania mogą odwoływać się do statycznych elementów członkowskich lub pola otaczającej klasy, ale nie wystąpień elementów członkowskich lub pola.</span><span class="sxs-lookup"><span data-stu-id="59b30-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="59b30-117">Statyczne `do` powiązania stają się częścią statycznego inicjatora dla klasy, która jest gwarantowane do wykonania przed pierwszym użyciu tej klasy.</span><span class="sxs-lookup"><span data-stu-id="59b30-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="59b30-118">Atrybuty są ignorowane w przypadku `do` powiązania w typach.</span><span class="sxs-lookup"><span data-stu-id="59b30-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="59b30-119">Jeśli atrybut jest wymagany dla kodu, który jest wykonywany w `do` powiązania go muszą być stosowane do konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="59b30-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="59b30-120">W poniższym kodzie klasy jest statyczną `do` powiązanie i niestatyczną `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="59b30-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="59b30-121">Obiekt ma Konstruktor, który zawiera dwa parametry `a` i `b`, dwa pola prywatne są one definiowane w `let` powiązania dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="59b30-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="59b30-122">Dwie właściwości są również określone.</span><span class="sxs-lookup"><span data-stu-id="59b30-122">Two properties are also defined.</span></span> <span data-ttu-id="59b30-123">Wszystkie te znajdują się w zakresie w niestatycznej `do` sekcję wiązania, jak pokazano wiersza, który wyświetla wszystkie te wartości.</span><span class="sxs-lookup"><span data-stu-id="59b30-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="59b30-124">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="59b30-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="59b30-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59b30-125">See also</span></span>

- [<span data-ttu-id="59b30-126">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="59b30-126">Members</span></span>](index.md)
- [<span data-ttu-id="59b30-127">Klasy</span><span class="sxs-lookup"><span data-stu-id="59b30-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="59b30-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="59b30-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="59b30-129">`let` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="59b30-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="59b30-130">`do` Powiązania</span><span class="sxs-lookup"><span data-stu-id="59b30-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
