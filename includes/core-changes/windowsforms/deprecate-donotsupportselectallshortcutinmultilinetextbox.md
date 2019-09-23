---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181799"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="59122-101">Przełącznik. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="59122-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="59122-102">Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="59122-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="59122-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="59122-103">Change description</span></span>

<span data-ttu-id="59122-104">Rozpoczynając od .NET Framework 4.6.1, wybierając klawisz <kbd>Ctrl</kbd> +  <xref:System.Windows.Forms.TextBox> <kbd>a</kbd> skrótu w kontrolce zaznacz wszystkie teksty.</span><span class="sxs-lookup"><span data-stu-id="59122-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="59122-105">W .NET Framework 4,6 i poprzednich wersjach,<kbd>wybranie klawisza skrótu</kbd> <kbd>Ctrl</kbd> + nie zakończyło się niepowodzeniem, aby zaznaczyć cały tekst <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> , jeśli właściwość `true` [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i właściwości zostały ustawione na.</span><span class="sxs-lookup"><span data-stu-id="59122-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="59122-106">Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="59122-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="59122-107">Aby uzyskać więcej informacji <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="59122-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="59122-108">W przypadku `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` platformy .NET Core przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="59122-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59122-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="59122-109">Version introduced</span></span>

<span data-ttu-id="59122-110">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="59122-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59122-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="59122-111">Recommended action</span></span>

<span data-ttu-id="59122-112">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="59122-112">Remove the switch.</span></span> <span data-ttu-id="59122-113">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="59122-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="59122-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="59122-114">Category</span></span>

<span data-ttu-id="59122-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59122-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59122-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="59122-116">Affected APIs</span></span>

- <span data-ttu-id="59122-117">Brak</span><span class="sxs-lookup"><span data-stu-id="59122-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
