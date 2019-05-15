---
title: Funkcje zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: fb55a8b248b085275f83d47b1f452cd07bd8dcb1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582640"
---
# <a name="user-defined-functions"></a><span data-ttu-id="1b221-102">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1b221-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1b221-103">używa metody w modelu obiektu, który reprezentuje funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1b221-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="1b221-104">Wyznacz metody jako funkcje, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeśli to konieczne, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1b221-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="1b221-105">Aby uzyskać więcej informacji, zobacz [LINQ to SQL Model obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="1b221-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="1b221-106">Aby uniknąć <xref:System.InvalidOperationException>zdefiniowany przez użytkownika funkcje w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi należeć do jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="1b221-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="1b221-107">Opakowana funkcja jako wywołania metody o atrybuty mapowania poprawne.</span><span class="sxs-lookup"><span data-stu-id="1b221-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="1b221-108">Aby uzyskać więcej informacji, zobacz [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="1b221-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="1b221-109">Statyczna metoda SQL specyficzne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b221-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="1b221-110">Funkcja obsługiwane przez metody .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b221-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="1b221-111">Tematy w tej sekcji przedstawiają sposób utworzenia i wywoływanie tych metod w aplikacji, jeśli możesz napisać kod.</span><span class="sxs-lookup"><span data-stu-id="1b221-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="1b221-112">Deweloperzy korzystający z programu Visual Studio zazwyczaj użyje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapować funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1b221-112">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b221-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1b221-113">In This Section</span></span>  
 [<span data-ttu-id="1b221-114">Instrukcje: Użyj funkcji skalarnej zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1b221-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="1b221-115">Opisuje sposób implementacji funkcji, która zwraca wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="1b221-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="1b221-116">Instrukcje: Używanie wartościami przechowywanymi w tabeli funkcji zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1b221-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="1b221-117">Opisuje sposób implementacji funkcji, która zwraca wartości w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1b221-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="1b221-118">Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1b221-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="1b221-119">W tym artykule opisano sposób wprowadzania tekście wywołania funkcji i różnice w wykonywania, gdy dochodzi do wywołania wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="1b221-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
