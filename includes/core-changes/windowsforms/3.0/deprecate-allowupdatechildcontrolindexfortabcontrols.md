---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937112"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls

Przełącznik zgodności `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` jest obsługiwany w Windows Forms w .NET Framework 4,6 i nowszych wersjach, ale nie jest obsługiwany w Windows Forms począwszy od platformy .NET Core 3,0.

#### <a name="change-description"></a>Opis zmiany

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
