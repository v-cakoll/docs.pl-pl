---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181749"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. DontSupportReentrantFilterMessage nie jest obsługiwany.

Przełącznik `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` zgodności, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.6.1, przełącznik zgodności `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` rozwiązuje możliwe <xref:System.IndexOutOfRangeException> wyjątki, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> komunikat jest wywoływany z implementacją niestandardową <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> . Aby uzyskać więcej informacji, [Zobacz Ograniczanie: Niestandardowe implementacje](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)IMessageFilter. PreFilterMessage.

W przypadku `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` platformy .NET Core przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
