---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281312"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Zmiana zachowania dla Vector2. Lerp i Vector4. Lerp

Implementacja <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> i <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> zmiana na prawidłowe konto dla błędu zaokrąglania zmiennoprzecinkowego.

#### <a name="change-description"></a>Zmień opis

Wcześniej <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> i <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> zostały zaimplementowane jako `value1 + (value2 - value1) * amount` . Jednak ze względu na błąd zaokrąglania liczb zmiennoprzecinkowych ten algorytm nie zawsze zwraca `value2` wartość, gdy `amount` jest `1.0f` .

W przypadku programu .NET 5,0 lub nowszego implementacja używa tego samego algorytmu co <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> `(value1 * (1.0f - amount)) + (value2 * amount)` . Ten algorytm poprawnie rozliczy dla błędu zaokrąglania. Teraz, gdy `amount` jest `1.0f` , wynik jest precyzyjna `value2` . Zaktualizowany algorytm umożliwia także swobodne zoptymalizowanie algorytmu przy użyciu, <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> gdy jest on dostępny.

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 7

#### <a name="recommended-action"></a>Zalecana akcja

Nie jest wymagane żadne działanie. Jeśli jednak chcesz zachować stare zachowanie, możesz zaimplementować własną `Lerp` funkcję, która używa poprzedniego algorytmu `value1 + (value2 - value1) * amount` .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
