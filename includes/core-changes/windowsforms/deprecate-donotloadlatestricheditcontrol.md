---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181805"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. DoNotLoadLatestRichEditControl nie jest obsługiwany.

Przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4.6.2 i poprzednich wersjach <xref:System.Windows.Forms.RichTextBox> kontrolka spowoduje utworzenie wystąpienia programu Win32 RichEdit Control v 3.0 i dla aplikacji, które są przeznaczone dla .NET Framework 4.7.1 <xref:System.Windows.Forms.RichTextBox> , kontrolka spowoduje utworzenie wystąpienia elementu RichEdit v 4.1 (w  *msftedit. dll*). Wprowadzono `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` przełącznik zgodności, aby umożliwić aplikacjom, które są przeznaczone .NET Framework 4.7.1 i nowsze wersje, aby zrezygnować z nowej kontrolki RichEdit v 4.1 i zamiast tego używać starego formantu RichEdit v3.

W przypadku `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` platformy .NET Core przełącznik nie jest obsługiwany. Obsługiwane są tylko nowe wersje <xref:System.Windows.Forms.RichTextBox> formantu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
