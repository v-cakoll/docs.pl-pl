---
title: "Types (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c7285e237b04c1290391c4bba3e62886dceb83c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-reference"></a><span data-ttu-id="47c6c-102">Types (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="47c6c-102">Types (C# Reference)</span></span>
<span data-ttu-id="47c6c-103">C# wpisanie systemu zawiera następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="47c6c-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="47c6c-104">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="47c6c-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="47c6c-105">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="47c6c-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="47c6c-106">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="47c6c-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="47c6c-107">Zmienne, które typy wartości są przechowywane dane, a te, które są typy referencyjne przechowywania odwołań do danych rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="47c6c-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="47c6c-108">Typy odwołań są również nazywane obiektów.</span><span class="sxs-lookup"><span data-stu-id="47c6c-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="47c6c-109">Typy wskaźnika, które mogą być używane tylko w [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) tryb.</span><span class="sxs-lookup"><span data-stu-id="47c6c-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="47c6c-110">Istnieje możliwość konwersji typu wartości na typ referencyjny i z powrotem do typu wartości za pomocą [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="47c6c-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="47c6c-111">Z wyjątkiem opakowanym typem wartościowym typu odwołania nie można przekonwertować na typ wartości.</span><span class="sxs-lookup"><span data-stu-id="47c6c-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="47c6c-112">W tej sekcji wprowadza również [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="47c6c-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="47c6c-113">Typy wartości są również wartości null, co oznacza, że można przechowywać dodatkowe stanu bez wartości.</span><span class="sxs-lookup"><span data-stu-id="47c6c-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="47c6c-114">Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="47c6c-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c6c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47c6c-115">See Also</span></span>  
 [<span data-ttu-id="47c6c-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="47c6c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="47c6c-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="47c6c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="47c6c-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="47c6c-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="47c6c-119">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="47c6c-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="47c6c-120">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="47c6c-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="47c6c-121">Typy</span><span class="sxs-lookup"><span data-stu-id="47c6c-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
