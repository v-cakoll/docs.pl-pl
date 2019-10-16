---
title: Buforowanie planu zapytania (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 020b2b3f08262fc15ace8603c26e2d6c059baafd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319406"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="084a9-102">Buforowanie planu zapytania (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="084a9-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="084a9-103">Za każdym razem, gdy podejmowana jest próba wykonania zapytania, potok zapytania wyszukuje w pamięci podręcznej planu zapytania, aby sprawdzić, czy dokładne zapytanie jest już skompilowane i dostępne.</span><span class="sxs-lookup"><span data-stu-id="084a9-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="084a9-104">Jeśli tak, ponownie używa buforowanego planu, zamiast tworzyć nowy.</span><span class="sxs-lookup"><span data-stu-id="084a9-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="084a9-105">Jeśli dopasowanie nie zostanie odnalezione w pamięci podręcznej planu zapytania, zapytanie jest kompilowane i buforowane.</span><span class="sxs-lookup"><span data-stu-id="084a9-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="084a9-106">Zapytanie jest identyfikowane za pomocą jego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekstu i kolekcji parametrów (nazw i typów).</span><span class="sxs-lookup"><span data-stu-id="084a9-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="084a9-107">Wszystkie porównania tekstu uwzględniają wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="084a9-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="084a9-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="084a9-108">Configuration</span></span>  
 <span data-ttu-id="084a9-109">Buforowanie planu zapytania można skonfigurować za pomocą <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="084a9-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="084a9-110">Aby włączyć lub wyłączyć buforowanie planu zapytania przy użyciu <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, należy ustawić tę właściwość na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="084a9-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="084a9-111">Wyłączenie pamięci podręcznej planu dla indywidualnych zapytań dynamicznych, które prawdopodobnie nie będą używane więcej, po zwiększeniu wydajności.</span><span class="sxs-lookup"><span data-stu-id="084a9-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="084a9-112">Buforowanie planu zapytania można włączyć za <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="084a9-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="084a9-113">Zalecane rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="084a9-113">Recommended Practice</span></span>  
 <span data-ttu-id="084a9-114">Zapytania dynamiczne należy unikać w ogóle.</span><span class="sxs-lookup"><span data-stu-id="084a9-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="084a9-115">Następujący przykład zapytania dynamicznego jest narażony na ataki z iniekcją SQL, ponieważ pobiera dane wprowadzane przez użytkownika bezpośrednio bez sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="084a9-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```
 
 <span data-ttu-id="084a9-116">W przypadku użycia dynamicznie generowanych zapytań należy rozważyć wyłączenie buforowania planu zapytania, aby uniknąć niepotrzebnego zużycia pamięci dla wpisów pamięci podręcznej, które nie są prawdopodobnie ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="084a9-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="084a9-117">Buforowanie planu zapytania dla zapytań statycznych i zapytań parametrycznych może zapewniać korzyści z wydajności.</span><span class="sxs-lookup"><span data-stu-id="084a9-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="084a9-118">Poniżej znajduje się przykład kwerendy statycznej:</span><span class="sxs-lookup"><span data-stu-id="084a9-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="084a9-119">Aby zapytania były odpowiednio dopasowane przez pamięć podręczną planu zapytania, powinny spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="084a9-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="084a9-120">Tekst zapytania powinien być stałym wzorcem, najlepiej ciągiem lub zasobem.</span><span class="sxs-lookup"><span data-stu-id="084a9-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="084a9-121">należy używać <xref:System.Data.EntityClient.EntityParameter> lub <xref:System.Data.Objects.ObjectParameter>, wszędzie tam, gdzie wartość dostarczona przez użytkownika musi zostać przekazana.</span><span class="sxs-lookup"><span data-stu-id="084a9-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="084a9-122">Należy unikać następujących wzorców zapytań, które niekoniecznie zużywają gniazda w pamięci podręcznej planu zapytania:</span><span class="sxs-lookup"><span data-stu-id="084a9-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="084a9-123">Zmiany do wielkości liter w tekście.</span><span class="sxs-lookup"><span data-stu-id="084a9-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="084a9-124">Zmiany w białych znakach.</span><span class="sxs-lookup"><span data-stu-id="084a9-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="084a9-125">Zmiany w wartościach literału.</span><span class="sxs-lookup"><span data-stu-id="084a9-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="084a9-126">Zmiany tekstu w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="084a9-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084a9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="084a9-127">See also</span></span>

- [<span data-ttu-id="084a9-128">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="084a9-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
