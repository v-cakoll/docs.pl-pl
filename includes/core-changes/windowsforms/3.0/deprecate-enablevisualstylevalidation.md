---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720941"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation

`Switch.System.Windows.Forms.EnableVisualStyleValidation`Przełącznik zgodności nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik zgodności zezwala aplikacji na rezygnację z walidacji stylów wizualnych dostarczonych w postaci liczbowej.

W przypadku platformy .NET Core `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik nie jest obsługiwany.

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
