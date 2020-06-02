---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 39301ad95761848b60b45cb5c18ede937f70c32c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283978"
---
# <a name="dotnet-new"></a>dotnet new

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet new`-Tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>Opis

`dotnet new`Polecenie tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.

Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.

### <a name="implicit-restore"></a>Przywracanie niejawne

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`TEMPLATE`**

  Szablon do wystąpienia po wywołaniu polecenia. Każdy szablon może mieć określone opcje, które można przekazać. Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).

  Można uruchomić `dotnet new --list` lub `dotnet new -l` wyświetlić listę wszystkich zainstalowanych szablonów. Jeśli `TEMPLATE` wartość nie jest dokładnym dopasowaniem do tekstu w kolumnie **Szablony** lub **krótka nazwa** z zwróconej tabeli, do tych dwóch kolumn jest wykonywane dopasowanie podciągu.

  Począwszy od zestawu SDK platformy .NET Core 3,0, interfejs wiersza polecenia wyszukuje szablony w NuGet.org, gdy wywoła `dotnet new` polecenie w następujących warunkach:

  - Jeśli interfejs wiersza polecenia nie może znaleźć dopasowania szablonu podczas wywoływania `dotnet new` , nie nawet częściowej.
  - Jeśli jest dostępna nowsza wersja szablonu. W takim przypadku projekt lub artefakt jest tworzony, ale interfejs wiersza polecenia ostrzega użytkownika o zaktualizowanej wersji szablonu.

  W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane wraz z zestaw .NET Core SDK. Język domyślny dla szablonu jest pokazywany w nawiasach. Kliknij link krótkiej nazwy, aby wyświetlić opcje konkretnego szablonu.

| Szablony                                    | Krótka nazwa                      | Język     | Tagi                                  | Wraca |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Aplikacja konsoli                          | [konsoli](#console)             | [C#], F #, VB | Wspólna/konsola                        | 1.0        |
| Biblioteka klas                                | [określono](#classlib)           | [C#], F #, VB | Wspólna/Biblioteka                        | 1.0        |
| Aplikacja WPF                              | [kodow](#wpf)                     | Znajd         | Common/WPF                            | 3.0        |
| Biblioteka klas WPF                            | [wpflib](#wpf)                  | Znajd         | Common/WPF                            | 3.0        |
| Biblioteka kontrolek niestandardowych WPF                   | [wpfcustomcontrollib](#wpf)     | Znajd         | Common/WPF                            | 3.0        |
| Biblioteka kontrolek użytkownika WPF                     | [wpfusercontrollib](#wpf)       | Znajd         | Common/WPF                            | 3.0        |
| Aplikacja Windows Forms (WinForms)         | [WinForms](#winforms)           | Znajd         | Typowe/WinForms                       | 3.0        |
| Biblioteka klas Windows Forms (WinForms)       | [winformslib](#winforms)        | Znajd         | Typowe/WinForms                       | 3.0        |
| Usługa procesu roboczego                               | [odpowiedzialn](#web-others)           | Znajd         | Common/Worker/sieć Web                     | 3.0        |
| Projekt testu jednostkowego                            | [MSTest](#test)                 | [C#], F #, VB | Test/MSTest                           | 1.0        |
| Projekt testowy NUnit 3                         | [NUnit](#nunit)                  | [C#], F #, VB | Test/NUnit                            | 2.1.400    |
| Element testowy NUnit 3                            | `nunit-test`                    | [C#], F #, VB | Test/NUnit                            | 2.2        |
| Projekt testu xUnit                           | [xUnit](#test)                  | [C#], F #, VB | Test/xUnit                            | 1.0        |
| Składnik Razor                              | `razorcomponent`                | Znajd         | Web/ASP. NET                           | 3.0        |
| Strona Razor                                   | [stronic](#page)                   | Znajd         | Web/ASP. NET                           | 2.0        |
| ViewImports MVC                              | [viewimports](#namespace)       | Znajd         | Web/ASP. NET                           | 2.0        |
| ViewStart MVC                                | `viewstart`                     | Znajd         | Web/ASP. NET                           | 2.0        |
| Aplikacja serwera Blazor                            | [blazorserver](#blazorserver)   | Znajd         | Sieć Web/Blazor                            | 3.0        |
| Aplikacja webassembly Blazor                       | `blazorwasm`                    | Znajd         | Sieć Web/Blazor/webassembly                            | 3.1.300    |
| ASP.NET Core puste                           | [witrynę](#web)                     | [C#], F #     | Sieć Web/pusta                             | 1.0        |
| Aplikacja sieci Web ASP.NET Core (Model-View-Controller) | [Standard](#web-options)             | [C#], F #     | Web/MVC                               | 1.0        |
| Aplikacja sieci Web ASP.NET Core                         | [webapp, Razor](#web-options)   | Znajd         | Web/MVC/Razor Pages                   | 2,2, 2,0   |
| ASP.NET Core ze Skośnością                    | [kątow](#spa)                 | Znajd         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core z usługą reaguj. js                   | [biern](#spa)                   | Znajd         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core z reakcjęmi. js i Redux         | [reactredux](#reactredux)       | Znajd         | Web/MVC/SPA                           | 2.0        |
| Biblioteka klas Razor                          | [razorclasslib](#razorclasslib) | Znajd         | Biblioteka klas sieci Web/Razor/Biblioteka/Razor | 2.1        |
| Internetowy interfejs API platformy ASP.NET Core                         | [WebApi](#webapi)               | [C#], F #     | Sieć Web/WebAPI                            | 1.0        |
| ASP.NET Core usługi gRPC                    | [grpc](#web-others)             | Znajd         | Sieć Web/gRPC                              | 3.0        |
| plik GITIGNORE dotnet                        | `gitignore`                     |              | Config                                | 3.0        |
| plik Global. JSON                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| Konfiguracja narzędzia NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| Plik manifestu narzędzia lokalnego dotnet              | `tool-manifest`                 |              | Config                                | 3.0        |
| Konfiguracja sieci Web                                   | `webconfig`                     |              | Config                                | 1.0        |
| Plik rozwiązania                                | `sln`                           |              | Rozwiązanie                              | 1.0        |
| Plik buforu protokołu                         | [proto](#namespace)             |              | Sieć Web/gRPC                              | 3.0        |

## <a name="options"></a>Opcje

- **`--dry-run`**

  Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu. Dostępne od wersji .NET Core 2,2 SDK.

- **`--force`**

  Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików. Jest to wymagane, gdy wybrany szablon spowoduje zastąpienie istniejących plików w katalogu wyjściowym.

- **`-h|--help`**

  Drukuje pomoc dla polecenia. Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu. Na przykład `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Instaluje pakiet szablonów z `PATH` lub `NUGET_ID` dostarczone. Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>` . Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje najnowszą stabilną wersję pakietu. Zobacz przykład w sekcji [przykładów](#examples) .
  
  Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.

  Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).

- **`-l|--list`**

  Wyświetla listę szablonów zawierających określoną nazwę. Jeśli nazwa nie zostanie określona, program wyświetli listę wszystkich szablonów.

- **`-lang|--language {C#|F#|VB}`**

  Język szablonu do utworzenia. Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ). Nieprawidłowy dla niektórych szablonów.

  > [!NOTE]
  > Niektóre powłoki interpretują `#` jako znak specjalny. W takich przypadkach należy ująć wartość parametru Language w cudzysłów. Na przykład `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Nazwa dla utworzonych danych wyjściowych. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.

- **`--nuget-source <SOURCE>`**

  Określa źródło NuGet do użycia podczas instalacji. Dostępne od wersji .NET Core 2,1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

- **`--type <TYPE>`**

  Filtruje szablony w oparciu o dostępne typy. Wstępnie zdefiniowane wartości to `project` , `item` , i `other` .

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` udostępniony. Gdy `<PATH|NUGET_ID>` wartość nie jest określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony. Podczas określania `NUGET_ID` nie należy umieszczać numeru wersji.

  Jeśli nie określisz parametru do tej opcji, polecenie wyświetli listę zainstalowanych szablonów i szczegółowe informacje o nich.

  > [!NOTE]
  > Aby odinstalować szablon przy użyciu programu `PATH` , należy w pełni zakwalifikować ścieżkę. Na przykład *C:/Users/ \<USER> /Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.
  > Nie dołączaj ostatecznego ukośnika katalogu w ścieżce szablonu.

