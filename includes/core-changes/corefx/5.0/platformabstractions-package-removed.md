---
ms.openlocfilehash: d85fb8df7afdc5f4c3faecebcd24d11677798bc9
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365621"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="a0f37-101">Usunięto pakiet Microsoft. DotNet. PlatformAbstractions</span><span class="sxs-lookup"><span data-stu-id="a0f37-101">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="a0f37-102">Nie zostaną wygenerowane żadne nowe wersje [pakietu NuGet Microsoft. dotnet. PlatformAbstractions](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) .</span><span class="sxs-lookup"><span data-stu-id="a0f37-102">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a0f37-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="a0f37-103">Change description</span></span>

<span data-ttu-id="a0f37-104">Wcześniej nowe wersje <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> biblioteki zostały utworzone wraz z nowymi wersjami programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a0f37-104">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="a0f37-105">W przód do biblioteki nie zostaną dodane żadne nowe funkcje i nie zostaną wydane żadne nowe wersje główne.</span><span class="sxs-lookup"><span data-stu-id="a0f37-105">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="a0f37-106">Jednak istniejące wersje biblioteki będą nadal działać i będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a0f37-106">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="a0f37-107"><xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>Biblioteka pokrywa się z interfejsami API, które są już ustanowione w systemie. \* przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="a0f37-107">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="a0f37-108">Ponadto niektóre <xref:Microsoft.DotNet.PlatformAbstractions> interfejsy API nie zostały zaprojektowane z tym samym poziomem kontroli i długoterminową obsługą jako resztą systemu. \* Programowania.</span><span class="sxs-lookup"><span data-stu-id="a0f37-108">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="a0f37-109">Na przykład program <xref:Microsoft.DotNet.PlatformAbstractions> używa `Platform` wyliczenia do opisywania bieżącej platformy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a0f37-109">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="a0f37-110">Ten projekt wyliczenia został jawnie odrzucony <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> , gdy interfejs API został zaprojektowany, aby umożliwić korzystanie z nowych platform i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a0f37-110">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="a0f37-111">Scenariusze włączane przez <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliotekę są teraz możliwe bez niej.</span><span class="sxs-lookup"><span data-stu-id="a0f37-111">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="a0f37-112">Istniejące wersje będą nadal działać, nawet w programie .NET 5,0 lub nowszym i będą obsługiwane wraz z poprzednimi wersjami platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a0f37-112">Existing versions will continue to work, even in .NET 5.0 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="a0f37-113">Jednak nowe funkcje nie zostaną dodane do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a0f37-113">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="a0f37-114">Zamiast tego nowe funkcje zostaną dodane do innych bibliotek i interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a0f37-114">Instead, new functionality will be added to other libraries and APIs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a0f37-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a0f37-115">Version introduced</span></span>

<span data-ttu-id="a0f37-116">5,0 wersja zapoznawcza 6</span><span class="sxs-lookup"><span data-stu-id="a0f37-116">5.0 Preview 6</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a0f37-117">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a0f37-117">Recommended action</span></span>

- <span data-ttu-id="a0f37-118">Można nadal używać starszych wersji biblioteki, jeśli spełniają one wymagania.</span><span class="sxs-lookup"><span data-stu-id="a0f37-118">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="a0f37-119">Jeśli starsze wersje nie spełniają Twoich wymagań, Zastąp użycie `PlatformAbstractions` interfejsów API zalecanymi zamiennikami.</span><span class="sxs-lookup"><span data-stu-id="a0f37-119">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="a0f37-120">`PlatformAbstractions`INTERFEJSU API</span><span class="sxs-lookup"><span data-stu-id="a0f37-120">`PlatformAbstractions` API</span></span> | <span data-ttu-id="a0f37-121">Zalecane zastąpienie</span><span class="sxs-lookup"><span data-stu-id="a0f37-121">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="a0f37-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> i <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a0f37-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="a0f37-123">Większość przypadków użycia dla `RuntimeEnvironment.OperatingSystem` i służy `RuntimeEnvironment.OperatingSystemVersion` do wyświetlania, na przykład wyświetlania użytkownikowi, rejestrowania i telemetrii.</span><span class="sxs-lookup"><span data-stu-id="a0f37-123">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="a0f37-124">Nie zaleca się przeprowadzania decyzji w czasie wykonywania na podstawie wersji systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a0f37-124">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="a0f37-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType>teraz zwraca poprawną wersję dla systemów operacyjnych Windows i macOS.</span><span class="sxs-lookup"><span data-stu-id="a0f37-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now returns the correct version for Windows and macOS operating systems.</span></span> <span data-ttu-id="a0f37-126">Jednak w przypadku większości dystrybucji systemu UNIX, co jest uznawane za "wersję systemu operacyjnego", nie jest tak proste.</span><span class="sxs-lookup"><span data-stu-id="a0f37-126">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="a0f37-127">Może to być na przykład wersja jądra systemu Linux lub wersja dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="a0f37-127">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="a0f37-128">Dla większości platform systemu UNIX <xref:System.Environment.OSVersion?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> zwracają wersję zwracaną przez program `uname` .</span><span class="sxs-lookup"><span data-stu-id="a0f37-128">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="a0f37-129">Aby uzyskać informacje o nazwie i wersji systemu Linux, zalecane podejście polega na odczytaniu pliku */etc/OS-Release* .</span><span class="sxs-lookup"><span data-stu-id="a0f37-129">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

#### <a name="category"></a><span data-ttu-id="a0f37-130">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a0f37-130">Category</span></span>

<span data-ttu-id="a0f37-131">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="a0f37-131">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a0f37-132">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a0f37-132">Affected APIs</span></span>

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
