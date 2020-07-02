---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620367"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="0c899-101">MinFreeMemoryPercentageToActiveService jest teraz przestrzegane</span><span class="sxs-lookup"><span data-stu-id="0c899-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="0c899-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0c899-102">Details</span></span>

<span data-ttu-id="0c899-103">To ustawienie określa minimalną ilość pamięci, która musi być dostępna na serwerze, zanim będzie można aktywować usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="0c899-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="0c899-104">Jest ona przeznaczona do zapobiegania <xref:System.OutOfMemoryException?displayProperty=fullName> wyjątkom.</span><span class="sxs-lookup"><span data-stu-id="0c899-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="0c899-105">W .NET Framework 4,5 to ustawienie nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="0c899-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="0c899-106">W .NET Framework 4.5.1 zostanie zaobserwowane ustawienie.</span><span class="sxs-lookup"><span data-stu-id="0c899-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0c899-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0c899-107">Suggestion</span></span>

<span data-ttu-id="0c899-108">Wyjątek występuje, jeśli wolna ilość dostępnej pamięci na serwerze sieci Web jest mniejsza niż wartość procentowa zdefiniowana przez ustawienie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0c899-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="0c899-109">Niektóre usługi WCF, które zostały pomyślnie uruchomione i działały w ograniczonym środowisku pamięci, mogą teraz kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0c899-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="0c899-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0c899-110">Name</span></span>    | <span data-ttu-id="0c899-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="0c899-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0c899-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="0c899-112">Scope</span></span>   |<span data-ttu-id="0c899-113">Mały</span><span class="sxs-lookup"><span data-stu-id="0c899-113">Minor</span></span>|
|<span data-ttu-id="0c899-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="0c899-114">Version</span></span>|<span data-ttu-id="0c899-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="0c899-115">4.5.1</span></span>|
|<span data-ttu-id="0c899-116">Typ</span><span class="sxs-lookup"><span data-stu-id="0c899-116">Type</span></span>|<span data-ttu-id="0c899-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0c899-117">Runtime</span></span>|
