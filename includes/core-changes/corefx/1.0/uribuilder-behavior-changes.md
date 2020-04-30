---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595688"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="8b1ee-101">Właściwości UriBuilder nie dołączają już znaków wiodących</span><span class="sxs-lookup"><span data-stu-id="8b1ee-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="8b1ee-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType>nie dołącza już znaku wiodącego `#` i nie <xref:System.UriBuilder.Query?displayProperty=nameWithType> dołącza już znaku wiodącego `?` , gdy jeden już istnieje.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8b1ee-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="8b1ee-103">Change description</span></span>

<span data-ttu-id="8b1ee-104"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> W .NET Framework właściwości <xref:System.UriBuilder.Query?displayProperty=nameWithType> i zawsze są poprzedzone znakiem `?` `#` lub, odpowiednio, do przechowywanej wartości.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="8b1ee-105">Takie zachowanie może skutkować `#` wielokrotnym `?` znakiem w wartości przechowywanej, jeśli ciąg zawiera już jeden z tych znaków wiodących.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="8b1ee-106">Na przykład wartość <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> może być równa `##main`.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="8b1ee-107">Począwszy od platformy .NET Core 1,0, te właściwości nie `#` dołączają `?` lub do przechowywanej wartości, jeśli jeden już występuje na początku ciągu.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8b1ee-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8b1ee-108">Version introduced</span></span>

<span data-ttu-id="8b1ee-109">1.0</span><span class="sxs-lookup"><span data-stu-id="8b1ee-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8b1ee-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8b1ee-110">Recommended action</span></span>

<span data-ttu-id="8b1ee-111">Nie trzeba już jawnie usuwać żadnego z tych znaków wiodących podczas ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="8b1ee-112">Jest to szczególnie przydatne podczas dołączania wartości, ponieważ nie jest już konieczne usuwanie interlinii `#` lub `?` każdorazowe dołączanie.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="8b1ee-113">Na przykład poniższy fragment kodu przedstawia różnicę zachowania między .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="8b1ee-114">W .NET Framework dane wyjściowe to `????one=1&two=2&three=3&four=4`.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="8b1ee-115">W programie .NET Core dane wyjściowe to `?one=1&two=2&three=3&four=4`.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="8b1ee-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8b1ee-116">Category</span></span>

<span data-ttu-id="8b1ee-117">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="8b1ee-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8b1ee-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8b1ee-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
