---
title: Porównanie właściwości i indeksatorów — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589468"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="35233-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="35233-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="35233-103">Indeksatory są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="35233-103">Indexers are like properties.</span></span> <span data-ttu-id="35233-104">Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości stosuje się również do metod dostępu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="35233-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="35233-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="35233-105">Property</span></span>|<span data-ttu-id="35233-106">Indeksatora</span><span class="sxs-lookup"><span data-stu-id="35233-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="35233-107">Umożliwia wywoływanie metod w taki sposób, jakby były publicznymi elementami członkowskimi danych.</span><span class="sxs-lookup"><span data-stu-id="35233-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="35233-108">Zezwala na dostęp do elementów w wewnętrznej kolekcji obiektów przy użyciu notacji tablicy dla samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="35233-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="35233-109">Dostępne za pomocą prostej nazwy.</span><span class="sxs-lookup"><span data-stu-id="35233-109">Accessed through a simple name.</span></span>|<span data-ttu-id="35233-110">Dostępne za za poorednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="35233-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="35233-111">Może być elementem członkowskim typu static lub instance.</span><span class="sxs-lookup"><span data-stu-id="35233-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="35233-112">Musi być elementem członkowskim wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="35233-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="35233-113">Metoda dostępu [Get](../../language-reference/keywords/get.md) właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="35233-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="35233-114">`get` Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator.</span><span class="sxs-lookup"><span data-stu-id="35233-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="35233-115">Metoda dostępu [Set](../../language-reference/keywords/set.md) właściwości zawiera parametr niejawny `value` .</span><span class="sxs-lookup"><span data-stu-id="35233-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="35233-116">Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator, a także parametr [Value.](../../language-reference/keywords/value.md) `set`</span><span class="sxs-lookup"><span data-stu-id="35233-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="35233-117">Obsługuje skróconą składnię [](../classes-and-structs/auto-implemented-properties.md)z zaimplementowanymi właściwościami.</span><span class="sxs-lookup"><span data-stu-id="35233-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="35233-118">Obsługuje składowe wyrażeń składowanych tylko dla indeksatorów tylko do pobrania.</span><span class="sxs-lookup"><span data-stu-id="35233-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35233-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35233-119">See also</span></span>

- [<span data-ttu-id="35233-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="35233-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35233-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="35233-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="35233-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="35233-122">Properties</span></span>](../classes-and-structs/properties.md)
