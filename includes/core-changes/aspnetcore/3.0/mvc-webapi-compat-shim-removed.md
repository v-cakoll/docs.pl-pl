---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393950"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Usunięto podkładkę zgodności interfejsu API sieci Web

Począwszy od ASP.NET Core `Microsoft.AspNetCore.Mvc.WebApiCompatShim` 3.0, pakiet nie jest już dostępny.

#### <a name="change-description"></a>Zmień opis

Pakiet `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) zapewnia częściową zgodność w ASP.NET Core z ASP.NET interfejsem API sieci Web 2 w celu uproszczenia migracji istniejących implementacji interfejsu Web API do ASP.NET Core. Jednak aplikacje korzystające z WebApiCompatShim nie korzystają z funkcji związanych z interfejsem API wysyłania w ostatnich wersjach ASP.NET Core. Takie funkcje obejmują ulepszone generowanie specyfikacji open API, znormalizowaną obsługę błędów i generowanie kodu klienta. Aby lepiej skoncentrować działania interfejsu API w 3.0, WebApiCompatShim został usunięty. Istniejące aplikacje używające WebApiCompatShim należy `[ApiController]` przeprowadzić migrację do nowszego modelu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Podkładka zgodności interfejsu API sieci Web była narzędziem migracji. Ogranicza dostęp użytkowników do nowych funkcji dodanych w ASP.NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Usuń użycie tej podkładki i migruj bezpośrednio do podobnej funkcji w samym ASP.NET Core.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
