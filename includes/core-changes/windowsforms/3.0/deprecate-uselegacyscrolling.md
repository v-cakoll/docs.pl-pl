---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937085"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany

Przełącznik zgodności `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Opis zmiany

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
