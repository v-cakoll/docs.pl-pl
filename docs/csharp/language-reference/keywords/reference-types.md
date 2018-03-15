---
title: "Typy odwołań (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e671abac6d49170ac76e4633c4f55c50dcbe01c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="1e483-102">Typy odwołań (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1e483-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="1e483-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="1e483-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="1e483-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="1e483-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="1e483-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="1e483-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="1e483-106">Z typami wartość każdej zmiennej ma własną kopię danych, a nie jest możliwe w dla operacji na jedną zmienną do wpływu na drugi (oprócz w odniesieniu się parametrem ref i out parametru zmienne; zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) i [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) modyfikator parametrów).</span><span class="sxs-lookup"><span data-stu-id="1e483-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter modifier).</span></span>  
  
 <span data-ttu-id="1e483-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="1e483-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="1e483-108">class</span><span class="sxs-lookup"><span data-stu-id="1e483-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="1e483-109">interface</span><span class="sxs-lookup"><span data-stu-id="1e483-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="1e483-110">delegate</span><span class="sxs-lookup"><span data-stu-id="1e483-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="1e483-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="1e483-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="1e483-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="1e483-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="1e483-113">object</span><span class="sxs-lookup"><span data-stu-id="1e483-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="1e483-114">string</span><span class="sxs-lookup"><span data-stu-id="1e483-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e483-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e483-115">See Also</span></span>  
 [<span data-ttu-id="1e483-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="1e483-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1e483-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1e483-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1e483-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1e483-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1e483-119">Typy</span><span class="sxs-lookup"><span data-stu-id="1e483-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="1e483-120">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="1e483-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
