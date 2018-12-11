---
title: Typy — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
ms.openlocfilehash: 41406e74a207f289968017f1f9869b23b165c34b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236664"
---
# <a name="types-c-reference"></a><span data-ttu-id="9ba19-102">Types (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9ba19-102">Types (C# Reference)</span></span>

<span data-ttu-id="9ba19-103">Wpisywanie system C# zawiera następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="9ba19-103">The C# typing system contains the following categories:</span></span>

- [<span data-ttu-id="9ba19-104">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="9ba19-104">Value types</span></span>](value-types.md)

- [<span data-ttu-id="9ba19-105">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="9ba19-105">Reference types</span></span>](reference-types.md)

- [<span data-ttu-id="9ba19-106">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="9ba19-106">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)

 <span data-ttu-id="9ba19-107">Zmienne, które są typami wartości przechowywania danych, a te, które są typami odwołań są przechowywane odwołania do danych rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="9ba19-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="9ba19-108">Wystąpienia typu referencyjnego są również określane jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="9ba19-108">Instances of reference types are also referred to as objects.</span></span> <span data-ttu-id="9ba19-109">Typy wskaźnika, które mogą być używane tylko w [niebezpieczne](unsafe.md) trybu.</span><span class="sxs-lookup"><span data-stu-id="9ba19-109">Pointer types can be used only in [unsafe](unsafe.md) mode.</span></span>

 <span data-ttu-id="9ba19-110">Można przekonwertować typu wartości na typ odwołania i z powrotem do typu wartości przy użyciu [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="9ba19-110">It's possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="9ba19-111">Z wyjątkiem opakowanym typem wartościowym nie można przekonwertować typu odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="9ba19-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>

 <span data-ttu-id="9ba19-112">Ta sekcja wprowadza również [void](void.md).</span><span class="sxs-lookup"><span data-stu-id="9ba19-112">This section also introduces [void](void.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ba19-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ba19-113">See also</span></span>

- [<span data-ttu-id="9ba19-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9ba19-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9ba19-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9ba19-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9ba19-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9ba19-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9ba19-117">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="9ba19-117">Reference Tables for Types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="9ba19-118">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="9ba19-118">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="9ba19-119">Typy</span><span class="sxs-lookup"><span data-stu-id="9ba19-119">Types</span></span>](../../programming-guide/types/index.md)
