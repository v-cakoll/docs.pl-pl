---
title: Porównanie właściwości i indeksatorów — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 31e6b4b10a6ffec031a2e41a2bd16c843f802fb7
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671678"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="c437b-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c437b-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="c437b-103">Indeksatory są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="c437b-103">Indexers are like properties.</span></span> <span data-ttu-id="c437b-104">Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości stosuje się również do metod dostępu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="c437b-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="c437b-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c437b-105">Property</span></span>|<span data-ttu-id="c437b-106">Indeksatora</span><span class="sxs-lookup"><span data-stu-id="c437b-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="c437b-107">Umożliwia wywoływanie metod w taki sposób, jakby były publicznymi elementami członkowskimi danych.</span><span class="sxs-lookup"><span data-stu-id="c437b-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="c437b-108">Zezwala na dostęp do elementów w wewnętrznej kolekcji obiektów przy użyciu notacji tablicy dla samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c437b-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="c437b-109">Dostępne za pomocą prostej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c437b-109">Accessed through a simple name.</span></span>|<span data-ttu-id="c437b-110">Dostępne za za poorednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="c437b-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="c437b-111">Może być elementem członkowskim typu static lub instance.</span><span class="sxs-lookup"><span data-stu-id="c437b-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="c437b-112">Musi być elementem członkowskim wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c437b-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="c437b-113">Metoda dostępu [Get](../../../csharp/language-reference/keywords/get.md) właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="c437b-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="c437b-114">`get` Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator.</span><span class="sxs-lookup"><span data-stu-id="c437b-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="c437b-115">Metoda dostępu [Set](../../../csharp/language-reference/keywords/set.md) właściwości zawiera parametr niejawny `value` .</span><span class="sxs-lookup"><span data-stu-id="c437b-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="c437b-116">Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator, a także parametr [Value.](../../../csharp/language-reference/keywords/value.md) `set`</span><span class="sxs-lookup"><span data-stu-id="c437b-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="c437b-117">Obsługuje skróconą składnię z [zaimplementowanymi właściwościami](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c437b-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="c437b-118">Obsługuje składowe wyrażeń składowanych tylko dla indeksatorów tylko do pobrania.</span><span class="sxs-lookup"><span data-stu-id="c437b-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c437b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c437b-119">See also</span></span>

- [<span data-ttu-id="c437b-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c437b-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c437b-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="c437b-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="c437b-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c437b-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
