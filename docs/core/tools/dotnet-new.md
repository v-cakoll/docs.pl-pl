---
title: nowe polecenia DotNet
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
ms.date: 10/24/2018
ms.openlocfilehash: 3a10aaa93af57e7beb86771e7d3b00b06fca14b2
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169693"
---
# <a name="dotnet-new"></a>nowe polecenia DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.

Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.

## <a name="arguments"></a>Argumenty

`TEMPLATE`

Szablon do utworzenia wystąpienia podczas wywoływania polecenia. Każdy szablon może być określone opcje, które można przekazać. Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300. Domyślny język dla szablonu jest wyświetlany w nawiasie.

|Opis szablonu                          | Nazwa szablonu    | Języki     |
|----------------------------------------------|------------------|---------------|
| Aplikacja konsolowa                          | `console`        | [C#], F#, VB  |
| Biblioteka klas                                | `classlib`       | [C#], F#, VB  |
| Projekt testów jednostkowych                            | `mstest`         | [C#], F#, VB  |
| projekt testu xUnit                           | `xunit`          | [C#], F#, VB  |
| Projekt testu NUnit                           | `nunit`          | [C#], F#, VB  |
| Strona razor                                   | `page`           | [C#]          |
| MVC ViewImports                              | `viewimports`    | [C#]          |
| MVC ViewStart                                | `viewstart`      | [C#]          |
| Platforma ASP.NET Core puste                           | `web`            | [C#], F#      |
| Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller) | `mvc`            | [C#], F#      |
| Aplikacja sieci Web platformy ASP.NET Core                         | `razor`, `webapp`| [C#]          |
| Platforma ASP.NET Core przy użyciu usługi Angular                    | `angular`        | [C#]          |
| Platforma ASP.NET Core z użyciem biblioteki React.js                   | `react`          | [C#]          |
| Platforma ASP.NET Core z użyciem biblioteki React.js i Redux         | `reactredux`     | [C#]          |
| Interfejs API sieci Web platformy ASP.NET Core                         | `webapi`         | [C#], F#      |
| Biblioteki klas razor                          | `razorclasslib`  | [C#]          |
| plik Global.JSON                             | `globaljson`     |               |
| NuGet config                                 | `nugetconfig`    |               |
| Konfiguracja sieci Web                                   | `webconfig`      |               |
| Plik rozwiązania                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą platformy .NET Core SDK 2.0. Domyślny język dla szablonu jest wyświetlany w nawiasie.

|Opis szablonu                          | Nazwa szablonu | Języki     |
|----------------------------------------------|---------------|---------------|
| Aplikacja konsolowa                          | `console`     | [C#], F#, VB  |
| Biblioteka klas                                | `classlib`    | [C#], F#, VB  |
| Projekt testów jednostkowych                            | `mstest`      | [C#], F#, VB  |
| projekt testu xUnit                           | `xunit`       | [C#], F#, VB  |
| Platforma ASP.NET Core puste                           | `web`         | [C#], F#      |
| Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller) | `mvc`         | [C#], F#      |
| Aplikacja sieci Web platformy ASP.NET Core                         | `razor`       | [C#]          |
| Platforma ASP.NET Core przy użyciu usługi Angular                    | `angular`     | [C#]          |
| Platforma ASP.NET Core z użyciem biblioteki React.js                   | `react`       | [C#]          |
| Platforma ASP.NET Core z użyciem biblioteki React.js i Redux         | `reactredux`  | [C#]          |
| Interfejs API sieci Web platformy ASP.NET Core                         | `webapi`      | [C#], F#      |
| plik Global.JSON                             | `globaljson`  |               |
| NuGet config                                 | `nugetconfig` |               |
| Konfiguracja sieci Web                                   | `webconfig`   |               |
| Plik rozwiązania                                | `sln`         |               |
| Strona razor                                   | `page`        |               |
| MVC ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą zestawu SDK programu .NET Core 1.x. Domyślny język dla szablonu jest wyświetlany w nawiasie.

|Opis szablonu  | Nazwa szablonu | Języki |
|----------------------|---------------|-----------|
| Aplikacja konsolowa  | `console`     | [C#], F#  |
| Biblioteka klas        | `classlib`    | [C#], F#  |
| Projekt testów jednostkowych    | `mstest`      | [C#], F#  |
| projekt testu xUnit   | `xunit`       | [C#], F#  |
| Platforma ASP.NET Core puste   | `web`         | [C#]      |
| Aplikacja sieci Web platformy ASP.NET Core | `mvc`         | [C#], F#  |
| Interfejs API sieci Web platformy ASP.NET Core | `webapi`      | [C#]      |
| NuGet config         | `nugetconfig` |           |
| Konfiguracja sieci Web           | `webconfig`   |           |
| Plik rozwiązania        | `sln`         |           |

---

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force`

Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki. Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.

`-h|--help`

Drukuje pomoc dotyczącą polecenia. Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane. Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`. Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet. Zobacz przykład w [przykłady](#examples) sekcji.

Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).

`-l|--list`

Wyświetla listę szablonów zawierających określonej nazwy. Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.

`-lang|--language {C#|F#|VB}`

Język szablonu w celu utworzenia. Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji). Nie jest prawidłowy dla niektórych szablonów.

> [!NOTE]
> Interpretowanie niektóre powłoki `#` jako znak specjalny. W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa utworzonej danych wyjściowych. Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.

`--nuget-source`

Określa źródła pakietów NuGet do użycia podczas instalacji.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, aby umieścić wygenerowanych danych wyjściowych. Ustawieniem domyślnym jest bieżący katalog.

`--type`

Filtrowanie na podstawie typów dostępnych szablonów. Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.

> [!NOTE]
> Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki. Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.
> Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force`

Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki. Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.

`-h|--help`

Drukuje pomoc dotyczącą polecenia. Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane. Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`. Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet. Zobacz przykład w [przykłady](#examples) sekcji.

Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).

`-l|--list`

Wyświetla listę szablonów zawierających określonej nazwy. Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.

`-lang|--language {C#|F#|VB}`

Język szablonu w celu utworzenia. Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji). Nie jest prawidłowy dla niektórych szablonów.

> [!NOTE]
> Interpretowanie niektóre powłoki `#` jako znak specjalny. W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa utworzonej danych wyjściowych. Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, aby umieścić wygenerowanych danych wyjściowych. Ustawieniem domyślnym jest bieżący katalog.

`--type`

Filtrowanie na podstawie typów dostępnych szablonów. Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.

> [!NOTE]
> Aby odinstalować szablonu korzystanie ze źródła `PATH`, należy do pełnej kwalifikacji ścieżki. Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie. Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.
> 
> Jeśli nie można określić `PATH` lub `NUGET_ID` argument niezbędnych do odinstalowania szablon systemem `dotnet new --uninstall` bez argumentu, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argument, trzeba je odinstalować.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia. Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force. Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.

`-h|--help`

Drukuje pomoc dotyczącą polecenia. Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.

`-l|--list`

Wyświetla listę szablonów zawierających określonej nazwy. Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.

`-lang|--language {C#|F#}`

Język szablonu w celu utworzenia. Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji). Nie jest prawidłowy dla niektórych szablonów.

> [!NOTE]
> Interpretowanie niektóre powłoki `#` jako znak specjalny. W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Nazwa utworzonej danych wyjściowych. Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacja, aby umieścić wygenerowanych danych wyjściowych. Ustawieniem domyślnym jest bieżący katalog.

---

## <a name="template-options"></a>Opcje szablonu

Każdy szablon projektu może być dostępne dodatkowe opcje. Szablony core są dostępne następujące opcje dodatkowe:

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

**Konsola usługi angular, react, reactredux dla platformy, razorclasslib**

  `--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**classlib**

`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard. Wartość domyślna to `netstandard2.0`.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**mstest, xunit**

`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.

**web**

`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

`--no-https` -Projekt nie wymaga protokołu HTTPS. Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — Bez uwierzytelniania (ustawienie domyślne).
- `IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
- `SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.
- `Windows` -Uwierzytelnianie Windows.

`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie. Za pomocą `IndividualB2C` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — Identyfikator klienta dla tego projektu. Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domena dzierżawy katalogu. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.

`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

`--no-https` -Projekt nie wymaga protokołu HTTPS. `app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`. Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — Bez uwierzytelniania (ustawienie domyślne).
- `Individual` -Uwierzytelnianie indywidualne.
- `IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
- `SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.
- `MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.
- `Windows` -Uwierzytelnianie Windows.

`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie. Za pomocą `IndividualB2C` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie. Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — Identyfikator klienta dla tego projektu. Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domena dzierżawy katalogu. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `/signin-oidc`.

`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.

`--use-browserlink` -Zawiera BrowserLink w projekcie.

`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

`--no-https` -Projekt nie wymaga protokołu HTTPS. `app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`. Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.

**Strona**

`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

**Konsola, angular, react reactredux dla platformy**

  `--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**classlib**

`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard. Wartość domyślna to `netstandard2.0`.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**mstest, xunit**

`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.

**web**

`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — Bez uwierzytelniania (ustawienie domyślne).
- `IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
- `SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.
- `Windows` -Uwierzytelnianie Windows.

`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie. Za pomocą `IndividualB2C` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — Identyfikator klienta dla tego projektu. Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domena dzierżawy katalogu. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.

`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia. Możliwe wartości to:

- `None` — Bez uwierzytelniania (ustawienie domyślne).
- `Individual` -Uwierzytelnianie indywidualne.
- `IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.
- `SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.
- `MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.
- `Windows` -Uwierzytelnianie Windows.

`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie. Za pomocą `IndividualB2C` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie. Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>` — Identyfikator klienta dla tego projektu. Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domena dzierżawy katalogu. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `/signin-oidc`.

`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.

`--use-browserlink` -Zawiera BrowserLink w projekcie.

`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.

**Strona**

`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**console, xunit, mstest, web, webapi**

`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp1.0` lub `netcoreapp1.1`. Wartość domyślna to `netcoreapp1.0`.

**classlib**

`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`. Wartość domyślna to `netstandard1.4`.

**mvc**

`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp1.0` lub `netcoreapp1.1`. Wartość domyślna to `netcoreapp1.0`.

`-au|--auth` -Typ uwierzytelniania do użycia. Wartości: `None` lub `Individual`. Wartość domyślna to `None`.

`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite. Wartości: `true` lub `false`. Wartość domyślna to `false`.

---

## <a name="examples"></a>Przykłady

Tworzenie F# projekt aplikacji konsoli w bieżącym katalogu:

`dotnet new console -lang F#`

Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):

`dotnet new classlib -lang VB -o MyLibrary`

Utwórz nowy projekt aplikacji w języku C# MVC ASP.NET Core w bieżącym katalogu bez uwierzytelniania:

`dotnet new mvc -au None`

Utwórz nową aplikację xUnit:

`dotnet new xunit`

Wyświetl wszystkie szablony dostępne dla platformy MVC:

`dotnet new mvc -l`

Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Zobacz także

* [Szablony niestandardowe dla nowej platformy dotnet](custom-templates.md)  
* [Tworzenie szablonu niestandardowego dla polecenia dotnet new](~/docs/core/tutorials/create-custom-template.md)  
* [repozytorium GitHub DotNet/dotnet-— przykłady szablonów](https://github.com/dotnet/dotnet-template-samples)  
* [Dostępne szablony dla nowej platformy dotnet](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
