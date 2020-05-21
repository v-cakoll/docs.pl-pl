---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721656"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl

`Switch.System.Windows.Forms.UseLegacyImages`Przełącznik zgodności, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4.6.2 i poprzednich wersjach <xref:System.Windows.Forms.RichTextBox> kontrolka spowoduje utworzenie wystąpienia programu Win32 RichEdit Control v 3.0 i dla aplikacji, które są przeznaczone dla .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> kontrolka spowoduje utworzenie wystąpienia elementu RichEdit v 4.1 (w *msftedit. dll*). `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Wprowadzono przełącznik zgodności, aby umożliwić aplikacjom, które są przeznaczone .NET Framework 4.7.1 i nowsze wersje, aby zrezygnować z nowej kontrolki RichEdit v 4.1 i zamiast tego używać starego formantu RichEdit v3.

W przypadku platformy .NET Core `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` przełącznik nie jest obsługiwany. Obsługiwane są tylko nowe wersje <xref:System.Windows.Forms.RichTextBox> formantu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
