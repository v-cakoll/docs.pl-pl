---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235540"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="25268-101">IPad nie należy używać w pliku niestandardowego możliwości, ponieważ jest on obecnie możliwości przeglądarki</span><span class="sxs-lookup"><span data-stu-id="25268-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

|   |   |
|---|---|
|<span data-ttu-id="25268-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="25268-102">Details</span></span>|<span data-ttu-id="25268-103">Począwszy od programu .NET Framework 4.5, iPad jest identyfikatora w pliku możliwości uzyskiwania informacji na temat przeglądarki ASP.NET domyślne z więc nie powinien on używany w pliku niestandardowego możliwości</span><span class="sxs-lookup"><span data-stu-id="25268-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>|
|<span data-ttu-id="25268-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="25268-104">Suggestion</span></span>|<span data-ttu-id="25268-105">Jeżeli wymagane są funkcje właściwe dla tabletu iPad, należy zmodyfikować zachowanie dla urządzenia iPad, ustawiając możliwości na refID wstępnie zdefiniowanych bram &quot;IPad&quot; zamiast, generując nowy &quot;IPad&quot; identyfikator według agenta użytkownika dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="25268-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>|
|<span data-ttu-id="25268-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="25268-106">Scope</span></span>|<span data-ttu-id="25268-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="25268-107">Edge</span></span>|
|<span data-ttu-id="25268-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="25268-108">Version</span></span>|<span data-ttu-id="25268-109">4.5</span><span class="sxs-lookup"><span data-stu-id="25268-109">4.5</span></span>|
|<span data-ttu-id="25268-110">Typ</span><span class="sxs-lookup"><span data-stu-id="25268-110">Type</span></span>|<span data-ttu-id="25268-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="25268-111">Runtime</span></span>|
