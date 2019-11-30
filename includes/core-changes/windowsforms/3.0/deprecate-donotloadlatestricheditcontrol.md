---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643985"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. DoNotLoadLatestRichEditControl nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyImages`, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4.6.2 i poprzednich wersjach kontrolka <xref:System.Windows.Forms.RichTextBox> może utworzyć wystąpienie dla systemu Win32 RichEdit Control v 3.0 i dla aplikacji, które są przeznaczone dla .NET Framework 4.7.1, formant <xref:System.Windows.Forms.RichTextBox> będzie tworzyć wystąpienie RichEdit v 4.1 (w *msftedit. dll*). Wprowadzono przełącznik zgodności `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`, aby umożliwić aplikacjom, które są przeznaczone .NET Framework 4.7.1 i nowsze wersje, aby zrezygnować z nowej kontrolki RichEdit v 4.1 i zamiast tego użyć starego formantu RichEdit v3.

W programie .NET Core przełącznik `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` nie jest obsługiwany. Obsługiwane są tylko nowe wersje kontrolki <xref:System.Windows.Forms.RichTextBox>.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
