---
title: dotnet nowe polecenie
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399127"
---
# <a name="dotnet-new"></a>dotnet new

**Ten artykuł dotyczy:** ✔️ .NET Core 2.0 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet new`- Tworzy nowy projekt, plik konfiguracyjny lub rozwiązanie na podstawie określonego szablonu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet new` tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.

Polecenie wywołuje [aparat szablonu,](https://github.com/dotnet/templating) aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.

## <a name="arguments"></a>Argumenty

- **`TEMPLATE`**

  Szablon do wystąpienia po wywołaniu polecenia. Każdy szablon może mieć określone opcje, które można przekazać. Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).

  Można uruchomić, `dotnet new --list` aby wyświetlić listę wszystkich zainstalowanych szablonów. Jeśli `TEMPLATE` wartość nie jest dokładne dopasowanie tekstu w **szablony** lub **krótka nazwa** kolumna z tabeli zwracanej, dopasowanie podciągu jest wykonywane na tych dwóch kolumnach.

  Począwszy od sdk .NET Core 3.0, wiersz wiersza polecenia `dotnet new` wyszukuje szablony w NuGet.org wywołania polecenia w następujących warunkach:

  - Jeśli wiersz wiersza wiersza wiersza nie `dotnet new`może znaleźć dopasowania szablonu podczas wywoływania , nawet częściowe.
  - Jeśli jest dostępna nowsza wersja szablonu. W takim przypadku projekt lub artefakt jest tworzony, ale cli ostrzega o zaktualizowanej wersji szablonu.

  Polecenie zawiera domyślną listę szablonów. Służy `dotnet new -l` do uzyskiwania listy dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane z .NET Core SDK. Domyślny język szablonu jest wyświetlany wewnątrz nawiasów. Kliknij łącze krótkiej nazwy, aby wyświetlić określone opcje szablonu.

