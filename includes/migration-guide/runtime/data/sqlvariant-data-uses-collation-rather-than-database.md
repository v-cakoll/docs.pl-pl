---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235533"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="49716-101">Dane typu Sql_variant używa sortowania sql_variant, a nie sortowania bazy danych</span><span class="sxs-lookup"><span data-stu-id="49716-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="49716-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="49716-102">Details</span></span>|<code>sql_variant</code> <span data-ttu-id="49716-103">danych używa <code>sql_variant</code> sortowania zamiast sortowania bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49716-103">data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="49716-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="49716-104">Suggestion</span></span>|<span data-ttu-id="49716-105">Ta zmiana dotyczy możliwego uszkodzenia danych, jeśli sortowanie bazy danych różni się od <code>sql_variant</code> sortowania.</span><span class="sxs-lookup"><span data-stu-id="49716-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="49716-106">W aplikacjach korzystających z uszkodzonych danych może wystąpić błąd.</span><span class="sxs-lookup"><span data-stu-id="49716-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="49716-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="49716-107">Scope</span></span>|<span data-ttu-id="49716-108">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="49716-108">Transparent</span></span>|
|<span data-ttu-id="49716-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="49716-109">Version</span></span>|<span data-ttu-id="49716-110">4.5</span><span class="sxs-lookup"><span data-stu-id="49716-110">4.5</span></span>|
|<span data-ttu-id="49716-111">Typ</span><span class="sxs-lookup"><span data-stu-id="49716-111">Type</span></span>|<span data-ttu-id="49716-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="49716-112">Runtime</span></span>|
