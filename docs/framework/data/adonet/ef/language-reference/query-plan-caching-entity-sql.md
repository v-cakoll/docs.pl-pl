---
title: Planu zapytania z pamięci podręcznej (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9b809962e11ee74a99f736769b47bf3052af5e8a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641463"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="86a03-102">Planu zapytania z pamięci podręcznej (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="86a03-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="86a03-103">Zawsze, gdy podejmowana jest próba, aby wykonać zapytanie, potok zapytanie wyszukuje pamięci podręcznej planu zapytania Czy dokładne zapytanie jest już skompilowane i dostępne.</span><span class="sxs-lookup"><span data-stu-id="86a03-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="86a03-104">Jeśli tak, używa buforowanego planu zamiast tworzenia nowej.</span><span class="sxs-lookup"><span data-stu-id="86a03-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="86a03-105">Jeśli dopasowanie nie zostanie znaleziony w pamięci podręcznej planu zapytania, kwerenda jest skompilowany i pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="86a03-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="86a03-106">Zapytanie jest identyfikowane za pomocą jego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekcji tekstu i parametrów (nazw i typy).</span><span class="sxs-lookup"><span data-stu-id="86a03-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="86a03-107">Wszystkie porównania tekstu jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="86a03-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="86a03-108">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="86a03-108">Configuration</span></span>  
 <span data-ttu-id="86a03-109">Buforowanie planu zapytania jest konfigurowane za pomocą <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="86a03-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="86a03-110">Aby włączyć lub wyłączyć buforowanie planu zapytania za pomocą <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, ustaw tę właściwość na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="86a03-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="86a03-111">Wyłączanie buforowanie planu dla poszczególnych zapytań dynamicznych, które prawdopodobnie celu można użyć więcej niż jeden raz poprawia wydajność.</span><span class="sxs-lookup"><span data-stu-id="86a03-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="86a03-112">Aby umożliwić buforowanie planu zapytania za pomocą <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="86a03-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="86a03-113">Zalecana praktyka</span><span class="sxs-lookup"><span data-stu-id="86a03-113">Recommended Practice</span></span>  
 <span data-ttu-id="86a03-114">Zapytania dynamiczne należy unikać, ogólnie rzecz biorąc.</span><span class="sxs-lookup"><span data-stu-id="86a03-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="86a03-115">W poniższym przykładzie zapytanie dynamiczne jest narażony na ataki przez wstrzyknięcie kodu SQL, ponieważ zajmuje trochę danych wejściowych użytkownika bezpośrednio, bez żadnych sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="86a03-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="86a03-116">Jeśli używasz dynamicznie generowanych zapytań, należy rozważyć wyłączenie, buforowanie planu zapytania w celu uniknięcia zużycie pamięci niepotrzebne dla wpisów pamięci podręcznej, które prawdopodobnie mogą być ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="86a03-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="86a03-117">Plan zapytania w pamięci podręcznej zapytań statycznych i sparametryzowane zapytania może zapewnić korzyści wydajności.</span><span class="sxs-lookup"><span data-stu-id="86a03-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="86a03-118">Oto przykład kwerendy statyczne:</span><span class="sxs-lookup"><span data-stu-id="86a03-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="86a03-119">Dla zapytań, które mają być dopasowywane prawidłowo o pamięci podręcznej planu zapytania mogą spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="86a03-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="86a03-120">Tekst zapytania należy wzór stałej, najlepiej stałym ciągiem lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="86a03-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="86a03-121"><xref:System.Data.EntityClient.EntityParameter> lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie muszą być przekazywane wartości dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="86a03-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="86a03-122">Należy unikać następujące wzorce zapytań, które zużywają niepotrzebnego miejsca w pamięci podręcznej planu zapytania:</span><span class="sxs-lookup"><span data-stu-id="86a03-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="86a03-123">Zmiany do rozróżniania wielkości liter w tekście.</span><span class="sxs-lookup"><span data-stu-id="86a03-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="86a03-124">Zmiany biały znak.</span><span class="sxs-lookup"><span data-stu-id="86a03-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="86a03-125">Zmiany wartości literału.</span><span class="sxs-lookup"><span data-stu-id="86a03-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="86a03-126">Zmiany tekstu w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="86a03-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a03-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86a03-127">See also</span></span>

- [<span data-ttu-id="86a03-128">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="86a03-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
