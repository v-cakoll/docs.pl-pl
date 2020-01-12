---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901582"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="98827-101">Hosting: AspNetCoreModule V1 został usunięty z pakietu hostingu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="98827-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="98827-102">Począwszy od ASP.NET Core 3,0, pakiet hostingu systemu Windows nie będzie zawierał AspNetCoreModule (ANCM) v1.</span><span class="sxs-lookup"><span data-stu-id="98827-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="98827-103">ANCM v2 jest zgodna z poprzednimi wersjami ANCM OutOfProcess i jest zalecane do użycia z aplikacjami ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="98827-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="98827-104">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="98827-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98827-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="98827-105">Version introduced</span></span>

<span data-ttu-id="98827-106">3.0</span><span class="sxs-lookup"><span data-stu-id="98827-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="98827-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="98827-107">Old behavior</span></span>

<span data-ttu-id="98827-108">ANCM v1 jest zawarta w pakiecie hostingu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="98827-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="98827-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="98827-109">New behavior</span></span>

<span data-ttu-id="98827-110">ANCM V1 nie jest uwzględniony w pakiecie hostingu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="98827-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="98827-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="98827-111">Reason for change</span></span>

<span data-ttu-id="98827-112">ANCM v2 jest zgodna z poprzednimi wersjami ANCM OutOfProcess i jest zalecane do użycia z aplikacjami ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="98827-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98827-113">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="98827-113">Recommended action</span></span>

<span data-ttu-id="98827-114">Używaj ANCM v2 z aplikacjami ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="98827-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="98827-115">Jeśli ANCM v1 jest wymagany, można go zainstalować przy użyciu pakietu hostingu systemu Windows w ASP.NET Core 2,1 lub 2,2.</span><span class="sxs-lookup"><span data-stu-id="98827-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="98827-116">Ta zmiana spowoduje przerwanie ASP.NET Core aplikacji 3,0, które:</span><span class="sxs-lookup"><span data-stu-id="98827-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="98827-117">Jawnie wybrana opcja korzystania z ANCM V1 z `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span><span class="sxs-lookup"><span data-stu-id="98827-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="98827-118">Mieć niestandardowy plik *Web. config* z `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span><span class="sxs-lookup"><span data-stu-id="98827-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="98827-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="98827-119">Category</span></span>

<span data-ttu-id="98827-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="98827-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98827-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="98827-121">Affected APIs</span></span>

<span data-ttu-id="98827-122">Brak</span><span class="sxs-lookup"><span data-stu-id="98827-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
