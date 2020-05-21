---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721179"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox

`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Przełącznik zgodności, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Rozpoczynając od .NET Framework 4.6.1, wybierając klawisz <kbd>Ctrl</kbd>  +  <kbd>a</kbd> skrótu w <xref:System.Windows.Forms.TextBox> kontrolce zaznacz wszystkie teksty. W .NET Framework 4,6 i poprzednich wersjach, wybranie <kbd>Ctrl</kbd>  +  <kbd>A</kbd> klawisza skrótu Ctrl nie zakończyło się niepowodzeniem, aby zaznaczyć cały tekst, jeśli właściwość [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> właściwości zostały ustawione na `true` . `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Przełącznik zgodności został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

W przypadku platformy .NET Core `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
