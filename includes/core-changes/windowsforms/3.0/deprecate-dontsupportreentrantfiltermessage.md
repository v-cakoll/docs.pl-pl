---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937032"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage

Przełącznik zgodności `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Opis zmiany

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
