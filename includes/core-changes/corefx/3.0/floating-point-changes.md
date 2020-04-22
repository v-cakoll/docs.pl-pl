---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021592"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="02f84-101">Zmieniono formatowanie zmiennoprzecinowe i analizowanie</span><span class="sxs-lookup"><span data-stu-id="02f84-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="02f84-102">Zmiennoprzecinające się parsowanie <xref:System.Double> i <xref:System.Single> formatowanie zachowanie (przez i typów) są teraz zgodne ze standardem IEEE.</span><span class="sxs-lookup"><span data-stu-id="02f84-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="02f84-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="02f84-103">Change description</span></span>

<span data-ttu-id="02f84-104">W .NET Core 2.2 i wcześniejszych <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType>wersjach formatowanie <xref:System.Double.Parse%2A?displayProperty=nameWithType>z <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> , i analizowanie z , , i nie są zgodne ze standardem IEEE.</span><span class="sxs-lookup"><span data-stu-id="02f84-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="02f84-105">W rezultacie nie można zagwarantować, że wartość będzie w obie strony z dowolnym obsługiwanym ciągiem w formacie standardowym lub niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="02f84-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="02f84-106">W przypadku niektórych danych wejściowych próba przeanalizowania sformatowanej wartości może zakończyć się niepowodzeniem, a w przypadku innych wartość analizowana nie jest równa wartości oryginalnej.</span><span class="sxs-lookup"><span data-stu-id="02f84-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="02f84-107">Począwszy od platformy .NET Core 3.0, operacje analizowania i formatowania są zgodne ze standardem IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="02f84-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="02f84-108">Gwarantuje to, że zachowanie typów zmiennoprzecinkowych w .NET odpowiada językom zgodnym z IEEE, takim jak C#.</span><span class="sxs-lookup"><span data-stu-id="02f84-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="02f84-109">Aby uzyskać więcej informacji, zobacz [zmiennoprzecinające analizy i formatowanie ulepszenia w programie .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) wpis w blogu.</span><span class="sxs-lookup"><span data-stu-id="02f84-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="02f84-110">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="02f84-110">Version introduced</span></span>

<span data-ttu-id="02f84-111">3.0</span><span class="sxs-lookup"><span data-stu-id="02f84-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="02f84-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="02f84-112">Recommended action</span></span>

<span data-ttu-id="02f84-113">Sekcja "Potencjalny wpływ na istniejący kod" w sekcji [Analizowanie zmiennoprzecinkowe i formatowanie ulepszeń w blogu .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugeruje zmiany w kodzie, jeśli zauważysz zmianę zachowania w porównaniu do aplikacji .NET Core 2.2 Ogólnie rzecz biorąc, wiąże się to z użyciem innego ciągu standardowego lub niestandardowego formatu w celu wymuszenia żądanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="02f84-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="02f84-114">Niektóre wyniki mogą nie mieć obejścia, jeśli były wcześniej niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="02f84-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="02f84-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="02f84-115">Category</span></span>

<span data-ttu-id="02f84-116">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="02f84-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="02f84-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="02f84-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
