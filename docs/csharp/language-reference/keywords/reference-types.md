---
title: Typy odwołań — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744518"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="e5f2d-102">Typy odwołań (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="e5f2d-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="e5f2d-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="e5f2d-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="e5f2d-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="e5f2d-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="e5f2d-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="e5f2d-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="e5f2d-106">W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem w przypadku zmiennych parametrów ref i out; zobacz [w](in-parameter-modifier.md), modyfikator parametru [ref](ref.md) i [out](out-parameter-modifier.md) ).</span><span class="sxs-lookup"><span data-stu-id="e5f2d-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="e5f2d-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="e5f2d-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="e5f2d-108">class</span><span class="sxs-lookup"><span data-stu-id="e5f2d-108">class</span></span>](class.md)

- [<span data-ttu-id="e5f2d-109">interface</span><span class="sxs-lookup"><span data-stu-id="e5f2d-109">interface</span></span>](interface.md)

- [<span data-ttu-id="e5f2d-110">delegate</span><span class="sxs-lookup"><span data-stu-id="e5f2d-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="e5f2d-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="e5f2d-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="e5f2d-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="e5f2d-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="e5f2d-113">object</span><span class="sxs-lookup"><span data-stu-id="e5f2d-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="e5f2d-114">string</span><span class="sxs-lookup"><span data-stu-id="e5f2d-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="e5f2d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5f2d-115">See also</span></span>

- [<span data-ttu-id="e5f2d-116">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="e5f2d-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e5f2d-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e5f2d-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e5f2d-118">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="e5f2d-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e5f2d-119">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="e5f2d-119">Value types</span></span>](../builtin-types/value-types.md)
