---
title: Dane telemetryczne sdk.NET Core
description: Odkryj funkcje telemetrii SDK .NET Core, które zbierają informacje o użyciu do analizy, jakie dane są zbierane i jak je wyłączyć.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 9d5d7ff09ade89712f2fbbe35224851bb1c28b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156689"
---
# <a name="net-core-sdk-telemetry"></a>Dane telemetryczne sdk.NET Core

Zestaw [SDK .NET Core](index.md) zawiera funkcję telemetrii, która zbiera dane użycia i informacje o wyjątkach po awarii procesora CLI.NET Core SDK includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes. .NET Core CLI pochodzi z .NET Core SDK i jest zestaw zleceń, które umożliwiają tworzenie, testowanie i publikowanie aplikacji .NET Core. Ważne jest, aby zespół .NET rozumiał, jak narzędzia są używane, dzięki czemu można je ulepszyć. Informacje o niepowodzeniach pomagają zespołowi rozwiązywać problemy i naprawiać błędy.

Zebrane dane są anonimowe i publikowane łącznie na licencji [Creative Commons Uznanie autorstwa.](https://creativecommons.org/licenses/by/4.0/)

## <a name="scope"></a>Zakres

`dotnet`ma dwie funkcje: uruchamianie aplikacji i wykonywanie poleceń wiersza polecenia. Dane telemetryczne nie `dotnet` są *zbierane* podczas uruchamiania aplikacji w następującym formacie:

- `dotnet [path-to-app].dll`

Dane telemetryczne *są zbierane* podczas korzystania z dowolnych [poleceń cli .NET Core,](index.md)takich jak:

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak zrezygnować

Funkcja telemetrii SDK .NET Core jest domyślnie włączona. Aby zrezygnować z funkcji telemetrii, `1` `true`ustaw zmienną środowiskową `DOTNET_CLI_TELEMETRY_OPTOUT` na lub .

Pojedynczy wpis telemetrii jest również wysyłany przez instalatora SDK .NET Core, gdy nastąpi pomyślna instalacja. Aby zrezygnować, `DOTNET_CLI_TELEMETRY_OPTOUT` należy ustawić zmienną środowiskową przed zainstalowaniem zestawu SDK .NET Core.

## <a name="disclosure"></a>Ujawnienie

Zestaw SDK .NET Core wyświetla tekst podobny do następującego po pierwszym uruchomieniu jednego z `dotnet build` [poleceń cli .NET Core](index.md) (na przykład). Tekst może się nieznacznie różnić w zależności od używanej wersji programu SDK. To środowisko "pierwszego uruchomienia" polega na tym, jak firma Microsoft powiadamia użytkownika o zbieraniu danych.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a>Punkty danych

Funkcja telemetrii nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail. Nie skanuje kodu i nie wyodrębnia danych na poziomie projektu, takich jak nazwa, repozytorium lub autor. Dane są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu technologii [usługi Azure Monitor,](https://azure.microsoft.com/services/monitor/) przechowywane w ramach ograniczonego dostępu i publikowane pod ścisłymi kontrolami zabezpieczeń z bezpiecznych systemów [usługi Azure Storage.](https://azure.microsoft.com/services/storage/)

Ochrona prywatności jest dla nas ważna. Jeśli podejrzewasz, że dane telemetryczne zbierają poufne dane lub dane są niebezpiecznie lub niewłaściwie obsługiwane, zgłoś problem w [dotnet@microsoft.com](mailto:dotnet@microsoft.com) repozytorium [dotnet/cli](https://github.com/dotnet/cli/issues) lub wyślij wiadomość e-mail do badania.

Funkcja telemetrii zbiera następujące dane:

| Wersje SDK | Dane |
|--------------|------|
| Wszystkie          | Sygnatura czasowa wywołania. |
| Wszystkie          | Polecenie wywoływane (na przykład "build"), haszowane począwszy od 2.1. |
| Wszystkie          | Trzy oktetowe adres IP używane do określenia lokalizacji geograficznej. |
| Wszystkie          | System operacyjny i wersja. |
| Wszystkie          | Identyfikator działania (RID) jest uruchomiony na sdk. |
| Wszystkie          | Wersja SDK .NET Core. |
| Wszystkie          | Profil telemetrii: wartość opcjonalna używana tylko z jawną zgodą użytkownika i używana wewnętrznie w firmie Microsoft. |
| >=2,0        | Argumenty i opcje polecenia: zbiera się kilka argumentów i opcji (nie dowolnych ciągów). Zobacz [zebrane opcje](#collected-options). Hashed po 2.1.300. |
| >=2,0         | Czy zestaw SDK jest uruchomiony w kontenerze. |
| >=2,0         | Platformdocelowych (ze `TargetFramework` zdarzenia), haszowane począwszy od 2.1. |
| >=2,0         | Hashed Media Access Control (MAC) adres: kryptograficznie (SHA256) anonimowy i unikatowy identyfikator dla komputera. |
| >=2,0         | Hashed bieżącego katalogu roboczego. |
| >=2,0         | Zainstaluj raport o powodzej sukcesu, z haszowany instalator exe nazwa_ |
| >= 2,1 300     | Wersja jądra. |
| >= 2,1 300     | Libc wydania/wersji. |
| >= 3,0,100     | Czy dane wyjściowe zostały przekierowane (prawda lub fałsz). |
| >= 3,0,100     | W awarii cli/SDK typ wyjątku i jego śledzenia stosu (tylko kod CLI/SDK znajduje się w śledzenia stosu wysłane). Aby uzyskać więcej informacji, zobacz [.NET Core CLI/SDK błąd wyjątek telemetrii zebranych](#net-core-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Zebrane opcje

Niektóre polecenia wysyłają dodatkowe dane. Pierwszy argument wysyła podzbiór poleceń:

| Polecenie               | Wysłane dane pierwszego argumentu                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | Pomoc polecenia jest przeszukiwana.  |
| `dotnet new <arg>`    | Nazwa szablonu (haszowane).             |
| `dotnet add <arg>`    | Słowo `package` lub `reference`.      |
| `dotnet remove <arg>` | Słowo `package` lub `reference`.      |
| `dotnet list <arg>`   | Słowo `package` lub `reference`.      |
| `dotnet sln <arg>`    | Słowo `add`, `list`lub `remove`.    |
| `dotnet nuget <arg>`  | Słowo `delete`, `locals`lub `push`. |

Podzbiór poleceń wysyła wybrane opcje, jeśli są używane, wraz z ich wartościami:

| Opcja                  | Polecenia                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | Wszystkie polecenia                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`                  |
| `--framework`           | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest` |
| `--runtime`             | `dotnet build`,  `dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

Z `--verbosity` wyjątkiem `--sdk-package-version`i , wszystkie inne wartości są haszowane począwszy od .NET Core 2.1.100 SDK.

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>Zebrane dane telemetryczne wyjątku awarii wiersza wiersza wiersza usługi .NET Core/SDK

Jeśli .NET Core CLI/SDK ulega awarii, zbiera nazwę wyjątku i śledzenia stosu kodu CLI/SDK. Te informacje są zbierane w celu oceny problemów i poprawy jakości .NET Core SDK i CLI. Ten artykuł zawiera informacje o gromadzonych przez nas danych. Zawiera również wskazówki dotyczące sposobu, w jaki użytkownicy budujący własną wersję sdk .NET Core mogą uniknąć nieumyślnego ujawnienia informacji osobistych lub poufnych.

### <a name="types-of-collected-data"></a>Rodzaje zebranych danych

Interfejs cli programu .NET Core zbiera informacje tylko dla wyjątków cli/SDK, a nie wyjątki w aplikacji. Zebrane dane zawierają nazwę wyjątku i śledzenia stosu. Ten ślad stosu jest kodem CLI/SDK.

W poniższym przykładzie przedstawiono rodzaj danych, które są zbierane:

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a>Unikanie nieumyślnego ujawnienia informacji

Współautorzy programu .NET Core i każda inna osoba, która uruchamia wersję sdk .NET Core SDK, którą sami stworzyli, powinni rozważyć ścieżkę do kodu źródłowego sdk. Jeśli wystąpi awaria podczas korzystania z .NET Core SDK, który jest niestandardową kompilacją debugowania lub skonfigurowany z niestandardowymi plikami symboli kompilacji, ścieżka pliku źródłowego sdk z komputera kompilacji jest zbierana jako część śledzenia stosu i nie jest haszowana.

Z tego powodu niestandardowe kompilacje sdk .NET Core nie powinny znajdować się w katalogach, których nazwy ścieżek udostępniają informacje osobiste lub poufne.

## <a name="see-also"></a>Zobacz też

- [.NET Core CLI Telemetria - Dane za II kwartał 2019](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [Źródło odwołania telemetrii (repozytorium dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
