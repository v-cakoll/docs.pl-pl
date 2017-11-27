---
title: "Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 102a6a97726fa19fcba0e6f19876a3935e8625f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="ed6e0-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ed6e0-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="ed6e0-103">Indeksatory są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-103">Indexers are like properties.</span></span> <span data-ttu-id="ed6e0-104">Z wyjątkiem różnice przedstawiono w poniższej tabeli wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości dotyczą akcesorów indeksatora również.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="ed6e0-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ed6e0-105">Property</span></span>|<span data-ttu-id="ed6e0-106">indeksator</span><span class="sxs-lookup"><span data-stu-id="ed6e0-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="ed6e0-107">Umożliwia metody do wywołania, tak jakby były publiczne elementy członkowskie danych.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="ed6e0-108">Umożliwia elementy kolekcji wewnętrznego obiektu można uzyskać dostęp przy użyciu tablicy notacji sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="ed6e0-109">Dostępne za pośrednictwem prostą nazwą.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-109">Accessed through a simple name.</span></span>|<span data-ttu-id="ed6e0-110">Dostępne za pośrednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="ed6e0-111">Może być statycznymi lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="ed6e0-112">Musi być członkiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="ed6e0-113">A [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="ed6e0-114">A `get` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="ed6e0-115">A [ustawić](../../../csharp/language-reference/keywords/set.md) akcesor właściwości zawiera niejawne `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="ed6e0-116">A `set` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora, a także aby [wartość](../../../csharp/language-reference/keywords/value.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="ed6e0-117">Obsługuje skrócony składni [Auto-Implemented właściwości](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ed6e0-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="ed6e0-118">Nie obsługuje skróconą składni.</span><span class="sxs-lookup"><span data-stu-id="ed6e0-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed6e0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed6e0-119">See Also</span></span>  
 [<span data-ttu-id="ed6e0-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ed6e0-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ed6e0-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="ed6e0-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="ed6e0-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ed6e0-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
