---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237431"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="f8db3-101">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="f8db3-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="f8db3-102">Aby ułatwić składanie klas <xref:System.Text.Json.Serialization.JsonConverterFactory>, Metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> została udostępniona jako publiczna i podano drugi argument typu <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="f8db3-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f8db3-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f8db3-103">Change description</span></span>

<span data-ttu-id="f8db3-104">Sygnatura metody `CreateConverter` w programie .NET Core wcześniejszym niż wersja 3,0 Preview 8 to:</span><span class="sxs-lookup"><span data-stu-id="f8db3-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="f8db3-105">W programie .NET Core 3,0 w wersji zapoznawczej 8 i nowszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="f8db3-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="f8db3-106">Przed wprowadzeniem tej zmiany trudno było tworzyć zapieczętowane konwertery fabryk, ponieważ nie było możliwości łatwego uzyskania <xref:System.Text.Json.Serialization.JsonConverter%601>.</span><span class="sxs-lookup"><span data-stu-id="f8db3-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="f8db3-107">Dzięki temu Metoda fabryki powinna być publiczna, a także przekazywać bieżące <xref:System.Text.Json.JsonSerializerOptions> Zezwalaj na znacznie bardziej elastyczne składanie.</span><span class="sxs-lookup"><span data-stu-id="f8db3-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f8db3-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f8db3-108">Version introduced</span></span>

<span data-ttu-id="f8db3-109">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="f8db3-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f8db3-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f8db3-110">Recommended action</span></span>

<span data-ttu-id="f8db3-111">Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="f8db3-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f8db3-112">Narażone interfejsy API</span><span class="sxs-lookup"><span data-stu-id="f8db3-112">Affected APIs</span></span>

<span data-ttu-id="f8db3-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f8db3-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
