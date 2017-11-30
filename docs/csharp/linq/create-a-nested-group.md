---
title: "Tworzenie grup zagnieżdżonych"
description: "Jak tworzenie grup zagnieżdżonych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a><span data-ttu-id="4dfaa-104">Tworzenie grup zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="4dfaa-104">Create a nested group</span></span>

<span data-ttu-id="4dfaa-105">Poniższy przykład przedstawia sposób tworzenia grup zagnieżdżonych w wyrażeniu zapytania składnika LINQ.</span><span class="sxs-lookup"><span data-stu-id="4dfaa-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="4dfaa-106">Każdej grupy, która jest tworzone zgodnie ze skonfigurowanym poziomie roku lub klasy uczniów następnie jest podzielony na grupy na podstawie nazw poszczególnych osób.</span><span class="sxs-lookup"><span data-stu-id="4dfaa-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dfaa-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4dfaa-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="4dfaa-108">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="4dfaa-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="4dfaa-109">Należy pamiętać, że trzy zagnieżdżone `foreach` pętle są wymagane do wykonywania iteracji wewnętrzne elementy grup zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="4dfaa-109">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfaa-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dfaa-110">See also</span></span>  
 [<span data-ttu-id="4dfaa-111">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="4dfaa-111">LINQ Query Expressions</span></span>](index.md)
