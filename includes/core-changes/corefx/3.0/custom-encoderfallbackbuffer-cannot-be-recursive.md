---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568157"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="6c19c-101">Niestandardowe wystąpienia Buforu ConerFallbackBuffer nie mogą wycofać się cyklicznie</span><span class="sxs-lookup"><span data-stu-id="6c19c-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="6c19c-102">Wystąpienia <xref:System.Text.EncoderFallbackBuffer> niestandardowe nie mogą wycofać się cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="6c19c-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="6c19c-103">Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi spowodować sekwencję znaków, która jest konwertowalna do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="6c19c-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="6c19c-104">W przeciwnym razie wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6c19c-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6c19c-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="6c19c-105">Change description</span></span>

<span data-ttu-id="6c19c-106">Podczas operacji transkodowania między znakami do bajtów program runtime wykrywa źle sformułowane lub niekonwertowalne sekwencje UTF-16 i udostępnia te znaki <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> do metody.</span><span class="sxs-lookup"><span data-stu-id="6c19c-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6c19c-107">Metoda `Fallback` określa, które znaki powinny być zastępowane oryginalnymi danymi niewymienialnymi, <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> a te znaki są opróżniane przez wywoływanie w pętli.</span><span class="sxs-lookup"><span data-stu-id="6c19c-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="6c19c-108">Następnie czas wykonywania próbuje przekodować te znaki podstawienia do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="6c19c-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="6c19c-109">Jeśli ta operacja zakończy się pomyślnie, czas wykonywania kontynuuje transkodowanie od miejsca, w którym zostało wyłączone w oryginalnym ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="6c19c-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="6c19c-110">W .NET Core Preview 7 i wcześniejszych <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> wersjach implementacje niestandardowe mogą zwracać sekwencje znaków, które nie są konwertowalne do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="6c19c-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="6c19c-111">Jeśli podstawione znaki nie mogą być transkodowane do kodowania <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> docelowego, czas wykonywania wywołuje metodę ponownie ze <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> znakami podstawienia, oczekując, że metoda zwróci nową sekwencję podstawienia.</span><span class="sxs-lookup"><span data-stu-id="6c19c-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="6c19c-112">Ten proces jest kontynuowany, dopóki czas wykonywania ostatecznie widzi dobrze sformułowane, kabriolet podstawienia lub do momentu osiągnięcia maksymalnej liczby rekursji.</span><span class="sxs-lookup"><span data-stu-id="6c19c-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="6c19c-113">Począwszy od .NET Core 3.0, implementacje niestandardowe <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi zwracać sekwencje znaków, które są konwertowalne do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="6c19c-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="6c19c-114">Jeśli podstawione znaki nie mogą być transkodowane <xref:System.ArgumentException> do kodowania docelowego, zgłaszany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="6c19c-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="6c19c-115">Czas wykonywania nie będzie już wykonywać wywołania <xref:System.Text.EncoderFallbackBuffer> cykliczne do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6c19c-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="6c19c-116">To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="6c19c-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="6c19c-117">Program runtime wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, której nie można przekonwertować na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="6c19c-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="6c19c-118">Określono <xref:System.Text.EncoderFallback> niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="6c19c-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="6c19c-119">Niestandardowe <xref:System.Text.EncoderFallback> próbuje zastąpić nową nieukształtowaną lub niewymienialną sekwencję UTF-16.</span><span class="sxs-lookup"><span data-stu-id="6c19c-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6c19c-120">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6c19c-120">Version introduced</span></span>

<span data-ttu-id="6c19c-121">3.0</span><span class="sxs-lookup"><span data-stu-id="6c19c-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6c19c-122">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6c19c-122">Recommended action</span></span>

<span data-ttu-id="6c19c-123">Większość programistów nie musi podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="6c19c-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="6c19c-124">Jeśli aplikacja używa <xref:System.Text.EncoderFallback> niestandardowego i <xref:System.Text.EncoderFallbackBuffer> klasy, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> upewnij się, że implementacja wypełnia bufor rezerwowy dobrze sformułowanymi danymi UTF-16, które są bezpośrednio konwertowalne do kodowania docelowego, gdy <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> metoda jest po raz pierwszy wywoływana przez program runtime.</span><span class="sxs-lookup"><span data-stu-id="6c19c-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="6c19c-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6c19c-125">Category</span></span>

<span data-ttu-id="6c19c-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6c19c-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6c19c-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6c19c-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
