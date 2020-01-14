---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937028"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox

Przełącznik zgodności `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Opis zmiany

Rozpoczynając od .NET Framework 4.6.1, wybierając pozycję <kbd>Ctrl</kbd> + <kbd>klawisz</kbd> skrótu w kontrolce <xref:System.Windows.Forms.TextBox> zaznacz opcję cały tekst. W .NET Framework 4,6 i poprzednich wersjach wybranie opcji <kbd>Ctrl</kbd> <kbd> + klawisza</kbd> skrótu nie powiodło się, aby zaznaczyć cały tekst, jeśli właściwości [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> były ustawione na `true`. Przełącznik zgodności `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie. Aby uzyskać więcej informacji, zobacz temat <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

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
