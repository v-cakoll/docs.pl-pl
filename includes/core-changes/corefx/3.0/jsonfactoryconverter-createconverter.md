---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147565"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="2d21f-101">Zmieniono podpis JsonFactoryConverter.CreateConverter</span><span class="sxs-lookup"><span data-stu-id="2d21f-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="2d21f-102">Aby ułatwić skład <xref:System.Text.Json.Serialization.JsonConverterFactory> klas, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> metoda została upubliczniona i biorąc <xref:System.Text.Json.JsonSerializerOptions>pod uwagę drugi argument typu .</span><span class="sxs-lookup"><span data-stu-id="2d21f-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2d21f-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="2d21f-103">Change description</span></span>

<span data-ttu-id="2d21f-104">Podpis metody `CreateConverter` w .NET Core przed wersją wersji 3.0 Preview 8 był:</span><span class="sxs-lookup"><span data-stu-id="2d21f-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="2d21f-105">W wersji .NET Core 3.0 Preview 8 i nowszych jest:</span><span class="sxs-lookup"><span data-stu-id="2d21f-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="2d21f-106">Przed tą zmianą trudno było skomponować zapieczętowane konwertery fabryczne, ponieważ nie było łatwego <xref:System.Text.Json.Serialization.JsonConverter%601> sposobu na uzyskanie z niego.</span><span class="sxs-lookup"><span data-stu-id="2d21f-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="2d21f-107">Publiczne upublicznienie metody fabrycznej, a także przekazywanie prądu <xref:System.Text.Json.JsonSerializerOptions> pozwala na znacznie bardziej elastyczny skład.</span><span class="sxs-lookup"><span data-stu-id="2d21f-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2d21f-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2d21f-108">Version introduced</span></span>

<span data-ttu-id="2d21f-109">3.0 Podgląd 8</span><span class="sxs-lookup"><span data-stu-id="2d21f-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2d21f-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2d21f-110">Recommended action</span></span>

<span data-ttu-id="2d21f-111">Klasy pochodne muszą zostać zaktualizowane i ponownie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="2d21f-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2d21f-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2d21f-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
