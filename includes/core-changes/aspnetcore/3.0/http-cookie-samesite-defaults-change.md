---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282527"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: niektóre ustawienia domyślne SameSite pliku cookie zmieniły się na brak

`SameSite`jest opcją dla plików cookie, która może pomóc w ograniczeniu liczby ataków na wiele witryn (CSRF). W przypadku wybrania tej opcji, niespójne wartości domyślne są używane w różnych ASP.NET Core interfejsów API. Niespójność spowodowała mylące wyniki. W przypadku ASP.NET Core 3,0 te wartości domyślne są lepiej wyrównane. Należy zadecydować, aby ta funkcja była oparta na poszczególnych składnikach.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Podobne ASP.NET Core interfejsy API używają różnych <xref:Microsoft.AspNetCore.Http.SameSiteMode> wartości domyślnych. Przykład niespójności jest widoczny `HttpResponse.Cookies.Append(String, String)` w i `HttpResponse.Cookies.Append(String, String, CookieOptions)`, które domyślnie są odpowiednio `SameSiteMode.None` i. `SameSiteMode.Lax`

#### <a name="new-behavior"></a>Nowe zachowanie

Wszystkie interfejsy API, których to `SameSiteMode.None`dotyczy, mają domyślnie wartość.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wartość domyślna została zmieniona w celu utworzenia `SameSite` funkcji wyboru.

#### <a name="recommended-action"></a>Zalecana akcja

Każdy składnik, który emituje pliki cookie, musi `SameSite` zdecydować, czy jest odpowiedni dla scenariuszy. Przejrzyj używane interfejsy API i skonfiguruj je ponownie `SameSite` zgodnie z potrzebami.

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
