---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021631"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="b97fd-101">Typ wyjątku serializatora `JsonException` Json zmieniono z na`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="b97fd-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="b97fd-102">W .NET Core 3.0 Preview 6 do 8 <xref:System.Text.Json.JsonException> serializator będzie zgłosić, gdy napotkał nieobsługiwane typ kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b97fd-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="b97fd-103">Począwszy od .NET Core 3.0 Preview 9, serializator zgłasza <xref:System.NotSupportedException> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b97fd-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b97fd-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="b97fd-104">Change description</span></span>

<span data-ttu-id="b97fd-105">W .NET Core 3.0 Preview 6 do podglądu <xref:System.Text.Json.JsonException> 8 serializator będzie zgłosić, gdy napotkał nieobsługiwane typ kolekcji pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b97fd-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="b97fd-106">*Nieobsługiwany typ kolekcji pochodnej* to dowolny typ kolekcji, którego nie można przypisać do jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="b97fd-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="b97fd-107">Ciąg IDictionary,T\<></span><span class="sxs-lookup"><span data-stu-id="b97fd-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="b97fd-108">Począwszy od .NET Core 3.0 Preview 9, serializator zgłasza <xref:System.NotSupportedException> When napotkania nieobsługiwał typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b97fd-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="b97fd-109">Nowy typ wyjątku lepiej odzwierciedla, dlaczego operacja deserializacji nie działa.</span><span class="sxs-lookup"><span data-stu-id="b97fd-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b97fd-110">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="b97fd-110">Version introduced</span></span>

<span data-ttu-id="b97fd-111">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="b97fd-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b97fd-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b97fd-112">Recommended action</span></span>

<span data-ttu-id="b97fd-113">Jeśli łapiesz <xref:System.Text.Json.JsonException> podczas deserializacji, warto rozważyć <xref:System.NotSupportedException>również połowu .</span><span class="sxs-lookup"><span data-stu-id="b97fd-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="b97fd-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b97fd-114">Category</span></span>

<span data-ttu-id="b97fd-115">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="b97fd-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b97fd-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b97fd-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
