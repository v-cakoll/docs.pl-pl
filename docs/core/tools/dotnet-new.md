---
title: polecenie Nowy DotNet - .NET Core interfejsu wiersza polecenia
description: "Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu."
keywords: DotNet nowe interfejsu wiersza polecenia, interfejsu wiersza polecenia polecenie .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a>nowe DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet new`— Umożliwia utworzenie nowego projektu, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet new` Polecenia oferują wygodny sposób zainicjować prawidłowy projekt .NET Core. 

Wywołania polecenia [aparatu szablonu](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.

## <a name="arguments"></a>Argumenty

`TEMPLATE`

Szablon można utworzyć wystąpienia po wywołaniu polecenia. Każdy szablon może mieć określone opcje, które można przekazać. Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablonów, które są zainstalowane przy użyciu zestawu SDK programu .NET Core 2.0. Język domyślny dla szablonu jest wyświetlany w nawiasie.

|Opis szablonu                          | Nazwa szablonu  | Języki     |
|----------------------------------------------|----------------|---------------|
| Aplikacji konsoli                          | konsola        | [C#] F #, VB  |
| Biblioteka klas                                | biblioteki klas       | [C#] F #, VB  |
| Jednostkowy projekt testowy                            | mstest         | [C#] F #, VB  |
| Projekt testowy xUnit                           | Xunit          | [C#] F #, VB  |
| Pusty platformy ASP.NET Core                           | sieci Web            | [C#] F #      |
| Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller) | MVC            | [C#] F #      |
| Aplikacja sieci Web platformy ASP.NET Core                         | razor          | [C#]          |
| Platformy ASP.NET Core z dyrektywy Angular                    | dyrektywy angular        | [C#]          |
| Platformy ASP.NET Core z React.js                   | Reakcji          | [C#]          |
| Platformy ASP.NET Core z React.js i Redux         | reactredux     | [C#]          |
| Interfejs API sieci Web platformy ASP.NET Core                         | webapi         | [C#] F #      |
| plik Global.JSON                             | globaljson     |               |
| Konfiguracja Nuget                                 | nugetconfig    |               |
| Konfiguracja sieci Web                                   | webconfig      |               |
| Plik rozwiązania                                | SLN            |               |
| Strona razor                                   | strona           |               |
| MVC/ViewImports                              | viewimports    |               |
| MVC ViewStart                                | viewstart      |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Polecenie zawiera domyślną listę szablonów. Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów. W poniższej tabeli przedstawiono szablonów, które są zainstalowane z platformą .NET Core 1.x zestawu SDK. Język domyślny dla szablonu jest wyświetlany w nawiasie.

|Opis szablonu  | Nazwa szablonu  | Języki |
|----------------------|----------------|-----------|
| Aplikacji konsoli  | konsola        | [C#] F #  |
| Biblioteka klas        | biblioteki klas       | [C#] F #  |
| Jednostkowy projekt testowy    | mstest         | [C#] F #  |
| Projekt testowy xUnit   | Xunit          | [C#] F #  |
| Pusty platformy ASP.NET Core   | sieci Web            | [C#]      |
| Aplikacja sieci Web platformy ASP.NET Core | MVC            | [C#] F #  |
| Interfejs API sieci Web platformy ASP.NET Core | webapi         | [C#]      |
| Konfiguracja Nuget         | nugetconfig    |           |
| Konfiguracja sieci Web           | webconfig      |           |
| Plik rozwiązania        | SLN            |           |

---

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--force`

Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki. Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.

`-h|--help`

Drukuje pomocy dla polecenia. Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane. Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).

`-l|--list`

Wyświetla listę szablonów zawierających określonej nazwy. Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.

`-lang|--language {C#|F#|VB}`

Język szablonu do utworzenia. Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji). Nie jest prawidłowy dla pewnych szablonów.

`-n|--name <OUTPUT_NAME>`

Nazwa utworzone dane wyjściowe. Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacji do umieszczenia wygenerowanych danych wyjściowych. Ustawieniem domyślnym jest bieżący katalog.

`--type`

Filtruje szablony oparte na dostępnych typów. Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.

> [!NOTE]
> Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki. Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.
> Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-all|--show-all`

Przedstawia wszystkie szablony dla określonego typu projektu, gdy działają w kontekście `dotnet new` tylko polecenia. Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force. Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.

`-h|--help`

Drukuje pomocy dla polecenia. Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.

`-l|--list`

Wyświetla listę szablonów zawierających określonej nazwy. Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu. Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.

`-lang|--language {C#|F#}`

Język szablonu do utworzenia. Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji). Nie jest prawidłowy dla pewnych szablonów.

`-n|--name <OUTPUT_NAME>`

Nazwa utworzone dane wyjściowe. Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.

`-o|--output <OUTPUT_DIRECTORY>`

Lokalizacji do umieszczenia wygenerowanych danych wyjściowych. Ustawieniem domyślnym jest bieżący katalog.

---

## <a name="template-options"></a>Opcje szablonu

Każdy szablon projektu może być dostępne dodatkowe opcje. Szablony core są następujące opcje dodatkowe:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**Konsola kątowego, reagować, reactredux**

`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.

**biblioteki klas**

`-f|--framework <FRAMEWORK>`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard. Wartość domyślna to `netstandard2.0`.

`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.

**mstest, xunit**

`-p|--enable-pack`— Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).

`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>`— Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.

**sieci Web**

`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.

`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia. Możliwe wartości to:

- `None`-Bez uwierzytelniania (ustawienie domyślne).
- `IndividualB2C`-Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.
- `SingleOrg`-Organizacji uwierzytelnianie dla pojedynczej dzierżawy.
- `Windows`— Uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia. Za pomocą `IndividualB2C` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`Identyfikator zasad logowania i rejestrowania dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`--aad-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory do nawiązania połączenia. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>`— Identyfikator klienta dla tego projektu. Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`-Domeny dla katalogu dzierżawcy. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>`-TenantId identyfikator katalogu do nawiązania połączenia. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access`— Umożliwia dostęp do odczytu do katalogu aplikacji. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.

`-uld|--use-local-db`— Określa, że LocalDB powinna być używana zamiast funkcji SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia. Możliwe wartości to:

- `None`-Bez uwierzytelniania (ustawienie domyślne).
- `Individual`-Poszczególnych uwierzytelniania.
- `IndividualB2C`-Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.
- `SingleOrg`-Organizacji uwierzytelnianie dla pojedynczej dzierżawy.
- `MultiOrg`-Organizacji uwierzytelnianie dla wielu dzierżawców.
- `Windows`— Uwierzytelnianie systemu Windows.

`--aad-b2c-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia. Za pomocą `IndividualB2C` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/tfp/` .

`-ssp|--susi-policy-id <ID>`Identyfikator zasad logowania i rejestrowania dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`-rp|--reset-password-policy-id <ID>`-Resetowania hasła zasad identyfikator dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`-ep|--edit-profile-policy-id <ID>`-Edycji profilu zasad identyfikator dla tego projektu. Za pomocą `IndividualB2C` uwierzytelniania.

`--aad-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory do nawiązania połączenia. Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania. Wartość domyślna to `https://login.microsoftonline.com/`.

`--client-id <ID>`— Identyfikator klienta dla tego projektu. Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania. Wartość domyślna to `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`-Domeny dla katalogu dzierżawcy. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `qualified.domain.name`.

`--tenant-id <ID>`-TenantId identyfikator katalogu do nawiązania połączenia. Za pomocą `SingleOrg` uwierzytelniania. Wartość domyślna to `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>`— Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI. Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania. Wartość domyślna to `/signin-oidc`.

`-r|--org-read-access`— Umożliwia dostęp do odczytu do katalogu aplikacji. Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.

`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.

`--use-browserlink`-Zawiera BrowserLink w projekcie.

`-uld|--use-local-db`— Określa, że LocalDB powinna być używana zamiast funkcji SQLite. Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.

`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.

**Strona**

`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

`-np|--no-pagemodel`-Tworzy tę stronę bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu. Wartość domyślna to `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**Konsola, xunit, mstest, sieci web, webapi**

`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp1.0` lub `netcoreapp1.1`. Wartość domyślna to `netcoreapp1.0`.

**biblioteki klas**

`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`. Wartość domyślna to `netstandard1.4`.

**MVC**

`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego. Wartości: `netcoreapp1.0` lub `netcoreapp1.1`. Wartość domyślna to `netcoreapp1.0`.

`-au|--auth`— Typ uwierzytelniania do użycia. Wartości: `None` lub `Individual`. Wartość domyślna to `None`.

`-uld|--use-local-db`— Określa, czy do korzystania z bazy danych LocalDB zamiast SQLite. Wartości: `true` lub `false`. Wartość domyślna to `false`.

---

## <a name="examples"></a>Przykłady

Utworzyć projekt aplikacji konsoli F # w bieżącym katalogu:

`dotnet new console -lang f#`

Utwórz .NET Standard projektu biblioteki klas w określonym katalogu (dostępne tylko z zestawu SDK programu .NET Core 2.0 lub nowsze wersje):

`dotnet new classlib -lang VB -o MyLibrary`

Bez uwierzytelniania przeznaczonych dla platformy .NET Core 2.0, Utwórz nowy projekt aplikacji platformy ASP.NET Core C# MVC w bieżącym katalogu:

`dotnet new mvc -au None -f netcoreapp2.0`

Utwórz nową aplikację xUnit przeznaczonych dla platformy .NET Core 2.0:

`dotnet new xunit --framework netcoreapp2.0`

Lista wszystkich dostępnych szablonów dla platformy MVC:

`dotnet new mvc -l`

## <a name="see-also"></a>Zobacz także

[Szablony niestandardowe dla nowego dotnet](custom-templates.md)  
[Tworzenie szablonu niestandardowego dla polecenia dotnet new](~/docs/core/tutorials/create-custom-template.md)  
[repozytorium GitHub DotNet/dotnet szablonu — przykłady](https://github.com/dotnet/dotnet-template-samples)  
[Dostępne szablony dla nowych dotnet](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
