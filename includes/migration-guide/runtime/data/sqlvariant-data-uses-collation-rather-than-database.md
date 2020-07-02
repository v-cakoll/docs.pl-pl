---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620288"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="3b262-101">Sql_variant dane używają sortowania sql_variant zamiast sortowania bazy danych</span><span class="sxs-lookup"><span data-stu-id="3b262-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="3b262-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3b262-102">Details</span></span>

<span data-ttu-id="3b262-103"><code>sql_variant</code>dane korzystają z <code>sql_variant</code> sortowania zamiast sortowania bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3b262-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3b262-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3b262-104">Suggestion</span></span>

<span data-ttu-id="3b262-105">Ta zmiana dotyczy możliwego uszkodzenia danych, jeśli sortowanie bazy danych różni się od <code>sql_variant</code> sortowania.</span><span class="sxs-lookup"><span data-stu-id="3b262-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="3b262-106">W aplikacjach korzystających z uszkodzonych danych może wystąpić błąd.</span><span class="sxs-lookup"><span data-stu-id="3b262-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="3b262-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3b262-107">Name</span></span>    | <span data-ttu-id="3b262-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="3b262-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3b262-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="3b262-109">Scope</span></span>   |<span data-ttu-id="3b262-110">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="3b262-110">Transparent</span></span>|
|<span data-ttu-id="3b262-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="3b262-111">Version</span></span>|<span data-ttu-id="3b262-112">4.5</span><span class="sxs-lookup"><span data-stu-id="3b262-112">4.5</span></span>|
|<span data-ttu-id="3b262-113">Typ</span><span class="sxs-lookup"><span data-stu-id="3b262-113">Type</span></span>|<span data-ttu-id="3b262-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3b262-114">Runtime</span></span>|
