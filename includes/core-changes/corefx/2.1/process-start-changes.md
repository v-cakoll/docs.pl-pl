---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021808"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="2bd6c-101">Zmiana wartości domyślnej UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="2bd6c-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="2bd6c-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>ma wartość domyślną `false` na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="2bd6c-103">W programie .NET Framework `true`jego wartością domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="2bd6c-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2bd6c-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="2bd6c-104">Change description</span></span>

<span data-ttu-id="2bd6c-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>umożliwia uruchomienie aplikacji bezpośrednio, na przykład z `Process.Start("mspaint.exe")` kodem takim jak uruchamia paint.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="2bd6c-106">Umożliwia również pośrednie uruchomienie skojarzonej <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> aplikacji, `true`jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="2bd6c-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="2bd6c-107">W programie .NET Framework <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> domyślną wartością `true`jest `Process.Start("mytextfile.txt")` , co oznacza, że kod, taki jak uruchomienie Notatnika, jeśli skojarzono pliki *.txt* z tym edytorem.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="2bd6c-108">Aby zapobiec pośredniemu uruchamianiu aplikacji w programie .NET `false`Framework, należy jawnie ustawić wartość <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2bd6c-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="2bd6c-109">W programie .NET Core <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> wartością domyślną jest `false`.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="2bd6c-110">Oznacza to, że domyślnie skojarzone aplikacje `Process.Start`nie są uruchamiane podczas wywoływania .</span><span class="sxs-lookup"><span data-stu-id="2bd6c-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="2bd6c-111">Ta zmiana została wprowadzona w .NET Core ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="2bd6c-112">Zazwyczaj <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> jest używany do uruchamiania aplikacji bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="2bd6c-113">Bezpośrednie uruchamianie aplikacji nie musi obejmować powłoki systemu Windows i ponosić skojarzony koszt wydajności.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="2bd6c-114">Aby przyspieszyć ten domyślny przypadek, program .NET Core zmienia domyślną wartość <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="2bd6c-115">Jeśli jej potrzebujesz, możesz zdecydować się na wolniejszą ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2bd6c-116">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="2bd6c-116">Version introduced</span></span>

<span data-ttu-id="2bd6c-117">2.1</span><span class="sxs-lookup"><span data-stu-id="2bd6c-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="2bd6c-118">We wcześniejszych wersjach programu `UseShellExecute` .NET Core nie został zaimplementowany dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2bd6c-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2bd6c-119">Recommended action</span></span>

<span data-ttu-id="2bd6c-120">Jeśli aplikacja opiera się na <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> stare <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> zachowanie, <xref:System.Diagnostics.ProcessStartInfo> wywołać z ustawioną `true` na obiekt.</span><span class="sxs-lookup"><span data-stu-id="2bd6c-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="2bd6c-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="2bd6c-121">Category</span></span>

<span data-ttu-id="2bd6c-122">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="2bd6c-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2bd6c-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2bd6c-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
