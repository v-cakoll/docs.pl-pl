---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393950"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="1c169-101">MVC: Usunięto podkładkę zgodności z interfejsem API sieci Web</span><span class="sxs-lookup"><span data-stu-id="1c169-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="1c169-102">Począwszy od ASP.NET Core 3,0, `Microsoft.AspNetCore.Mvc.WebApiCompatShim` pakiet nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="1c169-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1c169-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="1c169-103">Change description</span></span>

<span data-ttu-id="1c169-104">Pakiet `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) zapewnia częściową zgodność w ASP.NET Core z ASP.NET 4. x Web API 2, aby uprościć migrację istniejących implementacji interfejsów API sieci web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c169-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="1c169-105">Jednak aplikacje korzystające z WebApiCompatShim nie korzystają z funkcji związanych z interfejsem API wysyłanych w ostatnich wersjach ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c169-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="1c169-106">Takie funkcje obejmują ulepszoną generację funkcji tworzenia specyfikacji interfejsu API, ustandaryzowaną obsługę błędów i generowanie kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="1c169-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="1c169-107">Aby lepiej skupić się na działaniach interfejsu API w 3,0, WebApiCompatShim został usunięty.</span><span class="sxs-lookup"><span data-stu-id="1c169-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="1c169-108">Istniejące aplikacje używające WebApiCompatShim powinny migrować do nowszego `[ApiController]` modelu.</span><span class="sxs-lookup"><span data-stu-id="1c169-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1c169-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1c169-109">Version introduced</span></span>

<span data-ttu-id="1c169-110">3.0</span><span class="sxs-lookup"><span data-stu-id="1c169-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1c169-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="1c169-111">Reason for change</span></span>

<span data-ttu-id="1c169-112">Podkładka zgodności z interfejsem API sieci Web była narzędziem do migracji.</span><span class="sxs-lookup"><span data-stu-id="1c169-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="1c169-113">Ogranicza użytkownikowi dostęp do nowych funkcji dodanych w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c169-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1c169-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1c169-114">Recommended action</span></span>

<span data-ttu-id="1c169-115">Usuń użycie tej podkładki i Przeprowadź migrację bezpośrednio do podobnych funkcji w programie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c169-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="1c169-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1c169-116">Category</span></span>

<span data-ttu-id="1c169-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1c169-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c169-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1c169-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
