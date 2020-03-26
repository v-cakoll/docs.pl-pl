---
title: Dane telemetryczne sdk .NET Core
description: Odnajduj funkcje telemetryczne .NET Core SDK, które zbierają informacje o użyciu do analizy, które dane są zbierane i jak je wyłączyć.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: a79b791abc99331ff39f5e281ee0fdc62b258989
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507285"
---
# <a name="net-core-sdk-telemetry"></a>Dane telemetryczne sdk .NET Core

Zestaw [SDK rdzenia .NET](index.md) zawiera funkcję telemetryczną, która zbiera dane użycia i informacje o wyjątkach w przypadku awarii interfejsu wiersza polecenia .NET Core. Plik wiersza polecenia .NET Core jest dostarczany z zestawem .NET Core SDK i jest zestawem zleceń, które umożliwiają tworzenie, testowanie i publikowanie aplikacji .NET Core. Ważne jest, aby zespół platformy .NET zrozumiał, jak narzędzia są używane, dzięki czemu można je ulepszyć. Informacje o błędach pomaga zespołowi rozwiązać problemy i naprawić błędy.

Zebrane dane są anonimowe i publikowane łącznie na licencji [Creative Commons Attribution License.](https://creativecommons.org/licenses/by/4.0/)

## <a name="scope"></a>Zakres

`dotnet`ma dwie funkcje: uruchamianie aplikacji i wykonywanie poleceń INTERFEJSU WIERSZA polecenia. Telemetria nie jest `dotnet` *zbierana* podczas uruchamiania aplikacji w następującym formacie:

- `dotnet [path-to-app].dll`

Dane telemetryczne *są zbierane* podczas korzystania z dowolnego [polecenia .NET Core CLI,](index.md)takich jak:

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak zrezygnować

Funkcja telemetrii .NET Core SDK jest domyślnie włączona. Aby zrezygnować z funkcji telemetrii, `1` ustaw `true`zmienną środowiskową `DOTNET_CLI_TELEMETRY_OPTOUT` na lub .

Pojedynczy wpis telemetryczny jest również wysyłany przez instalatora pakietu .NET Core SDK po pomyślnej instalacji. Aby zrezygnować, przed `DOTNET_CLI_TELEMETRY_OPTOUT` zainstalowaniem zestawu .NET Core SDK należy ustawić zmienną środowiskową.

## <a name="disclosure"></a>Ujawnienie

Przy pierwszym uruchomieniu jednego z [poleceń .NET Core CLI](index.md) (na `dotnet build`przykład) w programie .NET Core SDK jest wyświetlany tekst podobny do następującego. Tekst może się nieznacznie różnić w zależności od wersji uruchomionego sdk. To środowisko "pierwszego uruchomienia" to sposób, w jaki firma Microsoft powiadamia użytkownika o zbieraniu danych.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

Aby wyłączyć ten komunikat i wiadomość powitalną `DOTNET_NOLOGO` .NET `true`Core, ustaw zmienną środowiskową na . Należy zauważyć, że ta zmienna nie ma wpływu na rezygnację telemetryczną.

## <a name="data-points"></a>Punkty danych

Funkcja telemetrii nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail. Nie skanuje kodu i nie wyodrębnia danych na poziomie projektu, takich jak nazwa, repozytorium lub autor. Dane są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu technologii [Usługi Azure Monitor,](https://azure.microsoft.com/services/monitor/) przechowywane w ograniczonym dostępie i publikowane pod ścisłą kontrolą zabezpieczeń z bezpiecznych systemów [usługi Azure Storage.](https://azure.microsoft.com/services/storage/)

Ochrona twojej prywatności jest dla nas ważna. Jeśli podejrzewasz, że dane telemetryczne zbierają poufne dane lub dane są niezabezpieczone lub niewłaściwie obsługiwane, zgłębij problem w repozytorium [dotnet/cli](https://github.com/dotnet/cli/issues) lub wyślij wiadomość e-mail do [dotnet@microsoft.com](mailto:dotnet@microsoft.com) badania.

Funkcja telemetrii zbiera następujące dane:

| Wersje SDK | Dane |
|--------------|------|
| Wszystkie          | Sygnatura czasowa wywołania. |
| Wszystkie          | Polecenie wywoływane (na przykład "build"), haszowane począwszy od 2.1. |
| Wszystkie          | Trzy oktetowe adresy IP używane do określenia lokalizacji geograficznej. |
| Wszystkie          | System operacyjny i wersja. |
| Wszystkie          | Identyfikator środowiska uruchomieniowego (RID) jest uruchomiony na SDK. |
| Wszystkie          | .NET Core SDK w wersji. |
| Wszystkie          | Profil telemetrii: wartość opcjonalna używana tylko z jawną zgodą użytkownika i używana wewnętrznie w firmie Microsoft. |
| >=2,0        | Argumenty i opcje polecenia: zbiera się kilka argumentów i opcji (nie dowolne ciągi). Zobacz [zebrane opcje](#collected-options). Hashed po 2.1.300. |
| >=2,0         | Czy SDK jest uruchomiony w kontenerze. |
| >=2,0         | Struktury docelowe (od `TargetFramework` zdarzenia), mieszane począwszy od 2.1. |
| >=2,0         | Hashed Media Access Control (MAC) adres: kryptograficznie (SHA256) anonimowy i unikatowy identyfikator komputera. |
| >=2,0         | Haszem bieżący katalog roboczy. |
| >=2,0         | Zainstaluj raport sukcesu z haszem instalatora exe nazwa pliku. |
| >=2,1,300     | Wersja jądra. |
| >=2,1,300     | Libc release/version. |
| >=3,0,100     | Czy dane wyjściowe zostały przekierowane (true czy false). |
| >=3,0,100     | W awarii interfejsu WIERSZA/SDK typu wyjątku i jego śledzenia stosu (tylko kod INTERFEJSU WIERSZA/SDKU jest zawarty w śledzenia stosu wysłane). Aby uzyskać więcej informacji, zobacz [.NET Core CLI/SDK crash dane telemetryczne wyjątku zebrane](#net-core-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Zebrane opcje

Niektóre polecenia wysyłają dodatkowe dane. Podzbiór poleceń wysyła pierwszy argument:

| Polecenie               | Wysłane dane pierwszego argumentu                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | Pomoc polecenia jest poszukiwany.  |
| `dotnet new <arg>`    | Nazwa szablonu (skrót).             |
| `dotnet add <arg>`    | Słowo `package` lub `reference`.      |
| `dotnet remove <arg>` | Słowo `package` lub `reference`.      |
| `dotnet list <arg>`   | Słowo `package` lub `reference`.      |
| `dotnet sln <arg>`    | Słowo `add`, `list`, `remove`lub .    |
| `dotnet nuget <arg>`  | Słowo `delete`, `locals`, `push`lub . |

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

Z `--verbosity` wyjątkiem `--sdk-package-version`i , wszystkie inne wartości są mieszane począwszy od .NET Core 2.1.100 SDK.

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>Dane telemetryczne wyjątku awarii .NET Core CLI/SDK zebrane

Jeśli plik CLI/SDK .NET Core ulegnie awarii, zbiera nazwę wyjątku i śledzenia stosu kodu interfejsu wiersza polecenia/sdku. Te informacje są zbierane w celu oceny problemów i poprawy jakości .NET Core SDK i CLI. Ten artykuł zawiera informacje o gromadzonych przez nas danych. Zawiera również wskazówki dotyczące sposobu, w jaki użytkownicy budujący własną wersję sdk .NET Core mogą uniknąć niezamierzonego ujawnienia informacji osobistych lub poufnych.

### <a name="types-of-collected-data"></a>Rodzaje gromadzonych danych

.NET Core CLI zbiera informacje tylko dla wyjątków interfejsu WIERSZA/SDK, a nie wyjątków w aplikacji. Zebrane dane zawiera nazwę wyjątku i śledzenia stosu. Ten ślad stosu jest z kodu CLI/SDK.

Poniższy przykład przedstawia rodzaj danych, które są zbierane:

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

### <a name="avoid-inadvertent-disclosure-of-information"></a>Unikanie nieumyślnego ujawniania informacji

Współautorzy programu .NET Core i inni, którzy uruchomili wersję sdk .NET Core, którą sami stworzyli, powinni rozważyć ścieżkę do ich kodu źródłowego SDK. Jeśli wystąpi awaria podczas korzystania z .NET Core SDK, który jest kompilacją debugowania niestandardowego lub skonfigurowany z niestandardowymi plikami symboli kompilacji, ścieżka pliku źródłowego SDK z komputera kompilacji jest zbierana jako część śledzenia stosu i nie jest mieszana.

Z tego powodu niestandardowe kompilacje sdk .NET Core nie powinny znajdować się w katalogach, których nazwy ścieżek ujawniają informacje osobiste lub poufne.

## <a name="see-also"></a>Zobacz też

- [.NET Core CLI Telemetry - Dane q2 2019](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [Źródło referencyjne telemetrii (repozytorium dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
