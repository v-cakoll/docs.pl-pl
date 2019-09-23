---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181799"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany.

Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Rozpoczynając od .NET Framework 4.6.1, wybierając klawisz <kbd>Ctrl</kbd> +  <xref:System.Windows.Forms.TextBox> <kbd>a</kbd> skrótu w kontrolce zaznacz wszystkie teksty. W .NET Framework 4,6 i poprzednich wersjach,<kbd>wybranie klawisza skrótu</kbd> <kbd>Ctrl</kbd> + nie zakończyło się niepowodzeniem, aby zaznaczyć cały tekst <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> , jeśli właściwość `true` [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) i właściwości zostały ustawione na. Przełącznik `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` zgodności został wprowadzony w .NET Framework 4.6.1, aby zachować oryginalne zachowanie. Aby uzyskać więcej informacji <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>, zobacz.

W przypadku `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` platformy .NET Core przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
