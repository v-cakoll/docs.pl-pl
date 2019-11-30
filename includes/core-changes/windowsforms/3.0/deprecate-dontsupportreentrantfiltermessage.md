---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644006"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. DontSupportReentrantFilterMessage nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.6.1, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` <xref:System.IndexOutOfRangeException> wyjątki, gdy komunikat <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> jest wywoływany przy użyciu niestandardowej implementacji <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z niestandardowymi implementacjami IMessageFilter. PreFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

W programie .NET Core przełącznik `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
