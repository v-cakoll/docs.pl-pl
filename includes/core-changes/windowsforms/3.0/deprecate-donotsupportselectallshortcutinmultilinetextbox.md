---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643992"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Rozpoczynając od .NET Framework 4.6.1, wybierając pozycję <kbd>Ctrl</kbd> + <kbd>klawisz</kbd> skrótu w kontrolce <xref:System.Windows.Forms.TextBox> zaznacz opcję cały tekst. W .NET Framework 4,6 i poprzednich wersjach wybranie opcji <kbd>Ctrl</kbd> <kbd> + klawisza</kbd> skrótu nie powiodło się, aby zaznaczyć cały tekst, jeśli właściwości [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> były ustawione na `true`. Przełącznik zgodności `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

W programie .NET Core przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
