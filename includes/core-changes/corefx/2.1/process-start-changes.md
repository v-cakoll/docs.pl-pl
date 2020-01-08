---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344879"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="f7795-101">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="f7795-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="f7795-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> ma wartość domyślną `false` na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f7795-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="f7795-103">Na .NET Framework wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="f7795-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f7795-104">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="f7795-104">Change description</span></span>

<span data-ttu-id="f7795-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> umożliwia bezpośrednie uruchamianie aplikacji, na przykład przy użyciu kodu, takiego jak `Process.Start("mspaint.exe")`, który uruchamia program Paint.</span><span class="sxs-lookup"><span data-stu-id="f7795-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="f7795-106">Umożliwia ona również pośrednio uruchomienie skojarzonej aplikacji, jeśli <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="f7795-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="f7795-107">Na .NET Framework wartość domyślna <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jest `true`, co oznacza, że kod taki jak `Process.Start("mytextfile.txt")` zostałby uruchomiony Notatnik, jeśli masz skojarzone pliki *txt* z tym edytorem.</span><span class="sxs-lookup"><span data-stu-id="f7795-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="f7795-108">Aby zapobiec pośredniemu uruchamianiu aplikacji na .NET Framework, musisz jawnie ustawić <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> do `false`.</span><span class="sxs-lookup"><span data-stu-id="f7795-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="f7795-109">W przypadku platformy .NET Core wartość domyślna dla <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="f7795-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="f7795-110">Oznacza to, że domyślnie skojarzone aplikacje nie są uruchamiane podczas wywoływania `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="f7795-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="f7795-111">Ta zmiana została wprowadzona w programie .NET Core ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f7795-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="f7795-112">Zazwyczaj <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> jest używany do bezpośredniego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7795-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="f7795-113">Bezpośrednie uruchamianie aplikacji nie wymaga ponoszenia powłoki systemu Windows i wiąże się z powiązanymi kosztami wydajności.</span><span class="sxs-lookup"><span data-stu-id="f7795-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="f7795-114">Aby ten przypadek domyślny był szybszy, program .NET Core zmieni wartość domyślną <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="f7795-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="f7795-115">Jeśli potrzebujesz, możesz zrezygnować z wolniejszej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f7795-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f7795-116">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f7795-116">Version introduced</span></span>

<span data-ttu-id="f7795-117">2.1</span><span class="sxs-lookup"><span data-stu-id="f7795-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="f7795-118">We wcześniejszych wersjach programu .NET Core `UseShellExecute` nie została zaimplementowana dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f7795-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f7795-119">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="f7795-119">Recommended action</span></span>

<span data-ttu-id="f7795-120">Jeśli aplikacja korzysta ze starego zachowania, wywołaj <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> z <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> ustawionym na `true` na obiekcie <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="f7795-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="f7795-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f7795-121">Category</span></span>

<span data-ttu-id="f7795-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f7795-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7795-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f7795-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
