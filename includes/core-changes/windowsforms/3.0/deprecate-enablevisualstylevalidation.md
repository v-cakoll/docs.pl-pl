---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937119"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation

Przełącznik zgodności `Switch.System.Windows.Forms.EnableVisualStyleValidation` nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Opis zmiany

W .NET Framework przełącznik zgodności `Switch.System.Windows.Forms.EnableVisualStyleValidation` zezwolił aplikacji na rezygnację z walidacji stylów wizualnych dostarczonych w postaci liczbowej.

W programie .NET Core przełącznik `Switch.System.Windows.Forms.EnableVisualStyleValidation` nie jest obsługiwany.

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
