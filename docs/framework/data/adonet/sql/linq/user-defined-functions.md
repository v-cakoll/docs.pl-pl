---
title: Funkcje zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792304"
---
# <a name="user-defined-functions"></a><span data-ttu-id="e07c6-102">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e07c6-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e07c6-103">używa metod w modelu obiektu do reprezentowania funkcji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e07c6-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="e07c6-104">Należy wyznaczyć metody jako funkcje, <xref:System.Data.Linq.Mapping.FunctionAttribute> stosując atrybut i, w razie potrzeby <xref:System.Data.Linq.Mapping.ParameterAttribute> , atrybut.</span><span class="sxs-lookup"><span data-stu-id="e07c6-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="e07c6-105">Aby uzyskać więcej informacji, zobacz [model obiektów LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="e07c6-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="e07c6-106">Aby uniknąć <xref:System.InvalidOperationException>, funkcje zdefiniowane przez użytkownika w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] muszą mieć jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="e07c6-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="e07c6-107">Funkcja opakowana jako wywołanie metody ma poprawne atrybuty mapowania.</span><span class="sxs-lookup"><span data-stu-id="e07c6-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="e07c6-108">Aby uzyskać więcej informacji, zobacz [Mapowanie oparte na atrybutach](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e07c6-108">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="e07c6-109">Statyczna metoda SQL specyficzna [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dla.</span><span class="sxs-lookup"><span data-stu-id="e07c6-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="e07c6-110">Funkcja obsługiwana przez metodę .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e07c6-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="e07c6-111">W tematach w tej sekcji pokazano, jak tworzyć i wywoływać te metody w aplikacji, jeśli piszesz kod samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="e07c6-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="e07c6-112">Deweloperzy korzystający z programu Visual Studio zwykle używają Object Relational Designer do mapowania funkcji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e07c6-112">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e07c6-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e07c6-113">In This Section</span></span>  
 [<span data-ttu-id="e07c6-114">Instrukcje: Korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami skalarnymi</span><span class="sxs-lookup"><span data-stu-id="e07c6-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="e07c6-115">Opisuje sposób implementowania funkcji zwracającej wartości skalarne.</span><span class="sxs-lookup"><span data-stu-id="e07c6-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="e07c6-116">Instrukcje: Korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami przechowywanymi w tabeli</span><span class="sxs-lookup"><span data-stu-id="e07c6-116">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="e07c6-117">Opisuje sposób implementowania funkcji zwracającej wartości tabeli.</span><span class="sxs-lookup"><span data-stu-id="e07c6-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="e07c6-118">Instrukcje: Wywołaj wbudowane funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e07c6-118">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="e07c6-119">Opisuje sposób wykonywania wywołań wbudowanych do funkcji i różnic w wykonywaniu, gdy wywołanie jest wykonywane w tekście.</span><span class="sxs-lookup"><span data-stu-id="e07c6-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
