---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649390"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="13001-101">Deserializacja obiektów między domen aplikacji może zakończyć się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="13001-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="13001-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="13001-102">Details</span></span>|<span data-ttu-id="13001-103">W niektórych przypadkach gdy aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji, próba deserializacji obiektów w logicznym kontekście wywołań między domenami aplikacji zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="13001-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="13001-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="13001-104">Suggestion</span></span>|<span data-ttu-id="13001-105">Zobacz [środki zaradcze: Deserializacja obiektów między domenami aplikacji](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="13001-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="13001-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="13001-106">Scope</span></span>|<span data-ttu-id="13001-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="13001-107">Edge</span></span>|
|<span data-ttu-id="13001-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="13001-108">Version</span></span>|<span data-ttu-id="13001-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="13001-109">4.5.1</span></span>|
|<span data-ttu-id="13001-110">Typ</span><span class="sxs-lookup"><span data-stu-id="13001-110">Type</span></span>|<span data-ttu-id="13001-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="13001-111">Runtime</span></span>|