- **`--update-apply`**

  Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane i instaluje je. Dostępne od wersji .NET Core 3,0 SDK.

- **`--update-check`**

  Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane. Dostępne od wersji .NET Core 3,0 SDK.

## <a name="template-options"></a>Opcje szablonu

Każdy szablon projektu może mieć dodatkowe opcje dostępne. Szablony podstawowe mają następujące dodatkowe opcje:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Dostępne od wersji .NET Core 3,0 SDK.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` Właściwość w utworzonym pliku projektu. Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3. Nieobsługiwane dla języka F #. Dostępne od wersji .NET Core 2,2 SDK.

  Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Jeśli określony, nie wykonuje przywracania niejawnego podczas tworzenia projektu. Dostępne od wersji .NET Core 2,2 SDK.

***

### <a name="classlib"></a>określono

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Wartości: `netcoreapp<version>` Aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard<version>` utworzyć bibliotekę klas .NET Standard. Wartość domyślna to `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` Właściwość w utworzonym pliku projektu. Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3. Nieobsługiwane dla języka F #. Dostępne od wersji .NET Core 2,2 SDK.

  Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Wartość domyślna to `netcoreapp3.1`. Dostępne od wersji .NET Core 3,1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` Właściwość w utworzonym pliku projektu. Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.

  Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>WinForms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Ustawia `LangVersion` Właściwość w utworzonym pliku projektu. Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.

  Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="worker-grpc"></a><a name="web-others"></a>proces roboczy, GRPC

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Wartość domyślna to `netcoreapp3.1`. Dostępne od wersji .NET Core 3,1 SDK.

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="mstest-xunit"></a><a name="test"></a>MSTest, xUnit

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja dostępna od wersji .NET Core 3,0 SDK.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="nunit"></a>NUnit

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="page"></a>stronic

- **`-na|--namespace <NAMESPACE_NAME>`**

  Przestrzeń nazw dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Tworzy stronę bez PageModel.

***

### <a name="viewimports-proto"></a><a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Przestrzeń nazw dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`-Brak uwierzytelniania (wartość domyślna).
  - `Individual`-Uwierzytelnianie indywidualne.
  - `IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.
  - `SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.
  - `MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.
  - `Windows`— Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`-rp|--reset-password-policy-id <ID>`**

  Identyfikator zasad resetowania hasła dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`-ep|--edit-profile-policy-id <ID>`**

  Edytuj identyfikator zasad profilu dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Używanie z usługą `SingleOrg` lub `MultiOrg` uwierzytelnianiem. Wartość domyślna to `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj z `IndividualB2C` , `SingleOrg` lub `MultiOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z `SingleOrg` uwierzytelnianiem. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania. Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `/signin-oidc`.

- **`-r|--org-read-access`**

  Zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` `MultiOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy,, `Individual` `IndividualB2C` `SingleOrg` lub `MultiOrg` nie są używane w programie `--auth` .

- **`-uld|--use-local-db`**

  Należy używać LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS.

***

### <a name="mvc-webapp"></a><a name="web-options"></a>MVC, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`-Brak uwierzytelniania (wartość domyślna).
  - `Individual`-Uwierzytelnianie indywidualne.
  - `IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.
  - `SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.
  - `MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.
  - `Windows`— Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`-rp|--reset-password-policy-id <ID>`**

  Identyfikator zasad resetowania hasła dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`-ep|--edit-profile-policy-id <ID>`**

  Edytuj identyfikator zasad profilu dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Używanie z usługą `SingleOrg` lub `MultiOrg` uwierzytelnianiem. Wartość domyślna to `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Użyj z `IndividualB2C` , `SingleOrg` lub `MultiOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z `SingleOrg` uwierzytelnianiem. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania. Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `/signin-oidc`.

- **`-r|--org-read-access`**

  Zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` `MultiOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy,, `Individual` `IndividualB2C` `SingleOrg` lub `MultiOrg` nie jest używany.

- **`-uld|--use-local-db`**

  Należy używać LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja dostępna od wersji .NET Core 3,0 SDK.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--use-browserlink`**

  Zawiera BrowserLink w projekcie. Opcja nie jest dostępna w programie .NET Core 2,2 i 3,1 SDK.