| Szablony                                    | Krótka nazwa                      | Język     | Tagi                                  | Wprowadzone |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Aplikacja konsolowa                          | [Konsoli](#console)             | [C#], F#, VB | Często/Konsola                        | 1.0        |
| Biblioteka klas                                | [Classlib](#classlib)           | [C#], F#, VB | Wspólne/Biblioteka                        | 1.0        |
| Aplikacja WPF                              | [Wpf](#wpf)                     | [C#]         | Często/WPF                            | 3.0        |
| Biblioteka klas WPF                            | [wpflib (wpflib)](#wpf)                  | [C#]         | Często/WPF                            | 3.0        |
| Biblioteka kontrolek niestandardowych WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Często/WPF                            | 3.0        |
| Biblioteka kontroli użytkownika WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Często/WPF                            | 3.0        |
| Aplikacja formularzy systemu Windows (Formularze WinForms)         | [Winforms](#winforms)           | [C#]         | Formularze wspólne/win                       | 3.0        |
| Biblioteka klas formularzy systemu Windows (WinForms)       | [winformslib (winformslib)](#winforms)        | [C#]         | Formularze wspólne/win                       | 3.0        |
| Obsługa pracowników                               | [Pracownik](#web-others)           | [C#]         | Wspólne/Pracownik/Sieć Web                     | 3.0        |
| Projekt testu jednostkowego                            | [Mstest](#test)                 | [C#], F#, VB | Test/TEST                           | 1.0        |
| Projekt testowy Jednostki 3                         | [Nunit](#nunit)                  | [C#], F#, VB | Test/NJednostka                            | 2.1.400    |
| Element testowy NUnit 3                            | `nunit-test`                    | [C#], F#, VB | Test/NJednostka                            | 2.2        |
| Projekt testu xUnit                           | [Xunit](#test)                  | [C#], F#, VB | Test/jednostka xUnit                            | 1.0        |
| Komponent maszynki do golenia                              | `razorcomponent`                | [C#]         | Sieć Web/ASP.NET                           | 3.0        |
| Strona brzytwy                                   | [Strona](#page)                   | [C#]         | Sieć Web/ASP.NET                           | 2.0        |
| MVC ViewImports                              | [viewimports (import widoku)](#namespace)       | [C#]         | Sieć Web/ASP.NET                           | 2.0        |
| MVC ViewStart                                | `viewstart`                     | [C#]         | Sieć Web/ASP.NET                           | 2.0        |
| Aplikacja Blazor Server                            | [serwer blazorserver](#blazorserver)   | [C#]         | Strona internetowa/Blazor                            | 3.0        |
| ASP.NET Rdzeń pusty                           | [Sieci web](#web)                     | [C#], F #     | Sieć Web/Pusta                             | 1.0        |
| ASP.NET Core Web App (Model-View-Controller) | [Mvc](#web-options)             | [C#], F #     | Sieć Web/MVC                               | 1.0        |
| ASP.NET Podstawowa aplikacja sieci Web                         | [webapp, brzytwa](#web-options)   | [C#]         | Strony internetowe/MVC/Razor                   | 2.2, 2.0   |
| ASP.NET rdzeń z kanciastym                    | [Kątowe](#spa)                 | [C#]         | Sieć Web/MVC/SPA                           | 2.0        |
| ASP.NET Core z React.js                   | [Reagować](#spa)                   | [C#]         | Sieć Web/MVC/SPA                           | 2.0        |
| ASP.NET Core z React.js i Redux         | [reactredux](#reactredux)       | [C#]         | Sieć Web/MVC/SPA                           | 2.0        |
| Biblioteka klas brzytwy                          | [brzytwaclasslib](#razorclasslib) | [C#]         | Biblioteka klas Web/Razor/Library/Razor | 2.1        |
| Internetowy interfejs API platformy ASP.NET Core                         | [Webapi](#webapi)               | [C#], F #     | Witryna sieci Web/WebAPI                            | 1.0        |
| ASP.NET Podstawowa usługa gRPC                    | [grpc (grpc)](#web-others)             | [C#]         | Sieć Web/gRPC                              | 3.0        |
| Plik buforu protokołu                         | [Proto](#namespace)             |              | Sieć Web/gRPC                              | 3.0        |
| dotnet gitignore plik                        | `gitignore`                     |              | Config                                | 3.0        |
| plik global.json                             | [globaljson (globaljson)](#globaljson)       |              | Config                                | 2.0        |
| Konfigurator NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| dotnet plik manifestu narzędzia lokalnego              | `tool-manifest`                 |              | Config                                | 3.0        |
| Konfiguracja sieci Web                                   | `webconfig`                     |              | Config                                | 1.0        |
| Plik rozwiązania                                | `sln`                           |              | Rozwiązanie                              | 1.0        |

## <a name="options"></a>Opcje

- **`--dry-run`**

  Wyświetla podsumowanie tego, co by się stało, gdyby dane polecenie zostało uruchomione. Dostępne od sdk .NET Core 2.2.

- **`--force`**

  Wymusza generowanie zawartości, nawet jeśli spowoduje to zmianę istniejących plików. Jest to wymagane, gdy wybrany szablon zastąpi istniejące pliki w katalogu wyjściowym.

- **`-h|--help`**

  Drukuje pomoc dla polecenia. Można go wywołać `dotnet new` dla samego polecenia lub dla dowolnego szablonu. Na przykład `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Instaluje pakiet szablonów z `PATH` lub `NUGET_ID` dostarczonego. Jeśli chcesz zainstalować wersję wwersji wstępnej pakietu szablonu, musisz określić `<package-name>::<package-version>`wersję w formacie . Domyślnie `dotnet new` przekazuje \* dla wersji, która reprezentuje najnowszą wersję pakietu stabilnego. Zobacz przykład w sekcji [Przykłady.](#examples)
  
  Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej stabilnej wersji, jeśli nie określono żadnej wersji.

  Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla dotnet new](custom-templates.md).

- **`-l|--list`**

  Wyświetla listę szablonów zawierających określoną nazwę. Jeśli nie określono nazwy, wyświetla listę wszystkich szablonów.

- **`-lang|--language {C#|F#|VB}`**

  Język szablonu do utworzenia. Akceptowany język różni się w zależności od szablonu (zobacz ustawienia domyślne w sekcji [argumentów).](#arguments) Nie dotyczy niektórych szablonów.

  > [!NOTE]
  > Niektóre skorupy `#` interpretują jako znak specjalny. W takich przypadkach załączaj wartość parametru języka w cudzysłowie. Na przykład `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Nazwa utworzonego wyjścia. Jeśli nie określono nazwy, używana jest nazwa bieżącego katalogu.

- **`--nuget-source`**

  Określa źródło NuGet do użycia podczas instalacji. Dostępne od sdk .NET Core 2.1.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Lokalizacja, aby umieścić wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

- **`--type`**

  Filtruje szablony na podstawie dostępnych typów. Wstępnie zdefiniowane wartości to "projekt", "element" lub "inny".

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Odinstalowuje pakiet szablonów w dostarczonym `PATH` lub `NUGET_ID` dostarczonym. Jeśli `<PATH|NUGET_ID>` wartość nie jest określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony. Określając `NUGET_ID`numer wersji, nie należy umieszczać.

  Jeśli nie określisz parametru tej opcji, polecenie wyświetla listę zainstalowanych szablonów i szczegółowe informacje o nich.

  > [!NOTE]
  > Aby odinstalować `PATH`szablon przy użyciu , musisz w pełni zakwalifikować ścieżkę. Na przykład *\<C:/Users/ USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie działać.
  > Nie należy uwzględniać końcowego ukośnika katalogu zakończenia na ścieżce szablonu.

- **`--update-apply`**

  Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane, i instaluje je. Dostępne od sdk .NET Core 3.0.

- **`--update-check`**

  Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane. Dostępne od sdk .NET Core 3.0.

## <a name="template-options"></a>Opcje szablonu

Każdy szablon projektu może mieć dodatkowe opcje dostępne. Podstawowe szablony mają następujące dodatkowe opcje:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Dostępne od sdk .NET Core 3.0.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3. Nie jest obsługiwana dla Języka F#. Dostępne od sdk .NET Core 2.2.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Jeśli określono, nie wykonuje przywracanie niejawne podczas tworzenia projektu. Dostępne od sdk .NET Core 2.2.

***

### <a name="classlib"></a>Classlib

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas `netstandard<version>` rdzenia .NET lub utworzyć bibliotekę klas standardowych .NET. Wartością domyślną jest `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3. Nie jest obsługiwana dla Języka F#. Dostępne od sdk .NET Core 2.2.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="wpf"></a>wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Wartością domyślną jest `netcoreapp3.1`. Dostępne od sdk .NET Core 3.1.

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="winforms"></a>winforms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="web-others"></a>pracownik, grpc

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Wartością domyślną jest `netcoreapp3.1`. Dostępne od sdk .NET Core 3.1.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="test"></a>mstest, xunit

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja dostępna od sdk .NET Core 3.0.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet](dotnet-pack.md).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="nunit"></a>Nunit

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet](dotnet-pack.md).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="page"></a>Strona

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obszar nazw dla wygenerowanego kodu. Wartością domyślną jest `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Tworzy stronę bez PageModel.

***

### <a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obszar nazw dla wygenerowanego kodu. Wartością domyślną jest `MyApp.Namespace`.

***

### <a name="blazorserver"></a>serwer blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `Individual`- Uwierzytelnianie indywidualne.
  - `IndividualB2C`- Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
  - `SingleOrg`- Uwierzytelnianie organizacyjne dla pojedynczej dzierżawy.
  - `MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.
  - `Windows`- Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory B2C, z którym chcesz się połączyć. Użyj `IndividualB2C` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestracji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-rp|--reset-password-policy-id <ID>`**

  Identyfikator zasad resetowania haseł dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-ep|--edit-profile-policy-id <ID>`**

  Identyfikator zasad profilu edit dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory, z którym chcesz się połączyć. Użyj `SingleOrg` z `MultiOrg` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelniania. Wartością domyślną jest `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator identyfikatora tenantid katalogu, z którymi chcesz się połączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Ścieżka żądania w ścieżce podstawowej aplikacji identyfikatora URI przekierowania. Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `/signin-oidc`.

- **`-r|--org-read-access`**

  Umożliwia tej aplikacji dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , `--auth`, , lub nie są używane do .

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS.

***

### <a name="web-options"></a>mvc, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `Individual`- Uwierzytelnianie indywidualne.
  - `IndividualB2C`- Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
  - `SingleOrg`- Uwierzytelnianie organizacyjne dla pojedynczej dzierżawy.
  - `MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.
  - `Windows`- Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory B2C, z którym chcesz się połączyć. Użyj `IndividualB2C` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestracji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-rp|--reset-password-policy-id <ID>`**

  Identyfikator zasad resetowania haseł dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-ep|--edit-profile-policy-id <ID>`**

  Identyfikator zasad profilu edit dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory, z którym chcesz się połączyć. Użyj `SingleOrg` z `MultiOrg` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelniania. Wartością domyślną jest `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator identyfikatora tenantid katalogu, z którymi chcesz się połączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Ścieżka żądania w ścieżce podstawowej aplikacji identyfikatora URI przekierowania. Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `/signin-oidc`.

- **`-r|--org-read-access`**

  Umożliwia tej aplikacji dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , , , lub nie są używane.

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja dostępna od sdk .NET Core 3.0.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--use-browserlink`**

  Zawiera BrowserLink w projekcie. Opcja nie jest dostępna w sdk .NET Core 2.2 i 3.1.

***

### <a name="spa"></a>kątowe, reagować

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Dostępne od sdk .NET Core 3.0.
  
  Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `Individual`- Uwierzytelnianie indywidualne.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma zastosowanie `None`tylko wtedy, gdy uwierzytelnianie jest .

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania. Dostępne od sdk .NET Core 3.0.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS.

***

### <a name="razorclasslib"></a>brzytwaclasslib

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`-s|--support-pages-and-views`**

  Obsługuje dodawanie tradycyjnych stron razor i widoki oprócz składników do tej biblioteki. Dostępne od sdk .NET Core 3.0.

***
  
### <a name="webapi"></a>Webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `IndividualB2C`- Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
  - `SingleOrg`- Uwierzytelnianie organizacyjne dla pojedynczej dzierżawy.
  - `Windows`- Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory B2C, z którym chcesz się połączyć. Użyj `IndividualB2C` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestracji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory, z którym chcesz się połączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj `IndividualB2C` z `SingleOrg` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Użyj `IndividualB2C` z `SingleOrg` uwierzytelnianiem lub uwierzytelniaj. Wartością domyślną jest `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator identyfikatora tenantid katalogu, z którymi chcesz się połączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Umożliwia tej aplikacji dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. `app.UseHsts`i `app.UseHttpsRedirection` nie są `Startup.Configure`dodawane do . Ta opcja ma `IndividualB2C` zastosowanie `SingleOrg` tylko wtedy, gdy nie są używane do uwierzytelniania.

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `IndividualB2C` uwierzytelniania.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="globaljson"></a>globaljson (globaljson)

- **`--sdk-version <VERSION_NUMBER>`**

  Określa wersję sdk .NET Core do użycia w pliku *global.json.*

***

## <a name="examples"></a>Przykłady

- Utwórz projekt aplikacji konsoli C#, określając nazwę szablonu:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Utwórz projekt aplikacji konsoli F# w bieżącym katalogu:

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Utwórz nowy projekt xUnit:

  ```dotnetcli
  dotnet new xunit
  ```

- Lista wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):

  ```dotnetcli
  dotnet new spa -l
  ```

- Lista wszystkich szablonów pasujących *do podciągu we.* Nie znaleziono dokładnego dopasowania, więc dopasowanie podciągów jest uruchamiane zarówno względem kolumn krótkiej nazwy, jak i nazwy.

  ```dotnetcli
  dotnet new we -l
  ```

- Spróbuj wywołać szablon pasujący *ng*. Jeśli nie można określić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są częściowymi dopasowaniami.

  ```dotnetcli
  dotnet new ng
  ```

- Zainstaluj wersję 2.0 szablonów SPA dla ASP.NET Core:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Lista zainstalowanych szablonów i szczegóły na ich temat, w tym jak je odinstalować:

  ```dotnetcli
  dotnet new -u
  ```

- Utwórz *global.json* w bieżącym katalogu, ustawiając wersję sdk na 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Zobacz też

- [Szablony niestandardowe dla dotnet nowy](custom-templates.md)
- [Tworzenie szablonu niestandardowego dla polecenia dotnet new](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)
- [Dostępne szablony dla dotnet nowych](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
