---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393908"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: przeniesiono nagłówki przyczepki do nowej kolekcji

We wcześniejszych wersjach Kestrel dodaliśmy nagłówki podzielonych punktów protokołu HTTP/1.1 do kolekcji nagłówków żądań, gdy treść żądania została odczytana na końcu. Takie zachowanie powodowało obawy dotyczące niejednoznaczności między nagłówkami i przyczepami. Podjęto decyzję o przeniesieniu przyczep do nowej kolekcji.

W ASP.NET Core 2,2 są niedostępne Wszystkie przyczepy z żądaniami HTTP/2, ale są teraz również dostępne w tej nowej kolekcji w ASP.NET Core 3,0.

Dodano nowe metody rozszerzenia żądania w celu uzyskania dostępu do tych przyczep.

Przyczepy protokołu HTTP/1.1 są dostępne po odczytaniu całej treści żądania.

Przyczepy protokołu HTTP/2 są dostępne po odebraniu ich od klienta. Klient nie wyśle przyczep do momentu, gdy cała treść żądania nie będzie co najmniej buforowana przez serwer. Może być konieczne odczytanie treści żądania w celu zwolnienia miejsca w buforze. Przyczepy są zawsze dostępne w przypadku odczytywania treści żądania na końcu. Przyczepy oznaczają koniec treści.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Nagłówki przyczepy z żądaniem zostaną dodane do kolekcji `HttpRequest.Headers`.

#### <a name="new-behavior"></a>Nowe zachowanie

Nagłówki przyczepy z żądaniem **nie znajdują** się w kolekcji `HttpRequest.Headers`. Aby uzyskiwać dostęp do nich, użyj następujących metod rozszerzających `HttpRequest`:

- `GetDeclaredTrailers()` — pobiera nagłówek "Przyczepka" żądania, który zawiera listę przyczep, które mają być oczekiwane po treści.
- `SupportsTrailers()`-wskazuje, czy żądanie obsługuje nagłówki przyczepy.
- `CheckTrailersAvailable()` — Określa, czy żądanie obsługuje przyczepy i czy są dostępne do odczytu.
- `GetTrailer(string trailerName)` — pobiera żądany końcowy nagłówek z odpowiedzi.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Przyczepy są kluczową funkcją w scenariuszach takich jak gRPC. Scalanie przyczep w programie w celu utworzenia nagłówków żądań było mylące dla użytkowników.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj metod rozszerzenia związanych z przyczepą w `HttpRequest`, aby uzyskać dostęp do przyczep.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
