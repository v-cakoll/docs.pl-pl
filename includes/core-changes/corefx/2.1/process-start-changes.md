---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449408"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="004b3-101">Zmiana wartości domyślnej programu UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="004b3-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="004b3-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>ma domyślną `false` wartość na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="004b3-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="004b3-103">W platformie .NET Framework `true`jego wartością domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="004b3-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="004b3-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="004b3-104">Change description</span></span>

<span data-ttu-id="004b3-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>umożliwia bezpośrednie uruchomienie aplikacji, na przykład za `Process.Start("mspaint.exe")` pomocą kodu, takiego jak uruchamianie programu Paint.</span><span class="sxs-lookup"><span data-stu-id="004b3-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="004b3-106">Umożliwia również pośrednie uruchomienie skojarzonej aplikacji, jeśli <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="004b3-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="004b3-107">W programie .NET Framework <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> wartością domyślną `true`jest `Process.Start("mytextfile.txt")` , co oznacza, że kod taki jak uruchomi Notatnik, jeśli pliki *txt* zostały skojarzone z tym edytorem.</span><span class="sxs-lookup"><span data-stu-id="004b3-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="004b3-108">Aby zapobiec pośredniemu uruchamianiu aplikacji w platformie .NET Framework, należy jawnie ustawić <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="004b3-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="004b3-109">W uspolu .NET Core <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`wartością domyślną jest wartość .</span><span class="sxs-lookup"><span data-stu-id="004b3-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="004b3-110">Oznacza to, że domyślnie skojarzone aplikacje `Process.Start`nie są uruchamiane podczas nawiązywania połączenia .</span><span class="sxs-lookup"><span data-stu-id="004b3-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="004b3-111">Ta zmiana została wprowadzona w .NET Core ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="004b3-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="004b3-112">Zazwyczaj <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> służy do bezpośredniego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="004b3-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="004b3-113">Bezpośrednie uruchomienie aplikacji nie musi obejmować powłoki systemu Windows i ponoszenia skojarzonych kosztów wydajności.</span><span class="sxs-lookup"><span data-stu-id="004b3-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="004b3-114">Aby przyspieszyć tę domyślną obudowę, program <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> .NET Core zmienia wartość domyślną wartości na `false`.</span><span class="sxs-lookup"><span data-stu-id="004b3-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="004b3-115">Jeśli jej potrzebujesz, możesz wybrać się na wolniejszą ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="004b3-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="004b3-116">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="004b3-116">Version introduced</span></span>

<span data-ttu-id="004b3-117">2.1</span><span class="sxs-lookup"><span data-stu-id="004b3-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="004b3-118">We wcześniejszych wersjach programu `UseShellExecute` .NET Core nie został zaimplementowany dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="004b3-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="004b3-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="004b3-119">Recommended action</span></span>

<span data-ttu-id="004b3-120">Jeśli aplikacja opiera się na <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> stare <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> zachowanie, wywołać `true` z ustawionyna <xref:System.Diagnostics.ProcessStartInfo> na obiekcie.</span><span class="sxs-lookup"><span data-stu-id="004b3-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="004b3-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="004b3-121">Category</span></span>

<span data-ttu-id="004b3-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="004b3-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="004b3-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="004b3-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
