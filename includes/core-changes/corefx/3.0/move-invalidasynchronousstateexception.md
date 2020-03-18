---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147552"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException przeniesiony do innego zestawu

Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została przeniesiona.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i <xref:System.ComponentModel.InvalidAsynchronousStateException> wcześniejszych wersjach klasa znajduje się w zestawie *System.ComponentModel.TypeConverter.*

Począwszy od .NET Core 3.0, znajduje się w zestawie *System.ComponentModel.Primitives.*

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana dotyczy tylko aplikacji, które <xref:System.ComponentModel.InvalidAsynchronousStateException> używają odbicia, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> aby załadować <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> przez wywołanie metody, takich jak lub przeciążenie, które zakłada, że typ znajduje się w określonym zestawie. W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu typu.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak.

<!--

### Affected APIs

- Not detectable via API analysis

-->
