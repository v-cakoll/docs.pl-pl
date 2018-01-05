---
title: Operator kanonicznej funkcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a4311b610859b36f1587e5e3f85e2a5f06503e1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="8e02a-102">Operator kanonicznej funkcji</span><span class="sxs-lookup"><span data-stu-id="8e02a-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8e02a-103">obejmuje funkcje canonical bitowe.</span><span class="sxs-lookup"><span data-stu-id="8e02a-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e02a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e02a-104">Remarks</span></span>  
 <span data-ttu-id="8e02a-105">W poniższej tabeli przedstawiono operatora testu koniunkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8e02a-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="8e02a-106">Te funkcje będą zwracać `Null` Jeśli `Null` danych wejściowych jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="8e02a-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="8e02a-107">Zwracany typ funkcji jest taka sama jak typy argumentów.</span><span class="sxs-lookup"><span data-stu-id="8e02a-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="8e02a-108">Argumenty muszą być tego samego typu, jeśli funkcja przyjmuje więcej niż jeden argument.</span><span class="sxs-lookup"><span data-stu-id="8e02a-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="8e02a-109">Aby wykonać operacje bitowe na różnych urządzeniach, należy rzutować na ten sam typ. jawne.</span><span class="sxs-lookup"><span data-stu-id="8e02a-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="8e02a-110">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8e02a-110">Function</span></span>|<span data-ttu-id="8e02a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="8e02a-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8e02a-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="8e02a-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="8e02a-113">Zwraca koniunkcję z `value1` i `value2` jako typ `value1` i `value2`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="8e02a-114">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="8e02a-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="8e02a-115">A `Byte`, `Int16`, `Int32`, i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="8e02a-116">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="8e02a-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="8e02a-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="8e02a-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="8e02a-118">Zwraca wartość logiczną negację `value`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="8e02a-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="8e02a-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="8e02a-120">A `Byte`, `Int16`, `Int32`, i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="8e02a-121">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="8e02a-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="8e02a-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="8e02a-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="8e02a-123">Zwraca z bitowego rozłączenia z `value1` i `value2` jako typ `value1` i `value2`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="8e02a-124">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="8e02a-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="8e02a-125">A `Byte`, `Int16`, `Int32` i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="8e02a-126">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="8e02a-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="8e02a-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="8e02a-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="8e02a-128">Zwraca z bitowego rozłączenia wyłącznego z `value1` i `value2` jako typ `value1` i `value2`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="8e02a-129">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="8e02a-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="8e02a-130">A `Byte`, `Int16`, `Int32` i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="8e02a-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="8e02a-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="8e02a-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="8e02a-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e02a-132">See Also</span></span>  
 [<span data-ttu-id="8e02a-133">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="8e02a-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
