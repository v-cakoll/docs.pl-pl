---
title: Kolejność wyników klauzuli join (LINQ w C#)
description: Dowiedz się, jak kolejność wyników klauzuli join LINQ w C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659868"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="6b502-103">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="6b502-103">Order the results of a join clause</span></span>

<span data-ttu-id="6b502-104">W tym przykładzie przedstawiono sposób uporządkowania wyników operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6b502-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="6b502-105">Należy pamiętać, że kolejność jest wykonywana po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6b502-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="6b502-106">Chociaż można używać `orderby` klauzuli z co najmniej źródła sekwencji przed sprzężenia, ogólnie nie zalecamy tego.</span><span class="sxs-lookup"><span data-stu-id="6b502-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="6b502-107">Niektórzy dostawcy LINQ może zachować kolejności po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6b502-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="6b502-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b502-108">Example</span></span>

<span data-ttu-id="6b502-109">To zapytanie tworzy sprzężenie grupy, a następnie sortuje grup oparty na element kategorii, który jest nadal w zakresie.</span><span class="sxs-lookup"><span data-stu-id="6b502-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="6b502-110">Wewnątrz inicjatora typu anonimowego podzapytaniu zamówień zgodnych elementów z sekwencji produktów.</span><span class="sxs-lookup"><span data-stu-id="6b502-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="6b502-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b502-111">See also</span></span>

- [<span data-ttu-id="6b502-112">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6b502-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="6b502-113">orderby, klauzula</span><span class="sxs-lookup"><span data-stu-id="6b502-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="6b502-114">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="6b502-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
