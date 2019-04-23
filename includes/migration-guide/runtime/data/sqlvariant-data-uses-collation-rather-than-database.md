---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235533"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="6911e-101">Dane typu Sql_variant używa sortowania sql_variant, a nie sortowania bazy danych</span><span class="sxs-lookup"><span data-stu-id="6911e-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6911e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6911e-102">Details</span></span>|<span data-ttu-id="6911e-103"><code>sql_variant</code> danych używa <code>sql_variant</code> sortowania zamiast sortowania bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6911e-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="6911e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6911e-104">Suggestion</span></span>|<span data-ttu-id="6911e-105">Ta zmiana dotyczy możliwego uszkodzenia danych, jeśli sortowanie bazy danych różni się od <code>sql_variant</code> sortowania.</span><span class="sxs-lookup"><span data-stu-id="6911e-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="6911e-106">W aplikacjach korzystających z uszkodzonych danych może wystąpić błąd.</span><span class="sxs-lookup"><span data-stu-id="6911e-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="6911e-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="6911e-107">Scope</span></span>|<span data-ttu-id="6911e-108">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="6911e-108">Transparent</span></span>|
|<span data-ttu-id="6911e-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="6911e-109">Version</span></span>|<span data-ttu-id="6911e-110">4.5</span><span class="sxs-lookup"><span data-stu-id="6911e-110">4.5</span></span>|
|<span data-ttu-id="6911e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="6911e-111">Type</span></span>|<span data-ttu-id="6911e-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6911e-112">Runtime</span></span>|
