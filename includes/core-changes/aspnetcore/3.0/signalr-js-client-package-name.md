---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901746"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="409cd-101">Sygnalizacja: zmieniono nazwę pakietu klienta języka JavaScript</span><span class="sxs-lookup"><span data-stu-id="409cd-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="409cd-102">W ASP.NET Core 3,0 w wersji zapoznawczej 7 nazwa pakietu klienta skryptu JavaScript została zmieniona z `@aspnet/signalr` na `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="409cd-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="409cd-103">Zmiana nazwy odzwierciedla fakt, że sygnalizujący jest przydatny w więcej niż zaledwie ASP.NET Core aplikacji, dzięki usłudze Azure Signal Service.</span><span class="sxs-lookup"><span data-stu-id="409cd-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="409cd-104">Aby reagować na tę zmianę, Zmień odwołania w plikach *Package. JSON* , instrukcje `require` i instrukcje `import` języka ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="409cd-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="409cd-105">W ramach tej zmiany nazwy nie zostanie zmieniony żaden interfejs API.</span><span class="sxs-lookup"><span data-stu-id="409cd-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="409cd-106">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="409cd-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="409cd-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="409cd-107">Version introduced</span></span>

<span data-ttu-id="409cd-108">3.0</span><span class="sxs-lookup"><span data-stu-id="409cd-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="409cd-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="409cd-109">Old behavior</span></span>

<span data-ttu-id="409cd-110">Pakiet klienta ma nazwę `@aspnet/signalr`.</span><span class="sxs-lookup"><span data-stu-id="409cd-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="409cd-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="409cd-111">New behavior</span></span>

<span data-ttu-id="409cd-112">Pakiet klienta ma nazwę `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="409cd-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="409cd-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="409cd-113">Reason for change</span></span>

<span data-ttu-id="409cd-114">Zmiana nazwy objaśnia, że sygnalizujący jest przydatne poza ASP.NET Core aplikacjami, dzięki usłudze Azure Signal Service.</span><span class="sxs-lookup"><span data-stu-id="409cd-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="409cd-115">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="409cd-115">Recommended action</span></span>

<span data-ttu-id="409cd-116">Przejdź do nowego pakietu `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="409cd-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="409cd-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="409cd-117">Category</span></span>

<span data-ttu-id="409cd-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="409cd-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="409cd-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="409cd-119">Affected APIs</span></span>

<span data-ttu-id="409cd-120">Brak</span><span class="sxs-lookup"><span data-stu-id="409cd-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
