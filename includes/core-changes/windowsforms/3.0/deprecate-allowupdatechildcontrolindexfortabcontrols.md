---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937112"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Przełącznik zgodności AllowUpdateChildControlForTabControl nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` zgodności jest obsługiwany w formularzach systemu Windows w wersji .NET Framework 4.6 i nowszej, ale nie jest obsługiwany w formularzach systemu Windows, począwszy od .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework 4.6 i nowszych wersjach wybranie karty zmienia kolejność swojej kolekcji formantów. Przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` zgodności umożliwia aplikacji pominąć to ponowne zamawianie, gdy to zachowanie jest niepożądane.

W .NET Core `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
