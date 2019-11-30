---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568079"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException — przeniesiony do innego zestawu

Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została przeniesiona.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została znaleziona w zestawie *System. ComponentModel. TypeConverter* .

Począwszy od platformy .NET Core 3,0, znajduje się on w zestawie *System. ComponentModel. prymityws* .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Ta zmiana dotyczy tylko aplikacji, które używają odbicia w celu załadowania <xref:System.ComponentModel.InvalidAsynchronousStateException> przez wywołanie metody, takiej jak <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub Przeciążenie <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, który zakłada, że typ znajduje się w określonym zestawie. W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!--

### Affected APIs

- Not detectable via API analysis

-->
