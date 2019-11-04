---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420476"
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet new` — tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.

## <a name="synopsis"></a>Streszczenie

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet new` polecenie zapewnia wygodny sposób zainicjowania prawidłowego projektu .NET Core.

Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.

## <a name="arguments"></a>Argumenty

`TEMPLATE`

Szablon do wystąpienia po wywołaniu polecenia. Każdy szablon może mieć określone opcje, które można przekazać. Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).

Jeśli wartość `TEMPLATE` nie jest dokładnym dopasowaniem do tekstu w kolumnie **templates** lub **short name** , do tych dwóch kolumn jest wykonywane dopasowanie podciągów.

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.2.100. Język domyślny dla szablonu jest pokazywany w nawiasach.

| Szablony                                    | Krótka nazwa        | Język     | Znaczniki                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| Aplikacja konsoli                          | `console`         | [C#], F#, VB | Wspólna/konsola                        |
| Biblioteka klas                                | `classlib`        | [C#], F#, VB | Wspólna/Biblioteka                        |
| Projekt testu jednostkowego                            | `mstest`          | [C#], F#, VB | Test/MSTest                           |
| Projekt testowy NUnit 3                         | `nunit`           | [C#], F#, VB | Test/NUnit                            |
| Element testowy NUnit 3                            | `nunit-test`      | [C#], F#, VB | Test/NUnit                            |
| Projekt testu xUnit                           | `xunit`           | [C#], F#, VB | Test/xUnit                            |
| Strona Razor                                   | `page`            | [C#]         | Web/ASP. NET                           |
| ViewImports MVC                              | `viewimports`     | [C#]         | Web/ASP. NET                           |
| ViewStart MVC                                | `viewstart`       | [C#]         | Web/ASP. NET                           |
| ASP.NET Core puste                           | `web`             | [C#],F#     | Sieć Web/pusta                             |
| Aplikacja sieci Web ASP.NET Core (Model-View-Controller) | `mvc`             | [C#],F#     | Web/MVC                               |
| Aplikacja sieci Web ASP.NET Core                         | `webapp`, `razor` | [C#]         | Web/MVC/Razor Pages                   |
| ASP.NET Core ze Skośnością                    | `angular`         | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core z usługą reaguj. js                   | `react`           | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core z reakcjęmi. js i Redux         | `reactredux`      | [C#]         | Web/MVC/SPA                           |
| Biblioteka klas Razor                          | `razorclasslib`   | [C#]         | Biblioteka klas sieci Web/Razor/Biblioteka/Razor |
| Interfejs API sieci Web ASP.NET Core                         | `webapi`          | [C#],F#     | Sieć Web/WebAPI                            |
| plik Global. JSON                             | `globaljson`      |              | Konfiguracja                                |
| Konfiguracja narzędzia NuGet                                 | `nugetconfig`     |              | Konfiguracja                                |
| Konfiguracja sieci Web                                   | `webconfig`       |              | Konfiguracja                                |
| Plik rozwiązania                                | `sln`             |              | Rozwiązanie                              |

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.1.300. Język domyślny dla szablonu jest pokazywany w nawiasach.

| Szablony                                    | Krótka nazwa      | Język     | Znaczniki                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| Aplikacja konsoli                          | `console`       | [C#], F#, VB | Wspólna/konsola                        |
| Biblioteka klas                                | `classlib`      | [C#], F#, VB | Wspólna/Biblioteka                        |
| Projekt testu jednostkowego                            | `mstest`        | [C#], F#, VB | Test/MSTest                           |
| Projekt testu xUnit                           | `xunit`         | [C#], F#, VB | Test/xUnit                            |
| Strona Razor                                   | `page`          | [C#]         | Web/ASP. NET                           |
| ViewImports MVC                              | `viewimports`   | [C#]         | Web/ASP. NET                           |
| ViewStart MVC                                | `viewstart`     | [C#]         | Web/ASP. NET                           |
| ASP.NET Core puste                           | `web`           | [C#],F#     | Sieć Web/pusta                             |
| Aplikacja sieci Web ASP.NET Core (Model-View-Controller) | `mvc`           | [C#],F#     | Web/MVC                               |
| Aplikacja sieci Web ASP.NET Core                         | `razor`         | [C#]         | Web/MVC/Razor Pages                   |
| ASP.NET Core ze Skośnością                    | `angular`       | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core z usługą reaguj. js                   | `react`         | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core z reakcjęmi. js i Redux         | `reactredux`    | [C#]         | Web/MVC/SPA                           | 
| Biblioteka klas Razor                          | `razorclasslib` | [C#]         | Biblioteka klas sieci Web/Razor/Biblioteka/Razor |
| Interfejs API sieci Web ASP.NET Core                         | `webapi`        | [C#],F#     | Sieć Web/WebAPI                            |
| plik Global. JSON                             | `globaljson`    |              | Konfiguracja                                |
| Konfiguracja narzędzia NuGet                                 | `nugetconfig`   |              | Konfiguracja                                |
| Konfiguracja sieci Web                                   | `webconfig`     |              | Konfiguracja                                |
| Plik rozwiązania                                | `sln`           |              | Rozwiązanie                              |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.0.0. Język domyślny dla szablonu jest pokazywany w nawiasach.

| Szablony                                    | Krótka nazwa    | Język     | Znaczniki                |
|----------------------------------------------|---------------|--------------|---------------------|
| Aplikacja konsoli                          | `console`     | [C#], F#, VB | Wspólna/konsola      |
| Biblioteka klas                                | `classlib`    | [C#], F#, VB | Wspólna/Biblioteka      |
| Projekt testu jednostkowego                            | `mstest`      | [C#], F#, VB | Test/MSTest         |
| Projekt testu xUnit                           | `xunit`       | [C#], F#, VB | Test/xUnit          |
| ASP.NET Core puste                           | `web`         | [C#],F#     | Sieć Web/pusta           |
| Aplikacja sieci Web ASP.NET Core (Model-View-Controller) | `mvc`         | [C#],F#     | Web/MVC             |
| Aplikacja sieci Web ASP.NET Core                         | `razor`       | [C#]         | Web/MVC/Razor Pages |
| ASP.NET Core ze Skośnością                    | `angular`     | [C#]         | Web/MVC/SPA         |
| ASP.NET Core z usługą reaguj. js                   | `react`       | [C#]         | Web/MVC/SPA         |
| ASP.NET Core z reakcjęmi. js i Redux         | `reactredux`  | [C#]         | Web/MVC/SPA         |
| Interfejs API sieci Web ASP.NET Core                         | `webapi`      | [C#],F#     | Sieć Web/WebAPI          |
| plik Global. JSON                             | `globaljson`  |              | Konfiguracja              |
| Konfiguracja narzędzia NuGet                                 | `nugetconfig` |              | Konfiguracja              |
| Konfiguracja sieci Web                                   | `webconfig`   |              | Konfiguracja              |
| Plik rozwiązania                                | `sln`         |              | Rozwiązanie            |
| Strona Razor                                   | `page`        |              | Web/ASP. NET         |
| ViewImports MVC                              | `viewimports` |              | Web/ASP. NET         |
| ViewStart MVC                                | `viewstart`   |              | Web/ASP. NET         |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -all`, aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 1.0.1. Język domyślny dla szablonu jest pokazywany w nawiasach.

| Szablony            | Krótka nazwa    | Język | Znaczniki           |
|----------------------|---------------|----------|----------------|
| Aplikacja konsoli  | `console`     | [C#],F# | Wspólna/konsola |
| Biblioteka klas        | `classlib`    | [C#],F# | Wspólna/Biblioteka |
| Projekt testu jednostkowego    | `mstest`      | [C#],F# | Test/MSTest    |
| Projekt testu xUnit   | `xunit`       | [C#],F# | Test/xUnit     |
| ASP.NET Core puste   | `web`         | [C#]     | Sieć Web/pusta      |
| Aplikacja sieci Web ASP.NET Core | `mvc`         | [C#],F# | Web/MVC        |
| Interfejs API sieci Web ASP.NET Core | `webapi`      | [C#]     | Sieć Web/WebAPI     |
| Konfiguracja narzędzia NuGet         | `nugetconfig` |          | Konfiguracja         |
| Konfiguracja sieci Web           | `webconfig`   |          | Konfiguracja         |
| Plik rozwiązania        | `sln`         |          | Rozwiązanie       |

---

## <a name="options"></a>Opcje

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

`--dry-run`

Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.

`--force`

Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików. Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.

`-h|--help`

Drukuje pomoc dla polecenia. Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instaluje pakiet źródłowy lub szablon z podanej `PATH` lub `NUGET_ID`. Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`. Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje ostatnią stabilną wersję pakietu. Zobacz przykład w sekcji [przykładów](#examples) .

Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).

`-l|--list`

Wyświetla listę szablonów zawierających określoną nazwę. Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.

`-lang|--language {C#|F#|VB}`

Język szablonu do utworzenia. Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ). Nieprawidłowy dla niektórych szablonów.

> [!NOTE]
> Niektóre powłoki interpretują `#` jako znak specjalny. W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa dla utworzonych danych wyjściowych. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.

`--nuget-source`

Określa źródło NuGet do użycia podczas instalacji.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

`--type`

Filtruje szablony w oparciu o dostępne typy. Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstalowuje pakiet źródłowy lub szablonowy na `PATH` lub `NUGET_ID` udostępniony. Podczas wykluczania wartości `<PATH|NUGET_ID>` są wyświetlane wszystkie aktualnie zainstalowane pakiety szablonów i powiązane z nimi szablony.

> [!NOTE]
> Aby odinstalować szablon przy użyciu `PATH`, musisz w pełni zakwalifikować ścieżkę. Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.
> Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--force`

Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików. Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.

`-h|--help`

Drukuje pomoc dla polecenia. Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instaluje pakiet źródłowy lub szablon z podanej `PATH` lub `NUGET_ID`. Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`. Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje ostatnią stabilną wersję pakietu. Zobacz przykład w sekcji [przykładów](#examples) .

Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).

`-l|--list`

Wyświetla listę szablonów zawierających określoną nazwę. Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.

`-lang|--language {C#|F#|VB}`

Język szablonu do utworzenia. Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ). Nieprawidłowy dla niektórych szablonów.

> [!NOTE]
> Niektóre powłoki interpretują `#` jako znak specjalny. W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa dla utworzonych danych wyjściowych. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.

`--nuget-source`

Określa źródło NuGet do użycia podczas instalacji.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

`--type`

Filtruje szablony w oparciu o dostępne typy. Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstalowuje pakiet źródłowy lub szablonowy na `PATH` lub `NUGET_ID` udostępniony.

> [!NOTE]
> Aby odinstalować szablon przy użyciu `PATH`, musisz w pełni zakwalifikować ścieżkę. Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.
> Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--force`

Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików. Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.

`-h|--help`

Drukuje pomoc dla polecenia. Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instaluje pakiet źródłowy lub szablon z podanej `PATH` lub `NUGET_ID`. Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`. Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje ostatnią stabilną wersję pakietu. Zobacz przykład w sekcji [przykładów](#examples) .

Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).

`-l|--list`

Wyświetla listę szablonów zawierających określoną nazwę. Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.

`-lang|--language {C#|F#|VB}`

Język szablonu do utworzenia. Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ). Nieprawidłowy dla niektórych szablonów.

> [!NOTE]
> Niektóre powłoki interpretują `#` jako znak specjalny. W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa dla utworzonych danych wyjściowych. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

`--type`

Filtruje szablony w oparciu o dostępne typy. Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstalowuje pakiet źródłowy lub szablonowy na `PATH` lub `NUGET_ID` udostępniony.

> [!NOTE]
> Aby odinstalować szablon przy użyciu `PATH`źródłowego, należy w pełni zakwalifikować ścieżkę. Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego. Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.
> 
> Jeśli nie możesz określić argumentu `PATH` lub `NUGET_ID` wymaganego do odinstalowania szablonu, uruchomienie `dotnet new --uninstall` bez argumentu spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argumentu wymaganego do ich odinstalowania.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-all|--show-all`

Wyświetla wszystkie szablony dla określonego typu projektu, gdy działa w kontekście polecenia `dotnet new`. W przypadku uruchomienia w kontekście określonego szablonu, takiego jak `dotnet new web -all`, `-all` jest interpretowana jako flaga tworzenia siły. Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.

`-h|--help`

Drukuje pomoc dla polecenia. Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.

`-l|--list`

Wyświetla listę szablonów zawierających określoną nazwę. Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.

`-lang|--language {C#|F#}`

Język szablonu do utworzenia. Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ). Nieprawidłowy dla niektórych szablonów.

> [!NOTE]
> Niektóre powłoki interpretują `#` jako znak specjalny. W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa dla utworzonych danych wyjściowych. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

---

## <a name="template-options"></a>Opcje szablonu

Każdy szablon projektu może mieć dodatkowe opcje dostępne. Szablony podstawowe mają następujące dodatkowe opcje:

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

**konsoli**

`--langVersion <VERSION_NUMBER>` — ustawia właściwość `LangVersion` w utworzonym pliku projektu. Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3. Nieobsługiwane w F#programie.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**kątowy, reagowanie, reactredux**

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

`--no-https` — projekt nie wymaga protokołu HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy nie są używane `IndividualAuth` ani `OrganizationalAuth`.

**razorclasslib**

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**określono**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp2.2` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard. Wartość domyślna to `netstandard2.0`.

`--langVersion <VERSION_NUMBER>` — ustawia właściwość `LangVersion` w utworzonym pliku projektu. Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3. Nieobsługiwane w F#programie.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**MSTest, xUnit**

`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**NUnit**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartość domyślna to `netcoreapp2.1`.

`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**stronic**

Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

`-np|--no-pagemodel` — tworzy stronę bez PageModel.

**viewimports**

Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

**witrynę**

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

`--no-https` — projekt nie wymaga protokołu HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy nie są używane `IndividualAuth` ani `OrganizationalAuth`.

**MVC, webapp**

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — brak uwierzytelniania (wartość domyślna).
- Uwierzytelnianie indywidualne `Individual`.
- `IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.
- `SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.
- `MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.
- `Windows` — uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `IndividualB2C`. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` — identyfikator zasad resetowania hasła dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` — Edytuj identyfikator zasad profilu dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — identyfikator klienta dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` — domena dzierżawy katalogu. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` — Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `/signin-oidc`.

`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`--no-https` — projekt nie wymaga protokołu HTTPS. `app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`. Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.

`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — brak uwierzytelniania (wartość domyślna).
- `IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.
- `SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.
- `Windows` — uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `IndividualB2C`. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — identyfikator klienta dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` — domena dzierżawy katalogu. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`--no-https` — projekt nie wymaga protokołu HTTPS. `app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`. Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.

`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` — określa wersję zestaw .NET Core SDK do użycia w pliku *Global. JSON* .

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

**konsole, kątowe, reagowanie, reactredux, razorclasslib**

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**określono**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp2.1` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard. Wartość domyślna to `netstandard2.0`.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**MSTest, xUnit**

`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` — określa wersję zestaw .NET Core SDK do użycia w pliku *Global. JSON* .

**witrynę**

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

`--no-https` — projekt nie wymaga protokołu HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy nie są używane `IndividualAuth` ani `OrganizationalAuth`.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — brak uwierzytelniania (wartość domyślna).
- `IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.
- `SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.
- `Windows` — uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `IndividualB2C`. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — identyfikator klienta dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` — domena dzierżawy katalogu. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

`--no-https` — projekt nie wymaga protokołu HTTPS. `app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`. Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — brak uwierzytelniania (wartość domyślna).
- Uwierzytelnianie indywidualne `Individual`.
- `IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.
- `SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.
- `MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.
- `Windows` — uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `IndividualB2C`. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` — identyfikator zasad resetowania hasła dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` — Edytuj identyfikator zasad profilu dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — identyfikator klienta dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` — domena dzierżawy katalogu. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` — Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `/signin-oidc`.

`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

`--use-browserlink` — zawiera BrowserLink w projekcie.

`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

`--no-https` — projekt nie wymaga protokołu HTTPS. `app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`. Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.

**stronic**

Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

`-np|--no-pagemodel` — tworzy stronę bez PageModel.

**viewimports**

Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

**konsole, kątowe, reagowanie, reactredux**

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**określono**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard. Wartość domyślna to `netstandard2.0`.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**MSTest, xUnit**

`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` — określa wersję zestaw .NET Core SDK do użycia w pliku *Global. JSON* .

**witrynę**

`--use-launch-settings` — zawiera plik *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — brak uwierzytelniania (wartość domyślna).
- `IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.
- `SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.
- `Windows` — uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `IndividualB2C`. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — identyfikator klienta dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` — domena dzierżawy katalogu. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--use-launch-settings` — zawiera plik *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.

`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — brak uwierzytelniania (wartość domyślna).
- Uwierzytelnianie indywidualne `Individual`.
- `IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.
- `SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.
- `MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.
- `Windows` — uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `IndividualB2C`. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` — identyfikator zasad resetowania hasła dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` — Edytuj identyfikator zasad profilu dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`.

`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — identyfikator klienta dla tego projektu. Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` — domena dzierżawy katalogu. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z uwierzytelnianiem `SingleOrg`. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` — Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania. Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`. Wartość domyślna to `/signin-oidc`.

`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--use-launch-settings` — zawiera plik *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.

`--use-browserlink` — zawiera BrowserLink w projekcie.

`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.

**stronic**

Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>`dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

`-np|--no-pagemodel` — tworzy stronę bez PageModel.

**viewimports**

Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>`dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

**konsole, xUnit, MSTest, Web, WebApi**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp1.0` lub `netcoreapp1.1`. Wartość domyślna to `netcoreapp1.0`.

**określono**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp1.0`, `netcoreapp1.1`lub `netstandard1.0` do `netstandard1.6`. Wartość domyślna to `netstandard1.4`.

**Standard**

`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp1.0` lub `netcoreapp1.1`. Wartość domyślna to `netcoreapp1.0`.

`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia. Wartości: `None` lub `Individual`. Wartość domyślna to `None`.

`-uld|--use-local-db` — określa, czy należy używać LocalDB zamiast oprogramowania SQLite. Wartości: `true` lub `false`. Wartość domyślna to `false`.

---

## <a name="examples"></a>Przykłady

Utwórz projekt C# aplikacji konsolowej, określając nazwę szablonu:

`dotnet new "Console Application"`

Utwórz projekt F# aplikacji konsolowej w bieżącym katalogu:

`dotnet new console -lang F#`

Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku wersji zestaw .NET Core SDK 2,0 lub nowszej):

`dotnet new classlib -lang VB -o MyLibrary`

Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:

`dotnet new mvc -au None`

Utwórz nowy projekt xUnit:

`dotnet new xunit`

Wyświetl listę wszystkich szablonów dostępnych dla MVC:

`dotnet new mvc -l`

Wyświetl listę wszystkich szablonów pasujących *do* podciągu. Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.

`dotnet new we -l`

Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*. Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.

`dotnet new ng`

Zainstaluj wersję 2,0 szablonów aplikacji jednostronicowych dla ASP.NET Core (opcja polecenia dostępna tylko dla zestaw .NET Core SDK 1,1 i nowszych wersji):

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 2.0.0 (dostępne tylko w zestaw .NET Core SDK 2,0 lub nowszych wersjach):

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Zobacz także

- [Szablony niestandardowe dla nowego dotnet](custom-templates.md)
- [Tworzenie szablonu niestandardowego dla polecenia dotnet new](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-Template-przykłady repozytorium GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Dostępne szablony dla nowego dotnet](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
