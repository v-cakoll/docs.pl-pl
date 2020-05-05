---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568126"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="7d5bd-101">Zmiany interfejsu API jsonelement</span><span class="sxs-lookup"><span data-stu-id="7d5bd-101">JsonElement API changes</span></span>

<span data-ttu-id="7d5bd-102">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 7, niektóre <xref:System.Text.Json.JsonElement> interfejsy API zostały zmienione w celu łatwiejszego odnajdowania i zwiększenia użyteczności.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7d5bd-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="7d5bd-103">Change description</span></span>

<span data-ttu-id="7d5bd-104">W programie .NET Core 3,0 w wersji <xref:System.Text.Json.JsonElement> zapoznawczej 7 interfejsy API zostały zmienione w następujący sposób, aby umożliwić łatwiejsze odnajdywanie i większą użyteczność.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="7d5bd-105">Wszystkie `WriteProperty` przeciążenia metod zostały usunięte z <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="7d5bd-106">Ma to wpływ na kod, taki jak następujące:</span><span class="sxs-lookup"><span data-stu-id="7d5bd-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="7d5bd-107">`WriteValue`Zmieniono nazwę na <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="7d5bd-108">Ma to wpływ na kod, taki jak następujące:</span><span class="sxs-lookup"><span data-stu-id="7d5bd-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="7d5bd-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>teraz zgłasza, <xref:System.ArgumentNullException> gdy parametr metody jest `null`.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7d5bd-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7d5bd-110">Version introduced</span></span>

<span data-ttu-id="7d5bd-111">3,0 wersja zapoznawcza 7</span><span class="sxs-lookup"><span data-stu-id="7d5bd-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7d5bd-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7d5bd-112">Recommended action</span></span>

<span data-ttu-id="7d5bd-113">Jeśli te zmiany wpływają na kod, możesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7d5bd-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="7d5bd-114">Nie istnieje zastępczy interfejs API dla `WriteProperty` przeciążenia w <xref:System.Text.Json.JsonElement>programie.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="7d5bd-115">Zamiast tego można wywołać jedno z <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> przeciążeń wraz z <xref:System.Text.Json.JsonElement.WriteTo%2A> metodą, aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="7d5bd-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="7d5bd-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="7d5bd-117">Zmień nazwę `WriteValue` metody na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="7d5bd-118">Parametr metody pozostaje niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="7d5bd-119">Na przykład poprzedni kod powinien zostać zmieniony na następujący:</span><span class="sxs-lookup"><span data-stu-id="7d5bd-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="7d5bd-120"><xref:System.ArgumentNullException> Obsługuj wywołania <xref:System.Text.Json.JsonElement.WriteTo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7d5bd-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7d5bd-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7d5bd-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
