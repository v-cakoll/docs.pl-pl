---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644020"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, który został wprowadzony w .NET Framework 4.7.2, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.7.2, przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` pozwala deweloperowi zrezygnować z nowego zachowania właściwości <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, która teraz zwraca odwołanie do kontroli źródła. Poprzednie zachowanie właściwości miało zwrócić `null`. Aby uzyskać więcej informacji, zobacz [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

W programie .NET Core przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
