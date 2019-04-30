---
title: Tworzenie grup zagnieżdżonych (LINQ w C#)
description: Dowiedz się, jak tworzenie grup zagnieżdżonych w wyrażeniu zapytania LINQ w C#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688621"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="966c0-103">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="966c0-103">Create a nested group</span></span>

<span data-ttu-id="966c0-104">Poniższy przykład pokazuje, jak tworzyć grupy zagnieżdżone w wyrażeniu zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="966c0-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="966c0-105">Każda grupa, utworzony zgodnie z poziomem roku lub klasy korporacyjnej dla uczniów następnie jest podzielona na grupy na podstawie nazw poszczególnych osób.</span><span class="sxs-lookup"><span data-stu-id="966c0-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="966c0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="966c0-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="966c0-107">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="966c0-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="966c0-108">Należy zauważyć, że trzy zagnieżdżone `foreach` pętle są wymagane do wykonywania iteracji wewnętrzne elementy zagnieżdżone grupy.</span><span class="sxs-lookup"><span data-stu-id="966c0-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="966c0-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="966c0-109">See also</span></span>

- [<span data-ttu-id="966c0-110">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="966c0-110">Language Integrated Query (LINQ)</span></span>](index.md)
