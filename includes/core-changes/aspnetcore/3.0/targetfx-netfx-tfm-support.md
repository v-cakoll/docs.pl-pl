---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937286"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="30cd2-101">Struktura docelowa: obsługa platformy .NET Framework porzucona</span><span class="sxs-lookup"><span data-stu-id="30cd2-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="30cd2-102">Począwszy od ASP.NET Core 3.0, .NET Framework jest nieobsługiwaną platformą docelową.</span><span class="sxs-lookup"><span data-stu-id="30cd2-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="30cd2-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="30cd2-103">Change description</span></span>

<span data-ttu-id="30cd2-104">.NET Framework 4.8 jest ostatnią wersją główną programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30cd2-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="30cd2-105">Nowe ASP.NET aplikacje Core powinny być zbudowane na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30cd2-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="30cd2-106">Począwszy od wersji .NET Core 3.0, można traktować ASP.NET Core 3.0 jako część .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30cd2-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="30cd2-107">Klienci korzystający z ASP.NET Core z platformą .NET Framework mogą kontynuować w pełni obsługiwany sposób przy użyciu [wersji 2.1 LTS.](https://www.microsoft.com/net/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="30cd2-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="30cd2-108">Wsparcie i serwis owanie dla 2.1 trwa co najmniej do 21 sierpnia 2021 r.</span><span class="sxs-lookup"><span data-stu-id="30cd2-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="30cd2-109">Ta data jest trzy lata po deklaracji wydania LTS na [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="30cd2-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="30cd2-110">Obsługa pakietów ASP.NET Core 2.1 **w platformie .NET Framework** będzie trwać przez czas nieokreślony, podobnie jak [zasady obsługi dla innych platform ASP.NET opartych na pakiecie.](https://dotnet.microsoft.com/platform/support/policy/aspnet)</span><span class="sxs-lookup"><span data-stu-id="30cd2-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="30cd2-111">Aby uzyskać więcej informacji na temat przenoszenia z platformy .NET Framework do platformy .NET Core, zobacz [Przenoszenie do .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="30cd2-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="30cd2-112">`Microsoft.Extensions`pakiety (takie jak rejestrowanie, iniekcji zależności i konfiguracji) i entity framework core nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="30cd2-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="30cd2-113">Będą nadal obsługiwać .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30cd2-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="30cd2-114">Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="30cd2-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30cd2-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="30cd2-115">Version introduced</span></span>

<span data-ttu-id="30cd2-116">3.0</span><span class="sxs-lookup"><span data-stu-id="30cd2-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="30cd2-117">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="30cd2-117">Old behavior</span></span>

<span data-ttu-id="30cd2-118">ASP.NET aplikacje Core mogą działać na platformie .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30cd2-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="30cd2-119">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="30cd2-119">New behavior</span></span>

<span data-ttu-id="30cd2-120">ASP.NET aplikacje Core można uruchamiać tylko w usłudze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30cd2-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30cd2-121">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="30cd2-121">Recommended action</span></span>

<span data-ttu-id="30cd2-122">Wykonaj jedno z następujących działań:</span><span class="sxs-lookup"><span data-stu-id="30cd2-122">Take one of the following actions:</span></span>

- <span data-ttu-id="30cd2-123">Utrzymuj aplikację na ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="30cd2-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="30cd2-124">Migrowanie aplikacji i zależności do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30cd2-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="30cd2-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="30cd2-125">Category</span></span>

<span data-ttu-id="30cd2-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30cd2-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30cd2-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="30cd2-127">Affected APIs</span></span>

<span data-ttu-id="30cd2-128">Brak</span><span class="sxs-lookup"><span data-stu-id="30cd2-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
