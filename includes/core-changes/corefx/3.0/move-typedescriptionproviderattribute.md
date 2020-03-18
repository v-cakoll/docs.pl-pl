---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147539"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>Atrybut TypeDescriptionProviderAttribute przeniesiony do innego zestawu

Klasa <xref:System.ComponentModel.TypeDescriptionProviderAttribute> została przeniesiona.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i <xref:System.ComponentModel.TypeDescriptionProviderAttribute> wcześniejszych wersjach Klasa znajduje się w assembly *System.ComponentModel.TypeConverter.*

Począwszy od .NET Core 3.0, znajduje się w zestawie *System.ObjectModel.*

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana dotyczy tylko aplikacji, które <xref:System.ComponentModel.TypeDescriptionProviderAttribute> używają odbicia do <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ładowania typu przez <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> wywołanie metody, takich jak lub przeciążenie, które zakłada, że typ znajduje się w określonym zestawie. W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu typu.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak.

<!--

### Affected APIs

- Not detectable via API analysis

-->
