---
title: Wywoływanie funkcji w składniku LINQ do zapytań jednostki
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 4aed9fd59cceb72baac9dc12a85c52787c4b3866
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506947"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="171f0-102">Wywoływanie funkcji w składniku LINQ do zapytań jednostki</span><span class="sxs-lookup"><span data-stu-id="171f0-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="171f0-103">Tematy w tej sekcji opisano sposób wywołania funkcji w składniku LINQ do zapytań jednostki.</span><span class="sxs-lookup"><span data-stu-id="171f0-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="171f0-104"><xref:System.Data.Objects.EntityFunctions> i <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy zapewniają dostęp do canonical i funkcje bazy danych jako część programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="171f0-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="171f0-105">Aby uzyskać więcej informacji, zobacz [jak: wywoływać funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) i [porady: wywoływanie funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="171f0-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="171f0-106">Proces wywoływania funkcji niestandardowej wymaga trzy podstawowe kroki:</span><span class="sxs-lookup"><span data-stu-id="171f0-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="171f0-107">Zdefiniuj funkcję w model koncepcyjny lub deklarowania funkcji w modelu magazynu.</span><span class="sxs-lookup"><span data-stu-id="171f0-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="171f0-108">Dodaj metodę do swojej aplikacji i Mapuj na funkcję w modelu z <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="171f0-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="171f0-109">Wywołanie funkcji w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="171f0-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="171f0-110">Aby uzyskać więcej informacji zobacz Tematy w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="171f0-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="171f0-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="171f0-111">In This Section</span></span>  
 [<span data-ttu-id="171f0-112">Instrukcje: Wywoływanie funkcji kanonicznych</span><span class="sxs-lookup"><span data-stu-id="171f0-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="171f0-113">Instrukcje: Wywoływanie funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="171f0-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="171f0-114">Instrukcje: Wywoływanie niestandardowych funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="171f0-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="171f0-115">Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="171f0-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="171f0-116">Instrukcje: Wywoływanie funkcji definiowanych przez model jako metod obiektu</span><span class="sxs-lookup"><span data-stu-id="171f0-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="171f0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="171f0-117">See Also</span></span>  
 [<span data-ttu-id="171f0-118">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="171f0-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="171f0-119">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="171f0-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="171f0-120">Omówienie pliku edmx</span><span class="sxs-lookup"><span data-stu-id="171f0-120">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="171f0-121">Porady: Definiowanie funkcji niestandardowych w modelu koncepcyjnym</span><span class="sxs-lookup"><span data-stu-id="171f0-121">How to: Define Custom Functions in the Conceptual Model</span></span>](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
