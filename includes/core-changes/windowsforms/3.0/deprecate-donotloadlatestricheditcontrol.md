---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937038"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl

Przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyImages`, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Opis zmiany

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
