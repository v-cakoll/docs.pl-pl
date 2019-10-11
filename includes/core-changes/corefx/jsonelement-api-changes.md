---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237433"
---
### <a name="jsonelement-api-changes"></a>Zmiany interfejsu API jsonelement

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 7, niektóre interfejsy API <xref:System.Text.Json.JsonElement> uległy zmianie, aby umożliwić łatwiejsze odnajdywanie i większą użyteczność.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 3,0 w wersji zapoznawczej 7 interfejsy API <xref:System.Text.Json.JsonElement> uległy zmianie w następujący sposób, aby ułatwić odnajdywanie i większą użyteczność.

1. Wszystkie przeciążenia metody `WriteProperty` zostały usunięte z <xref:System.Text.Json.JsonElement>. Ma to wpływ na kod, taki jak następujące:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. `WriteValue` zmieniono nazwę na <xref:System.Text.Json.JsonElement.WriteTo%2A>. Ma to wpływ na kod, taki jak następujące:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> teraz zgłasza <xref:System.ArgumentNullException>, gdy parametr metody jest `null`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 7

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli te zmiany wpływają na kod, możesz wykonać następujące czynności:

- Nie istnieje zastępczy interfejs API dla przeciążenia `WriteProperty` w <xref:System.Text.Json.JsonElement>. Zamiast tego można wywołać jeden z przeciążeń <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> wraz z metodą <xref:System.Text.Json.JsonElement.WriteTo%2A>, aby achieve ten sam wynik. Na przykład:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Zmień nazwę metody `WriteValue` na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>. Parametr metody pozostaje niezmieniony. Na przykład poprzedni kod powinien zostać zmieniony na następujący:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Obsłuż <xref:System.ArgumentNullException> w wywołaniach metody <xref:System.Text.Json.JsonElement.WriteTo%2A>.

#### <a name="affected-apis"></a>Narażone interfejsy API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
