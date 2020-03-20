---
title: Buforowanie planu kwerend (entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149989"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="285c8-102">Buforowanie planu kwerend (entity SQL)</span><span class="sxs-lookup"><span data-stu-id="285c8-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="285c8-103">Za każdym razem, gdy podejmowana jest próba wykonania kwerendy, potok zapytań wyszukuje swoją pamięć podręczną planu kwerend, aby zobaczyć, czy dokładna kwerenda jest już skompilowana i dostępna.</span><span class="sxs-lookup"><span data-stu-id="285c8-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="285c8-104">Jeśli tak, używa ponownie buforowanego planu, a nie tworzenie nowego.</span><span class="sxs-lookup"><span data-stu-id="285c8-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="285c8-105">Jeśli dopasowanie nie zostanie znalezione w pamięci podręcznej planu kwerendy, kwerenda jest kompilowana i buforowana.</span><span class="sxs-lookup"><span data-stu-id="285c8-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="285c8-106">Kwerenda jest identyfikowana przez jego kolekcję [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekstu i parametrów (nazwy i typy).</span><span class="sxs-lookup"><span data-stu-id="285c8-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="285c8-107">We wszystkich porównaniach tekstu rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="285c8-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="285c8-108">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="285c8-108">Configuration</span></span>  
 <span data-ttu-id="285c8-109">Buforowanie planu kwerend można konfigurować za pomocą pliku <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="285c8-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="285c8-110">Aby włączyć lub wyłączyć buforowanie <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>planu kwerend `true` za `false`pośrednictwem , ustaw tę właściwość na lub .</span><span class="sxs-lookup"><span data-stu-id="285c8-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="285c8-111">Wyłączenie buforowania planu dla poszczególnych zapytań dynamicznych, które są mało prawdopodobne, aby być używane więcej niż raz zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="285c8-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="285c8-112">Można włączyć buforowanie planu <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>kwerend za pośrednictwem programu .</span><span class="sxs-lookup"><span data-stu-id="285c8-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="285c8-113">Zalecana praktyka</span><span class="sxs-lookup"><span data-stu-id="285c8-113">Recommended Practice</span></span>  
 <span data-ttu-id="285c8-114">Ogólnie należy unikać zapytań dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="285c8-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="285c8-115">Poniższy przykład zapytania dynamicznego jest podatny na ataki iniekcji SQL, ponieważ pobiera dane wejściowe użytkownika bezpośrednio bez sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="285c8-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="285c8-116">Jeśli używasz kwerend generowanych dynamicznie, należy rozważyć wyłączenie buforowania planu kwerend, aby uniknąć niepotrzebnego zużycia pamięci dla wpisów pamięci podręcznej, które są mało prawdopodobne, aby być ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="285c8-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="285c8-117">Buforowanie planu kwerend w kwerendach statycznych i kwerendach sparametryzowanych może zapewnić korzyści z wydajności.</span><span class="sxs-lookup"><span data-stu-id="285c8-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="285c8-118">Poniżej przedstawiono przykład kwerendy statycznej:</span><span class="sxs-lookup"><span data-stu-id="285c8-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="285c8-119">Aby kwerendy były prawidłowo dopasowane przez pamięć podręczną planu kwerend, powinny one spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="285c8-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="285c8-120">Tekst kwerendy powinien być stałym wzorcem, najlepiej stałym ciągiem lub zasobem.</span><span class="sxs-lookup"><span data-stu-id="285c8-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="285c8-121"><xref:System.Data.EntityClient.EntityParameter>lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie musi zostać przekazana wartość dostarczona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="285c8-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="285c8-122">Należy unikać następujących wzorców zapytań, które niepotrzebnie zużywają gniazda w pamięci podręcznej planu kwerendy:</span><span class="sxs-lookup"><span data-stu-id="285c8-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="285c8-123">Zmiany w literze w tekście.</span><span class="sxs-lookup"><span data-stu-id="285c8-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="285c8-124">Zmiany w odstępie.</span><span class="sxs-lookup"><span data-stu-id="285c8-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="285c8-125">Zmiany wartości literału.</span><span class="sxs-lookup"><span data-stu-id="285c8-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="285c8-126">Zmiany w tekście wewnątrz komentarzy.</span><span class="sxs-lookup"><span data-stu-id="285c8-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285c8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="285c8-127">See also</span></span>

- [<span data-ttu-id="285c8-128">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="285c8-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
