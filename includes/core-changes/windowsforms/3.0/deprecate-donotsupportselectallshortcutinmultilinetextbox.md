---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937028"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności, który został wprowadzony w programie .NET Framework 4.6.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

Zaczynając od .NET Framework 4.6.1, wybierając klawisz skrótu <kbd>Ctrl</kbd> + <kbd>A</kbd> w formantie <xref:System.Windows.Forms.TextBox> zaznaczono cały tekst. W .NET Framework 4.6 i poprzednich wersjach wybranie klawisza skrótu <kbd>Ctrl</kbd> + <kbd>A</kbd> nie może zaznaczyć całego tekstu, jeśli [pole tekstowe.SkrótyWłączone](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> właściwości zostały ustawione na `true`. Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

W .NET Core `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
