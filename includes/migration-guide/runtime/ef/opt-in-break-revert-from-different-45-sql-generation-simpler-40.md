---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803263"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="99265-101">Zrezygnuj z przerwy, aby powrócić z różnych generacji SQL 4.5 do prostszego generowania SQL 4.0</span><span class="sxs-lookup"><span data-stu-id="99265-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="99265-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="99265-102">Details</span></span>|<span data-ttu-id="99265-103">Kwerendy, które produkują join instrukcji i zawierają wywołanie operacji ograniczania bez uprzedniego użycia OrderBy teraz produkować prostsze SQL.</span><span class="sxs-lookup"><span data-stu-id="99265-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="99265-104">Po uaktualnieniu do programu .NET Framework 4.5 te zapytania wywołały bardziej skomplikowany sql niż poprzednie wersje.</span><span class="sxs-lookup"><span data-stu-id="99265-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="99265-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="99265-105">Suggestion</span></span>|<span data-ttu-id="99265-106">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="99265-106">This feature is disabled by default.</span></span> <span data-ttu-id="99265-107">Jeśli entity framework generuje dodatkowe instrukcje JOIN, które powodują obniżenie wydajności, można <code>&lt;appSettings&gt;</code> włączyć tę funkcję, dodając następujący wpis do sekcji pliku konfiguracji aplikacji (app.config):</span><span class="sxs-lookup"><span data-stu-id="99265-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="99265-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="99265-108">Scope</span></span>|<span data-ttu-id="99265-109">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="99265-109">Transparent</span></span>|
|<span data-ttu-id="99265-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="99265-110">Version</span></span>|<span data-ttu-id="99265-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="99265-111">4.5.2</span></span>|
|<span data-ttu-id="99265-112">Typ</span><span class="sxs-lookup"><span data-stu-id="99265-112">Type</span></span>|<span data-ttu-id="99265-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="99265-113">Runtime</span></span>|
