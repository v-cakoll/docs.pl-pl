---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617297"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="db674-101">Walidacja schematu XML jest bardziej rygorystyczna</span><span class="sxs-lookup"><span data-stu-id="db674-101">XML schema validation is stricter</span></span>

#### <a name="details"></a><span data-ttu-id="db674-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="db674-102">Details</span></span>

<span data-ttu-id="db674-103">W programie .NET Framework 4.5 walidacja schematu XML jest bardziej rygorystyczna.</span><span class="sxs-lookup"><span data-stu-id="db674-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="db674-104">Jeśli element xsd:anyURI zostanie użyty w celu walidacji identyfikatora URI, takiego jak protokół mailto, walidacja nie powiedzie się, jeśli w identyfikatorze URI znajdują się spacje.</span><span class="sxs-lookup"><span data-stu-id="db674-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="db674-105">W poprzednich wersjach programu .NET Framework walidacja kończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="db674-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="db674-106">Ta zmiana dotyczy tylko aplikacji, których platformą docelową jest program .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="db674-106">The change affects only applications that target the .NET Framework 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="db674-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="db674-107">Suggestion</span></span>

<span data-ttu-id="db674-108">W razie potrzeby użycia mniej rygorystycznej walidacji (stosowanej w programie .NET Framework 4.0) można określić program .NET Framework 4.0 jako platformę docelową aplikacji używanej do walidacji.</span><span class="sxs-lookup"><span data-stu-id="db674-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="db674-109">Jednak w przypadku przekierowania do programu .NET Framework 4.5 należy wykonać przegląd kodu, aby upewnić się, że nieprawidłowe identyfikatory URI (ze spacjami) nie są oczekiwane jako wartości atrybutu z typem danych anyURI.</span><span class="sxs-lookup"><span data-stu-id="db674-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>

| <span data-ttu-id="db674-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="db674-110">Name</span></span>    | <span data-ttu-id="db674-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="db674-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="db674-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="db674-112">Scope</span></span>   | <span data-ttu-id="db674-113">Mały</span><span class="sxs-lookup"><span data-stu-id="db674-113">Minor</span></span>       |
| <span data-ttu-id="db674-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="db674-114">Version</span></span> | <span data-ttu-id="db674-115">4.5</span><span class="sxs-lookup"><span data-stu-id="db674-115">4.5</span></span>         |
| <span data-ttu-id="db674-116">Typ</span><span class="sxs-lookup"><span data-stu-id="db674-116">Type</span></span>    | <span data-ttu-id="db674-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="db674-117">Retargeting</span></span> |
