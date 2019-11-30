---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568126"
---
### <a name="jsonelement-api-changes"></a>Zmiany interfejsu API jsonelement

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 7, niektóre interfejsy API <xref:System.Text.Json.JsonElement> uległy zmianie, aby umożliwić łatwiejsze odnajdywanie i większą użyteczność.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 3,0 w wersji zapoznawczej 7 interfejsy API <xref:System.Text.Json.JsonElement> uległy zmianie w następujący sposób, aby ułatwić odnajdywanie i większą użyteczność.

1. Wszystkie przeciążenia metod `WriteProperty` zostały usunięte z <xref:System.Text.Json.JsonElement>. Ma to wpływ na kod, taki jak następujące:

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

1. Nazwa `WriteValue` została zmieniona jako <xref:System.Text.Json.JsonElement.WriteTo%2A>. Ma to wpływ na kod, taki jak następujące:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> teraz generuje <xref:System.ArgumentNullException>, gdy jego parametr metody jest `null`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 7

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli te zmiany wpływają na kod, możesz wykonać następujące czynności:

- Nie istnieje zastępczy interfejs API dla przeciążenia `WriteProperty` w <xref:System.Text.Json.JsonElement>. Zamiast tego można wywołać jeden z przeciążeń <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> oraz metodę <xref:System.Text.Json.JsonElement.WriteTo%2A>, aby osiągnąć ten sam wynik. Na przykład:

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

- Obsługuj <xref:System.ArgumentNullException> w wywołaniach metody <xref:System.Text.Json.JsonElement.WriteTo%2A>.

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
