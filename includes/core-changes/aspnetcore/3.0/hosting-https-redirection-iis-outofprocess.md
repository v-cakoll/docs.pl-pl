---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937299"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hosting: przekierowanie HTTPS włączone dla aplikacji pozaprocesowych usług IIS

Wersja 13.0.19218.0 [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) do hostowania za pośrednictwem usług IIS poza procesem umożliwia istniejącą funkcję przekierowania HTTPS dla aplikacji ASP.NET Core 3.0 i 2.2.

Aby uzyskać do dyskusji, zobacz [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

ASP.NET Core 2.1 szablon projektu po raz pierwszy wprowadzono <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>obsługę metod pośredniczynienia HTTPS, takich jak i . Włączenie przekierowania HTTPS wymagało dodania konfiguracji, ponieważ aplikacje w programach nie używają domyślnego portu 443. [Protokół HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) jest aktywny tylko wtedy, gdy żądanie jest już przy użyciu protokołu HTTPS. Localhost jest pomijany domyślnie.

#### <a name="new-behavior"></a>Nowe zachowanie

W ASP.NET Core 3.0 [ulepszono](https://github.com/dotnet/AspNetCore/pull/4685)scenariusz HTTPS iIS . Dzięki ulepszeniu aplikacja może odnajdywać porty HTTPS serwera i domyślnie działać. `UseHttpsRedirection` Składnik w procesie dokonał odnajdywania portów za pomocą `IServerAddresses` funkcji, która ma wpływ tylko na ASP.NET aplikacji Core 3.0, ponieważ biblioteka w procesie jest wersjonowana przy pomocą struktury. Składnik poza procesem zmieniony w celu `ASPNETCORE_HTTPS_PORT` automatycznego dodawania zmiennej środowiskowej. Ta zmiana dotyczyła zarówno ASP.NET aplikacji Core 2.2 i 3.0, ponieważ składnik pozaprocesowy jest współużytkowany globalnie. ASP.NET nie ma to wpływu na aplikacje Core 2.1, ponieważ domyślnie używają poprzedniej wersji programu ANCM.

Poprzednie zachowanie zostało zmodyfikowane w ASP.NET Core 3.0.1 i 3.1.0 Preview 3, aby odwrócić zmiany zachowania w ASP.NET Core 2.x. Te zmiany dotyczą tylko aplikacji pozaprocesowych usług IIS.

Jak opisano powyżej, instalacja ASP.NET Core 3.0.0 miała `UseHttpsRedirection` efekt uboczny aktywowania pośrednieniu w ASP.NET aplikacjach Core 2.x. Zmiana została wdrożena do ANCM w ASP.NET Core 3.0.1 i 3.1.0 Preview 3 w taki sposób, że ich instalacja nie ma już tego wpływu na ASP.NET aplikacji Core 2.x. Zmienna środowiskowa, `ASPNETCORE_HTTPS_PORT` którą ancm wypełnił w ASP.NET `ASPNETCORE_ANCM_HTTPS_PORT` Core 3.0.0, została zmieniona na w ASP.NET Core 3.0.1 i 3.1.0 Preview 3. `UseHttpsRedirection`został również zaktualizowany w tych wersjach, aby zrozumieć zarówno nowe, jak i stare zmienne. ASP.NET Core 2.x nie zostanie zaktualizowany. W rezultacie powraca do poprzedniego zachowania jest domyślnie wyłączone.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ulepszona funkcjonalność ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Zalecana akcja

Nie jest wymagana żadna akcja, jeśli chcesz, aby wszyscy klienci używali protokołu HTTPS. Aby zezwolić niektórym klientom na korzystanie z protokołu HTTP, należy wykonać jedną z następujących czynności:

* Usuń wywołania `UseHttpsRedirection` `UseHsts` do i z `Startup.Configure` metody projektu i ponownie wdrożyć aplikację.
* W pliku *web.config* ustaw `ASPNETCORE_HTTPS_PORT` zmienną środowiskową na pusty ciąg. Ta zmiana może wystąpić bezpośrednio na serwerze bez ponownego wdrażania aplikacji. Przykład:

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection`nadal mogą być:

* Aktywowany ręcznie w ASP.NET Core 2.x, ustawiając zmienną `ASPNETCORE_HTTPS_PORT` środowiskową na odpowiedni numer portu (443 w większości scenariuszy produkcyjnych).
* Dezaktywowany w ASP.NET Core `ASPNETCORE_ANCM_HTTPS_PORT` 3.x przez zdefiniowanie z pustą wartością ciągu. Ta wartość jest ustawiona w taki `ASPNETCORE_HTTPS_PORT` sam sposób, jak w poprzednim przykładzie.

Komputery z ASP.NET aplikacjami Core 3.0.0 powinny zainstalować ASP.NET core 3.0.1 przed zainstalowaniem ASP.NET Core 3.1.0 Preview 3 ANCM. W ten sposób `UseHttpsRedirection` zapewnia, że nadal działa zgodnie z oczekiwaniami dla ASP.NET aplikacji Core 3.0.

W usłudze Azure App Service ancm wdraża na oddzielnym harmonogramie od czasu wykonywania ze względu na jego globalny charakter. Ancm został wdrożony na platformie Azure z tych zmian po ASP.NET Core 3.0.1 i 3.1.0 zostały wdrożone.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
