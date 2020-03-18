---
title: Struktura projektu dla aplikacji Blazor
description: Dowiedz się, jak porównywane są struktury projektów ASP.NET Web Forms i Blazor.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401579"
---
# <a name="project-structure-for-blazor-apps"></a>Struktura projektu dla aplikacji Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Pomimo znacznych różnic w strukturze projektu, ASP.NET Web Forms i Blazor mają wiele podobnych koncepcji. Tutaj przyjrzymy się strukturze projektu Blazora i porównamy go z projektem ASP.NET Web Forms.

Aby utworzyć pierwszą aplikację Blazor, postępuj zgodnie z instrukcjami w [krokach rozpoczęcia pracy blazora.](/aspnet/core/blazor/get-started) Możesz postępować zgodnie z instrukcjami, aby utworzyć aplikację Blazor Server lub aplikację Blazor WebAssembly hostowane w ASP.NET Core. Z wyjątkiem logiki specyficzne dla modelu hostingu, większość kodu w obu projektach jest taka sama.

## <a name="project-file"></a>Plik projektu

Aplikacje Blazor Server to projekty .NET Core. Plik projektu dla aplikacji Blazor Server jest tak prosty, jak to tylko możliwe:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Plik projektu dla aplikacji Blazor WebAssembly wygląda nieco bardziej zaangażowany (dokładne numery wersji mogą się różnić):

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

Projekty Blazor WebAssembly są przeznaczone dla standardu .NET zamiast .NET Core, ponieważ są uruchamiane w przeglądarce w czasie wykonywania platformy WebAssembly opartej na ustom .NET. Nie można zainstalować programu .NET w przeglądarce sieci Web, tak jak na serwerze lub komputerze dewelopera. W związku z tym projekt odwołuje się do struktury Blazor przy użyciu poszczególnych odwołań do pakietów.

Dla porównania, domyślny projekt ASP.NET Web Forms zawiera prawie 300 wierszy XML w pliku *csproj,* z których większość jawnie wyświetla listę różnych plików kodu i zawartości w projekcie. Wiele uproszczeń w projektach opartych na standardzie .NET Core i .NET pochodzi z domyślnych `Microsoft.NET.Sdk.Web` obiektów docelowych i właściwości importowanych przez odwoływanie się do sdk, często określanego jako po prostu internetowy zestaw SDK. Internetowy zestaw SDK zawiera symbole wieloznaczne i inne udogodnienia, które upraszczają dołączanie do projektu plików kodu i zawartości. Nie trzeba jawnie wyświetlać listę plików. Podczas określania wartości docelowej .NET Core, web SDK dodaje również odwołania do struktury platformy .NET Core i ASP.NET Core udostępnionych. Struktury są widoczne z węzła**Struktury** **zależności** > w oknie **Eksploratora rozwiązań.** Struktury udostępnione są kolekcje zestawów, które zostały zainstalowane na komputerze podczas instalowania .NET Core.

Mimo że są one obsługiwane, poszczególne odwołania do zestawu są mniej typowe w projektach .NET Core. Większość zależności projektu są obsługiwane jako odwołania nuget pakietu. W projektach programu .NET Core należy odwoływać się tylko do zależności od zależności pakietów najwyższego poziomu. Zależności przechodnie są uwzględniane automatycznie. Zamiast używać pliku *packages.config* powszechnie spotykanego w projektach ASP.NET Web Forms do odwoływania `<PackageReference>` się do pakietów, odwołania do pakietów są dodawane do pliku projektu przy użyciu elementu.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Punkt wejścia

Punkt wejścia aplikacji Blazor Server jest zdefiniowany w *pliku Program.cs,* jak widać w aplikacji Konsola. Gdy aplikacja jest wykonywana, tworzy i uruchamia wystąpienie hosta sieci web przy użyciu ustawień domyślnych specyficznych dla aplikacji sieci web. Host internetowy zarządza cyklem życia aplikacji Blazor Server i konfiguruje usługi na poziomie hosta. Przykładami takich usług są konfiguracja, rejestrowanie, wstrzykiwanie zależności i serwer HTTP. Kod ten jest w większości standardowy i często pozostaje bez zmian.

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

Aplikacje Blazor WebAssembly definiują również punkt wejścia w *Program.cs*. Kod wygląda nieco inaczej. Kod jest podobny, ponieważ konfiguruje hosta aplikacji w celu świadczenia tych samych usług na poziomie hosta dla aplikacji. Host aplikacji WebAssembly nie konfiguruje jednak serwera HTTP, ponieważ jest wykonywany bezpośrednio w przeglądarce.

