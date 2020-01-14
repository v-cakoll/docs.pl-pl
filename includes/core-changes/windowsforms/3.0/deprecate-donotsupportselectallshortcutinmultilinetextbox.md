---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937028"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="e0746-101">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="e0746-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="e0746-102">Przełącznik zgodności `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0746-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e0746-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="e0746-103">Change description</span></span>

<span data-ttu-id="e0746-104">Rozpoczynając od .NET Framework 4.6.1, wybierając pozycję <kbd>Ctrl</kbd> + <kbd>klawisz</kbd> skrótu w kontrolce <xref:System.Windows.Forms.TextBox> zaznacz opcję cały tekst.</span><span class="sxs-lookup"><span data-stu-id="e0746-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="e0746-105">W .NET Framework 4,6 i poprzednich wersjach wybranie opcji <kbd>Ctrl</kbd> <kbd> + klawisza</kbd> skrótu nie powiodło się, aby zaznaczyć cały tekst, jeśli właściwości [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> były ustawione na `true`.</span><span class="sxs-lookup"><span data-stu-id="e0746-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="e0746-106">Przełącznik zgodności `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e0746-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="e0746-107">Aby uzyskać więcej informacji, zobacz temat <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0746-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e0746-108">W programie .NET Core przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="e0746-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e0746-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e0746-109">Version introduced</span></span>

<span data-ttu-id="e0746-110">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="e0746-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e0746-111">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="e0746-111">Recommended action</span></span>

<span data-ttu-id="e0746-112">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="e0746-112">Remove the switch.</span></span> <span data-ttu-id="e0746-113">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="e0746-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e0746-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="e0746-114">Category</span></span>

<span data-ttu-id="e0746-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0746-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e0746-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e0746-116">Affected APIs</span></span>

- <span data-ttu-id="e0746-117">Brak</span><span class="sxs-lookup"><span data-stu-id="e0746-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
