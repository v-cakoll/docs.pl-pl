---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937038"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności, który został wprowadzony w programie .NET Framework 4.7.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4.6.2 i <xref:System.Windows.Forms.RichTextBox> poprzednich wersjach formant będzie utworzyć wystąpienia w usytuanym win32 RichEdit kontroli v3.0 i dla aplikacji, które są przeznaczone do .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> formant będzie wystąpienia RichEdit v4.1 (w *msftedit.dll*). Przełącznik `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` zgodności został wprowadzony, aby umożliwić aplikacjom docelowym .NET Framework 4.7.1 i nowszym wersjom rezygnację z nowego formantu RichEdit v4.1 i zamiast tego użyj starego formantu RichEdit v3.

W .NET Core `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` przełącznik nie jest obsługiwany. Obsługiwane są tylko <xref:System.Windows.Forms.RichTextBox> nowe wersje formantu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
