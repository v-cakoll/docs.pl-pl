---
title: "Wyrażenia zapytań (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 46777cbe47e7d97fd3baaa1353787f33cff9f0aa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="98150-102">Wyrażenia zapytań (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="98150-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="98150-103">Wyrażenia zapytania łączy wielu operatorów innego zapytania w jednym składni.</span><span class="sxs-lookup"><span data-stu-id="98150-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="98150-104">zawiera różne rodzaje wyrażeń, takie jak: [literały](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [zmienne](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operatory, [funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), ustawienie operatory i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="98150-104"> provides various kinds of expressions, including the following: [literals](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parameters](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operators, [functions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="98150-105">Aby uzyskać więcej informacji, zobacz [odwołania do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="98150-105">For more information, see [Entity SQL Reference](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="98150-106">Klauzule</span><span class="sxs-lookup"><span data-stu-id="98150-106">Clauses</span></span>  
 <span data-ttu-id="98150-107">Wyrażenia zapytania składa się z szeregu klauzule dotyczące kolekcji obiektów kolejne czynności.</span><span class="sxs-lookup"><span data-stu-id="98150-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="98150-108">Są one oparte na klauzule tego samego odnaleźć w standardzie instrukcję SQL select: [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [gdzie](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [o](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), i [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="98150-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), and [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="98150-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="98150-109">Scope</span></span>  
 <span data-ttu-id="98150-110">Nazwy określone w klauzuli FROM są wprowadzane do zakresu od w kolejności wyświetlania od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="98150-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="98150-111">Na liście łączenia wyrażenia mogą odwoływać się do zdefiniowanych wcześniej na liście nazw.</span><span class="sxs-lookup"><span data-stu-id="98150-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="98150-112">Właściwości publiczne elementów określonych w klauzuli FROM nie są dodawane do zakresu od: muszą być zawsze przywoływane przez nazwę kwalifikowaną alias.</span><span class="sxs-lookup"><span data-stu-id="98150-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="98150-113">Zwykle wszystkie części wyrażenie select są traktowane jako w zakresie od.</span><span class="sxs-lookup"><span data-stu-id="98150-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98150-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98150-114">See Also</span></span>  
 [<span data-ttu-id="98150-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="98150-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
