---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620308"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="3a280-101">Cofnięcie zgody na przywrócenie z różnych 4,5 generacji SQL do 4,0 prostszej generacji SQL</span><span class="sxs-lookup"><span data-stu-id="3a280-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="3a280-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3a280-102">Details</span></span>

<span data-ttu-id="3a280-103">Zapytania, które tworzą instrukcje JOIN i zawierają wywołanie operacji ograniczającej bez wcześniejszego użycia polecenia OrderBy teraz generują prostsze SQL.</span><span class="sxs-lookup"><span data-stu-id="3a280-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="3a280-104">Po uaktualnieniu do .NET Framework 4,5 te zapytania wygenerowały bardziej skomplikowane SQL niż poprzednie wersje.</span><span class="sxs-lookup"><span data-stu-id="3a280-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3a280-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3a280-105">Suggestion</span></span>

<span data-ttu-id="3a280-106">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="3a280-106">This feature is disabled by default.</span></span> <span data-ttu-id="3a280-107">Jeśli Entity Framework generuje dodatkowe instrukcje JOIN, które powodują spadek wydajności, możesz włączyć tę funkcję, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji pliku konfiguracji aplikacji (app.config):</span><span class="sxs-lookup"><span data-stu-id="3a280-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3a280-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3a280-108">Name</span></span>    | <span data-ttu-id="3a280-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="3a280-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a280-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="3a280-110">Scope</span></span>   |<span data-ttu-id="3a280-111">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="3a280-111">Transparent</span></span>|
|<span data-ttu-id="3a280-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="3a280-112">Version</span></span>|<span data-ttu-id="3a280-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="3a280-113">4.5.2</span></span>|
|<span data-ttu-id="3a280-114">Typ</span><span class="sxs-lookup"><span data-stu-id="3a280-114">Type</span></span>|<span data-ttu-id="3a280-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3a280-115">Runtime</span></span>|
