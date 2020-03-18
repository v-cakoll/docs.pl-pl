---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568126"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="30b06-101">Zmiany interfejsu API JsonElement</span><span class="sxs-lookup"><span data-stu-id="30b06-101">JsonElement API changes</span></span>

<span data-ttu-id="30b06-102">Począwszy od .NET Core 3.0 Preview 7, niektóre <xref:System.Text.Json.JsonElement> interfejsy API zostały zmienione, aby umożliwić łatwiejsze odnajdowanie i większą użyteczność.</span><span class="sxs-lookup"><span data-stu-id="30b06-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="30b06-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="30b06-103">Change description</span></span>

<span data-ttu-id="30b06-104">W wersji .NET Core 3.0 Preview 7 interfejsy API zostały zmienione w następujący sposób, <xref:System.Text.Json.JsonElement> aby umożliwić łatwiejsze odnajdowanie i większą użyteczność.</span><span class="sxs-lookup"><span data-stu-id="30b06-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="30b06-105">Wszystkie `WriteProperty` przeciążenia metody <xref:System.Text.Json.JsonElement>zostały usunięte z .</span><span class="sxs-lookup"><span data-stu-id="30b06-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="30b06-106">Ma to wpływ na kod, taki jak:</span><span class="sxs-lookup"><span data-stu-id="30b06-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="30b06-107">`WriteValue`zmieniono nazwę <xref:System.Text.Json.JsonElement.WriteTo%2A>na .</span><span class="sxs-lookup"><span data-stu-id="30b06-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="30b06-108">Ma to wpływ na kod, taki jak:</span><span class="sxs-lookup"><span data-stu-id="30b06-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="30b06-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>teraz wyrzuca, <xref:System.ArgumentNullException> gdy `null`jego parametr metody jest .</span><span class="sxs-lookup"><span data-stu-id="30b06-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30b06-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="30b06-110">Version introduced</span></span>

<span data-ttu-id="30b06-111">3.0 Podgląd 7</span><span class="sxs-lookup"><span data-stu-id="30b06-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30b06-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="30b06-112">Recommended action</span></span>

<span data-ttu-id="30b06-113">Jeśli te zmiany mają wpływ na kod, można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="30b06-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="30b06-114">Nie ma zastępczego interfejsu `WriteProperty` API <xref:System.Text.Json.JsonElement>dla przeciążeń w .</span><span class="sxs-lookup"><span data-stu-id="30b06-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="30b06-115">Zamiast tego można wywołać <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> jeden z <xref:System.Text.Json.JsonElement.WriteTo%2A> przeciążeń wraz z metodą, aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="30b06-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="30b06-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="30b06-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="30b06-117">Zmień nazwę `WriteValue` metody <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>na .</span><span class="sxs-lookup"><span data-stu-id="30b06-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="30b06-118">Parametr metody pozostaje niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="30b06-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="30b06-119">Na przykład poprzedni kod powinien zostać zmieniony na następujący:</span><span class="sxs-lookup"><span data-stu-id="30b06-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="30b06-120">Obsługa <xref:System.ArgumentNullException> wywołań in <xref:System.Text.Json.JsonElement.WriteTo%2A> do metody.</span><span class="sxs-lookup"><span data-stu-id="30b06-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30b06-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="30b06-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
