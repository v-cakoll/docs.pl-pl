---
title: Funkcje zdefiniowane przez użytkownika
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 2e015b8fff16ade9bbe93e5e036c53d5527b961f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="user-defined-functions"></a><span data-ttu-id="00584-102">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="00584-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="00584-103"> używa metody w modelu obiektu do reprezentowania funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="00584-103"> uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="00584-104">Możesz określić metod jako funkcje, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeżeli jest to wymagane, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="00584-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="00584-105">Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="00584-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="00584-106">Aby uniknąć <xref:System.InvalidOperationException>, zdefiniowane przez użytkownika funkcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi być w jednym z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="00584-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
-   <span data-ttu-id="00584-107">Opakowana funkcja jako wywołanie metody o atrybuty poprawne mapowania.</span><span class="sxs-lookup"><span data-stu-id="00584-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="00584-108">Aby uzyskać więcej informacji, zobacz [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="00584-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="00584-109">Statycznej metody SQL specyficzne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00584-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
-   <span data-ttu-id="00584-110">Obsługiwane przez funkcję [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] metody.</span><span class="sxs-lookup"><span data-stu-id="00584-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="00584-111">Tematy w tej sekcji przedstawiają sposób tworzą i wywołania tych metod w aplikacji, podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="00584-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="00584-112">Za pomocą programu Visual Studio Deweloperzy zazwyczaj użyje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="00584-112">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00584-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="00584-113">In This Section</span></span>  
 [<span data-ttu-id="00584-114">Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="00584-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="00584-115">Zawiera opis sposobu implementacji funkcji, która zwraca wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="00584-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="00584-116">Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="00584-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="00584-117">Zawiera opis sposobu implementacji funkcji zwracającej tabelę wartości.</span><span class="sxs-lookup"><span data-stu-id="00584-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="00584-118">Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="00584-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="00584-119">Zawiera opis sposobu wprowadzania wbudowanego wywołania funkcji i różnice podczas wykonywania, gdy połączenie jest nawiązywane w tekście.</span><span class="sxs-lookup"><span data-stu-id="00584-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
