---
title: Typy odwołań (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: f99415fc9a2b728917cdf829ffb9e25823a824dd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210909"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="91e9f-102">Typy odwołań (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="91e9f-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="91e9f-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="91e9f-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="91e9f-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="91e9f-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="91e9f-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="91e9f-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="91e9f-106">Z typami wartości każda zmienna ma własną kopię danych i nie jest możliwe dla operacji na jednej zmiennej miały wpływ na inne (z wyjątkiem w przypadku właściwości w ref i out zmiennych parametrów; zobacz [w](in-parameter-modifier.md), [ref](ref.md) i [się](out-parameter-modifier.md) modyfikator parametrów).</span><span class="sxs-lookup"><span data-stu-id="91e9f-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="91e9f-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="91e9f-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="91e9f-108">class</span><span class="sxs-lookup"><span data-stu-id="91e9f-108">class</span></span>](class.md)

- [<span data-ttu-id="91e9f-109">interface</span><span class="sxs-lookup"><span data-stu-id="91e9f-109">interface</span></span>](interface.md)

- [<span data-ttu-id="91e9f-110">delegate</span><span class="sxs-lookup"><span data-stu-id="91e9f-110">delegate</span></span>](delegate.md)

 <span data-ttu-id="91e9f-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="91e9f-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="91e9f-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="91e9f-112">dynamic</span></span>](dynamic.md)

- [<span data-ttu-id="91e9f-113">object</span><span class="sxs-lookup"><span data-stu-id="91e9f-113">object</span></span>](object.md)

- [<span data-ttu-id="91e9f-114">string</span><span class="sxs-lookup"><span data-stu-id="91e9f-114">string</span></span>](string.md)

## <a name="see-also"></a><span data-ttu-id="91e9f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91e9f-115">See also</span></span>

- [<span data-ttu-id="91e9f-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="91e9f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="91e9f-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="91e9f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="91e9f-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="91e9f-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="91e9f-119">Typy</span><span class="sxs-lookup"><span data-stu-id="91e9f-119">Types</span></span>](types.md)
- [<span data-ttu-id="91e9f-120">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="91e9f-120">Value Types</span></span>](value-types.md)