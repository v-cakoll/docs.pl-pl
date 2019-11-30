---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568191"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="384e5-101">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="384e5-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="384e5-102">Aby ułatwić składanie klas <xref:System.Text.Json.Serialization.JsonConverterFactory>, Metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> została udostępniona jako publiczna i podano drugi argument typu <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="384e5-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="384e5-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="384e5-103">Change description</span></span>

<span data-ttu-id="384e5-104">Sygnatura metody `CreateConverter` w programie .NET Core wcześniejszym niż wersja 3,0 Preview 8 była:</span><span class="sxs-lookup"><span data-stu-id="384e5-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="384e5-105">W programie .NET Core 3,0 w wersji zapoznawczej 8 i nowszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="384e5-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="384e5-106">Przed wprowadzeniem tej zmiany trudno było tworzyć zapieczętowane konwertery fabryk, ponieważ nie było łatwo możliwe uzyskanie <xref:System.Text.Json.Serialization.JsonConverter%601> od niego.</span><span class="sxs-lookup"><span data-stu-id="384e5-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="384e5-107">Zastosowanie metody fabryki jako publicznej i przekazanie bieżącej <xref:System.Text.Json.JsonSerializerOptions> pozwala na znacznie bardziej elastyczne składanie.</span><span class="sxs-lookup"><span data-stu-id="384e5-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="384e5-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="384e5-108">Version introduced</span></span>

<span data-ttu-id="384e5-109">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="384e5-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="384e5-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="384e5-110">Recommended action</span></span>

<span data-ttu-id="384e5-111">Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="384e5-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="384e5-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="384e5-112">Affected APIs</span></span>

<span data-ttu-id="384e5-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="384e5-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
