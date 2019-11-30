---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643971"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.7.1, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` przełączenia zgodności zezwala deweloperom na rezygnację z niezależnych <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji. Przełącznik przywrócił starsze zachowanie, w którym <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> jest ignorowany, jeśli jest obecny tekst kontekstu, a deweloper jest zobowiązany do użycia akcji <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> na formancie przed akcją <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

W programie .NET Core przełącznik `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
