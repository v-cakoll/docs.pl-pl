---
title: Tworzenie grup zagnieżdżonych
description: Jak tworzenie grup zagnieżdżonych.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="create-a-nested-group"></a><span data-ttu-id="55202-103">Tworzenie grup zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="55202-103">Create a nested group</span></span>

<span data-ttu-id="55202-104">Poniższy przykład przedstawia sposób tworzenia grup zagnieżdżonych w wyrażeniu zapytania składnika LINQ.</span><span class="sxs-lookup"><span data-stu-id="55202-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="55202-105">Każdej grupy, która jest tworzone zgodnie ze skonfigurowanym poziomie roku lub klasy uczniów następnie jest podzielony na grupy na podstawie nazw poszczególnych osób.</span><span class="sxs-lookup"><span data-stu-id="55202-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55202-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="55202-106">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="55202-107">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="55202-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="55202-108">Należy pamiętać, że trzy zagnieżdżone `foreach` pętle są wymagane do wykonywania iteracji wewnętrzne elementy grup zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="55202-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55202-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55202-109">See also</span></span>  
 [<span data-ttu-id="55202-110">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="55202-110">LINQ Query Expressions</span></span>](index.md)
