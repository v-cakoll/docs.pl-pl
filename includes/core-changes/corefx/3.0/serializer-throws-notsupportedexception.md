---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568226"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="c6e97-101">Json serializator typ `JsonException` wyjątku zmieniony z na`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="c6e97-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="c6e97-102">W .NET Core 3.0 Preview 6 do 8 <xref:System.Text.Json.JsonException> serializator będzie rzucać po napotkaniu nieobsługiwanego typu kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c6e97-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="c6e97-103">Począwszy od .NET Core 3.0 Preview 9, serializator rzuca <xref:System.NotSupportedException> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c6e97-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c6e97-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="c6e97-104">Change description</span></span>

<span data-ttu-id="c6e97-105">W .NET Core 3.0 Preview 6 do podglądu <xref:System.Text.Json.JsonException> 8 serializator będzie rzucać po napotkaniu nieobsługiwanego typu kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c6e97-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="c6e97-106">Nieobsługiwany *typ kolekcji pochodnej* to dowolny typ kolekcji, którego nie można przypisać do jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="c6e97-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="c6e97-107">\<Ciąg iSłownik,T></span><span class="sxs-lookup"><span data-stu-id="c6e97-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="c6e97-108">Począwszy od .NET Core 3.0 Preview 9, serializator zgłasza <xref:System.NotSupportedException> Po napotkaniu nieobsługiwanego typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c6e97-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="c6e97-109">Nowy typ wyjątku lepiej odzwierciedla, dlaczego operacja deserializacji nie działa.</span><span class="sxs-lookup"><span data-stu-id="c6e97-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c6e97-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="c6e97-110">Version introduced</span></span>

<span data-ttu-id="c6e97-111">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="c6e97-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c6e97-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="c6e97-112">Recommended action</span></span>

<span data-ttu-id="c6e97-113">Jeśli podczas deserializacji jest przechwytywanie, <xref:System.Text.Json.JsonException> <xref:System.NotSupportedException>warto rozważyć również wychwytywanie .</span><span class="sxs-lookup"><span data-stu-id="c6e97-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="c6e97-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c6e97-114">Category</span></span>

<span data-ttu-id="c6e97-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c6e97-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c6e97-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c6e97-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
