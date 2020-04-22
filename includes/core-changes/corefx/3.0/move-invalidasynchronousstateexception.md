---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021562"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException przeniesiono do innego zestawu

Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została przeniesiona.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i <xref:System.ComponentModel.InvalidAsynchronousStateException> wcześniejszych wersjach klasa znajduje się w *zespole System.ComponentModel.TypeConverter.*

Począwszy od .NET Core 3.0, znajduje się w *system.ComponentModel.Primitives* złożenia.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana dotyczy tylko aplikacji, które <xref:System.ComponentModel.InvalidAsynchronousStateException> używają odbicia, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> aby załadować <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> przez wywołanie metody, takie jak lub przeciążenie, która zakłada, że typ znajduje się w określonym zestawie. W takim przypadku zestaw zestawu, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu typu.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak.

<!--

### Affected APIs

- Not detectable via API analysis

-->
