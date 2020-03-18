---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568126"
---
### <a name="jsonelement-api-changes"></a>Zmiany interfejsu API JsonElement

Począwszy od .NET Core 3.0 Preview 7, niektóre <xref:System.Text.Json.JsonElement> interfejsy API zostały zmienione, aby umożliwić łatwiejsze odnajdowanie i większą użyteczność.

#### <a name="change-description"></a>Zmień opis

W wersji .NET Core 3.0 Preview 7 interfejsy API zostały zmienione w następujący sposób, <xref:System.Text.Json.JsonElement> aby umożliwić łatwiejsze odnajdowanie i większą użyteczność.

1. Wszystkie `WriteProperty` przeciążenia metody <xref:System.Text.Json.JsonElement>zostały usunięte z . Ma to wpływ na kod, taki jak:

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

1. `WriteValue`zmieniono nazwę <xref:System.Text.Json.JsonElement.WriteTo%2A>na . Ma to wpływ na kod, taki jak:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>teraz wyrzuca, <xref:System.ArgumentNullException> gdy `null`jego parametr metody jest .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 7

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli te zmiany mają wpływ na kod, można wykonać następujące czynności:

- Nie ma zastępczego interfejsu `WriteProperty` API <xref:System.Text.Json.JsonElement>dla przeciążeń w . Zamiast tego można wywołać <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> jeden z <xref:System.Text.Json.JsonElement.WriteTo%2A> przeciążeń wraz z metodą, aby osiągnąć ten sam wynik. Przykład:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Zmień nazwę `WriteValue` metody <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>na . Parametr metody pozostaje niezmieniony. Na przykład poprzedni kod powinien zostać zmieniony na następujący:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Obsługa <xref:System.ArgumentNullException> wywołań in <xref:System.Text.Json.JsonElement.WriteTo%2A> do metody.

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
