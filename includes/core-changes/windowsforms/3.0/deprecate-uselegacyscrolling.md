---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937085"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Przełącznik zgodności DomainUpDown.UseLegacyScrolling nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` zgodności, który został wprowadzony w programie .NET Framework 4.7.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.7.1, przełącznik `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` zgodności pozwolił <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> deweloperom zrezygnować z niezależnych i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji. Przełącznik przywrócił starsze zachowanie, w <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> którym jest ignorowany, jeśli tekst kontekstu jest <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> obecny, a deweloper <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> jest wymagany do użycia akcji w forsce przed akcją. Aby uzyskać więcej informacji, zobacz [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

W .NET Core `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

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
