---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937022"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>UseLegacyContextMenuStripSourceControlValue przełącznik zgodności nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` zgodności, który został wprowadzony w programie .NET Framework 4.7.2, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.7.2, przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` zgodności umożliwia deweloperowi zrezygnować z nowego zachowania <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> właściwości, która teraz zwraca odwołanie do kontroli źródła. Poprzednie zachowanie właściwości było powrót `null`. Aby uzyskać więcej informacji, zobacz [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

W .NET Core `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
