---
title: Wywoływanie funkcji w zapytaniach składnika LINQ to Entities
description: Skorzystaj z poniższych artykułów, aby zobaczyć, jak klasy EntityFunctions i SqlFunctions zapewniają dostęp do funkcji kanonicznych i baz danych w ramach Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286860"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="769f7-103">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="769f7-103">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="769f7-104">W tematach w tej sekcji opisano sposób wywoływania funkcji w LINQ to Entities zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="769f7-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="769f7-105"><xref:System.Data.Objects.EntityFunctions>Klasy i <xref:System.Data.Objects.SqlClient.SqlFunctions> zapewniają dostęp do funkcji kanonicznych i baz danych w ramach Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="769f7-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="769f7-106">Aby uzyskać więcej informacji, zobacz [instrukcje: wywoływanie funkcji kanonicznych](how-to-call-canonical-functions.md) i [instrukcje: wywoływanie funkcji bazy danych](how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="769f7-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="769f7-107">Proces wywoływania funkcji niestandardowej wymaga wykonania trzech podstawowych czynności:</span><span class="sxs-lookup"><span data-stu-id="769f7-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="769f7-108">Zdefiniuj funkcję w modelu koncepcyjnym lub Zadeklaruj funkcję w modelu magazynu.</span><span class="sxs-lookup"><span data-stu-id="769f7-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="769f7-109">Dodaj metodę do aplikacji i zamapuj ją na funkcję w modelu z <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="769f7-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="769f7-110">Wywołaj funkcję w kwerendzie LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="769f7-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="769f7-111">Więcej informacji znajduje się w tematach w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="769f7-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="769f7-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="769f7-112">In This Section</span></span>  
 [<span data-ttu-id="769f7-113">Instrukcje: Wywoływanie funkcji kanonicznych</span><span class="sxs-lookup"><span data-stu-id="769f7-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="769f7-114">Instrukcje: Wywoływanie funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="769f7-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="769f7-115">Instrukcje: Wywoływanie niestandardowych funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="769f7-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="769f7-116">Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="769f7-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="769f7-117">Instrukcje: Wywoływanie funkcji definiowanych przez model jako metod obiektu</span><span class="sxs-lookup"><span data-stu-id="769f7-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="769f7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="769f7-118">See also</span></span>

- [<span data-ttu-id="769f7-119">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="769f7-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="769f7-120">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="769f7-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="769f7-121">[Plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="769f7-121">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="769f7-122">[Instrukcje: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="769f7-122">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
