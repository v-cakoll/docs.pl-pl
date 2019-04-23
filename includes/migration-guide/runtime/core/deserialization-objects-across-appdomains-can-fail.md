---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804696"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="cbe05-101">Deserializacja obiektów między domen aplikacji może zakończyć się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="cbe05-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cbe05-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cbe05-102">Details</span></span>|<span data-ttu-id="cbe05-103">W niektórych przypadkach gdy aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji, próba deserializacji obiektów w logicznym kontekście wywołań między domenami aplikacji zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cbe05-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="cbe05-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cbe05-104">Suggestion</span></span>|<span data-ttu-id="cbe05-105">Zobacz [środki zaradcze: Deserializacja obiektów między domenami aplikacji](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="cbe05-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="cbe05-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="cbe05-106">Scope</span></span>|<span data-ttu-id="cbe05-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="cbe05-107">Edge</span></span>|
|<span data-ttu-id="cbe05-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="cbe05-108">Version</span></span>|<span data-ttu-id="cbe05-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="cbe05-109">4.5.1</span></span>|
|<span data-ttu-id="cbe05-110">Typ</span><span class="sxs-lookup"><span data-stu-id="cbe05-110">Type</span></span>|<span data-ttu-id="cbe05-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cbe05-111">Runtime</span></span>|
