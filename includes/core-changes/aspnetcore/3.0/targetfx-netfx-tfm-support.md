---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549586"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="680ca-101">Struktura docelowa: porzucona obsługa .NET Framework</span><span class="sxs-lookup"><span data-stu-id="680ca-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="680ca-102">Począwszy od ASP.NET Core 3.0, .NET Framework jest nieobsługiconą platformą docelową.</span><span class="sxs-lookup"><span data-stu-id="680ca-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="680ca-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="680ca-103">Change description</span></span>

<span data-ttu-id="680ca-104">.NET Framework 4.8 jest ostatnią główną wersją programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="680ca-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="680ca-105">Nowe aplikacje ASP.NET Core powinny być oparte na programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="680ca-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="680ca-106">Począwszy od wersji .NET Core 3.0, możesz myśleć o ASP.NET Core 3.0 jako o części .NET Core.</span><span class="sxs-lookup"><span data-stu-id="680ca-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="680ca-107">Klienci korzystający z ASP.NET Core z programem .NET Framework mogą kontynuować w pełni obsługiwany sposób, korzystając z [wersji 2.1 LTS.](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="680ca-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="680ca-108">Obsługa i obsługa 2.1 trwa co najmniej do 21 sierpnia 2021 r.</span><span class="sxs-lookup"><span data-stu-id="680ca-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="680ca-109">Ta data jest trzy lata po deklaracji wydania LTS na [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="680ca-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span></span> <span data-ttu-id="680ca-110">Obsługa pakietów core 2.1 ASP.NET **w programie .NET Framework** będzie rozszerzana na czas nieokreślony, podobnie jak zasady obsługi innych platform ASP.NET [opartych na pakiecie.](https://dotnet.microsoft.com/platform/support/policy/aspnet)</span><span class="sxs-lookup"><span data-stu-id="680ca-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="680ca-111">Aby uzyskać więcej informacji na temat przenoszenia z programu .NET Framework na program .NET Core, zobacz [Przenoszenie do platformy .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="680ca-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="680ca-112">`Microsoft.Extensions`pakiety (takie jak rejestrowanie, iniekcji zależności i konfiguracji) i Entity Framework Core nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="680ca-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="680ca-113">Będą nadal obsługiwać standard .NET.</span><span class="sxs-lookup"><span data-stu-id="680ca-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="680ca-114">Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="680ca-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="680ca-115">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="680ca-115">Version introduced</span></span>

<span data-ttu-id="680ca-116">3.0</span><span class="sxs-lookup"><span data-stu-id="680ca-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="680ca-117">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="680ca-117">Old behavior</span></span>

<span data-ttu-id="680ca-118">ASP.NET aplikacje Core mogą być uruchamiane w programie .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="680ca-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="680ca-119">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="680ca-119">New behavior</span></span>

<span data-ttu-id="680ca-120">ASP.NET aplikacje Core można uruchamiać tylko w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="680ca-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="680ca-121">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="680ca-121">Recommended action</span></span>

<span data-ttu-id="680ca-122">Wykonaj jedno z następujących działań:</span><span class="sxs-lookup"><span data-stu-id="680ca-122">Take one of the following actions:</span></span>

- <span data-ttu-id="680ca-123">Utrzymuj aplikację na ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="680ca-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="680ca-124">Migrowanie aplikacji i zależności do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="680ca-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="680ca-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="680ca-125">Category</span></span>

<span data-ttu-id="680ca-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="680ca-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="680ca-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="680ca-127">Affected APIs</span></span>

<span data-ttu-id="680ca-128">Brak</span><span class="sxs-lookup"><span data-stu-id="680ca-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
