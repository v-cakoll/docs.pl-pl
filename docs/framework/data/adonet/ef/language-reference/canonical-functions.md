---
title: Canonical funkcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f676c88691f0ba80ca682d720adf649ab612cfb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="canonical-functions"></a><span data-ttu-id="a9889-102">Canonical funkcji</span><span class="sxs-lookup"><span data-stu-id="a9889-102">Canonical Functions</span></span>
<span data-ttu-id="a9889-103">W tej sekcji omówiono kanonicznej funkcji, które są obsługiwane przez wszystkich dostawców danych i mogą być używane przez wszystkie technologie wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="a9889-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="a9889-104">Canonical funkcji nie może zostać rozszerzony przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="a9889-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="a9889-105">Te funkcje canonical będzie translacji odpowiedniej funkcji źródła danych dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="a9889-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="a9889-106">Dzięki temu wywołania funkcji wyrażony w postaci typowych między źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="a9889-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="a9889-107">Ponieważ te funkcje canonical są niezależne od źródeł danych, argumentów i zwracane typy funkcji kanonicznej są definiowane pod względem typów w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a9889-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="a9889-108">Jednak niektóre źródła danych mogą nie obsługiwać wszystkie typy w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a9889-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="a9889-109">Gdy kanonicznej funkcji są używane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania, odpowiednią funkcję zostanie wywołana w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a9889-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="a9889-110">Wszystkie funkcje canonical mają zarówno zachowanie dane wejściowe na wartość null, jak i warunki błędów jawnie określony.</span><span class="sxs-lookup"><span data-stu-id="a9889-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="a9889-111">Dostawców magazynu muszą być zgodne z tego zachowania, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie wymusza to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a9889-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="a9889-112">W przypadku scenariuszy LINQ zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] obejmują metody CLR mapowania do metod w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a9889-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="a9889-113">Mapy metody CLR kanonicznej funkcji, dzięki czemu określonego zestawu metod poprawnie przypisze, niezależnie od tego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a9889-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="a9889-114">Canonical funkcje Namespace</span><span class="sxs-lookup"><span data-stu-id="a9889-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="a9889-115">Przestrzeń nazw dla funkcji kanonicznej jest <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="a9889-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="a9889-116"><xref:System.Data.Metadata.Edm> Przestrzeni nazw jest automatycznie uwzględniany we wszystkich zapytań.</span><span class="sxs-lookup"><span data-stu-id="a9889-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="a9889-117">Jednak jeśli innej przestrzeni nazw jest importowany zawierający funkcję z taką samą nazwę jak kanonicznej funkcji (w <xref:System.Data.Metadata.Edm> przestrzeni nazw), należy określić przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="a9889-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9889-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a9889-118">In This Section</span></span>  
 [<span data-ttu-id="a9889-119">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="a9889-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="a9889-120">W tym artykule omówiono agregacji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9889-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="a9889-121">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="a9889-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="a9889-122">W tym artykule omówiono matematyczne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9889-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="a9889-123">Funkcje ciągów Canonical</span><span class="sxs-lookup"><span data-stu-id="a9889-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="a9889-124">W tym artykule omówiono ciąg [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9889-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="a9889-125">Funkcji daty i godziny Canonical</span><span class="sxs-lookup"><span data-stu-id="a9889-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="a9889-126">W tym artykule omówiono Data i godzina [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9889-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="a9889-127">Funkcje bitowe Canonical</span><span class="sxs-lookup"><span data-stu-id="a9889-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="a9889-128">W tym artykule omówiono bitowo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9889-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="a9889-129">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="a9889-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="a9889-130">W tym artykule omówiono przestrzennym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9889-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="a9889-131">Inne funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="a9889-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="a9889-132">W tym artykule omówiono funkcje nie są sklasyfikowane jako bitowe, daty/godziny, ciąg, matematyczne lub agregacji.</span><span class="sxs-lookup"><span data-stu-id="a9889-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9889-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9889-133">See Also</span></span>  
 [<span data-ttu-id="a9889-134">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a9889-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="a9889-135">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a9889-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a9889-136">Model koncepcyjny Canonical do mapowania funkcji serwera SQL</span><span class="sxs-lookup"><span data-stu-id="a9889-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="a9889-137">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="a9889-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
