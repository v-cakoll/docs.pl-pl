---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282527"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: Niektóre ustawienia domyślne tej samej witryny zostały zmienione na Brak

`SameSite`jest opcją dla plików cookie, które mogą pomóc w ograniczeniu niektórych ataków csrf (Cross-Site Request Forgery). Gdy ta opcja została początkowo wprowadzona, niespójne wartości domyślne były używane w różnych ASP.NET podstawowych interfejsów API. Niespójność doprowadziła do mylących wyników. Od ASP.NET Core 3.0 te wartości domyślne są lepiej wyrównane. Należy wyrazić zgodę na tę funkcję na podstawie pojmą.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Podobne ASP.NET podstawowe interfejsy <xref:Microsoft.AspNetCore.Http.SameSiteMode> API używały różnych wartości domyślnych. Przykład niespójności jest widoczny `HttpResponse.Cookies.Append(String, String)` w `HttpResponse.Cookies.Append(String, String, CookieOptions)`i , `SameSiteMode.None` które `SameSiteMode.Lax`domyślnie do i , odpowiednio.

#### <a name="new-behavior"></a>Nowe zachowanie

Wszystkie interfejsy API, których dotyczy problem, domyślnie . `SameSiteMode.None`

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wartość domyślna została `SameSite` zmieniona, aby wprowadzić funkcję opt-in.

#### <a name="recommended-action"></a>Zalecana akcja

Każdy składnik, który emituje pliki `SameSite` cookie musi zdecydować, czy jest odpowiedni dla jego scenariuszy. Przejrzyj użycie interfejsów API, których dotyczy problem, i ponownie skonfiguruj `SameSite` w razie potrzeby.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
