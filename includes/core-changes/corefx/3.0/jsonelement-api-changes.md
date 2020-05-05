---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568126"
---
### <a name="jsonelement-api-changes"></a>Zmiany interfejsu API jsonelement

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 7, niektóre <xref:System.Text.Json.JsonElement> interfejsy API zostały zmienione w celu łatwiejszego odnajdowania i zwiększenia użyteczności.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 3,0 w wersji <xref:System.Text.Json.JsonElement> zapoznawczej 7 interfejsy API zostały zmienione w następujący sposób, aby umożliwić łatwiejsze odnajdywanie i większą użyteczność.

1. Wszystkie `WriteProperty` przeciążenia metod zostały usunięte z <xref:System.Text.Json.JsonElement>. Ma to wpływ na kod, taki jak następujące:

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

1. `WriteValue`Zmieniono nazwę na <xref:System.Text.Json.JsonElement.WriteTo%2A>. Ma to wpływ na kod, taki jak następujące:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>teraz zgłasza, <xref:System.ArgumentNullException> gdy parametr metody jest `null`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 7

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli te zmiany wpływają na kod, możesz wykonać następujące czynności:

- Nie istnieje zastępczy interfejs API dla `WriteProperty` przeciążenia w <xref:System.Text.Json.JsonElement>programie. Zamiast tego można wywołać jedno z <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> przeciążeń wraz z <xref:System.Text.Json.JsonElement.WriteTo%2A> metodą, aby osiągnąć ten sam wynik. Przykład:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Zmień nazwę `WriteValue` metody na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>. Parametr metody pozostaje niezmieniony. Na przykład poprzedni kod powinien zostać zmieniony na następujący:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <xref:System.ArgumentNullException> Obsługuj wywołania <xref:System.Text.Json.JsonElement.WriteTo%2A> metody.

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
