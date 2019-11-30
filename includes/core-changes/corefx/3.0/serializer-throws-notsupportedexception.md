---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568226"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Typ wyjątku serializatora JSON został zmieniony z `JsonException` na `NotSupportedException`

W programie .NET Core 3,0 w wersji zapoznawczej 6 do 8, serializator zgłosi <xref:System.Text.Json.JsonException>, gdy napotka nieobsługiwany typ kolekcji pochodnej. Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, serializator zgłosi <xref:System.NotSupportedException> zamiast.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 3,0 w wersji zapoznawczej 6 do wersji zapoznawczej 8 serializator zgłosi <xref:System.Text.Json.JsonException>, gdy napotka nieobsługiwany typ kolekcji pochodnej. *Nieobsługiwany typ kolekcji pochodnej* jest dowolnym typem kolekcji, którego nie można przypisać do jednego z następujących typów:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [Ciąg\<IDictionary, T >](xref:System.Collections.Generic.IDictionary%602)

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9, serializator zgłasza <xref:System.NotSupportedException> w przypadku napotkania nieobsługiwanego typu kolekcji. Nowy typ wyjątku lepiej odzwierciedla dlaczego operacja deserializacji kończy się niepowodzeniem.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli podczas deserializacji <xref:System.Text.Json.JsonException> są przechwytywane, warto rozważyć również przechwycenie <xref:System.NotSupportedException>.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
