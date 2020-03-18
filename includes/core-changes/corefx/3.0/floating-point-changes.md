---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568166"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="d5d28-101">Zmieniono zachowanie formatowania i analizowania zmiennoprzecinkowego</span><span class="sxs-lookup"><span data-stu-id="d5d28-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="d5d28-102">Przeanalizowanie i formatowanie zmiennoprzecinkowych (według <xref:System.Double> typów) <xref:System.Single> są teraz zgodne ze standardem IEEE.</span><span class="sxs-lookup"><span data-stu-id="d5d28-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d5d28-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d5d28-103">Change description</span></span>

<span data-ttu-id="d5d28-104">W .NET Core 2.2 i wcześniejszych <xref:System.Double.ToString%2A?displayProperty=nameWithType> wersjach formatowanie <xref:System.Single.ToString%2A?displayProperty=nameWithType>i <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>analizowanie z , , , <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nie są zgodne ze specyfikacją IEEE.</span><span class="sxs-lookup"><span data-stu-id="d5d28-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="d5d28-105">W rezultacie nie można zagwarantować, że wartość będzie roundtrip z dowolnego obsługiwanego standardowego lub niestandardowego ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="d5d28-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="d5d28-106">W przypadku niektórych danych wejściowych próba przeanalizowania sformatowanej wartości może zakończyć się niepowodzeniem, a dla innych wartość przeanalizowana nie jest równa wartości oryginalnej.</span><span class="sxs-lookup"><span data-stu-id="d5d28-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="d5d28-107">Począwszy od .NET Core 3.0, operacje analizy i formatowania są zgodne ze standardem IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="d5d28-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="d5d28-108">Gwarantuje to, że zachowanie typów zmiennoprzecinkowych w .NET jest zgodne z zachowaniem języków zgodnych ze specyfikacją IEEE, takich jak C#.</span><span class="sxs-lookup"><span data-stu-id="d5d28-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="d5d28-109">Aby uzyskać więcej informacji, zobacz [ulepszenia analizy i formatowania zmiennoprzecinkowych w blogu .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)</span><span class="sxs-lookup"><span data-stu-id="d5d28-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d5d28-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d5d28-110">Version introduced</span></span>

<span data-ttu-id="d5d28-111">3.0</span><span class="sxs-lookup"><span data-stu-id="d5d28-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d5d28-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d5d28-112">Recommended action</span></span>

<span data-ttu-id="d5d28-113">Sekcja "Potencjalny wpływ na istniejący kod" [ulepszeń analizy i formatowania zmiennoprzecinkowego w blogu .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugeruje zmiany w kodzie, jeśli obserwujesz zmianę zachowania w porównaniu z aplikacjami .NET Core 2.2 Ogólnie, wiąże się to z użyciem innego standardowego lub niestandardowego ciągu formatu w celu wymuszenia żądanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="d5d28-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="d5d28-114">Niektóre wyniki mogą nie mieć obejścia, jeśli były wcześniej niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="d5d28-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="d5d28-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d5d28-115">Category</span></span>

<span data-ttu-id="d5d28-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="d5d28-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d5d28-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d5d28-117">Affected APIs</span></span>

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
