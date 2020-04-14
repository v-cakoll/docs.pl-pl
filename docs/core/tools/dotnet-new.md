---
title: dotnet nowe polecenie
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 1b1a6efa7bf2753b6c23cc7af1e26867f8632b96
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242884"
---
# <a name="dotnet-new"></a>dotnet new

**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach

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

Polecenie `dotnet new` tworzy projekt .NET Core lub inne artefakty oparte na szablonie.

Polecenie wywołuje [aparat szablonów,](https://github.com/dotnet/templating) aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.

## <a name="arguments"></a>Argumenty

- **`TEMPLATE`**

  Szablon do wystąpienia po wywołaniu polecenia. Każdy szablon może mieć określone opcje, które można przekazać. Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).

  Można uruchomić, `dotnet new --list` aby wyświetlić listę wszystkich zainstalowanych szablonów. Jeśli `TEMPLATE` wartość nie jest dokładne dopasowanie tekstu w **szablony** lub **nazwa skrócona** kolumny z tabeli zwracanej, dopasowanie podciąg jest wykonywane na tych dwóch kolumnach.

  Począwszy od pliku .NET Core 3.0 SDK, funkcja CLI wyszukuje szablony w NuGet.org podczas wywoływania `dotnet new` polecenia w następujących warunkach:

  - Jeśli cli nie można znaleźć dopasowania szablonu podczas wywoływania `dotnet new`, nawet częściowe.
  - Jeśli dostępna jest nowsza wersja szablonu. W takim przypadku tworzony jest projekt lub artefakt, ale cli ostrzega o zaktualizowanej wersji szablonu.

  Polecenie zawiera domyślną listę szablonów. Służy `dotnet new -l` do uzyskiwania listy dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są fabrycznie zainstalowane z pakietem .NET Core SDK. Domyślny język szablonu jest wyświetlany wewnątrz nawiasów. Kliknij łącze do krótkiej nazwy, aby wyświetlić określone opcje szablonu.