- **`-rrc|--razor-runtime-compilation`**

  Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania. Opcja dostępna od wersji .NET Core 3.1.201 SDK.

***

### <a name="angular-react"></a><a name="spa"></a>kątowy, reagowanie

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Dostępne od wersji .NET Core 3,0 SDK.
  
  Możliwe wartości są następujące:

  - `None`-Brak uwierzytelniania (wartość domyślna).
  - `Individual`-Uwierzytelnianie indywidualne.

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy uwierzytelnianie jest `None` .

- **`-uld|--use-local-db`**

  Należy używać LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania. Dostępne od wersji .NET Core 3,0 SDK.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`--no-https`**

  Wyłącza protokół HTTPS.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

- **`-s|--support-pages-and-views`**

  Obsługuje dodawanie tradycyjnych stron Razor i widoków oprócz składników do tej biblioteki. Dostępne od wersji .NET Core 3,0 SDK.

***
  
### <a name="webapi"></a>WebApi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ uwierzytelniania do użycia. Możliwe wartości są następujące:

  - `None`-Brak uwierzytelniania (wartość domyślna).
  - `IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.
  - `SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.
  - `Windows`— Uwierzytelnianie systemu Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie. Użyj z `IndividualB2C` uwierzytelnianiem. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Identyfikator zasad logowania i rejestrowania dla tego projektu. Użyj z `IndividualB2C` uwierzytelnianiem.

