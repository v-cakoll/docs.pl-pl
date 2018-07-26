---
title: Tworzenie grup zagnieżdżonych (LINQ w C#)
description: Dowiedz się, jak tworzenie grup zagnieżdżonych w wyrażeniu zapytania LINQ w C#.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: c973048d0859f61596c62c294131b8c00d0039f8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404752"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="b4444-103">Tworzenie grup zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="b4444-103">Create a nested group</span></span>

<span data-ttu-id="b4444-104">Poniższy przykład pokazuje, jak tworzyć grupy zagnieżdżone w wyrażeniu zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="b4444-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="b4444-105">Każda grupa, utworzony zgodnie z poziomem roku lub klasy korporacyjnej dla uczniów następnie jest podzielona na grupy na podstawie nazw poszczególnych osób.</span><span class="sxs-lookup"><span data-stu-id="b4444-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="b4444-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4444-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="b4444-107">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b4444-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="b4444-108">Należy zauważyć, że trzy zagnieżdżone `foreach` pętle są wymagane do wykonywania iteracji wewnętrzne elementy zagnieżdżone grupy.</span><span class="sxs-lookup"><span data-stu-id="b4444-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4444-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4444-109">See also</span></span>

[<span data-ttu-id="b4444-110">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b4444-110">Language Integrated Query (LINQ)</span></span>](index.md)