| Szablony                                    | Krótka nazwa                      | Język     | Tagi                                  | Wprowadzone |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Aplikacja konsoli                          | [Konsoli](#console)             | [C#], F#, VB | Wspólne/konsolowe                        | 1.0        |
| Biblioteka klas                                | [Classlib](#classlib)           | [C#], F#, VB | Wspólne/Biblioteka                        | 1.0        |
| Aplikacja WPF                              | [Wpf](#wpf)                     | [C#]         | Często/WPF                            | 3.0        |
| Biblioteka klas WPF                            | [wpflib](#wpf)                  | [C#]         | Często/WPF                            | 3.0        |
| Biblioteka kontrolek niestandardowych WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Często/WPF                            | 3.0        |
| Biblioteka kontroli użytkownika WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Często/WPF                            | 3.0        |
| Aplikacja Windows Forms (WinForms)         | [Winforms](#winforms)           | [C#]         | Wspólne/WinForms                       | 3.0        |
| Biblioteka klas formularzy Windows Forms (WinForms)       | [winformslib](#winforms)        | [C#]         | Wspólne/WinForms                       | 3.0        |
| Usługa dla pracowników                               | [Pracownik](#web-others)           | [C#]         | Często/Pracownik/Sieć Web                     | 3.0        |
| Projekt testu jednostkowego                            | [Mstest](#test)                 | [C#], F#, VB | Test/TEST MSTest                           | 1.0        |
| Projekt testowy NUnit 3                         | [Nunit](#nunit)                  | [C#], F#, VB | Test/NUnit                            | 2.1.400    |
| NUnit 3 Przedmiot testowy                            | `nunit-test`                    | [C#], F#, VB | Test/NUnit                            | 2.2        |
| xUnit Projekt testowy                           | [Xunit](#test)                  | [C#], F#, VB | Test/xJednostka                            | 1.0        |
| Komponent maszynki do golenia                              | `razorcomponent`                | [C#]         | Sieć Web/ASP.NET                           | 3.0        |
| Strona Razor                                   | [Strona](#page)                   | [C#]         | Sieć Web/ASP.NET                           | 2.0        |
| Porty widoków MVC                              | [viewimports](#namespace)       | [C#]         | Sieć Web/ASP.NET                           | 2.0        |
| Początek widoku MVC                                | `viewstart`                     | [C#]         | Sieć Web/ASP.NET                           | 2.0        |
| Aplikacja serwera Blazor                            | [blazorserver](#blazorserver)   | [C#]         | Sieć Web/Blazor                            | 3.0        |
| ASP.NET rdzeń pusty                           | [Sieci web](#web)                     | [C#], F #     | Sieć Web/Puste                             | 1.0        |
| ASP.NET Core Web App (kontroler widoku modelu) | [Mvc](#web-options)             | [C#], F #     | Sieć Web/MVC                               | 1.0        |
| ASP.NET podstawowa aplikacja sieci Web                         | [webapp, brzytwa](#web-options)   | [C#]         | Strony internetowe/MVC/Brzytwa                   | 2.2, 2.0   |
| ASP.NET rdzeń z kątowym                    | [Kątowe](#spa)                 | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core z React.js                   | [Reagować](#spa)                   | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core z React.js i Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2.0        |
| Biblioteka klas razor                          | [brzytwaklasyb](#razorclasslib) | [C#]         | Web/ Razor/Biblioteka/Razor Klasa Biblioteka | 2.1        |
| Internetowy interfejs API platformy ASP.NET Core                         | [Webapi](#webapi)               | [C#], F #     | Sieć Web/WebAPI                            | 1.0        |
| ASP.NET podstawowa usługa gRPC                    | [grpc (grpc)](#web-others)             | [C#]         | Sieć/gRPC                              | 3.0        |
| Plik buforu protokołu                         | [Proto](#namespace)             |              | Sieć/gRPC                              | 3.0        |
| plik dotnet gitignore                        | `gitignore`                     |              | Config                                | 3.0        |
| plik global.json                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| Konfiguracja NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| plik manifestu narzędzia lokalnego dotnet              | `tool-manifest`                 |              | Config                                | 3.0        |
| Konfigurga internetowa                                   | `webconfig`                     |              | Config                                | 1.0        |
| Plik rozwiązania                                | `sln`                           |              | Rozwiązanie                              | 1.0        |

## <a name="options"></a>Opcje

- **`--dry-run`**

  Wyświetla podsumowanie tego, co by się stało, gdyby dane polecenie zostało uruchomione. Dostępne od .NET Core 2.2 SDK.

- **`--force`**

  Wymusza generowanie zawartości, nawet jeśli spowoduje to zmianę istniejących plików. Jest to wymagane, gdy wybrany szablon zastąpi istniejące pliki w katalogu wyjściowym.

- **`-h|--help`**

  Drukuje pomoc dla polecenia. Można go wywołać `dotnet new` dla samego polecenia lub dla dowolnego szablonu. Na przykład `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Instaluje pakiet `PATH` szablonów `NUGET_ID` z lub dostarczone. Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w `<package-name>::<package-version>`formacie . Domyślnie `dotnet new` przechodzi \* do wersji, która reprezentuje najnowszą stabilną wersję pakietu. Zobacz przykład w sekcji [Przykłady.](#examples)
  
  Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.

  Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla dotnet new](custom-templates.md).

- **`-l|--list`**

  Wyświetla listę szablonów zawierających określoną nazwę. Jeśli nazwa nie zostanie określona, wyświetla listę wszystkich szablonów.

- **`-lang|--language {C#|F#|VB}`**

  Język szablonu do utworzenia. Akceptowany język różni się w zależności od szablonu (zobacz wartości domyślne w sekcji [argumenty).](#arguments) Nie dotyczy niektórych szablonów.

  > [!NOTE]
  > Niektóre skorupy `#` interpretują jako znak specjalny. W takich przypadkach należy ująć wartość parametru języka w cudzysłowach. Na przykład `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Nazwa utworzonego wyjścia. Jeśli nazwa nie zostanie określona, używana jest nazwa bieżącego katalogu.

- **`--nuget-source`**

  Określa źródło NuGet, które ma być używane podczas instalacji. Dostępne od .NET Core 2.1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Lokalizacja, aby umieścić wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

- **`--type`**

  Filtruje szablony na podstawie dostępnych typów. Wstępnie zdefiniowane wartości to "projekt", "element" lub "inny".

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` pod warunkiem. Gdy `<PATH|NUGET_ID>` wartość nie zostanie określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony. Podczas określania `NUGET_ID`, nie należy dołączać numer wersji.

  Jeśli nie określisz parametru tej opcji, polecenie zawiera listę zainstalowanych szablonów i szczegółowe informacje o nich.

  > [!NOTE]
  > Aby odinstalować `PATH`szablon przy użyciu programu , musisz w pełni zakwalifikować ścieżkę. Na przykład *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie działać.
  > Nie dołączaj ostatecznego ukośnika katalogu kończącego na ścieżce szablonu.

- **`--update-apply`**

  Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane, i instaluje je. Dostępne od .NET Core 3.0 SDK.

- **`--update-check`**

  Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane. Dostępne od .NET Core 3.0 SDK.

## <a name="template-options"></a>Opcje szablonu

Każdy szablon projektu może mieć dostępne dodatkowe opcje. Podstawowe szablony mają następujące dodatkowe opcje:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Dostępne od .NET Core 3.0 SDK.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3. Nie jest obsługiwany dla języka F#. Dostępne od .NET Core 2.2 SDK.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Jeśli określono, nie wykonuje niejawnego przywracania podczas tworzenia projektu. Dostępne od .NET Core 2.2 SDK.

***

### <a name="classlib"></a>Classlib

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas `netstandard<version>` .NET Core lub utworzyć bibliotekę klas standardowych platformy .NET. Wartością domyślną jest `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3. Nie jest obsługiwany dla języka F#. Dostępne od .NET Core 2.2 SDK.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Wartością domyślną jest `netcoreapp3.1`. Dostępne od .NET Core 3.1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>winforms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` właściwość w utworzonym pliku projektu. Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.

  Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="worker-grpc"></a><a name="web-others"></a>pracownik, grpc

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Wartością domyślną jest `netcoreapp3.1`. Dostępne od .NET Core 3.1 SDK.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="mstest-xunit"></a><a name="test"></a>mstest, xunit

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Opcja dostępna od pliku .NET Core 3.0 SDK.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="nunit"></a>Nunit

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="page"></a>Strona

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obszar nazw dla wygenerowanego kodu. Wartością domyślną jest `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Tworzy stronę bez PageModel.

***

### <a name="viewimports-proto"></a><a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obszar nazw dla wygenerowanego kodu. Wartością domyślną jest `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `Individual`- Indywidualne uwierzytelnianie.
  - `IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.
  - `SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.
  - `MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.
  - `Windows`- Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia. Użyj `IndividualB2C` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestracji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-rp|--reset-password-policy-id <ID>`**

  Identyfikator zasad resetowania haseł dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-ep|--edit-profile-policy-id <ID>`**

  Identyfikator zasad profilu edycji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory do nawiązania połączenia. Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania. Wartością domyślną jest `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia. Wartością domyślną jest `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania. Wartością domyślną jest `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania. Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania. Wartością domyślną jest `/signin-oidc`.

- **`-r|--org-read-access`**

  Umożliwia tej aplikacji dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , `--auth`, lub nie są używane do .

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Opcja niedostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS.

***

### <a name="mvc-webapp"></a><a name="web-options"></a>mvc, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `Individual`- Indywidualne uwierzytelnianie.
  - `IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.
  - `SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.
  - `MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.
  - `Windows`- Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia. Użyj `IndividualB2C` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestracji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-rp|--reset-password-policy-id <ID>`**

  Identyfikator zasad resetowania haseł dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`-ep|--edit-profile-policy-id <ID>`**

  Identyfikator zasad profilu edycji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory do nawiązania połączenia. Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania. Wartością domyślną jest `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia. Wartością domyślną jest `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania. Wartością domyślną jest `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania. Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania. Wartością domyślną jest `/signin-oidc`.

- **`-r|--org-read-access`**

  Umożliwia tej aplikacji dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , , lub nie są używane.

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Opcja dostępna od pliku .NET Core 3.0 SDK.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

- **`--use-browserlink`**

  Zawiera BrowserLink w projekcie. Opcja niedostępna w zestawach SDK .NET Core 2.2 i 3.1.

- **`-rrc|--razor-runtime-compilation`**

  Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania. Opcja dostępna od pliku .NET Core 3.1 SDK.

***

### <a name="angular-react"></a><a name="spa"></a>kątowe, reagować

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Dostępne od .NET Core 3.0 SDK.
  
  Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `Individual`- Indywidualne uwierzytelnianie.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma zastosowanie `None`tylko wtedy, gdy uwierzytelnianie jest .

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania. Dostępne od .NET Core 3.0 SDK.

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Opcja niedostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

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

  Określa [strukturę](../../standard/frameworks.md) docelową. Opcja niedostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS.

***

### <a name="razorclasslib"></a>brzytwaklasyb

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

- **`-s|--support-pages-and-views`**

  Obsługuje dodawanie tradycyjnych stron razor i widoki oprócz składników do tej biblioteki. Dostępne od .NET Core 3.0 SDK.

***
  
### <a name="webapi"></a>Webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`- Brak uwierzytelniania (domyślnie).
  - `IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.
  - `SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.
  - `Windows`- Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia. Użyj `IndividualB2C` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestracji dla tego projektu. Użyj `IndividualB2C` z uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie usługi Azure Active Directory do nawiązania połączenia. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania. Wartością domyślną jest `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania. Wartością domyślną jest `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć. Użyj `SingleOrg` z uwierzytelnianiem. Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Umożliwia tej aplikacji dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza *launchSettings.json* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. `app.UseHsts`i `app.UseHttpsRedirection` nie są `Startup.Configure`dodawane do . Ta opcja ma `IndividualB2C` zastosowanie `SingleOrg` tylko wtedy, gdy lub nie są używane do uwierzytelniania.

- **`-uld|--use-local-db`**

  Określa LocalDB powinny być używane zamiast SQLite. Dotyczy tylko `IndividualB2C` uwierzytelniania.

- **`-f|--framework <FRAMEWORK>`**

  Określa [strukturę](../../standard/frameworks.md) docelową. Opcja niedostępna w sdk .NET Core 2.2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas tworzenia projektu.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Określa wersję pliku .NET Core SDK, który ma być używany w pliku *global.json.*

***

## <a name="examples"></a>Przykłady

- Utwórz projekt aplikacji konsoli języka C#, określając nazwę szablonu:

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

- Utwórz nowy projekt core ASP.NET c# MVC w bieżącym katalogu bez uwierzytelniania:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Utwórz nowy projekt xUnit:

  ```dotnetcli
  dotnet new xunit
  ```

- Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):List all templates available for Single Page Application (SPA) templates:

  ```dotnetcli
  dotnet new spa -l
  ```

- Wyświetl listę wszystkich szablonów pasujących do podciągów *my.* Nie znaleziono dokładnego dopasowania, więc dopasowanie podciągu działa zarówno względem krótkiej nazwy, jak i kolumn nazw.

  ```dotnetcli
  dotnet new we -l
  ```

- Próba wywołania szablonu pasującego *ng*. Jeśli nie można określić pojedynczego dopasowania, wyświetl listę szablonów, które są częściowymi dopasowaniami.

  ```dotnetcli
  dotnet new ng
  ```

- Zainstaluj wersję 2.0 szablonów SPA dla ASP.NET Core:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Wyświetl listę zainstalowanych szablonów i szczegółowe informacje na ich temat, w tym sposób ich odinstalowania:

  ```dotnetcli
  dotnet new -u
  ```

- Utwórz *global.json* w bieżącym katalogu ustawienie wersji SDK do 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Zobacz też

- [Szablony niestandardowe dla dotnet new](custom-templates.md)
- [Tworzenie szablonu niestandardowego dla polecenia dotnet new](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-template-samples Repo GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Dostępne szablony dla dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
