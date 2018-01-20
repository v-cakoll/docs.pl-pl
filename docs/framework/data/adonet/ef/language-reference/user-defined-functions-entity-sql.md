---
title: "Funkcje zdefiniowane przez użytkownika (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e5cfc9685c1e088722b24b54b4a0368d52fda29
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="1b4a0-102">Funkcje zdefiniowane przez użytkownika (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1b4a0-102">User-Defined Functions (Entity SQL)</span></span>
<span data-ttu-id="1b4a0-103">Jednostki SQL obsługuje wywoływanie funkcji zdefiniowanej przez użytkownika w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="1b4a0-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="1b4a0-104">Można zdefiniować następujące wbudowane funkcje z zapytaniem (zobacz [porady: wywoływanie funkcji zdefiniowanych przez użytkownika](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) lub w ramach modelu koncepcyjnego (zobacz [jak: zdefiniować funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)).</span><span class="sxs-lookup"><span data-stu-id="1b4a0-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)).</span></span> <span data-ttu-id="1b4a0-105">Model koncepcyjny funkcje są zdefiniowane jako polecenie SQL jednostki w [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elementu [funkcja](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) elementu w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="1b4a0-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) element of a [Function](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="1b4a0-106">Jednostki SQL umożliwia zdefiniowanie funkcje w samo polecenie zapytania.</span><span class="sxs-lookup"><span data-stu-id="1b4a0-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="1b4a0-107">[Funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator definiuje funkcji śródwierszowych.</span><span class="sxs-lookup"><span data-stu-id="1b4a0-107">The [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="1b4a0-108">Można zdefiniować wiele funkcji za pomocą jednego polecenia, a te funkcje mogą mieć taką samą nazwę funkcji, tak długo, jak sygnatury funkcji są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="1b4a0-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="1b4a0-109">Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1b4a0-109">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4a0-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b4a0-110">See Also</span></span>  
 [<span data-ttu-id="1b4a0-111">Funkcje</span><span class="sxs-lookup"><span data-stu-id="1b4a0-111">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
