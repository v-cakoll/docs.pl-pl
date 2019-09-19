---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119283"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Typ wyjątku serializatora JSON został `JsonException` zmieniony z na`NotSupportedException`

W programie .NET Core 3,0 w wersji zapoznawczej 6 do 8, <xref:System.Text.Json.JsonException> serializator zostałby zgłosić, gdy napotka nieobsługiwany typ kolekcji pochodnej. Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 <xref:System.NotSupportedException> , serializator zgłasza zamiast.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 3,0 w wersji zapoznawczej 6 do wersji zapoznawczej 8, serializator <xref:System.Text.Json.JsonException> zgłosi błąd, gdy napotka nieobsługiwany typ kolekcji pochodnej. *Nieobsługiwany typ kolekcji pochodnej* jest dowolnym typem kolekcji, którego nie można przypisać do jednego z następujących typów:

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [Ciąg\<IDictionary, T >](xref:System.Collections.Generic.IDictionary%602)

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 <xref:System.NotSupportedException> , serializator zgłasza nieobsługiwany typ kolekcji. Nowy typ wyjątku lepiej odzwierciedla dlaczego operacja deserializacji kończy się niepowodzeniem.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli są przechwytywane <xref:System.Text.Json.JsonException> podczas deserializacji, warto rozważyć również <xref:System.NotSupportedException>przechwycenie.

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
