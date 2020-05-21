---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721179"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="db29c-101">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="db29c-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="db29c-102">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Przełącznik zgodności, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="db29c-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="db29c-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="db29c-103">Change description</span></span>

<span data-ttu-id="db29c-104">Rozpoczynając od .NET Framework 4.6.1, wybierając klawisz <kbd>Ctrl</kbd>  +  <kbd>a</kbd> skrótu w <xref:System.Windows.Forms.TextBox> kontrolce zaznacz wszystkie teksty.</span><span class="sxs-lookup"><span data-stu-id="db29c-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="db29c-105">W .NET Framework 4,6 i poprzednich wersjach, wybranie <kbd>Ctrl</kbd>  +  <kbd>A</kbd> klawisza skrótu Ctrl nie zakończyło się niepowodzeniem, aby zaznaczyć cały tekst, jeśli właściwość [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> właściwości zostały ustawione na `true` .</span><span class="sxs-lookup"><span data-stu-id="db29c-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="db29c-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Przełącznik zgodności został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="db29c-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="db29c-107">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db29c-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="db29c-108">W przypadku platformy .NET Core `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="db29c-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="db29c-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="db29c-109">Version introduced</span></span>

<span data-ttu-id="db29c-110">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="db29c-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="db29c-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="db29c-111">Recommended action</span></span>

<span data-ttu-id="db29c-112">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="db29c-112">Remove the switch.</span></span> <span data-ttu-id="db29c-113">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="db29c-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="db29c-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="db29c-114">Category</span></span>

<span data-ttu-id="db29c-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db29c-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="db29c-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="db29c-116">Affected APIs</span></span>

- <span data-ttu-id="db29c-117">Brak</span><span class="sxs-lookup"><span data-stu-id="db29c-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
