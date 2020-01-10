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
ms.openlocfilehash: 16e7cdc624979f9a35e287ea5274bd9398c83132
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715175"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="25669-102">Typy odwołań (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="25669-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="25669-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="25669-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="25669-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="25669-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="25669-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="25669-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="25669-106">W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem w przypadku zmiennych parametrów ref i out; zobacz [w](in-parameter-modifier.md), modyfikator parametru [ref](ref.md) i [out](out-parameter-modifier.md) ).</span><span class="sxs-lookup"><span data-stu-id="25669-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="25669-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="25669-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="25669-108">class</span><span class="sxs-lookup"><span data-stu-id="25669-108">class</span></span>](class.md)

- [<span data-ttu-id="25669-109">interface</span><span class="sxs-lookup"><span data-stu-id="25669-109">interface</span></span>](interface.md)

- [<span data-ttu-id="25669-110">delegate</span><span class="sxs-lookup"><span data-stu-id="25669-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="25669-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="25669-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="25669-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="25669-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="25669-113">object</span><span class="sxs-lookup"><span data-stu-id="25669-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="25669-114">string</span><span class="sxs-lookup"><span data-stu-id="25669-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="25669-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25669-115">See also</span></span>

- [<span data-ttu-id="25669-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="25669-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25669-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="25669-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="25669-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="25669-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="25669-119">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="25669-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="25669-120">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="25669-120">Value types</span></span>](value-types.md)
