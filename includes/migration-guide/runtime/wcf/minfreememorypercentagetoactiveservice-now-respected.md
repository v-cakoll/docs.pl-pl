---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235638"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="e8693-101">MinFreeMemoryPercentageToActiveService teraz jest zachowana.</span><span class="sxs-lookup"><span data-stu-id="e8693-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e8693-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e8693-102">Details</span></span>|<span data-ttu-id="e8693-103">To ustawienie określa minimalną ilość pamięci, która musi być dostępny na serwerze, zanim można aktywować usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="e8693-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="e8693-104">Zaprojektowano w celu zapobieżenia <xref:System.OutOfMemoryException?displayProperty=name> wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e8693-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="e8693-105">W .NET Framework 4.5 ustawienie to nie miało wpływu.</span><span class="sxs-lookup"><span data-stu-id="e8693-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="e8693-106">W programie .NET Framework 4.5.1 ustawienie zostanie wykryty.</span><span class="sxs-lookup"><span data-stu-id="e8693-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="e8693-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e8693-107">Suggestion</span></span>|<span data-ttu-id="e8693-108">Wystąpi wyjątek, jeśli pamięci na serwerze sieci web jest mniejsza niż wartość procentowa zdefiniowane przez ustawienie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8693-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="e8693-109">Niektórych usług WCF, które pomyślnie uruchomiona i został uruchomiony w środowisku ograniczone pamięci może teraz zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e8693-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="e8693-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="e8693-110">Scope</span></span>|<span data-ttu-id="e8693-111">Mały</span><span class="sxs-lookup"><span data-stu-id="e8693-111">Minor</span></span>|
|<span data-ttu-id="e8693-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="e8693-112">Version</span></span>|<span data-ttu-id="e8693-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e8693-113">4.5.1</span></span>|
|<span data-ttu-id="e8693-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e8693-114">Type</span></span>|<span data-ttu-id="e8693-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e8693-115">Runtime</span></span>|
