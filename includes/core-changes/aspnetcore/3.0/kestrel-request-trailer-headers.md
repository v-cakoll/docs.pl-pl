---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393908"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: Prośba nagłówków przyczepy przeniesiony do nowej kolekcji

W poprzednich wersjach Kestrel dodał http/1.1 fragmentowane nagłówki przyczepy do kolekcji nagłówków żądań, gdy treść żądania została odczytana do końca. To zachowanie wywołało obawy o niejednoznaczność między nagłówkami i przyczepami. Podjęto decyzję o przeniesieniu przyczep do nowej kolekcji.

Zwiastuny z prośbami HTTP/2 były niedostępne w ASP.NET Core 2.2, ale teraz są również dostępne w tej nowej kolekcji w ASP.NET Core 3.0.

Dodano nowe metody rozszerzania żądań, aby uzyskać dostęp do tych przyczep.

Przyczepy HTTP/1.1 są dostępne po przeczytaniu całego korpusu wniosku.

Przyczepy HTTP/2 są dostępne po otrzymaniu ich od klienta. Klient nie wyśle zwiastunów, dopóki cała treść żądania nie zostanie przynajmniej buforowana przez serwer. Może być konieczne odczytanie treści żądania, aby zwolnić miejsce w buforze. Przyczepy są zawsze dostępne, jeśli czytasz ciało wniosku do końca. Przyczepy oznaczają koniec nadwozia.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Nagłówki zwiastuna żądania zostaną `HttpRequest.Headers` dodane do kolekcji.

#### <a name="new-behavior"></a>Nowe zachowanie

Nagłówki zwiastunów żądania nie są `HttpRequest.Headers` **obecne** w kolekcji. Aby uzyskać do `HttpRequest` nich dostęp, użyj następujących metod rozszerzenia:

- `GetDeclaredTrailers()`- Pobiera żądanie "Trailer" nagłówek, który wyświetla, które przyczepy oczekiwać po ciele.
- `SupportsTrailers()`- Wskazuje, czy żądanie obsługuje odbieranie nagłówków przyczepy.
- `CheckTrailersAvailable()`- Określa, czy żądanie obsługuje przyczepy i czy są one dostępne do odczytu.
- `GetTrailer(string trailerName)`- Pobiera żądanego końcowego nagłówka z odpowiedzi.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Przyczepy są kluczową cechą w scenariuszach takich jak gRPC. Scalanie przyczep w celu żądania nagłówków było mylące dla użytkowników.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj metod rozszerzenia związanych z `HttpRequest` przyczepą, aby uzyskać dostęp do przyczep.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
