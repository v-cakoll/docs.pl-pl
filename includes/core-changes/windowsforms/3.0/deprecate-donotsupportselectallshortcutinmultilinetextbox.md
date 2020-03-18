---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937028"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="972e9-101">Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="972e9-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="972e9-102">Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności, który został wprowadzony w programie .NET Framework 4.6.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="972e9-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="972e9-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="972e9-103">Change description</span></span>

<span data-ttu-id="972e9-104">Zaczynając od .NET Framework 4.6.1, wybierając klawisz skrótu <kbd>Ctrl</kbd> + <kbd>A</kbd> w formantie <xref:System.Windows.Forms.TextBox> zaznaczono cały tekst.</span><span class="sxs-lookup"><span data-stu-id="972e9-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="972e9-105">W .NET Framework 4.6 i poprzednich wersjach wybranie klawisza skrótu <kbd>Ctrl</kbd> + <kbd>A</kbd> nie może zaznaczyć całego tekstu, jeśli [pole tekstowe.SkrótyWłączone](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> właściwości zostały ustawione na `true`.</span><span class="sxs-lookup"><span data-stu-id="972e9-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="972e9-106">Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="972e9-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="972e9-107">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="972e9-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="972e9-108">W .NET Core `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="972e9-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="972e9-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="972e9-109">Version introduced</span></span>

<span data-ttu-id="972e9-110">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="972e9-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="972e9-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="972e9-111">Recommended action</span></span>

<span data-ttu-id="972e9-112">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="972e9-112">Remove the switch.</span></span> <span data-ttu-id="972e9-113">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="972e9-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="972e9-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="972e9-114">Category</span></span>

<span data-ttu-id="972e9-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="972e9-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="972e9-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="972e9-116">Affected APIs</span></span>

- <span data-ttu-id="972e9-117">Brak</span><span class="sxs-lookup"><span data-stu-id="972e9-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
