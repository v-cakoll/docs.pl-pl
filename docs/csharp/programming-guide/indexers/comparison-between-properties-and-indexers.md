---
title: Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 3a78b97f2cac1f2c49be03bc351d9b6f4b6438e6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861445"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="286e1-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="286e1-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="286e1-103">Indeksatory są podobne właściwości.</span><span class="sxs-lookup"><span data-stu-id="286e1-103">Indexers are like properties.</span></span> <span data-ttu-id="286e1-104">Z wyjątkiem różnic pokazano w poniższej tabeli wszystkich reguł, które są zdefiniowane dla metod dostępu do właściwości dotyczą metod dostępu indeksatora również.</span><span class="sxs-lookup"><span data-stu-id="286e1-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="286e1-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="286e1-105">Property</span></span>|<span data-ttu-id="286e1-106">Indeksator</span><span class="sxs-lookup"><span data-stu-id="286e1-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="286e1-107">Zezwala na metody wywołane, tak jakby były publiczne elementy członkowskie danych.</span><span class="sxs-lookup"><span data-stu-id="286e1-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="286e1-108">Umożliwia elementy kolekcji wewnętrznego obiektu można uzyskać dostęp przy użyciu tablicy notacji sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="286e1-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="286e1-109">Dostępna za pośrednictwem prostej nazwie.</span><span class="sxs-lookup"><span data-stu-id="286e1-109">Accessed through a simple name.</span></span>|<span data-ttu-id="286e1-110">Dostępna za pośrednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="286e1-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="286e1-111">Może być statyczna lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="286e1-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="286e1-112">Musi być składową wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="286e1-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="286e1-113">A [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="286e1-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="286e1-114">A `get` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora.</span><span class="sxs-lookup"><span data-stu-id="286e1-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="286e1-115">A [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu właściwości zawiera niejawny `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="286e1-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="286e1-116">A `set` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora, a także [wartość](../../../csharp/language-reference/keywords/value.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="286e1-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="286e1-117">Obsługuje skrócony składni [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="286e1-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="286e1-118">Nie obsługuje skróconej składni.</span><span class="sxs-lookup"><span data-stu-id="286e1-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="286e1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="286e1-119">See Also</span></span>

- [<span data-ttu-id="286e1-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="286e1-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="286e1-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="286e1-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="286e1-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="286e1-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
