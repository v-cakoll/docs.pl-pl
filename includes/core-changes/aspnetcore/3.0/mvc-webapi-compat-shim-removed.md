---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393950"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Usunięto podkładkę zgodności z interfejsem API sieci Web

Począwszy od ASP.NET Core 3,0, pakiet `Microsoft.AspNetCore.Mvc.WebApiCompatShim` nie jest już dostępny.

#### <a name="change-description"></a>Zmień opis

Pakiet `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) zapewnia częściową zgodność ASP.NET Core z ASP.NET 4. x Web API 2, aby uprościć migrację istniejących implementacji interfejsów API sieci Web do ASP.NET Core. Jednak aplikacje korzystające z WebApiCompatShim nie korzystają z funkcji związanych z interfejsem API wysyłanych w ostatnich wersjach ASP.NET Core. Takie funkcje obejmują ulepszoną generację funkcji tworzenia specyfikacji interfejsu API, ustandaryzowaną obsługę błędów i generowanie kodu klienta. Aby lepiej skupić się na działaniach interfejsu API w 3,0, WebApiCompatShim został usunięty. Istniejące aplikacje używające WebApiCompatShim powinny migrować do nowszego modelu `[ApiController]`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Podkładka zgodności z interfejsem API sieci Web była narzędziem do migracji. Ogranicza użytkownikowi dostęp do nowych funkcji dodanych w ASP.NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Usuń użycie tej podkładki i Przeprowadź migrację bezpośrednio do podobnych funkcji w programie ASP.NET Core.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
