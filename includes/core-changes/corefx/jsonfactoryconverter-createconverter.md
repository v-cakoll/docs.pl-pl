---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237431"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Zmieniono sygnaturę JsonFactoryConverter. isconverter

Aby ułatwić składanie klas <xref:System.Text.Json.Serialization.JsonConverterFactory>, Metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> została udostępniona jako publiczna i podano drugi argument typu <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="change-description"></a>Zmień opis

Sygnatura metody `CreateConverter` w programie .NET Core wcześniejszym niż wersja 3,0 Preview 8 to: 

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

Przed wprowadzeniem tej zmiany trudno było tworzyć zapieczętowane konwertery fabryk, ponieważ nie było możliwości łatwego uzyskania <xref:System.Text.Json.Serialization.JsonConverter%601>. Dzięki temu Metoda fabryki powinna być publiczna, a także przekazywać bieżące <xref:System.Text.Json.JsonSerializerOptions> Zezwalaj na znacznie bardziej elastyczne składanie.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="recommended-action"></a>Zalecana akcja

Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.

#### <a name="affected-apis"></a>Narażone interfejsy API

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
