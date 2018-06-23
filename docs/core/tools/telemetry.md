---
title: Dane telemetryczne zestawu SDK programu .NET core
description: Odkryj funkcje telemetrii .NET Core SDK, które zbierają informacje o użyciu do analizy, które dane są zbierane i jak go wyłączyć.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: f60a1eaa7b869676dfbb67529e7878ca9b9ca34a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314880"
---
# <a name="net-core-sdk-telemetry"></a>Dane telemetryczne zestawu SDK programu .NET core

[.NET Core SDK](index.md) obejmuje [funkcji telemetrii](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) która zbiera informacje o użyciu. Jest ważne, czy .NET Team rozumie używania narzędzi, można poprawić. Aby uzyskać więcej informacji, zobacz [co zostały dowiedzieliśmy się z .NET Core SDK Telemetrii](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).

Zebrane dane są anonimowe i opublikowane w zagregowanej formie do użycia przez firmę Microsoft i społecznością w obszarze [Creative Commons autorstwa licencji](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Zakres

`dotnet` Polecenia jest używane do uruchomienia aplikacjach i interfejsu wiersza polecenia platformy .NET Core. `dotnet` Samo polecenie nie zbierać dane telemetryczne. Uruchom polecenia interfejsu wiersza polecenia platformy .NET Core przez `dotnet` polecenia zbieranie danych telemetrycznych.

Dane telemetryczne *nie włączono* przy użyciu `dotnet` poleceń, za pomocą polecenia, nie dołączonych:

- `dotnet`
- `dotnet [path-to-app]`

Dane telemetryczne *włączono* przy użyciu [polecenia interfejsu wiersza polecenia platformy .NET Core](index.md), takich jak:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak wykluczyć

Funkcja telemetrii .NET Core SDK jest domyślnie włączona. Opcja rezygnacji z funkcją telemetrii przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmienną środowiskową `1` lub `true`.

## <a name="data-points"></a>Punkty danych

Funkcja zbiera następujące dane:

- Sygnatura czasowa wywołania&#8224;
- Polecenie wywoływane (na przykład "kompilacji")&#8224;
- Adres IP trzy octet umożliwia określenie lokalizacji geograficznych&#8224;
- `ExitCode` polecenie
- Test runner (do projekty testowe)
- Wersja systemu operacyjnego i&#8224;
- Określa, czy znajdują się w węźle środowisk uruchomieniowych identyfikatorów środowiska wykonawczego
- Wersja zestawu SDK programu .NET core&#8224;

&#8224;Ta metryka jest opublikowana.

Począwszy od programu .NET Core SDK 2.0, nowe punkty danych są zbierane:

- `dotnet` polecenie Opcje i argumenty: tylko znane opcje i argumenty są zbierane (nie dowolne ciągi).
- Określa, czy zestaw SDK jest uruchomiona w kontenerze.
- Docelowych platform.
- Wartość skrótu adresów MAC: kryptograficznie (SHA256) anonimowych, jak i unikatowy identyfikator dla maszyny. Ten pomiar nie jest opublikowana.
- Skrótu bieżącego katalogu roboczego.

Funkcja nie zbieraj danych osobowych, takich jak nazwy użytkowników lub adresy e-mail. Nie skanuje kodu, a nie wyodrębnić poufnych danych na poziomie projektu, takie jak nazwa, repozytorium lub autora. Danych są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu [usługi Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywany w ograniczonym dostępem i publikowane w obszarze opcji ograniczeniami zabezpieczeń z bezpiecznego [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.

Zespół .NET chce dowiedzieć się, jak są używane narzędzia i jeśli działają poprawnie, nie co tworzysz przy użyciu narzędzi. Jeśli podejrzewasz zbiera dane telemetryczne danych poufnych lub że dane są nimi lub niewłaściwie obsługi plików problemu w [dotnet/cli](https://github.com/dotnet/cli/issues) repozytorium, aby umożliwić zbadanie problemu.

## <a name="published-data"></a>Opublikowane dane

Dane publikowane jest dostępna co kwartał i znajduje się w [dane użycia zestawu SDK programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md). Kolumn w pliku danych są:

- Znacznik czasu
- Occurrences&#8224;
- Polecenie
- Geography&#8225;
- Rodzina systemów operacyjnych
- RuntimeID
- OSVersion
- Wersjazestawusdk

&#8224;*Wystąpień* kolumny Wyświetla łączna liczba Użyj tego polecenia dla tego wiersza metryki danego dnia.

&#8225;Zazwyczaj *geograficzne* kolumnie jest wyświetlana nazwa kraju. W niektórych przypadkach kontynencie z Antarktyka pojawia się w tej kolumnie, albo z powodu pracowników naukowo-badawczych przy użyciu platformy .NET Core Antarktyka lub nieprawidłowej lokalizacji dane.

### <a name="example"></a>Przykład

| Znacznik czasu      | Wystąpienia | Polecenie | Lokalizacja geograficzna | Rodzina systemów operacyjnych | RuntimeID     | OSVersion | Wersjazestawusdk |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | Uruchom     | Ugandy    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Zestawy danych

[2016 - K3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 - KWARTAŁ 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 - 1.](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 - K2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[2017 - K3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[2017 - KWARTAŁ 4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

Dodatkowe zestawy danych są publikowane, przy użyciu standardowego formatu adresu URL. Zastąp `<YEAR>` roku i Zastąp `<QUARTER>` z kwartału roku (Użyj `1`, `2`, `3`, lub `4`). Pliki znajdują się w wartości tabulatorami (*TSV*) format.

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licencji

Rozkład Microsoft .NET Core jest licencjonowana z [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula). Ta licencja zawiera sekcja "Dane" Aby włączyć telemetrii (pokazana poniżej).

[Pakietów NuGet programu .NET](https://www.nuget.org/profiles/dotnetframework) użyć tego samego licencji, ale nie włączysz telemetrii (zobacz [zakres](#scope)).

> 2. DATA. Oprogramowanie może zbierać informacje o Tobie i korzystanie z oprogramowania i wysyłać do firmy Microsoft. Firma Microsoft może używać tych informacji do poprawy naszych produktów i usług. Możesz dowiedzieć się więcej o zbieraniu danych i użyć w dokumentacji pomocy i poufności informacji w http://go.microsoft.com/fwlink/?LinkId=528096. Korzystanie z oprogramowania działa jako Twojej zgody na nich.

## <a name="disclosure"></a>Ujawnienie

.NET Core SDK zawiera następujący tekst przy pierwszym uruchomieniu jednego z [polecenia interfejsu wiersza polecenia platformy .NET Core](index.md) (na przykład `dotnet restore`). Tekst może się nieco różnić w zależności od wersji zestawu SDK jest uruchomiona. To środowisko "najpierw uruchom" jest jak Microsoft powiadomi użytkownika o zbierania danych.

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

[Co zostało dowiedzieliśmy się z .NET Core SDK Telemetrii](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[Dane telemetryczne źródła odniesienia (repozytorium dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)  
[Dane użycia zestawu SDK programu .NET core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)  
