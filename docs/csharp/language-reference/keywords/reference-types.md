---
title: Typy odwołań — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744518"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="c8803-102">Typy odwołań (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="c8803-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="c8803-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="c8803-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="c8803-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="c8803-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="c8803-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="c8803-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="c8803-106">W przypadku typów wartości każda zmienna ma własną kopię danych i nie jest możliwe, aby operacje na jednej zmiennej wpływały na drugą (z wyjątkiem zmiennych parametrów in, ref i out; patrz [w](in-parameter-modifier.md), [ref](ref.md) i [out](out-parameter-modifier.md) parameter modifier).</span><span class="sxs-lookup"><span data-stu-id="c8803-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="c8803-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="c8803-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="c8803-108">Klasa</span><span class="sxs-lookup"><span data-stu-id="c8803-108">class</span></span>](class.md)

- [<span data-ttu-id="c8803-109">Interfejs</span><span class="sxs-lookup"><span data-stu-id="c8803-109">interface</span></span>](interface.md)

- [<span data-ttu-id="c8803-110">delegate</span><span class="sxs-lookup"><span data-stu-id="c8803-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="c8803-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="c8803-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="c8803-112">Dynamiczne</span><span class="sxs-lookup"><span data-stu-id="c8803-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="c8803-113">obiekt</span><span class="sxs-lookup"><span data-stu-id="c8803-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="c8803-114">ciąg</span><span class="sxs-lookup"><span data-stu-id="c8803-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="c8803-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8803-115">See also</span></span>

- [<span data-ttu-id="c8803-116">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c8803-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c8803-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c8803-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c8803-118">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="c8803-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="c8803-119">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="c8803-119">Value types</span></span>](../builtin-types/value-types.md)
