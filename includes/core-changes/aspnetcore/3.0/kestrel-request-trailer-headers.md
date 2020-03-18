---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393908"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="0546e-101">Kestrel: Prośba nagłówków przyczepy przeniesiony do nowej kolekcji</span><span class="sxs-lookup"><span data-stu-id="0546e-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="0546e-102">W poprzednich wersjach Kestrel dodał http/1.1 fragmentowane nagłówki przyczepy do kolekcji nagłówków żądań, gdy treść żądania została odczytana do końca.</span><span class="sxs-lookup"><span data-stu-id="0546e-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="0546e-103">To zachowanie wywołało obawy o niejednoznaczność między nagłówkami i przyczepami.</span><span class="sxs-lookup"><span data-stu-id="0546e-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="0546e-104">Podjęto decyzję o przeniesieniu przyczep do nowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0546e-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="0546e-105">Zwiastuny z prośbami HTTP/2 były niedostępne w ASP.NET Core 2.2, ale teraz są również dostępne w tej nowej kolekcji w ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0546e-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="0546e-106">Dodano nowe metody rozszerzania żądań, aby uzyskać dostęp do tych przyczep.</span><span class="sxs-lookup"><span data-stu-id="0546e-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="0546e-107">Przyczepy HTTP/1.1 są dostępne po przeczytaniu całego korpusu wniosku.</span><span class="sxs-lookup"><span data-stu-id="0546e-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="0546e-108">Przyczepy HTTP/2 są dostępne po otrzymaniu ich od klienta.</span><span class="sxs-lookup"><span data-stu-id="0546e-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="0546e-109">Klient nie wyśle zwiastunów, dopóki cała treść żądania nie zostanie przynajmniej buforowana przez serwer.</span><span class="sxs-lookup"><span data-stu-id="0546e-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="0546e-110">Może być konieczne odczytanie treści żądania, aby zwolnić miejsce w buforze.</span><span class="sxs-lookup"><span data-stu-id="0546e-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="0546e-111">Przyczepy są zawsze dostępne, jeśli czytasz ciało wniosku do końca.</span><span class="sxs-lookup"><span data-stu-id="0546e-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="0546e-112">Przyczepy oznaczają koniec nadwozia.</span><span class="sxs-lookup"><span data-stu-id="0546e-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0546e-113">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0546e-113">Version introduced</span></span>

<span data-ttu-id="0546e-114">3.0</span><span class="sxs-lookup"><span data-stu-id="0546e-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0546e-115">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="0546e-115">Old behavior</span></span>

<span data-ttu-id="0546e-116">Nagłówki zwiastuna żądania zostaną `HttpRequest.Headers` dodane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0546e-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0546e-117">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="0546e-117">New behavior</span></span>

<span data-ttu-id="0546e-118">Nagłówki zwiastunów żądania nie są `HttpRequest.Headers` **obecne** w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0546e-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="0546e-119">Aby uzyskać do `HttpRequest` nich dostęp, użyj następujących metod rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="0546e-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="0546e-120">`GetDeclaredTrailers()`- Pobiera żądanie "Trailer" nagłówek, który wyświetla, które przyczepy oczekiwać po ciele.</span><span class="sxs-lookup"><span data-stu-id="0546e-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="0546e-121">`SupportsTrailers()`- Wskazuje, czy żądanie obsługuje odbieranie nagłówków przyczepy.</span><span class="sxs-lookup"><span data-stu-id="0546e-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="0546e-122">`CheckTrailersAvailable()`- Określa, czy żądanie obsługuje przyczepy i czy są one dostępne do odczytu.</span><span class="sxs-lookup"><span data-stu-id="0546e-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="0546e-123">`GetTrailer(string trailerName)`- Pobiera żądanego końcowego nagłówka z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="0546e-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0546e-124">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="0546e-124">Reason for change</span></span>

<span data-ttu-id="0546e-125">Przyczepy są kluczową cechą w scenariuszach takich jak gRPC.</span><span class="sxs-lookup"><span data-stu-id="0546e-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="0546e-126">Scalanie przyczep w celu żądania nagłówków było mylące dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0546e-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0546e-127">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="0546e-127">Recommended action</span></span>

<span data-ttu-id="0546e-128">Użyj metod rozszerzenia związanych z `HttpRequest` przyczepą, aby uzyskać dostęp do przyczep.</span><span class="sxs-lookup"><span data-stu-id="0546e-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="0546e-129">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0546e-129">Category</span></span>

<span data-ttu-id="0546e-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0546e-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0546e-131">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0546e-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
