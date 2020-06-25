---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365658"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="9d7ce-101">Wbudowana obsługa środowiska WinRT jest usuwana z platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9d7ce-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="9d7ce-102">Wbudowana obsługa użycia interfejsów API [środowiska wykonawczego systemu Windows](/uwp/winrt-cref/winrt-type-system) w programie .NET jest usuwana.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9d7ce-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9d7ce-103">Version introduced</span></span>

<span data-ttu-id="9d7ce-104">5,0 wersja zapoznawcza 6</span><span class="sxs-lookup"><span data-stu-id="9d7ce-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="9d7ce-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="9d7ce-105">Change description</span></span>

<span data-ttu-id="9d7ce-106">Wcześniej CoreCLR może zużywać [pliki metadanych systemu Windows (WinMD)](/uwp/winrt-cref/winmd-files) do aktywnych i korzystać z typów WinRT.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="9d7ce-107">Począwszy od platformy .NET 5,0, CoreCLR nie może już bezpośrednio korzystać z plików WinMD.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="9d7ce-108">Jeśli próbujesz odwołać się do nieobsługiwanego zestawu, uzyskasz <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="9d7ce-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="9d7ce-109">W przypadku aktywowania klasy WinRT uzyskasz <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="9d7ce-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="9d7ce-110">Ta nieprzerwana zmiana została wprowadzona z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="9d7ce-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="9d7ce-111">Dlatego WinRT można opracowywać i ulepszyć niezależnie od środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="9d7ce-112">Dla symetrii z systemami międzyoperacyjnymi udostępnianymi dla innych systemów operacyjnych, takich jak iOS i Android.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="9d7ce-113">W celu skorzystania z innych funkcji platformy .NET, takich jak funkcje języka C#, konsolidacja w języku pośrednim (IL) i kompilacja przed czasem (AOT).</span><span class="sxs-lookup"><span data-stu-id="9d7ce-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="9d7ce-114">Aby uprościć bazę kodu środowiska uruchomieniowego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9d7ce-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9d7ce-115">Recommended action</span></span>

- <span data-ttu-id="9d7ce-116">Usuń odwołania do [pakietu Microsoft. Windows. Sdk.](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) Contracts i zastąp je odwołaniami do [pakietu Microsoft.Windows.Sdk.NET](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span><span class="sxs-lookup"><span data-stu-id="9d7ce-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) and replace them with references to the [Microsoft.Windows.SDK.NET package](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span></span>

- <span data-ttu-id="9d7ce-117">Za pomocą łańcucha narzędzi [/WinRT języka C#](/windows/uwp/csharp-winrt/) można generować lub dostosowywać interfejsy API i typy środowiska WinRT w programie .NET 5,0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="9d7ce-117">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types in .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="9d7ce-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9d7ce-118">Category</span></span>

<span data-ttu-id="9d7ce-119">Interop</span><span class="sxs-lookup"><span data-stu-id="9d7ce-119">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9d7ce-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9d7ce-120">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
