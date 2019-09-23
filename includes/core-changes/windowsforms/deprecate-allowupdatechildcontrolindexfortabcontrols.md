---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181715"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls nie jest obsługiwany.

Przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` zgodności jest obsługiwany w Windows Forms na .NET Framework 4,6 i nowszych wersjach, ale nie jest obsługiwany w Windows Forms począwszy od platformy .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4,6 i nowszych wersjach, wybranie karty zmienia kolejność kolekcji kontrolek. Przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` zgodności pozwala aplikacji pominąć tę zmianę kolejności, jeśli to zachowanie jest niepożądane.

W przypadku `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` platformy .NET Core przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
