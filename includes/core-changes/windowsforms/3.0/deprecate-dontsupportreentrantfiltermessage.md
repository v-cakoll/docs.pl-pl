---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937032"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` zgodności, który został wprowadzony w programie .NET Framework 4.6.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.6.1, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` przełącznik <xref:System.IndexOutOfRangeException> zgodności adresy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> możliwych wyjątków, gdy komunikat jest wywoływana z implementacji niestandardowej. <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> Aby uzyskać więcej informacji, zobacz [Łagodzenia: Niestandardowe implementacje IMessageFilter.PreFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

W .NET Core `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
