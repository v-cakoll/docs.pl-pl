---
title: Planu zapytania z pamięci podręcznej (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 75c097d66ae23d32465b5a717ae627d35cdc003f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671138"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="65383-102">Planu zapytania z pamięci podręcznej (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="65383-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="65383-103">Zawsze, gdy podejmowana jest próba, aby wykonać zapytanie, potok zapytanie wyszukuje pamięci podręcznej planu zapytania Czy dokładne zapytanie jest już skompilowane i dostępne.</span><span class="sxs-lookup"><span data-stu-id="65383-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="65383-104">Jeśli tak, używa buforowanego planu zamiast tworzenia nowej.</span><span class="sxs-lookup"><span data-stu-id="65383-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="65383-105">Jeśli dopasowanie nie zostanie znaleziony w pamięci podręcznej planu zapytania, kwerenda jest skompilowany i pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="65383-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="65383-106">Zapytanie jest identyfikowane za pomocą jego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekcji tekstu i parametrów (nazw i typy).</span><span class="sxs-lookup"><span data-stu-id="65383-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="65383-107">Wszystkie porównania tekstu jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="65383-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="65383-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="65383-108">Configuration</span></span>  
 <span data-ttu-id="65383-109">Buforowanie planu zapytania jest konfigurowane za pomocą <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="65383-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="65383-110">Aby włączyć lub wyłączyć buforowanie planu zapytania za pomocą <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, ustaw tę właściwość na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="65383-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="65383-111">Wyłączanie buforowanie planu dla poszczególnych zapytań dynamicznych, które prawdopodobnie celu można użyć więcej niż jeden raz poprawia wydajność.</span><span class="sxs-lookup"><span data-stu-id="65383-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="65383-112">Aby umożliwić buforowanie planu zapytania za pomocą <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="65383-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="65383-113">Zalecana praktyka</span><span class="sxs-lookup"><span data-stu-id="65383-113">Recommended Practice</span></span>  
 <span data-ttu-id="65383-114">Zapytania dynamiczne należy unikać, ogólnie rzecz biorąc.</span><span class="sxs-lookup"><span data-stu-id="65383-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="65383-115">W poniższym przykładzie zapytanie dynamiczne jest narażony na ataki przez wstrzyknięcie kodu SQL, ponieważ zajmuje trochę danych wejściowych użytkownika bezpośrednio, bez żadnych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="65383-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="65383-116">Jeśli używasz dynamicznie generowanych zapytań, należy rozważyć wyłączenie, buforowanie planu zapytania w celu uniknięcia zużycie pamięci niepotrzebne dla wpisów pamięci podręcznej, które prawdopodobnie mogą być ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="65383-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="65383-117">Plan zapytania w pamięci podręcznej zapytań statycznych i sparametryzowane zapytania może zapewnić korzyści wydajności.</span><span class="sxs-lookup"><span data-stu-id="65383-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="65383-118">Oto przykład kwerendy statyczne:</span><span class="sxs-lookup"><span data-stu-id="65383-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="65383-119">Dla zapytań, które mają być dopasowywane prawidłowo o pamięci podręcznej planu zapytania mogą spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="65383-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
-   <span data-ttu-id="65383-120">Tekst zapytania należy wzór stałej, najlepiej stałym ciągiem lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="65383-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
-   <span data-ttu-id="65383-121"><xref:System.Data.EntityClient.EntityParameter> lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie muszą być przekazywane wartości dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65383-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="65383-122">Należy unikać następujące wzorce zapytań, które zużywają niepotrzebnego miejsca w pamięci podręcznej planu zapytania:</span><span class="sxs-lookup"><span data-stu-id="65383-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
-   <span data-ttu-id="65383-123">Zmiany do rozróżniania wielkości liter w tekście.</span><span class="sxs-lookup"><span data-stu-id="65383-123">Changes to letter case in the text.</span></span>  
  
-   <span data-ttu-id="65383-124">Zmiany biały znak.</span><span class="sxs-lookup"><span data-stu-id="65383-124">Changes to white space.</span></span>  
  
-   <span data-ttu-id="65383-125">Zmiany wartości literału.</span><span class="sxs-lookup"><span data-stu-id="65383-125">Changes to literal values.</span></span>  
  
-   <span data-ttu-id="65383-126">Zmiany tekstu w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="65383-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65383-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65383-127">See also</span></span>
- [<span data-ttu-id="65383-128">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="65383-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