- **`--aad-instance <INSTANCE>`**

  Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie. Użyj z `SingleOrg` uwierzytelnianiem. Wartość domyślna to `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Identyfikator klienta dla tego projektu. Używanie z usługą `IndividualB2C` lub `SingleOrg` uwierzytelnianiem. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Domena dzierżawy katalogu. Używanie z usługą `IndividualB2C` lub `SingleOrg` uwierzytelnianiem. Wartość domyślna to `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie. Użyj z `SingleOrg` uwierzytelnianiem. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Zezwala tej aplikacji na dostęp do odczytu do katalogu. Dotyczy tylko `SingleOrg` uwierzytelniania.

- **`--exclude-launch-settings`**

  Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.

- **`--no-https`**

  Wyłącza protokół HTTPS. `app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure` . Ta opcja ma zastosowanie tylko wtedy `IndividualB2C` , gdy lub `SingleOrg` nie są używane do uwierzytelniania.

- **`-uld|--use-local-db`**

  Należy używać LocalDB zamiast oprogramowania SQLite. Dotyczy tylko `IndividualB2C` uwierzytelniania.

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę](../../standard/frameworks.md) docelową. Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.

  W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:

  | Wersja zestawu SDK | Wartość domyślna   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas tworzenia projektu.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .

***

## <a name="examples"></a>Przykłady

- Utwórz projekt aplikacji konsolowej w języku C#, określając nazwę szablonu:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Utwórz projekt aplikacji konsolowej F # w bieżącym katalogu:

  ```dotnetcli
  dotnet new console -lang "F#"
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

- Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):

  ```dotnetcli
  dotnet new spa -l
  ```

- Wyświetl listę wszystkich szablonów pasujących *do* podciągu. Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.

  ```dotnetcli
  dotnet new we -l
  ```

- Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*. Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.

  ```dotnetcli
  dotnet new ng
  ```

- Zainstaluj wersję 2,0 szablonów SPA dla ASP.NET Core:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Wyświetl listę zainstalowanych szablonów i szczegółowe informacje o nich, w tym sposoby ich odinstalowywania:

  ```dotnetcli
  dotnet new -u
  ```

- Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Zobacz także

- [Szablony niestandardowe dla nowego dotnet](custom-templates.md)
- [Tworzenie szablonu niestandardowego dla polecenia dotnet new](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-Template-przykłady repozytorium GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Dostępne szablony dla nowego dotnet](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
