---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568226"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json serializator typ `JsonException` wyjątku zmieniony z na`NotSupportedException`

W .NET Core 3.0 Preview 6 do 8 <xref:System.Text.Json.JsonException> serializator będzie rzucać po napotkaniu nieobsługiwanego typu kolekcji pochodnej. Począwszy od .NET Core 3.0 Preview 9, serializator rzuca <xref:System.NotSupportedException> zamiast tego.

#### <a name="change-description"></a>Zmień opis

W .NET Core 3.0 Preview 6 do podglądu <xref:System.Text.Json.JsonException> 8 serializator będzie rzucać po napotkaniu nieobsługiwanego typu kolekcji pochodnej. Nieobsługiwany *typ kolekcji pochodnej* to dowolny typ kolekcji, którego nie można przypisać do jednego z następujących typów:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [\<Ciąg iSłownik,T>](xref:System.Collections.Generic.IDictionary%602)

Począwszy od .NET Core 3.0 Preview 9, serializator zgłasza <xref:System.NotSupportedException> Po napotkaniu nieobsługiwanego typu kolekcji. Nowy typ wyjątku lepiej odzwierciedla, dlaczego operacja deserializacji nie działa.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli podczas deserializacji jest przechwytywanie, <xref:System.Text.Json.JsonException> <xref:System.NotSupportedException>warto rozważyć również wychwytywanie .

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
