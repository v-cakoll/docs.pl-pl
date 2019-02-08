---
title: Wywoływanie funkcji w składniku LINQ do zapytań jednostki
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 8cb861c72f33a7dff3d6bef94719ae590a13706d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828153"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="caef1-102">Wywoływanie funkcji w składniku LINQ do zapytań jednostki</span><span class="sxs-lookup"><span data-stu-id="caef1-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="caef1-103">Tematy w tej sekcji opisano sposób wywołania funkcji w składniku LINQ do zapytań jednostki.</span><span class="sxs-lookup"><span data-stu-id="caef1-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="caef1-104"><xref:System.Data.Objects.EntityFunctions> i <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy zapewniają dostęp do canonical i funkcje bazy danych jako część programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="caef1-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="caef1-105">Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie funkcji kanonicznych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) i [jak: Wywoływanie funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="caef1-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="caef1-106">Proces wywoływania funkcji niestandardowej wymaga trzy podstawowe kroki:</span><span class="sxs-lookup"><span data-stu-id="caef1-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="caef1-107">Zdefiniuj funkcję w model koncepcyjny lub deklarowania funkcji w modelu magazynu.</span><span class="sxs-lookup"><span data-stu-id="caef1-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="caef1-108">Dodaj metodę do swojej aplikacji i Mapuj na funkcję w modelu z <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="caef1-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="caef1-109">Wywołanie funkcji w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="caef1-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="caef1-110">Aby uzyskać więcej informacji zobacz Tematy w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="caef1-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="caef1-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="caef1-111">In This Section</span></span>  
 [<span data-ttu-id="caef1-112">Instrukcje: Wywoływanie funkcji kanonicznych</span><span class="sxs-lookup"><span data-stu-id="caef1-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="caef1-113">Instrukcje: Wywoływanie funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="caef1-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="caef1-114">Instrukcje: Wywoływanie niestandardowych funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="caef1-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="caef1-115">Instrukcje: Wywoływanie funkcji definiowanych przez Model w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="caef1-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="caef1-116">Instrukcje: Wywoływanie funkcji definiowanych przez Model jako metod obiektu</span><span class="sxs-lookup"><span data-stu-id="caef1-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="caef1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caef1-117">See also</span></span>
- [<span data-ttu-id="caef1-118">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="caef1-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [<span data-ttu-id="caef1-119">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="caef1-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- <span data-ttu-id="caef1-120">[Omówienie pliku edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="caef1-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="caef1-121">[Instrukcje: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="caef1-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
