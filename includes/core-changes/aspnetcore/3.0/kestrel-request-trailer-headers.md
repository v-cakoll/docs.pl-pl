---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393908"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="d925a-101">Kestrel: przeniesiono nagłówki przyczepki do nowej kolekcji</span><span class="sxs-lookup"><span data-stu-id="d925a-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="d925a-102">We wcześniejszych wersjach Kestrel dodaliśmy nagłówki podzielonych punktów protokołu HTTP/1.1 do kolekcji nagłówków żądań, gdy treść żądania została odczytana na końcu.</span><span class="sxs-lookup"><span data-stu-id="d925a-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="d925a-103">Takie zachowanie powodowało obawy dotyczące niejednoznaczności między nagłówkami i przyczepami.</span><span class="sxs-lookup"><span data-stu-id="d925a-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="d925a-104">Podjęto decyzję o przeniesieniu przyczep do nowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d925a-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="d925a-105">W ASP.NET Core 2,2 są niedostępne Wszystkie przyczepy z żądaniami HTTP/2, ale są teraz również dostępne w tej nowej kolekcji w ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d925a-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="d925a-106">Dodano nowe metody rozszerzenia żądania w celu uzyskania dostępu do tych przyczep.</span><span class="sxs-lookup"><span data-stu-id="d925a-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="d925a-107">Przyczepy protokołu HTTP/1.1 są dostępne po odczytaniu całej treści żądania.</span><span class="sxs-lookup"><span data-stu-id="d925a-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="d925a-108">Przyczepy protokołu HTTP/2 są dostępne po odebraniu ich od klienta.</span><span class="sxs-lookup"><span data-stu-id="d925a-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="d925a-109">Klient nie wyśle przyczep do momentu, gdy cała treść żądania nie będzie co najmniej buforowana przez serwer.</span><span class="sxs-lookup"><span data-stu-id="d925a-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="d925a-110">Może być konieczne odczytanie treści żądania w celu zwolnienia miejsca w buforze.</span><span class="sxs-lookup"><span data-stu-id="d925a-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="d925a-111">Przyczepy są zawsze dostępne w przypadku odczytywania treści żądania na końcu.</span><span class="sxs-lookup"><span data-stu-id="d925a-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="d925a-112">Przyczepy oznaczają koniec treści.</span><span class="sxs-lookup"><span data-stu-id="d925a-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d925a-113">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d925a-113">Version introduced</span></span>

<span data-ttu-id="d925a-114">3.0</span><span class="sxs-lookup"><span data-stu-id="d925a-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d925a-115">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="d925a-115">Old behavior</span></span>

<span data-ttu-id="d925a-116">Nagłówki przyczepy z żądaniem zostaną dodane do kolekcji `HttpRequest.Headers`.</span><span class="sxs-lookup"><span data-stu-id="d925a-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d925a-117">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="d925a-117">New behavior</span></span>

<span data-ttu-id="d925a-118">Nagłówki przyczepy z żądaniem **nie znajdują** się w kolekcji `HttpRequest.Headers`.</span><span class="sxs-lookup"><span data-stu-id="d925a-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="d925a-119">Aby uzyskiwać dostęp do nich, użyj następujących metod rozszerzających `HttpRequest`:</span><span class="sxs-lookup"><span data-stu-id="d925a-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="d925a-120">`GetDeclaredTrailers()` — pobiera nagłówek "Przyczepka" żądania, który zawiera listę przyczep, które mają być oczekiwane po treści.</span><span class="sxs-lookup"><span data-stu-id="d925a-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="d925a-121">`SupportsTrailers()`-wskazuje, czy żądanie obsługuje nagłówki przyczepy.</span><span class="sxs-lookup"><span data-stu-id="d925a-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="d925a-122">`CheckTrailersAvailable()` — Określa, czy żądanie obsługuje przyczepy i czy są dostępne do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d925a-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="d925a-123">`GetTrailer(string trailerName)` — pobiera żądany końcowy nagłówek z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d925a-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d925a-124">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="d925a-124">Reason for change</span></span>

<span data-ttu-id="d925a-125">Przyczepy są kluczową funkcją w scenariuszach takich jak gRPC.</span><span class="sxs-lookup"><span data-stu-id="d925a-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="d925a-126">Scalanie przyczep w programie w celu utworzenia nagłówków żądań było mylące dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="d925a-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d925a-127">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d925a-127">Recommended action</span></span>

<span data-ttu-id="d925a-128">Użyj metod rozszerzenia związanych z przyczepą w `HttpRequest`, aby uzyskać dostęp do przyczep.</span><span class="sxs-lookup"><span data-stu-id="d925a-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="d925a-129">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d925a-129">Category</span></span>

<span data-ttu-id="d925a-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d925a-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d925a-131">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d925a-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
