---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117146"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="2ee8f-101">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="2ee8f-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="2ee8f-102">Aby ułatwić składanie <xref:System.Text.Json.Serialization.JsonConverterFactory> klas <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> , metoda została udostępniona jako publiczna i podano drugi argument typu <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="2ee8f-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="details"></a><span data-ttu-id="2ee8f-103">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2ee8f-103">Details</span></span>

<span data-ttu-id="2ee8f-104">Sygnatura `CreateConverter` metody w programie .NET Core wcześniejsza niż wersja 3,0 Preview 8 była:</span><span class="sxs-lookup"><span data-stu-id="2ee8f-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="2ee8f-105">W programie .NET Core 3,0 w wersji zapoznawczej 8 i nowszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="2ee8f-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="2ee8f-106">Przed wprowadzeniem tej zmiany trudno było tworzyć zapieczętowane konwertery fabryk, ponieważ nie było to łatwe <xref:System.Text.Json.Serialization.JsonConverter%601> w użyciu.</span><span class="sxs-lookup"><span data-stu-id="2ee8f-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="2ee8f-107">Uczynienie metody fabryki jako publiczną, a także <xref:System.Text.Json.JsonSerializerOptions> przekazanie bieżącego zezwolenia na znacznie bardziej elastyczne składanie.</span><span class="sxs-lookup"><span data-stu-id="2ee8f-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ee8f-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2ee8f-108">Version introduced</span></span>

<span data-ttu-id="2ee8f-109">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="2ee8f-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ee8f-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2ee8f-110">Recommended action</span></span>

<span data-ttu-id="2ee8f-111">Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="2ee8f-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ee8f-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2ee8f-112">Affected APIs</span></span>

<span data-ttu-id="2ee8f-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2ee8f-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
