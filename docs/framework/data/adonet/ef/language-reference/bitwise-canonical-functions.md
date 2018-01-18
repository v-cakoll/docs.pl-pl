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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d703b2467d508324f3eb39b822c239484ac1c6e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="ecee3-102">Operator kanonicznej funkcji</span><span class="sxs-lookup"><span data-stu-id="ecee3-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ecee3-103">obejmuje funkcje canonical bitowe.</span><span class="sxs-lookup"><span data-stu-id="ecee3-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecee3-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecee3-104">Remarks</span></span>  
 <span data-ttu-id="ecee3-105">W poniższej tabeli przedstawiono operatora testu koniunkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ecee3-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="ecee3-106">Te funkcje będą zwracać `Null` Jeśli `Null` danych wejściowych jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="ecee3-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="ecee3-107">Zwracany typ funkcji jest taka sama jak typy argumentów.</span><span class="sxs-lookup"><span data-stu-id="ecee3-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="ecee3-108">Argumenty muszą być tego samego typu, jeśli funkcja przyjmuje więcej niż jeden argument.</span><span class="sxs-lookup"><span data-stu-id="ecee3-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="ecee3-109">Aby wykonać operacje bitowe na różnych urządzeniach, należy rzutować na ten sam typ. jawne.</span><span class="sxs-lookup"><span data-stu-id="ecee3-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="ecee3-110">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ecee3-110">Function</span></span>|<span data-ttu-id="ecee3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ecee3-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ecee3-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="ecee3-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="ecee3-113">Zwraca koniunkcję z `value1` i `value2` jako typ `value1` i `value2`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="ecee3-114">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ecee3-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="ecee3-115">A `Byte`, `Int16`, `Int32`, i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="ecee3-116">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="ecee3-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="ecee3-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="ecee3-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="ecee3-118">Zwraca wartość logiczną negację `value`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="ecee3-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ecee3-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="ecee3-120">A `Byte`, `Int16`, `Int32`, i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="ecee3-121">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="ecee3-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="ecee3-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="ecee3-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="ecee3-123">Zwraca z bitowego rozłączenia z `value1` i `value2` jako typ `value1` i `value2`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="ecee3-124">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ecee3-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="ecee3-125">A `Byte`, `Int16`, `Int32` i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="ecee3-126">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="ecee3-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="ecee3-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="ecee3-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="ecee3-128">Zwraca z bitowego rozłączenia wyłącznego z `value1` i `value2` jako typ `value1` i `value2`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="ecee3-129">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ecee3-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="ecee3-130">A `Byte`, `Int16`, `Int32` i `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ecee3-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="ecee3-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="ecee3-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="ecee3-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecee3-132">See Also</span></span>  
 [<span data-ttu-id="ecee3-133">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="ecee3-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
