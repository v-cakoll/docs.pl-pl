---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549586"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="2d108-101">Platforma docelowa: porzucona obsługa .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d108-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="2d108-102">Począwszy od ASP.NET Core 3,0, .NET Framework jest nieobsługiwaną strukturą docelową.</span><span class="sxs-lookup"><span data-stu-id="2d108-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2d108-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="2d108-103">Change description</span></span>

<span data-ttu-id="2d108-104">.NET Framework 4,8 to Ostatnia wersja główna .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d108-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="2d108-105">Nowe aplikacje ASP.NET Core powinny być oparte na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d108-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="2d108-106">Począwszy od wersji programu .NET Core 3,0, można traktować ASP.NET Core 3,0 jako część platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d108-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="2d108-107">Klienci korzystający z ASP.NET Core z .NET Framework mogą kontynuować w pełni obsługiwaną pracę przy użyciu [wersji 2,1 LTS](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="2d108-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="2d108-108">Obsługa i obsługa 2,1 są kontynuowane do dnia 21 sierpnia 2021.</span><span class="sxs-lookup"><span data-stu-id="2d108-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="2d108-109">Ta data jest trzy lata po deklaracji wydania LTS zgodnie z [zasadami pomocy technicznej dla platformy .NET](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="2d108-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span></span> <span data-ttu-id="2d108-110">Obsługa pakietów ASP.NET Core 2,1 **w .NET Framework** zostanie rozbudowana w nieskończoność, podobnie jak w [przypadku innych platform ASP.NET opartych na pakietach](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="2d108-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="2d108-111">Aby uzyskać więcej informacji na temat przenoszenia z .NET Framework do programu .NET Core, zobacz [przenoszenie do platformy .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d108-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="2d108-112">`Microsoft.Extensions`nie ma to wpływu na pakiety (takie jak rejestrowanie, iniekcja zależności i konfiguracja Entity Framework Core).</span><span class="sxs-lookup"><span data-stu-id="2d108-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="2d108-113">Będą oni nadal obsługiwać .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2d108-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="2d108-114">Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="2d108-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2d108-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2d108-115">Version introduced</span></span>

<span data-ttu-id="2d108-116">3.0</span><span class="sxs-lookup"><span data-stu-id="2d108-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2d108-117">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="2d108-117">Old behavior</span></span>

<span data-ttu-id="2d108-118">Aplikacje ASP.NET Core mogą działać na platformie .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d108-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2d108-119">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="2d108-119">New behavior</span></span>

<span data-ttu-id="2d108-120">Aplikacje ASP.NET Core można uruchamiać tylko na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d108-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2d108-121">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2d108-121">Recommended action</span></span>

<span data-ttu-id="2d108-122">Wykonaj jedno z następujących działań:</span><span class="sxs-lookup"><span data-stu-id="2d108-122">Take one of the following actions:</span></span>

- <span data-ttu-id="2d108-123">Zachowaj swoją aplikację na ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="2d108-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="2d108-124">Migruj swoją aplikację i zależności do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d108-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="2d108-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="2d108-125">Category</span></span>

<span data-ttu-id="2d108-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2d108-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2d108-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2d108-127">Affected APIs</span></span>

<span data-ttu-id="2d108-128">Brak</span><span class="sxs-lookup"><span data-stu-id="2d108-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
