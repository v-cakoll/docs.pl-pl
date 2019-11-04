---
title: Typy odwołań — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 61b9f8096e1b2093b1ea5589f4336618cd189c34
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422455"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="8815a-102">Typy odwołań (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="8815a-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="8815a-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="8815a-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="8815a-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="8815a-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="8815a-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="8815a-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="8815a-106">W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem w przypadku zmiennych parametrów ref i out; zobacz [w](in-parameter-modifier.md), modyfikator parametru [ref](ref.md) i [out](out-parameter-modifier.md) ).</span><span class="sxs-lookup"><span data-stu-id="8815a-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="8815a-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="8815a-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="8815a-108">class</span><span class="sxs-lookup"><span data-stu-id="8815a-108">class</span></span>](class.md)

- [<span data-ttu-id="8815a-109">interface</span><span class="sxs-lookup"><span data-stu-id="8815a-109">interface</span></span>](interface.md)

- [<span data-ttu-id="8815a-110">delegate</span><span class="sxs-lookup"><span data-stu-id="8815a-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="8815a-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="8815a-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="8815a-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="8815a-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="8815a-113">object</span><span class="sxs-lookup"><span data-stu-id="8815a-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="8815a-114">string</span><span class="sxs-lookup"><span data-stu-id="8815a-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="8815a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8815a-115">See also</span></span>

- [<span data-ttu-id="8815a-116">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="8815a-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8815a-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8815a-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8815a-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8815a-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8815a-119">Typy</span><span class="sxs-lookup"><span data-stu-id="8815a-119">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="8815a-120">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="8815a-120">Value Types</span></span>](value-types.md)
