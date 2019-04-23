---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774269"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="eebc6-101">Podział opcjonalnych można przywrócić z innego 4.5 generowanie kodu SQL prostsze 4.0 generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="eebc6-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="eebc6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="eebc6-102">Details</span></span>|<span data-ttu-id="eebc6-103">Zapytania, które generuje instrukcje JOIN i zawierać wywołanie ograniczającą operacji bez uprzedniego przy użyciu OrderBy teraz tworzyć prostsze SQL.</span><span class="sxs-lookup"><span data-stu-id="eebc6-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="eebc6-104">Po uaktualnieniu do wersji .NET Framework 4.5, te zapytania utworzone SQL bardziej skomplikowane niż w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="eebc6-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="eebc6-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="eebc6-105">Suggestion</span></span>|<span data-ttu-id="eebc6-106">Ta funkcja jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="eebc6-106">This feature is disabled by default.</span></span> <span data-ttu-id="eebc6-107">Jeśli Entity Framework wygeneruje dodatkowe instrukcje JOIN, które powodują spadek wydajności, możesz włączyć tę funkcję, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcję pliku konfiguracji aplikacji (app.config):</span><span class="sxs-lookup"><span data-stu-id="eebc6-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="eebc6-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="eebc6-108">Scope</span></span>|<span data-ttu-id="eebc6-109">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="eebc6-109">Transparent</span></span>|
|<span data-ttu-id="eebc6-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="eebc6-110">Version</span></span>|<span data-ttu-id="eebc6-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="eebc6-111">4.5.2</span></span>|
|<span data-ttu-id="eebc6-112">Typ</span><span class="sxs-lookup"><span data-stu-id="eebc6-112">Type</span></span>|<span data-ttu-id="eebc6-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="eebc6-113">Runtime</span></span>|
