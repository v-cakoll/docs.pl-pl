---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937299"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hosting: włączono przekierowywanie protokołu HTTPS dla aplikacji pozaprocesowych usług IIS

Wersja 13.0.19218.0 [modułu ASP.NET Core (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) do hostingu za pośrednictwem usług IIS umożliwia korzystanie z istniejącej funkcji przekierowywania HTTPS dla aplikacji ASP.NET Core 3,0 i 2,2.

Aby zapoznać się z omówieniem, zobacz [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Szablon projektu ASP.NET Core 2,1 został po raz pierwszy wprowadzony do obsługi metod oprogramowania pośredniczącego HTTPS, takich jak <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> i <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>. Włączenie przekierowania HTTPS wymaga dodania konfiguracji, ponieważ aplikacje w trakcie tworzenia nie używają domyślnego portu 443. [Protokół HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) jest aktywny tylko wtedy, gdy żądanie już korzysta z protokołu HTTPS. Domyślnie pominięto hosta lokalnego.

#### <a name="new-behavior"></a>Nowe zachowanie

W ASP.NET Core 3,0 scenariusz HTTPS usług IIS został [ulepszony](https://github.com/dotnet/AspNetCore/pull/4685). Dzięki ulepszeniu aplikacja może odnaleźć porty HTTPS serwera i wprowadzić `UseHttpsRedirection` pracy domyślnie. Składnik w procesie przetworzył odnajdywanie portów przy użyciu funkcji `IServerAddresses`, która ma wpływ tylko na aplikacje ASP.NET Core 3,0, ponieważ biblioteka w procesie ma wersję z platformą. Składnik pozaprocesowe został zmieniony, aby automatycznie dodać zmienną środowiskową `ASPNETCORE_HTTPS_PORT`. Ta zmiana dotyczyła zarówno aplikacji ASP.NET Core 2,2, jak i 3,0, ponieważ składnik pozaprocesowe jest współużytkowany globalnie. Nie ma to wpływu na aplikacje ASP.NET Core 2,1, ponieważ domyślnie korzystają z wcześniejszej wersji ANCM.

Powyższe zachowanie zostało zmodyfikowane w ASP.NET Core 3.0.1 i 3.1.0 w wersji zapoznawczej 3 w celu odwrócenia zmiany zachowania w ASP.NET Core 2. x. Zmiany te mają wpływ tylko na aplikacje pozaprocesowe w programie IIS.

Jak opisano powyżej, instalacja ASP.NET Core 3.0.0 miała efekt uboczny aktywowania `UseHttpsRedirection` oprogramowania pośredniczącego w aplikacjach ASP.NET Core 2. x. Wprowadzono zmianę w ANCM w ASP.NET Core 3.0.1 i 3.1.0 Preview 3, która nie ma już wpływu na aplikacje ASP.NET Core 2. x. Zmienna środowiskowa `ASPNETCORE_HTTPS_PORT` ANCM wprowadzona w ASP.NET Core 3.0.0 została zmieniona na `ASPNETCORE_ANCM_HTTPS_PORT` w ASP.NET Core 3.0.1 i 3.1.0 Preview 3. `UseHttpsRedirection` został także zaktualizowany w tych wersjach, aby zrozumieć zarówno nowe, jak i stare zmienne. ASP.NET Core 2. x nie zostanie zaktualizowany. W związku z tym przywraca poprzednie zachowanie, które jest domyślnie wyłączone.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ulepszona funkcja ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli chcesz, aby wszyscy klienci korzystali z protokołu HTTPS, nie jest wymagana żadna akcja. Aby umożliwić niektórym klientom korzystanie z protokołu HTTP, wykonaj jedną z następujących czynności:

* Usuń wywołania `UseHttpsRedirection` i `UseHsts` z metody `Startup.Configure` projektu i ponownie Wdróż aplikację.
* W pliku *Web. config* Ustaw zmienną środowiskową `ASPNETCORE_HTTPS_PORT` na pusty ciąg. Ta zmiana może wystąpić bezpośrednio na serwerze bez ponownego wdrażania aplikacji. Na przykład:

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection` nadal można:

* Aktywowane ręcznie w ASP.NET Core 2. x przez ustawienie zmiennej środowiskowej `ASPNETCORE_HTTPS_PORT` na odpowiedni numer portu (443 w większości scenariuszy produkcyjnych).
* Zdezaktywowane w ASP.NET Core 3. x przez zdefiniowanie `ASPNETCORE_ANCM_HTTPS_PORT` z pustą wartością ciągu. Ta wartość jest ustawiana w taki sam sposób jak w przypadku powyższego przykładu `ASPNETCORE_HTTPS_PORT`.

Maszyny, na których uruchomiono ASP.NET Core aplikacje 3.0.0, powinny zainstalować środowisko uruchomieniowe ASP.NET Core 3.0.1 przed zainstalowaniem ASP.NET Core 3.1.0 Preview 3 ANCM. Dzięki temu `UseHttpsRedirection` nadal działać zgodnie z oczekiwaniami dla aplikacji ASP.NET Core 3,0.

W Azure App Service ANCM wdraża w osobnym harmonogramie z poziomu środowiska uruchomieniowego z powodu jego globalnego charakteru. ANCM został wdrożony na platformie Azure z tymi zmianami po wdrożeniu ASP.NET Core 3.0.1 i 3.1.0.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
