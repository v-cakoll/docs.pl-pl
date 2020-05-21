---
ms.openlocfilehash: e1c55eab0b968daab7322350e201b49149e63215
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721254"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Przełącznik zgodności jest obsługiwany w Windows Forms na .NET Framework 4,6 i nowszych wersjach, ale nie jest obsługiwany w Windows Forms począwszy od platformy .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4,6 i nowszych wersjach, wybranie karty zmienia kolejność kolekcji kontrolek. `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Przełącznik zgodności pozwala aplikacji pominąć tę zmianę kolejności, jeśli to zachowanie jest niepożądane.

W przypadku platformy .NET Core `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