Aplikacje Blazor `Startup` mają klasę zamiast pliku *Global.asax,* aby zdefiniować logikę uruchamiania aplikacji. Klasa `Startup` służy do konfigurowania aplikacji i dowolnych usług specyficznych dla aplikacji. W aplikacji Blazor Server `Startup` klasa jest używana do konfigurowania punktu końcowego dla połączenia w czasie rzeczywistym używanego przez Blazora między przeglądarkami klienta a serwerem. W aplikacji Blazor WebAssembly `Startup` klasa definiuje składniki główne aplikacji i gdzie powinny być renderowane. Przyjrzymy się głębiej `Startup` klasie w sekcji [uruchamiania aplikacji.](./app-startup.md)

## <a name="static-files"></a>Pliki statyczne

W przeciwieństwie do projektów ASP.NET Web Forms, nie wszystkie pliki w projekcie Blazor mogą być wymagane jako pliki statyczne. Tylko pliki w folderze *wwwroot* można adresować w sieci Web. Ten folder jest określany jako "katalog główny sieci Web" aplikacji. Wszystko poza katalogiem głównym aplikacji *nie jest* adresowalne w sieci Web. Ta konfiguracja zapewnia dodatkowy poziom zabezpieczeń, który zapobiega przypadkowemu ujawnieniu plików projektu w sieci Web.

## <a name="configuration"></a>Konfigurowanie

Konfiguracja w aplikacjach ASP.NET formularzy sieci Web jest zazwyczaj obsługiwana przy użyciu jednego lub większej liczby plików *web.config.* Aplikacje Blazor zazwyczaj nie mają plików *web.config.* Jeśli tak, plik jest używany tylko do konfigurowania ustawień specyficznych dla usług IIS, gdy są hostowane w usianych przez usługi IIS. Zamiast tego aplikacje Blazor Server używają abstrakcji konfiguracji ASP.NET Core (aplikacje Blazor WebAssembly nie obsługują obecnie tych samych abstrakcji konfiguracji, ale może to być funkcja dodana w przyszłości). Na przykład domyślna aplikacja Blazor Server przechowuje niektóre ustawienia w *appsettings.json*.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

Dowiemy się więcej o konfiguracji w ASP.NET projektów podstawowych w [sekcji Konfiguracja.](./config.md)

## <a name="razor-components"></a>Elementy maszynki do golenia

Większość plików w projektach Blazor a *plikami .brzytwa.* Razor jest językiem szablonów opartym na html i C#, który jest używany do dynamicznego generowania interfejsu użytkownika w sieci Web. *Pliki .brzytwa* definiują składniki, które tworzą interfejsu aplikacji. W przeważającej części składniki są identyczne zarówno dla blazor server i Blazor WebAssembly aplikacji. Składniki w blazorze są analogiczne do formantów użytkownika w ASP.NET formularzach sieci Web.

Każdy plik składnika Razor jest kompilowany do klasy .NET, gdy projekt jest zbudowany. Wygenerowana klasa przechwytuje stan składnika, logikę renderowania, metody cyklu życia, programy obsługi zdarzeń i inną logikę. Przyjrzymy się tworzeniu komponentów w [sekcji Building wielokrotnego użytku z blazorem.](./components.md)

Pliki *_Imports.razor* nie są plikami komponentu Razor. Zamiast tego definiują zestaw dyrektyw Razor do zaimportowania do innych plików *.razor* w tym samym folderze i w jego podfolderach. Na przykład plik *_Imports.razor* jest konwencjonalnym `using` sposobem dodawania instrukcji dla często używanych obszarów nazw:

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a>Strony

Gdzie są strony w aplikacjach Blazor? Blazor nie definiuje oddzielnego rozszerzenia pliku dla adresowalnych stron, takich jak pliki *.aspx* w aplikacjach ASP.NET Web Forms. Zamiast tego strony są definiowane przez przypisywanie tras do komponentów. Trasa jest zazwyczaj przypisana przy użyciu dyrektywy `@page` Razor. Na przykład `Counter` komponent, który jest autorem pliku *Pages/Counter.razor,* definiuje następującą trasę:

```razor
@page "/counter"
```

Routing w Blazor jest obsługiwany po stronie klienta, a nie na serwerze. Gdy użytkownik nawiguje w przeglądarce, Blazor przechwytuje nawigację, a następnie renderuje komponent z pasującą trasą.

