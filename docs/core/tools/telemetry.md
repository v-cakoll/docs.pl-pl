---
title: Dane telemetryczne zestaw .NET Core SDK
description: Odkryj zestaw .NET Core SDK funkcje telemetrii, które zbierają informacje o użyciu analizy, zbierane dane i jak je wyłączyć.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 0917dae23588ccd1809252aaf484c397e84561c7
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226572"
---
# <a name="net-core-sdk-telemetry"></a>Dane telemetryczne zestaw .NET Core SDK

[Zestaw .NET Core SDK](index.md) zawiera funkcję telemetrii, która zbiera dane dotyczące użycia i informacje o wyjątkach, gdy interfejs wiersza polecenia platformy .NET Core awarie. Interfejs wiersza polecenia platformy .NET Core zawiera zestaw .NET Core SDK i jest zestawem zleceń, które umożliwiają kompilowanie, testowanie i publikowanie aplikacji platformy .NET Core. Ważne jest, aby zespół .NET wiedział, w jaki sposób narzędzia są używane, aby można je było ulepszyć. Informacje o błędach ułatwiają zespołowi Rozwiązywanie problemów i rozwiązywanie usterek.

Zebrane dane są anonimowe i publikowane jako zagregowane w ramach [licencji Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Zakres

`dotnet`Program ma dwie funkcje: do uruchamiania aplikacji i wykonywania poleceń interfejsu wiersza polecenia. Dane telemetryczne *nie są zbierane* podczas korzystania `dotnet` z programu w celu uruchomienia aplikacji w następującym formacie:

- `dotnet [path-to-app].dll`

Dane telemetryczne *są zbierane* przy użyciu dowolnego [polecenia interfejs wiersza polecenia platformy .NET Core](index.md), takich jak:

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak zrezygnować

Funkcja telemetrii zestaw .NET Core SDK jest domyślnie włączona. Aby zrezygnować z funkcji telemetrii, należy ustawić `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową na `1` lub `true` .

W przypadku pomyślnej instalacji wysyłany jest również pojedynczy wpis telemetrii przez Instalatora zestaw .NET Core SDK. Aby zrezygnować z programu, należy ustawić `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową przed zainstalowaniem zestaw .NET Core SDK.

## <a name="disclosure"></a>Mogąc

Zestaw .NET Core SDK wyświetla tekst podobny do poniższego po pierwszym uruchomieniu jednego z [poleceń interfejs wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet build` ). Tekst może się nieco różnić w zależności od używanej wersji zestawu SDK. To "pierwsze uruchomienie" polega na tym, jak firma Microsoft powiadamia użytkownika o zbieraniu danych.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

Aby wyłączyć ten komunikat i komunikat powitalny platformy .NET Core, ustaw dla `DOTNET_NOLOGO` zmiennej środowiskowej wartość `true` . Należy zauważyć, że ta zmienna nie ma wpływu na rezygnację z telemetrii.

## <a name="data-points"></a>Punkty danych

Funkcja telemetrii nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail. Nie skanuje kodu i nie wyodrębnia danych na poziomie projektu, takich jak Name, Repository lub Author. Dane są bezpiecznie przesyłane do serwerów firmy Microsoft przy użyciu technologii [Azure monitor](https://azure.microsoft.com/services/monitor/) , w ramach ograniczonego dostępu, i publikowane w ramach ścisłych kontroli zabezpieczeń z bezpiecznych systemów [usługi Azure Storage](https://azure.microsoft.com/services/storage/) .

Ochrona prywatności jest dla nas ważna. Jeśli podejrzewasz, że Telemetria zbiera dane poufne lub dane są w sposób niezabezpieczony lub niewłaściwie obsłużone, należy rozwiązać problem w repozytorium [dotnet/SDK](https://github.com/dotnet/sdk/issues) lub wysłać wiadomość e-mail do [dotnet@microsoft.com](mailto:dotnet@microsoft.com) badania.

Funkcja telemetrii zbiera następujące dane:

| Wersje zestawu SDK | Dane |
|--------------|------|
| Wszystko          | Sygnatura czasowa wywołania. |
| Wszystko          | Wywołano polecenie (na przykład "Kompilacja"), wartość skrótu rozpoczynająca się w 2,1. |
| Wszystko          | Trzy adresy IP używane do określenia lokalizacji geograficznej. |
| Wszystko          | System operacyjny i wersja. |
| Wszystko          | Identyfikator środowiska uruchomieniowego (RID), na którym jest uruchomiony zestaw SDK. |
| Wszystko          | Wersja zestaw .NET Core SDK. |
| Wszystko          | Profil telemetrii: opcjonalna wartość używana tylko z jawnym zapytaniem użytkownika i używana wewnętrznie w firmie Microsoft. |
| >= 2,0        | Argumenty polecenia i opcje: zbierane są kilka argumentów i opcji (nie dowolnych ciągów). Zobacz [zebrane opcje](#collected-options). Skrót po 2.1.300. |
| >= 2,0         | Czy zestaw SDK działa w kontenerze. |
| >= 2,0         | Platformy docelowe (ze `TargetFramework` zdarzenia), które zostały zmieszane, począwszy od 2,1. |
| >= 2,0         | Adres MAC w postaci skrótu Access Control: kryptograficzny (SHA256) anonimowy i unikatowy identyfikator dla komputera. |
| >= 2,0         | Skrót bieżącego katalogu roboczego. |
| >= 2,0         | Zainstaluj Raport z sukcesem z nazwą pliku exe Instalatora. |
| >= 2.1.300     | Wersja jądra. |
| >= 2.1.300     | Libc wydanie/wersja. |
| >= 3.0.100     | Czy dane wyjściowe zostały przekierowane (wartość true lub false). |
| >= 3.0.100     | W przypadku awarii interfejsu wiersza polecenia/zestawu SDK typ wyjątku i jego ślad stosu (kod interfejsu wiersza polecenia/zestawu SDK jest dołączony do wysyłanego śladu stosu). Aby uzyskać więcej informacji, zobacz dane [telemetryczne wyjątku awarii interfejs wiersza polecenia platformy .NET Core/SDK](#net-core-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Zebrane opcje

Niektóre polecenia wysyłają dodatkowe dane. Podzbiór poleceń wysyła pierwszy argument:

| Polecenie               | Wysłane dane pierwszego argumentu                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | Trwa kwerenda pomocy dla polecenia.  |
| `dotnet new <arg>`    | Nazwa szablonu (wartość skrótu).             |
| `dotnet add <arg>`    | Słowo `package` lub `reference` .      |
| `dotnet remove <arg>` | Słowo `package` lub `reference` .      |
| `dotnet list <arg>`   | Słowo `package` lub `reference` .      |
| `dotnet sln <arg>`    | Słowo `add` , `list` , lub `remove` .    |
| `dotnet nuget <arg>`  | Słowo `delete` , `locals` , lub `push` . |

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

Z wyjątkiem `--verbosity` i `--sdk-package-version` , wszystkie inne wartości są zmieszane, począwszy od platformy .NET Core 2.1.100 SDK.

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>Zebrane dane telemetryczne wyjątku awarii interfejs wiersza polecenia platformy .NET Core/SDK

Jeśli wystąpi awaria interfejs wiersza polecenia platformy .NET Core/SDK, zbierane są informacje o nazwie i śladie stosu dla kodu CLI/SDK. Te informacje są zbierane w celu oceny problemów i poprawy jakości zestaw .NET Core SDK i interfejsu wiersza polecenia. Ten artykuł zawiera informacje o zbieranych danych. Zawiera również wskazówki dotyczące sposobu, w jaki użytkownicy tworzą własne wersje zestaw .NET Core SDK mogą uniknąć przypadkowego ujawnienia informacji osobistych lub poufnych.

### <a name="types-of-collected-data"></a>Typy zebranych danych

Interfejs wiersza polecenia platformy .NET Core zbiera informacje tylko dla wyjątków CLI/SDK, a nie wyjątków w aplikacji. Zebrane dane zawierają nazwę wyjątku i ślad stosu. Ten ślad stosu jest kodem CLI/SDK.

Poniższy przykład przedstawia rodzaj zbieranych danych:

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

### <a name="avoid-inadvertent-disclosure-of-information"></a>Unikaj przypadkowego ujawnienia informacji

Współautorzy platformy .NET Core i inne osoby, na których jest uruchomiona wersja zestaw .NET Core SDK należy wziąć pod uwagę ścieżkę do kodu źródłowego zestawu SDK. Jeśli wystąpi awaria podczas korzystania z zestaw .NET Core SDK, który jest kompilacją niestandardową lub skonfigurowaną za pomocą niestandardowych plików symboli kompilacji, ścieżka pliku źródłowego zestawu SDK z maszyny kompilacji jest zbierana jako część śladu stosu i nie ma wartości skrótu.

Z tego powodu niestandardowe kompilacje zestaw .NET Core SDK nie powinny znajdować się w katalogach, których nazwy ścieżek ujawniają osobiste lub poufne informacje.

## <a name="see-also"></a>Zobacz także

- [Dane telemetryczne interfejs wiersza polecenia platformy .NET Core-2019 Q2](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [Źródło odwołania telemetrii (repozytorium dotnet/SDK)](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
