---
title: Porównanie właściwości i indeksatorów - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712133"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="352cf-102">Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="352cf-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="352cf-103">Indeksatory są jak właściwości.</span><span class="sxs-lookup"><span data-stu-id="352cf-103">Indexers are like properties.</span></span> <span data-ttu-id="352cf-104">Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla akcesorów właściwości stosuje się również do akcesorów indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="352cf-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="352cf-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="352cf-105">Property</span></span>|<span data-ttu-id="352cf-106">Indeksator</span><span class="sxs-lookup"><span data-stu-id="352cf-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="352cf-107">Umożliwia wywoływanie metod tak, jakby były członkami danych publicznych.</span><span class="sxs-lookup"><span data-stu-id="352cf-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="352cf-108">Umożliwia dostęp do elementów wewnętrznej kolekcji obiektu przy użyciu notacji tablicowej na samym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="352cf-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="352cf-109">Dostęp za pomocą prostej nazwy.</span><span class="sxs-lookup"><span data-stu-id="352cf-109">Accessed through a simple name.</span></span>|<span data-ttu-id="352cf-110">Dostęp za pośrednictwem indeksu.</span><span class="sxs-lookup"><span data-stu-id="352cf-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="352cf-111">Może być statyczny lub element członkowski wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="352cf-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="352cf-112">Musi być członkiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="352cf-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="352cf-113">[A accessor](../../language-reference/keywords/get.md) właściwości nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="352cf-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="352cf-114">Akcesor `get` indeksatora ma taką samą listę parametrów formalnych jak indeksator.</span><span class="sxs-lookup"><span data-stu-id="352cf-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="352cf-115">[Set](../../language-reference/keywords/set.md) akcesor właściwości `value` zawiera parametr niejawny.</span><span class="sxs-lookup"><span data-stu-id="352cf-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="352cf-116">Akcesor `set` indeksatora ma taką samą listę parametrów formalnych jak indeksator, a także do parametru [value.](../../language-reference/keywords/value.md)</span><span class="sxs-lookup"><span data-stu-id="352cf-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="352cf-117">Obsługuje skróconą składnię za pomocą [właściwości autoimplementowanych](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="352cf-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="352cf-118">Obsługuje wyrażenie zabudowane elementy członkowskie dla uzyskać tylko indeksatory.</span><span class="sxs-lookup"><span data-stu-id="352cf-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="352cf-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="352cf-119">See also</span></span>

- [<span data-ttu-id="352cf-120">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="352cf-120">C# Programming Guide</span></span>](../index.md)
- <span data-ttu-id="352cf-121">[Indexers](./index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="352cf-121">[Indexers](./index.md)</span></span>
- [<span data-ttu-id="352cf-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="352cf-122">Properties</span></span>](../classes-and-structs/properties.md)
