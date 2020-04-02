---
title: Konfiguracja aplikacji
description: Dowiedz się, jak skonfigurować aplikacje Blazor bez użycia ConfigurationManager.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588247"
---
# <a name="app-configuration"></a>Konfiguracja aplikacji

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Podstawowym sposobem ładowania konfiguracji aplikacji w formularzach sieci Web są&mdash;wpisy w pliku *web.config* na serwerze lub powiązany plik konfiguracyjny, do którego odwołuje się *plik web.config*. Obiekt statyczny `ConfigurationManager` służy do interakcji z ustawieniami aplikacji, ciągami połączeń repozytorium danych i innymi dostawcami konfiguracji rozszerzonej, które są dodawane do aplikacji. Typowe jest, aby zobaczyć interakcje z konfiguracją aplikacji, jak widać w poniższym kodzie:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

W przypadku ASP.NET Core i blazora po stronie serwera plik *web.config* może być obecny, jeśli aplikacja jest hostowana na serwerze Windows IIS. Jednak nie ma `ConfigurationManager` interakcji z tej konfiguracji i można odbierać więcej konfiguracji aplikacji strukturalnych z innych źródeł. Przyjrzyjmy się, jak konfiguracja jest zbierana i jak nadal można uzyskać dostęp do informacji o konfiguracji z pliku *web.config.*

## <a name="configuration-sources"></a>Źródła konfiguracji

ASP.NET Core rozpoznaje, że istnieje wiele źródeł konfiguracji, których możesz użyć dla swojej aplikacji. Struktura próbuje zaoferować najlepsze z tych funkcji domyślnie. Konfiguracja jest odczytywana i agregowana z tych różnych źródeł przez ASP.NET Core. Później załadowane wartości dla tego samego klucza konfiguracji mają pierwszeństwo przed wcześniejszymi wartościami.

ASP.NET Core został zaprojektowany tak, aby był świadomy chmury i ułatwiał konfigurację aplikacji zarówno operatorom, jak i deweloperom. ASP.NET Core jest świadomy środowiska i wie, czy działa `Production` `Development` w Twoim lub środowisku. Wskaźnik środowiska jest ustawiony `ASPNETCORE_ENVIRONMENT` w zmiennej środowiskowej systemu. Jeśli żadna wartość nie jest skonfigurowana, `Production` domyślnie aplikacja działa w środowisku.

Aplikacja może wyzwalać i dodawać konfigurację z kilku źródeł na podstawie nazwy środowiska. Domyślnie konfiguracja jest ładowana z następujących zasobów w podanej kolejności:

1. *appsettings.json,* jeśli jest obecny
1. *appsettings. {ENVIRONMENT_NAME}.json,* jeśli jest obecny
1. Plik wpisów tajnych użytkownika na dysku, jeśli jest obecny
1. Zmienne środowiskowe
1. Argumenty wiersza polecenia

## <a name="appsettingsjson-format-and-access"></a>appsettings.json format i dostęp

Plik *appsettings.json* może być hierarchiczny z wartościami ustrukturyzowanymi w następujący sposób:

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

Po przedstawieniu z poprzednim JSON, system konfiguracji spłaszcza wartości podrzędne i odwołuje się do ich w pełni kwalifikowanych ścieżek hierarchicznych. Dwukropek`:`( ) oddziela każdą właściwość w hierarchii. Na przykład klucz `section1:key0` konfiguracji uzyskuje `section1` dostęp do `key0` wartości literału obiektu.

## <a name="user-secrets"></a>Wpisy tajne użytkownika

Wpisy tajne użytkownika to:

* Wartości konfiguracji, które są przechowywane w pliku JSON na stacji roboczej dewelopera, poza folderem tworzenia aplikacji.
* Ładowany tylko `Development` podczas pracy w środowisku.
* Skojarzone z określoną aplikacją.
* Zarządzane za pomocą `user-secrets` polecenia .NET Core CLI.

Skonfiguruj aplikację dla magazynu `user-secrets` wpisów tajnych, wykonując polecenie:

```dotnetcli
dotnet user-secrets init
```

Poprzednie polecenie dodaje `UserSecretsId` element do pliku projektu. Element zawiera identyfikator GUID, który jest używany do kojarzenia wpisów tajnych z aplikacją. Następnie można zdefiniować klucz `set` tajny za pomocą polecenia. Przykład:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

Poprzednie polecenie udostępnia `Parent:ApiKey` klucz konfiguracji na stacji roboczej dewelopera `12345`o wartości .

Aby uzyskać więcej informacji na temat tworzenia, przechowywania i zarządzania wpisami tajnymi użytkowników, zobacz [Bezpieczne przechowywanie wpisów tajnych aplikacji w rozwoju w dokumencie ASP.NET Core.](/aspnet/core/security/app-secrets)

## <a name="environment-variables"></a>Zmienne środowiskowe

