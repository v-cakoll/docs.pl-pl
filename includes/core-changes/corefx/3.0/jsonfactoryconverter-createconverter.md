---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147565"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Zmieniono sygnaturę JsonFactoryConverter. isconverter

Aby ułatwić składanie <xref:System.Text.Json.Serialization.JsonConverterFactory> klas, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> Metoda została udostępniona jako publiczna i podano drugi argument typu. <xref:System.Text.Json.JsonSerializerOptions>

#### <a name="change-description"></a>Zmień opis

Sygnatura `CreateConverter` metody w programie .NET Core wcześniejsza niż wersja 3,0 Preview 8 była:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

W programie .NET Core 3,0 w wersji zapoznawczej 8 i nowszych wersjach:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Przed wprowadzeniem tej zmiany trudno było tworzyć zapieczętowane konwertery fabryk, ponieważ nie było to łatwe w <xref:System.Text.Json.Serialization.JsonConverter%601> użyciu. Uczynienie metody fabryki jako publiczną, a także <xref:System.Text.Json.JsonSerializerOptions> przekazanie bieżącego zezwolenia na znacznie bardziej elastyczne składanie.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="recommended-action"></a>Zalecana akcja

Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
