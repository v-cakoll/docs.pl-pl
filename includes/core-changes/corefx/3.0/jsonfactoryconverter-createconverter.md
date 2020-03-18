---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147565"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Zmieniono podpis JsonFactoryConverter.CreateConverter

Aby ułatwić skład <xref:System.Text.Json.Serialization.JsonConverterFactory> klas, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> metoda została upubliczniona i biorąc <xref:System.Text.Json.JsonSerializerOptions>pod uwagę drugi argument typu .

#### <a name="change-description"></a>Zmień opis

Podpis metody `CreateConverter` w .NET Core przed wersją wersji 3.0 Preview 8 był:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

W wersji .NET Core 3.0 Preview 8 i nowszych jest:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Przed tą zmianą trudno było skomponować zapieczętowane konwertery fabryczne, ponieważ nie było łatwego <xref:System.Text.Json.Serialization.JsonConverter%601> sposobu na uzyskanie z niego. Publiczne upublicznienie metody fabrycznej, a także przekazywanie prądu <xref:System.Text.Json.JsonSerializerOptions> pozwala na znacznie bardziej elastyczny skład.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 8

#### <a name="recommended-action"></a>Zalecana akcja

Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
