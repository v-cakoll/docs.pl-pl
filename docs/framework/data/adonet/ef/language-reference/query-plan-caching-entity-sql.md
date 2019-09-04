---
title: Buforowanie planu zapytania (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: ca95f3aed5c092247a97bbfe5b0237a45b95ae16
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249285"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="f6bb7-102">Buforowanie planu zapytania (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f6bb7-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="f6bb7-103">Za każdym razem, gdy podejmowana jest próba wykonania zapytania, potok zapytania wyszukuje w pamięci podręcznej planu zapytania, aby sprawdzić, czy dokładne zapytanie jest już skompilowane i dostępne.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="f6bb7-104">Jeśli tak, ponownie używa buforowanego planu, zamiast tworzyć nowy.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="f6bb7-105">Jeśli dopasowanie nie zostanie odnalezione w pamięci podręcznej planu zapytania, zapytanie jest kompilowane i buforowane.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="f6bb7-106">Zapytanie jest identyfikowane za pomocą [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jego tekstu i kolekcji parametrów (nazw i typów).</span><span class="sxs-lookup"><span data-stu-id="f6bb7-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="f6bb7-107">Wszystkie porównania tekstu uwzględniają wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f6bb7-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f6bb7-108">Configuration</span></span>  
 <span data-ttu-id="f6bb7-109">Buforowanie planu zapytania można skonfigurować za pomocą <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="f6bb7-110">Aby włączyć lub wyłączyć buforowanie planu zapytania przez <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, należy ustawić tę właściwość `true` na `false`lub.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="f6bb7-111">Wyłączenie pamięci podręcznej planu dla indywidualnych zapytań dynamicznych, które prawdopodobnie nie będą używane więcej, po zwiększeniu wydajności.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="f6bb7-112">Można włączyć buforowanie planu zapytania przez <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="f6bb7-113">Zalecane rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f6bb7-113">Recommended Practice</span></span>  
 <span data-ttu-id="f6bb7-114">Zapytania dynamiczne należy unikać w ogóle.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="f6bb7-115">Następujący przykład zapytania dynamicznego jest narażony na ataki z iniekcją SQL, ponieważ pobiera dane wprowadzane przez użytkownika bezpośrednio bez sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="f6bb7-116">W przypadku użycia dynamicznie generowanych zapytań należy rozważyć wyłączenie buforowania planu zapytania, aby uniknąć niepotrzebnego zużycia pamięci dla wpisów pamięci podręcznej, które nie są prawdopodobnie ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="f6bb7-117">Buforowanie planu zapytania dla zapytań statycznych i zapytań parametrycznych może zapewniać korzyści z wydajności.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="f6bb7-118">Poniżej znajduje się przykład kwerendy statycznej:</span><span class="sxs-lookup"><span data-stu-id="f6bb7-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="f6bb7-119">Aby zapytania były odpowiednio dopasowane przez pamięć podręczną planu zapytania, powinny spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="f6bb7-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="f6bb7-120">Tekst zapytania powinien być stałym wzorcem, najlepiej ciągiem lub zasobem.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="f6bb7-121"><xref:System.Data.EntityClient.EntityParameter>lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie należy przekazać wartość dostarczoną przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="f6bb7-122">Należy unikać następujących wzorców zapytań, które niekoniecznie zużywają gniazda w pamięci podręcznej planu zapytania:</span><span class="sxs-lookup"><span data-stu-id="f6bb7-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="f6bb7-123">Zmiany do wielkości liter w tekście.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="f6bb7-124">Zmiany w białych znakach.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="f6bb7-125">Zmiany w wartościach literału.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="f6bb7-126">Zmiany tekstu w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="f6bb7-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6bb7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6bb7-127">See also</span></span>

- [<span data-ttu-id="f6bb7-128">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f6bb7-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
