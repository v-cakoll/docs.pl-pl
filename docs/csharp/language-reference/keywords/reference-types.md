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
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="c33d8-102">Typy odwołań (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c33d8-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="c33d8-103">Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="c33d8-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="c33d8-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="c33d8-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="c33d8-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="c33d8-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="c33d8-106">Z typami wartość każdej zmiennej ma własną kopię danych, a nie jest możliwe w dla operacji na jedną zmienną do wpływu na drugi (z wyjątkiem w przypadku ref i out parametru zmiennych, zobacz [ref](../../../csharp/language-reference/keywords/ref.md) i [parametru out Modyfikator](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="c33d8-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of ref and out parameter variables, see [ref](../../../csharp/language-reference/keywords/ref.md) and [out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span></span>  
  
 <span data-ttu-id="c33d8-107">Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:</span><span class="sxs-lookup"><span data-stu-id="c33d8-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="c33d8-108">klasy</span><span class="sxs-lookup"><span data-stu-id="c33d8-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="c33d8-109">Interfejs</span><span class="sxs-lookup"><span data-stu-id="c33d8-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="c33d8-110">Delegowanie</span><span class="sxs-lookup"><span data-stu-id="c33d8-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="c33d8-111">W języku C# są także dostępne następujące wbudowane typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="c33d8-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="c33d8-112">dynamiczne</span><span class="sxs-lookup"><span data-stu-id="c33d8-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="c33d8-113">obiekt</span><span class="sxs-lookup"><span data-stu-id="c33d8-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="c33d8-114">ciąg</span><span class="sxs-lookup"><span data-stu-id="c33d8-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="c33d8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c33d8-115">See Also</span></span>  
 [<span data-ttu-id="c33d8-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="c33d8-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c33d8-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c33d8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c33d8-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c33d8-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c33d8-119">Typy</span><span class="sxs-lookup"><span data-stu-id="c33d8-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="c33d8-120">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="c33d8-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
