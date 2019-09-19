---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117146"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Zmieniono sygnaturę JsonFactoryConverter. isconverter

Aby ułatwić składanie <xref:System.Text.Json.Serialization.JsonConverterFactory> klas <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> , metoda została udostępniona jako publiczna i podano drugi argument typu <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="details"></a>Szczegóły

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

Przed wprowadzeniem tej zmiany trudno było tworzyć zapieczętowane konwertery fabryk, ponieważ nie było to łatwe <xref:System.Text.Json.Serialization.JsonConverter%601> w użyciu. Uczynienie metody fabryki jako publiczną, a także <xref:System.Text.Json.JsonSerializerOptions> przekazanie bieżącego zezwolenia na znacznie bardziej elastyczne składanie.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="recommended-action"></a>Zalecana akcja

Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
