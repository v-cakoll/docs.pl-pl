---
title: Porównanie właściwości i indeksatorów — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712133"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="06e8e-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="06e8e-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="06e8e-103">Indeksatory są podobne do właściwości.</span><span class="sxs-lookup"><span data-stu-id="06e8e-103">Indexers are like properties.</span></span> <span data-ttu-id="06e8e-104">Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości stosuje się również do metod dostępu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="06e8e-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="06e8e-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="06e8e-105">Property</span></span>|<span data-ttu-id="06e8e-106">Indeksator</span><span class="sxs-lookup"><span data-stu-id="06e8e-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="06e8e-107">Umożliwia wywoływanie metod w taki sposób, jakby były publicznymi elementami członkowskimi danych.</span><span class="sxs-lookup"><span data-stu-id="06e8e-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="06e8e-108">Zezwala na dostęp do elementów w wewnętrznej kolekcji obiektów przy użyciu notacji tablicy dla samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="06e8e-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="06e8e-109">Dostępne za pomocą prostej nazwy.</span><span class="sxs-lookup"><span data-stu-id="06e8e-109">Accessed through a simple name.</span></span>|<span data-ttu-id="06e8e-110">Dostępne za za poorednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="06e8e-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="06e8e-111">Może być elementem członkowskim typu static lub instance.</span><span class="sxs-lookup"><span data-stu-id="06e8e-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="06e8e-112">Musi być elementem członkowskim wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06e8e-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="06e8e-113">Metoda dostępu [Get](../../language-reference/keywords/get.md) właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="06e8e-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="06e8e-114">Metoda dostępu `get` indeksatora ma taką samą formalną listę parametrów jak indeksator.</span><span class="sxs-lookup"><span data-stu-id="06e8e-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="06e8e-115">Metoda dostępu [Set](../../language-reference/keywords/set.md) właściwości zawiera niejawny parametr `value`.</span><span class="sxs-lookup"><span data-stu-id="06e8e-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="06e8e-116">Metoda dostępu `set` indeksatora ma taką samą formalną listę parametrów jak indeksator, a także parametr [Value](../../language-reference/keywords/value.md) .</span><span class="sxs-lookup"><span data-stu-id="06e8e-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="06e8e-117">Obsługuje skróconą składnię z [zaimplementowanymi właściwościami](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="06e8e-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="06e8e-118">Obsługuje składowe wyrażeń składowanych tylko dla indeksatorów tylko do pobrania.</span><span class="sxs-lookup"><span data-stu-id="06e8e-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06e8e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06e8e-119">See also</span></span>

- [<span data-ttu-id="06e8e-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="06e8e-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06e8e-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="06e8e-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="06e8e-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="06e8e-122">Properties</span></span>](../classes-and-structs/properties.md)
