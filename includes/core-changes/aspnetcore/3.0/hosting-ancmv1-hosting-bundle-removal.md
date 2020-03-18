---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901582"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="48ea1-101">Hosting: AspNetCoreModule V1 usunięty z pakietu hostingowego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="48ea1-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="48ea1-102">Począwszy od ASP.NET Core 3.0, pakiet hostingowy systemu Windows nie będzie zawierał aspNetCoreModule (ANCM) V1.</span><span class="sxs-lookup"><span data-stu-id="48ea1-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="48ea1-103">ANCM V2 jest wstecznie kompatybilny z ANCM OutOfProcess i jest zalecany do użytku z aplikacjami ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="48ea1-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="48ea1-104">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="48ea1-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="48ea1-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="48ea1-105">Version introduced</span></span>

<span data-ttu-id="48ea1-106">3.0</span><span class="sxs-lookup"><span data-stu-id="48ea1-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="48ea1-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="48ea1-107">Old behavior</span></span>

<span data-ttu-id="48ea1-108">ANCM V1 znajduje się w pakiecie hostingowym systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="48ea1-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="48ea1-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="48ea1-109">New behavior</span></span>

<span data-ttu-id="48ea1-110">Ancm V1 nie jest uwzględniony w pakiecie hostingu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="48ea1-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="48ea1-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="48ea1-111">Reason for change</span></span>

<span data-ttu-id="48ea1-112">ANCM V2 jest wstecznie kompatybilny z ANCM OutOfProcess i jest zalecany do użytku z aplikacjami ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="48ea1-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="48ea1-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="48ea1-113">Recommended action</span></span>

<span data-ttu-id="48ea1-114">Użyj ANCM V2 z ASP.NET aplikacjami Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="48ea1-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="48ea1-115">Jeśli wymagany jest ancm V1, można go zainstalować za pomocą pakietu hostingowego ASP.NET Core 2.1 lub 2.2 Windows Hosting Bundle.</span><span class="sxs-lookup"><span data-stu-id="48ea1-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="48ea1-116">Ta zmiana spowoduje przerwanie ASP.NET aplikacji Core 3.0, które:</span><span class="sxs-lookup"><span data-stu-id="48ea1-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="48ea1-117">Wyraźnie zdecydował się na korzystanie z `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`ANCM V1 z .</span><span class="sxs-lookup"><span data-stu-id="48ea1-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="48ea1-118">Mieć niestandardowy plik *web.config* z . `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`</span><span class="sxs-lookup"><span data-stu-id="48ea1-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="48ea1-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="48ea1-119">Category</span></span>

<span data-ttu-id="48ea1-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="48ea1-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="48ea1-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="48ea1-121">Affected APIs</span></span>

<span data-ttu-id="48ea1-122">Brak</span><span class="sxs-lookup"><span data-stu-id="48ea1-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
