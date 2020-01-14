---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937286"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="90465-101">Platforma docelowa: porzucona obsługa .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90465-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="90465-102">Począwszy od ASP.NET Core 3,0, .NET Framework jest nieobsługiwaną strukturą docelową.</span><span class="sxs-lookup"><span data-stu-id="90465-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="90465-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="90465-103">Change description</span></span>

<span data-ttu-id="90465-104">.NET Framework 4,8 to Ostatnia wersja główna .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90465-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="90465-105">Nowe aplikacje ASP.NET Core powinny być oparte na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90465-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="90465-106">Począwszy od wersji programu .NET Core 3,0, można traktować ASP.NET Core 3,0 jako część platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90465-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="90465-107">Klienci korzystający z ASP.NET Core z .NET Framework mogą kontynuować w pełni obsługiwaną pracę przy użyciu [wersji 2,1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="90465-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="90465-108">Obsługa i obsługa 2,1 są kontynuowane do dnia 21 sierpnia 2021.</span><span class="sxs-lookup"><span data-stu-id="90465-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="90465-109">Ta data jest trzy lata po deklaracji wydania LTS zgodnie z [zasadami pomocy technicznej dla platformy .NET](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="90465-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="90465-110">Obsługa pakietów ASP.NET Core 2,1 **w .NET Framework** zostanie rozbudowana w nieskończoność, podobnie jak w [przypadku innych platform ASP.NET opartych na pakietach](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="90465-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="90465-111">Aby uzyskać więcej informacji na temat przenoszenia z .NET Framework do programu .NET Core, zobacz [przenoszenie do platformy .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="90465-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="90465-112">nie ma to wpływu na pakiety `Microsoft.Extensions` (takie jak rejestrowanie, iniekcja zależności i konfiguracja Entity Framework Core).</span><span class="sxs-lookup"><span data-stu-id="90465-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="90465-113">Będą oni nadal obsługiwać .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="90465-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="90465-114">Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="90465-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="90465-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="90465-115">Version introduced</span></span>

<span data-ttu-id="90465-116">3.0</span><span class="sxs-lookup"><span data-stu-id="90465-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="90465-117">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="90465-117">Old behavior</span></span>

<span data-ttu-id="90465-118">Aplikacje ASP.NET Core mogą działać na platformie .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90465-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="90465-119">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="90465-119">New behavior</span></span>

<span data-ttu-id="90465-120">Aplikacje ASP.NET Core można uruchamiać tylko na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90465-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="90465-121">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="90465-121">Recommended action</span></span>

<span data-ttu-id="90465-122">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="90465-122">Take one of the following actions:</span></span>

- <span data-ttu-id="90465-123">Zachowaj swoją aplikację na ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="90465-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="90465-124">Migruj swoją aplikację i zależności do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90465-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="90465-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="90465-125">Category</span></span>

<span data-ttu-id="90465-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="90465-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90465-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="90465-127">Affected APIs</span></span>

<span data-ttu-id="90465-128">Brak</span><span class="sxs-lookup"><span data-stu-id="90465-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
