---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021631"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Typ wyjątku serializatora `JsonException` Json zmieniono z na`NotSupportedException`

W .NET Core 3.0 Preview 6 do 8 <xref:System.Text.Json.JsonException> serializator będzie zgłosić, gdy napotkał nieobsługiwane typ kolekcji pochodnej. Począwszy od .NET Core 3.0 Preview 9, serializator zgłasza <xref:System.NotSupportedException> zamiast tego.

#### <a name="change-description"></a>Zmień opis

W .NET Core 3.0 Preview 6 do podglądu <xref:System.Text.Json.JsonException> 8 serializator będzie zgłosić, gdy napotkał nieobsługiwane typ kolekcji pochodnej. *Nieobsługiwany typ kolekcji pochodnej* to dowolny typ kolekcji, którego nie można przypisać do jednego z następujących typów:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [Ciąg IDictionary,T\<>](xref:System.Collections.Generic.IDictionary%602)

Począwszy od .NET Core 3.0 Preview 9, serializator zgłasza <xref:System.NotSupportedException> When napotkania nieobsługiwał typu kolekcji. Nowy typ wyjątku lepiej odzwierciedla, dlaczego operacja deserializacji nie działa.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli łapiesz <xref:System.Text.Json.JsonException> podczas deserializacji, warto rozważyć <xref:System.NotSupportedException>również połowu .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
