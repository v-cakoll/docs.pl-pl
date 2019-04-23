---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981653"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="e2462-101">IPad nie należy używać w pliku niestandardowego możliwości, ponieważ jest on obecnie możliwości przeglądarki</span><span class="sxs-lookup"><span data-stu-id="e2462-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e2462-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e2462-102">Details</span></span>|<span data-ttu-id="e2462-103">Począwszy od programu .NET Framework 4.5, iPad jest identyfikatora w pliku możliwości uzyskiwania informacji na temat przeglądarki ASP.NET domyślne z więc nie powinien on używany w pliku niestandardowego możliwości</span><span class="sxs-lookup"><span data-stu-id="e2462-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>|
|<span data-ttu-id="e2462-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e2462-104">Suggestion</span></span>|<span data-ttu-id="e2462-105">Jeżeli wymagane są funkcje właściwe dla tabletu iPad, należy zmodyfikować zachowanie dla urządzenia iPad, ustawiając możliwości na refID wstępnie zdefiniowanych bram &quot;IPad&quot; zamiast, generując nowy &quot;IPad&quot; identyfikator według agenta użytkownika dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="e2462-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>|
|<span data-ttu-id="e2462-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="e2462-106">Scope</span></span>|<span data-ttu-id="e2462-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="e2462-107">Edge</span></span>|
|<span data-ttu-id="e2462-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="e2462-108">Version</span></span>|<span data-ttu-id="e2462-109">4.5</span><span class="sxs-lookup"><span data-stu-id="e2462-109">4.5</span></span>|
|<span data-ttu-id="e2462-110">Typ</span><span class="sxs-lookup"><span data-stu-id="e2462-110">Type</span></span>|<span data-ttu-id="e2462-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e2462-111">Runtime</span></span>|
