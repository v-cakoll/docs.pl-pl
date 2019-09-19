---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119283"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="12975-101">Typ wyjątku serializatora JSON został `JsonException` zmieniony z na`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="12975-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="12975-102">W programie .NET Core 3,0 w wersji zapoznawczej 6 do 8, <xref:System.Text.Json.JsonException> serializator zostałby zgłosić, gdy napotka nieobsługiwany typ kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12975-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="12975-103">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 <xref:System.NotSupportedException> , serializator zgłasza zamiast.</span><span class="sxs-lookup"><span data-stu-id="12975-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="12975-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="12975-104">Change description</span></span>

<span data-ttu-id="12975-105">W programie .NET Core 3,0 w wersji zapoznawczej 6 do wersji zapoznawczej 8, serializator <xref:System.Text.Json.JsonException> zgłosi błąd, gdy napotka nieobsługiwany typ kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="12975-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="12975-106">*Nieobsługiwany typ kolekcji pochodnej* jest dowolnym typem kolekcji, którego nie można przypisać do jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="12975-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [<span data-ttu-id="12975-107">Ciąg\<IDictionary, T ></span><span class="sxs-lookup"><span data-stu-id="12975-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="12975-108">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 <xref:System.NotSupportedException> , serializator zgłasza nieobsługiwany typ kolekcji.</span><span class="sxs-lookup"><span data-stu-id="12975-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="12975-109">Nowy typ wyjątku lepiej odzwierciedla dlaczego operacja deserializacji kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="12975-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12975-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12975-110">Version introduced</span></span>

<span data-ttu-id="12975-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="12975-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12975-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="12975-112">Recommended action</span></span>

<span data-ttu-id="12975-113">Jeśli są przechwytywane <xref:System.Text.Json.JsonException> podczas deserializacji, warto rozważyć również <xref:System.NotSupportedException>przechwycenie.</span><span class="sxs-lookup"><span data-stu-id="12975-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="12975-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="12975-114">Category</span></span>

<span data-ttu-id="12975-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="12975-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12975-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="12975-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
