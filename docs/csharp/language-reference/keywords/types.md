---
title: Types (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
ms.openlocfilehash: c5c29f5d9a1a4e25e2d5f8816a0df31fa9a91fb1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506324"
---
# <a name="types-c-reference"></a><span data-ttu-id="c1628-102">Types (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c1628-102">Types (C# Reference)</span></span>
<span data-ttu-id="c1628-103">Wpisywanie system C# zawiera następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="c1628-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="c1628-104">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="c1628-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="c1628-105">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="c1628-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="c1628-106">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="c1628-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="c1628-107">Zmienne, które są typami wartości przechowywania danych, a te, które są typami odwołań są przechowywane odwołania do danych rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="c1628-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="c1628-108">Typy odwołań są również określane jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="c1628-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="c1628-109">Typy wskaźnika, które mogą być używane tylko w [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) trybu.</span><span class="sxs-lookup"><span data-stu-id="c1628-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="c1628-110">Można przekonwertować typu wartości na typ odwołania i z powrotem do typu wartości przy użyciu [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="c1628-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="c1628-111">Z wyjątkiem opakowanym typem wartościowym nie można przekonwertować typu odwołania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="c1628-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="c1628-112">Ta sekcja wprowadza również [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="c1628-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="c1628-113">Typy wartości są również dopuszczającego wartość null, co oznacza, że przechowują dodatkowy stan-wartość.</span><span class="sxs-lookup"><span data-stu-id="c1628-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="c1628-114">Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c1628-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1628-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1628-115">See Also</span></span>

- [<span data-ttu-id="c1628-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c1628-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c1628-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c1628-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c1628-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c1628-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c1628-119">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="c1628-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [<span data-ttu-id="c1628-120">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="c1628-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="c1628-121">Typy</span><span class="sxs-lookup"><span data-stu-id="c1628-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
