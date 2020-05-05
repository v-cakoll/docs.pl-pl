---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021631"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="6eee3-101">Typ wyjątku serializatora JSON został `JsonException` zmieniony z na`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="6eee3-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="6eee3-102">W programie .NET Core 3,0 w wersji zapoznawczej 6 do 8, <xref:System.Text.Json.JsonException> serializator zostałby zgłosić, gdy napotka nieobsługiwany typ kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6eee3-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="6eee3-103">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 <xref:System.NotSupportedException> , serializator zgłasza zamiast.</span><span class="sxs-lookup"><span data-stu-id="6eee3-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6eee3-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="6eee3-104">Change description</span></span>

<span data-ttu-id="6eee3-105">W programie .NET Core 3,0 w wersji zapoznawczej 6 do wersji zapoznawczej 8, serializator zgłosi błąd, <xref:System.Text.Json.JsonException> gdy napotka nieobsługiwany typ kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6eee3-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="6eee3-106">*Nieobsługiwany typ kolekcji pochodnej* jest dowolnym typem kolekcji, którego nie można przypisać do jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="6eee3-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="6eee3-107">Ciąg\<IDictionary, T></span><span class="sxs-lookup"><span data-stu-id="6eee3-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="6eee3-108">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9 <xref:System.NotSupportedException> , serializator zgłasza nieobsługiwany typ kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6eee3-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="6eee3-109">Nowy typ wyjątku lepiej odzwierciedla dlaczego operacja deserializacji kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6eee3-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6eee3-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6eee3-110">Version introduced</span></span>

<span data-ttu-id="6eee3-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="6eee3-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6eee3-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6eee3-112">Recommended action</span></span>

<span data-ttu-id="6eee3-113">Jeśli są przechwytywane <xref:System.Text.Json.JsonException> podczas deserializacji, warto rozważyć również przechwycenie <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="6eee3-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="6eee3-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6eee3-114">Category</span></span>

<span data-ttu-id="6eee3-115">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6eee3-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6eee3-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6eee3-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