Następny zestaw wartości załadowanych do konfiguracji aplikacji to zmienne środowiskowe systemu. Wszystkie ustawienia zmiennych środowiskowych systemu są teraz dostępne za pośrednictwem interfejsu API konfiguracji. Wartości hierarchiczne są spłaszczane i oddzielone znakami dwukropek podczas odczytu wewnątrz aplikacji. Jednak niektóre systemy operacyjne nie zezwalają na nazwy zmiennych środowiska znaków dwukropka. ASP.NET Core rozwiązuje to ograniczenie, konwertując wartości,`__`które mają podwójne podkreślenia ( ) na dwukropek, gdy są dostępne. Wartość `Parent:ApiKey` z sekcji wpisów tajnych użytkownika powyżej można `Parent__ApiKey`zastąpić zmienną środowiskową .

## <a name="command-line-arguments"></a>Argumenty wiersza polecenia

Konfigurację można również podać jako argumenty wiersza polecenia po uruchomieniu aplikacji. Użyj notacji double-dash (`--`)`/`lub forward-slash ( ( ), aby wskazać nazwę ustawionej wartości konfiguracji i wartość, która ma być skonfigurowana. Składnia przypomina następujące polecenia:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Powrót web.config

Jeśli aplikacja została wdrożona w systemie Windows w serwisach IIS, plik *web.config* nadal konfiguruje usługi IIS do zarządzania aplikacją. Domyślnie iIS dodaje odwołanie do ASP.NET Core Module (ANCM). ANCM to natywny moduł usług IIS, który obsługuje aplikację zamiast serwera sieci Web Kestrel. Ta sekcja *web.config* przypomina następujące znaczniki XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

Konfiguracja specyficzne dla aplikacji można `environmentVariables` zdefiniować `aspNetCore` przez zagnieżdżanie elementu w elemencie. Wartości zdefiniowane w tej sekcji są przedstawiane aplikacji ASP.NET Core jako zmienne środowiskowe. Zmienne środowiskowe ładują się odpowiednio podczas tego segmentu uruchamiania aplikacji.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>Odczyt konfiguracji w aplikacji

ASP.NET Core zapewnia konfigurację <xref:Microsoft.Extensions.Configuration.IConfiguration> aplikacji za pośrednictwem interfejsu. Ten interfejs konfiguracyjny powinien być wymagany przez składniki Blazora, strony Blazora i wszelkie inne ASP.NET klasy zarządzanej przez core, która wymaga dostępu do konfiguracji. Struktura ASP.NET Core automatycznie wypełni ten interfejs wcześniej skonfigurowaną konfiguracją rozwiązaną. Na stronie Blazor lub narzutów Razor składnika można `IConfiguration` wstrzyknąć obiekt z dyrektywą `@inject` u góry pliku *.brzytwa* w ten sposób:

```razor
@inject IConfiguration Configuration
```

Ta poprzednia instrukcja udostępnia `IConfiguration` `Configuration` obiekt jako zmienną w pozostałej części szablonu Razor.

Poszczególne ustawienia konfiguracji można odczytać, określając hierarchię ustawień konfiguracji poszukiwaną jako parametr indeksatora:

```csharp
var mySetting = Configuration["section1:key0"];
```

Można pobrać całe sekcje konfiguracji <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> przy użyciu metody, aby pobrać kolekcję kluczy w `GetSection("section1")` określonej lokalizacji ze składnią podobną do pobierania konfiguracji dla sekcji 1 z wcześniejszego przykładu.

## <a name="strongly-typed-configuration"></a>Konfiguracja silnie typizowana

Za pomocą formularzy sieci Web można było utworzyć silnie typ <xref:System.Configuration.ConfigurationSection> konfiguracji, który dziedziczył z typu i skojarzonych typów. A `ConfigurationSection` można skonfigurować niektóre reguły biznesowe i przetwarzania dla tych wartości konfiguracji.

W ASP.NET Core można określić hierarchię klas, która będzie odbierać wartości konfiguracji. Klasy te:

* Nie trzeba dziedziczyć z klasy nadrzędnej.
* Powinien `public` zawierać właściwości, które pasują do właściwości i odwołania do typu dla struktury konfiguracji, którą chcesz przechwycić.

W przypadku wcześniejszego przykładu *appsettings.json* można zdefiniować następujące klasy do przechwytywania wartości:

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

Tę hierarchię klas można wypełnić, dodając `Startup.ConfigureServices` następujący wiersz do metody:

```csharp
services.Configure<MyConfig>(Configuration);
```

W pozostałej części aplikacji można dodać parametr wejściowy `@inject` do klas lub dyrektywy `IOptions<MyConfig>` w szablonach razor typu, aby otrzymać silnie wpisane ustawienia konfiguracji. Właściwość `IOptions<MyConfig>.Value` przyniesie `MyConfig` wartość wypełniona z ustawień konfiguracji.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Więcej informacji na temat funkcji Opcje można znaleźć we [wzorcu Opcje w](/aspnet/core/fundamentals/configuration/options#options-interfaces) dokumencie ASP.NET Core.

>[!div class="step-by-step"]
>[Poprzedni](middleware.md)
>[następny](security-authentication-authorization.md)
