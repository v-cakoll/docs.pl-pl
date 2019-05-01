---
title: Dane telemetryczne zestawu SDK programu .NET core
description: Poznaj funkcje telemetryczne zestawu .NET Core SDK, które zbierają informacje o użyciu dla analizy, które dane są zbierane i jak go wyłączyć.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 2ef6ade36092ff5a17b0cc420dc4859409d459ce
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63773839"
---
# <a name="net-core-sdk-telemetry"></a>Dane telemetryczne zestawu SDK programu .NET core

[Zestawu .NET Core SDK](index.md) obejmuje [funkcji telemetrii](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) które zbiera informacje o użyciu. Należy pamiętać, że zespół .NET wiedział, jak te narzędzia są używane, dzięki czemu można poprawić. Aby uzyskać więcej informacji, zobacz [poznane z platformy .NET Core SDK Telemetrii](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).

Zebrane dane są anonimowe i opublikowane w zagregowanej formie do użycia przez firmę Microsoft i społeczności w ramach [licencji Creative Commons: uznanie autorstwa License](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Zakres

`dotnet` Polecenie służy do uruchamiania aplikacji i interfejsu wiersza polecenia platformy .NET Core. `dotnet` Samo polecenie nie zbiera dane telemetryczne. Polecenia interfejsu wiersza polecenia platformy .NET Core są uruchamiane przez `dotnet` polecenia zbieranie danych telemetrycznych.

Dane telemetryczne *nie włączono* przy użyciu `dotnet` polecenia, za pomocą polecenia, nie dołączonych:

- `dotnet`
- `dotnet [path-to-app]`

Dane telemetryczne *włączono* przy użyciu [poleceń interfejsu wiersza polecenia platformy .NET Core](index.md), takich jak:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak zrezygnować

Funkcja danych telemetrycznych zestawu SDK programu .NET Core jest włączona domyślnie. Zrezygnować z funkcji danych telemetrycznych przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej, aby `1` lub `true`.

## <a name="data-points"></a>Punkty danych

Ta funkcja zbiera następujące dane:

- Sygnatura czasowa wywołania&#8224;
- Polecenie wywoływane (na przykład "build")&#8224;
- Trzy octet adres IP używany do określenia lokalizacji geograficznej&#8224;
- `ExitCode` polecenia
- Narzędzie Test runner (dla projektów testowych)
- Wersja systemu operacyjnego i&#8224;
- Czy identyfikatory środowiska uruchomieniowego znajdują się w węźle środowiska uruchomieniowe
- Wersja zestawu .NET core SDK&#8224;

&#8224;Ta metryka jest publikowany.

Począwszy od programu .NET Core 2.0 SDK nowe punkty danych są zbierane:

- `dotnet` polecenie Opcje i argumenty: tylko znane opcje i argumenty są zbierane (nie dowolne ciągi).
- Czy zestaw SDK jest uruchomiona w kontenerze.
- Platformy docelowe.
- Mieszana adres MAC: kryptograficznie (SHA256) anonimowe i unikatowy identyfikator dla maszyny. Ta metryka nie jest opublikowana.
- Skrótu bieżącego katalogu roboczego.

Ta funkcja nie zbiera danych osobowych, takich jak nazwy użytkowników lub adresy e-mail. Go nie skanowanie Twojego kodu, a nie wyodrębnić poufnych danych na poziomie projektu, takie jak nazwa repozytorium i autora. Dane są przesyłane w bezpieczny sposób do serwerów firmy Microsoft przy użyciu [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywane w obszarze ograniczony dostęp i opublikowane w ramach rygorystyczne kontrole zabezpieczeń z bezpiecznym [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.

Zespół .NET chce wiedzieć, jak te narzędzia są używane, a jeśli działają poprawnie, nie co w przypadku tworzenia za pomocą narzędzi. Jeśli podejrzewasz, że zbiera dane telemetryczne poufne dane, lub że dane są insecurely lub niewłaściwie obsługiwane, Prześlij zgłoszenie do [interfejsu wiersza poleceniadotnet/](https://github.com/dotnet/cli/issues) repozytorium na potrzeby badania.

## <a name="published-data"></a>Opublikowane dane

Dane publikowane jest dostępny co kwartał i znajduje się w [danych użycia programu .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md). Dostępne są następujące kolumny w pliku danych:

- Znacznik czasu
- Occurrences&#8224;
- Polecenie
- Geography&#8225;
- Rodzina systemów operacyjnych
- RuntimeID
- OSVersion
- SDKVersion

&#8224;*Wystąpień* kolumnie jest wyświetlana łączna liczba użycia tego polecenia dla tego wiersza metryk tego samego dnia.

&#8225;Zazwyczaj *Geografia* kolumnie jest wyświetlana nazwa kraju. W niektórych przypadkach kontynent z Antarktyda pojawia się w tej kolumnie, albo z powodu pracowników naukowo-badawczych przy użyciu platformy .NET Core w Antarktyda lub nieprawidłowej lokalizacji danych.

### <a name="example"></a>Przykład

| Znacznik czasu      | Wystąpienia | Polecenie | Lokalizacja geograficzna | Rodzina systemów operacyjnych | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | Uruchom     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Zestawy danych

- [2016 - K3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [2016 - KWARTAŁ 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [2017 - 1.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [2017 - Q2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [2017 - K3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [2017 - KWARTAŁ 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

Dodatkowe zestawy danych są ogłaszane przy użyciu standardowego formatu adresu URL. Zastąp `<YEAR>` rokiem i Zastąp `<QUARTER>` z kwartał roku (Użyj `1`, `2`, `3`, lub `4`). Pliki znajdują się w wartości rozdzielane znakami tabulacji (*TSV*) format.

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licencja

Dystrybucja programu Microsoft .NET Core jest licencjonowany za pomocą [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Mirosoft .NET Library](https://aka.ms/dotnet-core-eula). Aby uzyskać szczegółowe informacje dotyczące zbierania i przetwarzania danych zobacz sekcję zatytułowaną "Dane".

[Pakiety .NET NuGet](https://www.nuget.org/profiles/dotnetframework) użyć tego samego licencji, ale nie włączysz danych telemetrycznych (zobacz [zakres](#scope)).

## <a name="disclosure"></a>Ujawnienie

.NET Core SDK zawiera następujący tekst, przy pierwszym uruchomieniu jednego z [poleceń interfejsu wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet restore`). Tekst może się nieco różnić w zależności od wersji zestawu SDK jest uruchomiona. To środowisko "najpierw uruchom" to, jak firma Microsoft przekaże Ci o zbieraniu danych.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a>Zobacz także

- [Czego się nauczyliśmy z platformy .NET Core SDK Telemetrii](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/)
- [Źródło odwołania danych telemetrycznych (repozytorium dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [Dane użycia zestawu SDK programu .NET core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
