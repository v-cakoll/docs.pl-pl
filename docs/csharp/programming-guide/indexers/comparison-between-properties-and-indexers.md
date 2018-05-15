---
title: Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="60c14-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="60c14-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="60c14-103">Indeksatory są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="60c14-103">Indexers are like properties.</span></span> <span data-ttu-id="60c14-104">Z wyjątkiem różnice przedstawiono w poniższej tabeli wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości dotyczą akcesorów indeksatora również.</span><span class="sxs-lookup"><span data-stu-id="60c14-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="60c14-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="60c14-105">Property</span></span>|<span data-ttu-id="60c14-106">indeksator</span><span class="sxs-lookup"><span data-stu-id="60c14-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="60c14-107">Umożliwia metody do wywołania, tak jakby były publiczne elementy członkowskie danych.</span><span class="sxs-lookup"><span data-stu-id="60c14-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="60c14-108">Umożliwia elementy kolekcji wewnętrznego obiektu można uzyskać dostęp przy użyciu tablicy notacji sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="60c14-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="60c14-109">Dostępne za pośrednictwem prostą nazwą.</span><span class="sxs-lookup"><span data-stu-id="60c14-109">Accessed through a simple name.</span></span>|<span data-ttu-id="60c14-110">Dostępne za pośrednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="60c14-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="60c14-111">Może być statycznymi lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60c14-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="60c14-112">Musi być członkiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60c14-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="60c14-113">A [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="60c14-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="60c14-114">A `get` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora.</span><span class="sxs-lookup"><span data-stu-id="60c14-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="60c14-115">A [ustawić](../../../csharp/language-reference/keywords/set.md) akcesor właściwości zawiera niejawne `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="60c14-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="60c14-116">A `set` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora, a także aby [wartość](../../../csharp/language-reference/keywords/value.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="60c14-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="60c14-117">Obsługuje skrócony składni [Auto-Implemented właściwości](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="60c14-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="60c14-118">Nie obsługuje skróconą składni.</span><span class="sxs-lookup"><span data-stu-id="60c14-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60c14-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60c14-119">See Also</span></span>  
 [<span data-ttu-id="60c14-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="60c14-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="60c14-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="60c14-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="60c14-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="60c14-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
