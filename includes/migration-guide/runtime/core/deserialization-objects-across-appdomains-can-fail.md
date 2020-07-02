---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620217"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="7a7a2-101">Deserializacja obiektów w domenach AppDomain może zakończyć się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="7a7a2-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="7a7a2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7a7a2-102">Details</span></span>

<span data-ttu-id="7a7a2-103">W niektórych przypadkach, gdy aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji, próba deserializacji obiektów w kontekście wywołania logicznego między domenami aplikacji zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7a7a2-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7a7a2-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7a7a2-104">Suggestion</span></span>

<span data-ttu-id="7a7a2-105">Zobacz [łagodzenie: deserializacja obiektów w domenach aplikacji](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="7a7a2-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="7a7a2-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7a7a2-106">Name</span></span>    | <span data-ttu-id="7a7a2-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="7a7a2-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7a7a2-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="7a7a2-108">Scope</span></span>   |<span data-ttu-id="7a7a2-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="7a7a2-109">Edge</span></span>|
|<span data-ttu-id="7a7a2-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="7a7a2-110">Version</span></span>|<span data-ttu-id="7a7a2-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7a7a2-111">4.5.1</span></span>|
|<span data-ttu-id="7a7a2-112">Typ</span><span class="sxs-lookup"><span data-stu-id="7a7a2-112">Type</span></span>|<span data-ttu-id="7a7a2-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7a7a2-113">Runtime</span></span>|
