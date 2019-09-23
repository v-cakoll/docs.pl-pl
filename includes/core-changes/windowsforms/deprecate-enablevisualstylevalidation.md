---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181784"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. EnableVisualStyleValidation nie jest obsługiwany.

Przełącznik `Switch.System.Windows.Forms.EnableVisualStyleValidation` zgodności nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

W .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik zgodności zezwala aplikacji na rezygnację z walidacji stylów wizualnych dostarczonych w postaci liczbowej. 

W przypadku `Switch.System.Windows.Forms.EnableVisualStyleValidation` platformy .NET Core przełącznik nie jest obsługiwany.

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
