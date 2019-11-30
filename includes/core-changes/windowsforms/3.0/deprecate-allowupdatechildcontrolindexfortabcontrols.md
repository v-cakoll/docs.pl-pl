---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643999"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` jest obsługiwany w Windows Forms w .NET Framework 4,6 i nowszych wersjach, ale nie jest obsługiwany w Windows Forms począwszy od platformy .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4,6 i nowszych wersjach, wybranie karty zmienia kolejność kolekcji kontrolek. Przełącznik zgodności `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` pozwala aplikacji pominąć tę zmianę kolejności, jeśli to zachowanie jest niepożądane.

W programie .NET Core przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
