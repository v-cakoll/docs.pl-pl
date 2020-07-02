---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614880"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>Właściwość ContextMenuStrip. SourceControl zawiera prawidłową kontrolkę w przypadku zagnieżdżonych kontrolki ToolStripMenuItems

#### <a name="details"></a>Szczegóły

W .NET Framework 4.7.1 i poprzednich wersjach <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> Właściwość nieprawidłowo zwraca wartość null, jeśli użytkownik otworzy menu z formantów zagnieżdżonych <xref:System.Windows.Forms.ToolStripMenuItem> . W .NET Framework 4.7.2 i nowszych <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> Właściwość jest zawsze ustawiana na rzeczywistą kontrolę źródła.

#### <a name="suggestion"></a>Sugestia

**Jak wybrać lub wycofać te zmiany** Aby aplikacja mogła korzystać z tych zmian, musi ona działać na .NET Framework 4.7.2 lub nowszym. Aplikacja może korzystać z tych zmian w jeden z następujących sposobów:

- Jest ona przeznaczona dla .NET Framework 4.7.2. Ta zmiana jest domyślnie włączona w Windows Forms aplikacjach przeznaczonych dla .NET Framework 4.7.2 lub nowszych.
- Jest ona przeznaczona dla .NET Framework 4.7.1 lub wcześniejszej wersji i [wyłączają](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) się ze starszych zachowań ułatwień dostępu, dodając następujący `<runtime>` przykład AppContext do sekcji pliku app.config i ustawiając go na `false` , jak pokazano w poniższym przykładzie.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

Aplikacje ukierunkowane na .NET Framework 4.7.2 lub nowsze i chcą zachować starsze zachowanie mogą zrezygnować z używania wartości kontroli źródła starszej przez jawne ustawienie tego przełącznika AppContext na `true` .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
