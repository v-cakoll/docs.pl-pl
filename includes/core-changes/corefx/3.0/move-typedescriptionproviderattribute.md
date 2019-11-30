---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568170"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute przeniesiony do innego zestawu

Klasa <xref:System.ComponentModel.TypeDescriptionProviderAttribute> została przeniesiona.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach Klasa <xref:System.ComponentModel.TypeDescriptionProviderAttribute> została znaleziona w zestawie *System. ComponentModel. TypeConverter* .

Począwszy od platformy .NET Core 3,0, znajduje się on w zestawie *System. ObjectModel* .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Ta zmiana dotyczy tylko aplikacji, które używają odbicia do ładowania typu <xref:System.ComponentModel.TypeDescriptionProviderAttribute> przez wywołanie metody, takiej jak <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub Przeciążenie <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, który zakłada, że typ znajduje się w określonym zestawie. W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!--

### Affected APIs

- Not detectable via API analysis

-->