Trasy składników nie są obecnie wywnioskowane przez lokalizację pliku składnika, tak jak w nich znajdują się w odniesieniu do stron *.aspx.* Ta funkcja może zostać dodana w przyszłości. Każda trasa musi być określona jawnie na składniku. Przechowywanie składników routingu w folderze *Strony* nie ma specjalnego znaczenia i jest wyłącznie konwencją.

Przyjrzymy się bardziej szczegółowo routingu w Blazor w [sekcji Strony, routing i układy.](./pages-routing-layouts.md)

## <a name="layout"></a>Układ

W ASP.NET aplikacjach formularzy sieci Web wspólny układ strony jest obsługiwany przy użyciu stron wzorcowych *(Site.Master).* W aplikacjach Blazor układ strony jest obsługiwany przy użyciu składników układu *(Shared/MainLayout.brzytwa).* Składniki układu zostaną omówione bardziej szczegółowo w sekcji [Strona, routing i układy.](./pages-routing-layouts.md)

## <a name="bootstrap-blazor"></a>Bootstrap Blazor

Aby bootstrap Blazor, aplikacja musi:

- Określ, gdzie na stronie powinien być renderowany składnik główny *(App.Razor).*
- Dodaj odpowiedni skrypt struktury Blazora.

W aplikacji Blazor Server strona hosta składnika głównego jest zdefiniowana w pliku *_Host.cshtml.* Ten plik definiuje stronę razor, a nie składnik. Strony razor używają składni Razor do definiowania strony adresowalnej serwera, bardzo podobnej do strony *.aspx.* Metoda `Html.RenderComponentAsync<TComponent>(RenderMode)` służy do definiowania, gdzie powinien być renderowany składnik na poziomie głównym. Opcja `RenderMode` wskazuje sposób, w jaki składnik powinien być renderowany. W poniższej tabeli przedstawiono `RenderMode` obsługiwane opcje.

|Opcja                        |Opis       |
|------------------------------|------------------|
|`RenderMode.Server`           |Renderowane interaktywnie po nawiązaniu połączenia z przeglądarką|
|`RenderMode.ServerPrerendered`|Najpierw wstępnie renderowane, a następnie renderowane interaktywnie|
|`RenderMode.Static`           |Renderowane jako zawartość statyczna|

Odwołanie do skryptu *do _framework/blazor.server.js* ustanawia połączenie w czasie rzeczywistym z serwerem, a następnie zajmuje się wszystkimi interakcjami użytkownika i aktualizacjami interfejsu użytkownika.

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

W aplikacji Blazor WebAssembly strona hosta jest prostym statycznym plikiem HTML w obszarze *wwwroot/index.html*. Element `<app>` służy do wskazania, gdzie powinien być renderowany składnik główny.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

Określony składnik do renderowania jest skonfigurowany `Startup.Configure` w metodzie aplikacji za pomocą odpowiedniego selektora CSS wskazującego, gdzie składnik powinien być renderowany.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a>Tworzenie danych wyjściowych

Po zbudowaniu projektu Blazor wszystkie pliki składowe i kodowe Razor są kompilowane w jeden zespół. W przeciwieństwie do projektów ASP.NET Web Forms Blazor nie obsługuje kompilacji interfejsu użytkownika w czasie wykonywania.

## <a name="run-the-app"></a>Uruchomienie aplikacji

Aby uruchomić aplikację Blazor `F5` Server, naciśnij klawisz Visual Studio. Aplikacje Blazor nie obsługują kompilacji w czasie wykonywania. Aby wyświetlić wyniki zmian znaczników kodu i składnika, odbuduj i uruchom ponownie aplikację za pomocą dołączonego debugera. Jeśli uruchomisz bez dołączonego`Ctrl+F5`debugera ( ), Visual Studio obserwuje zmiany plików i ponownie uruchamia aplikację w miarę wprowadzania zmian. Ręcznie odświeżaj przeglądarkę w miarę wprowadzanych zmian.

Aby uruchomić aplikację Blazor WebAssembly, wybierz jedną z następujących metod:

- Uruchom projekt klienta bezpośrednio przy użyciu serwera deweloperów.
- Uruchom projekt serwera podczas hostowania aplikacji z ASP.NET Core.

Aplikacje Blazor WebAssembly nie obsługują debugowania przy użyciu programu Visual Studio. Aby uruchomić aplikację, `Ctrl+F5` użyj `F5`zamiast . Zamiast tego można debugować aplikacje Blazor WebAssembly bezpośrednio w przeglądarce. Szczegółowe informacje można znaleźć w [ASP.NET Core Blazor.](/aspnet/core/blazor/debug)

>[!div class="step-by-step"]
>[Poprzedni](hosting-models.md)
>[następny](app-startup.md)
