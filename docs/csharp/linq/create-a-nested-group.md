---
title: Tworzenie grupy zagnieżdżonej (LINQ w języku C#)
description: Dowiedz się, jak utworzyć grupę zagnieżdżoną w wyrażeniu kwerendy LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688621"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="0f211-103">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="0f211-103">Create a nested group</span></span>

<span data-ttu-id="0f211-104">W poniższym przykładzie pokazano, jak tworzyć grupy zagnieżdżone w wyrażeniu kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="0f211-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="0f211-105">Każda grupa, która jest tworzona zgodnie z rokiem studenckim lub poziomem oceny, jest następnie podzielona na grupy na podstawie imion osób.</span><span class="sxs-lookup"><span data-stu-id="0f211-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="0f211-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f211-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="0f211-107">W tym przykładzie znajdują się odwołania do obiektów zdefiniowanych w przykładowym kodzie w [query kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="0f211-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="0f211-108">Należy zauważyć, `foreach` że trzy zagnieżdżone pętle są wymagane do itetensji nad elementami wewnętrznymi grupy zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="0f211-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f211-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f211-109">See also</span></span>

- [<span data-ttu-id="0f211-110">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0f211-110">Language Integrated Query (LINQ)</span></span>](index.md)
