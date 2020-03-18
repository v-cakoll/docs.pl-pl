---
title: Publikowanie aplikacji
description: Dowiedz się więcej o sposobach publikowania aplikacji .NET Core. .NET Core może publikować aplikacje specyficzne dla platformy lub między platformami. Aplikację można opublikować jako niezależną lub zależną od czasu wykonywania. Każdy tryb wpływa na sposób, w jaki użytkownik uruchamia aplikację.
ms.date: 01/31/2020
ms.openlocfilehash: 3b9c3b7f29af12477874b7a31ef0de4750719de0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399064"
---
# <a name="net-core-application-publishing-overview"></a>Omówienie publikowania aplikacji .NET Core

Aplikacje tworzone za pomocą programu .NET Core mogą być publikowane w dwóch różnych trybach, a tryb wpływa na sposób, w jaki użytkownik uruchamia aplikację.

Publikowanie aplikacji jako *niezależna* tworzy aplikację, która zawiera program .NET Core i biblioteki oraz aplikacji i jej zależności. Użytkownicy aplikacji można uruchomić go na komputerze, który nie ma zainstalowanego programu uruchomieniowego .NET Core.

Publikowanie aplikacji jako *zależne od czasu wykonywania* tworzy aplikację, która zawiera tylko samą aplikację i jej zależności. Użytkownicy aplikacji muszą oddzielnie zainstalować program .NET Core.

Oba tryby publikowania domyślnie tworzą plik wykonywalny specyficzny dla platformy. Aplikacje zależne od czasu wykonywania można tworzyć bez pliku wykonywalnego, a te aplikacje są wieloplatformowe.

Po wyprodukowaniu pliku wykonywalnego można określić platformę docelową z identyfikatorem czasu wykonywania (RID). Aby uzyskać więcej informacji o identyfikatorach RID, zobacz [.NET Core RID Catalog](../rid-catalog.md).

W poniższej tabeli przedstawiono polecenia używane do publikowania aplikacji jako zależne jednych lub samodzielnych dla wersji sdk:

| Typ                                                                                 | Zestaw SDK 2.1 | Zestaw SDK 3.x | Polecenie |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [plik wykonywalny zależny od czasu wykonywania](#publish-runtime-dependent) dla bieżącej platformy. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [plik wykonywalny zależny od czasu wykonywania](#publish-runtime-dependent) dla określonej platformy.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [zależny chorążcej wieloplatformowej binarny](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [samodzielny plik wykonywalny](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Aby uzyskać więcej informacji, zobacz [polecenie publikowania dotnet.NET Core .](../tools/dotnet-publish.md)

## <a name="produce-an-executable"></a>Tworzenie pliku wykonywalnego

Pliki wykonywalne nie są wieloplatformowe. Są one specyficzne dla systemu operacyjnego i architektury procesora. Podczas publikowania aplikacji i tworzenia pliku wykonywalnego można opublikować aplikację jako [niezależną](#publish-self-contained) lub [zależną od czasu wykonywania.](#publish-runtime-dependent) Publikowanie aplikacji jako niezależnej zawiera program .NET Core w czasie wykonywania z aplikacją, a użytkownicy aplikacji nie muszą się martwić o zainstalowanie .NET Core przed uruchomieniem aplikacji. Aplikacje opublikowane jako zależne od czasu wykonywania nie zawierają czasu uruchomieniowego i bibliotek programu .NET Core; uwzględniane są tylko zależności aplikacji i innych firm.

Następujące polecenia generują plik wykonywalny:

| Typ                                                                                 | Zestaw SDK 2.1 | Zestaw SDK 3.x | Polecenie |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [plik wykonywalny zależny od czasu wykonywania](#publish-runtime-dependent) dla bieżącej platformy. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [plik wykonywalny zależny od czasu wykonywania](#publish-runtime-dependent) dla określonej platformy.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [samodzielny plik wykonywalny](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Tworzenie wieloplatformowego pliku binarnego

Pliki binarne między platformami są tworzone podczas publikowania aplikacji jako [zależne od czasu wykonywania](#publish-runtime-dependent), w postaci pliku *dll.* Nazwa pliku *dll* pochodzi od projektu. Na przykład, jeśli masz aplikację o nazwie **word_reader**, tworzony jest plik o nazwie *word_reader.dll.* Aplikacje opublikowane w ten sposób `dotnet <filename.dll>` są uruchamiane za pomocą polecenia i mogą być uruchamiane na dowolnej platformie.

Pliki binarne między platformami można uruchamiać w dowolnym systemie operacyjnym, o ile docelowy czas uruchomieniowy .NET Core jest już zainstalowany. Jeśli docelowy program .NET Core nie jest zainstalowany, aplikacja może działać przy użyciu nowszego czasu uruchomieniowego, jeśli aplikacja jest skonfigurowana do przewijania do przodu. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od czasu wykonywania przewijają się do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

Następujące polecenie tworzy plik binarny między platformami:

| Typ                                                                                 | Zestaw SDK 2.1 | Zestaw SDK 3.x | Polecenie |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [zależny chorążcej wieloplatformowej binarny](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publikowanie zależności od czasu wykonywania

Aplikacje opublikowane jako zależne od czasu wykonywania są wieloplatformowe i nie zawierają czasu uruchomieniowego .NET Core. Użytkownik aplikacji jest wymagany do zainstalowania środowiska uruchomieniowego .NET Core.

Publikowanie aplikacji jako zależne od czasu wykonawczego tworzy [plik binarny między platformami](#produce-a-cross-platform-binary) jako plik *dll* i [plik wykonywalny specyficzny dla platformy,](#produce-an-executable) który jest przeznaczony dla bieżącej platformy. *Dll* jest wieloplatformowy, podczas gdy plik wykonywalny nie jest. Na przykład, jeśli opublikujesz aplikację o nazwie **word_reader** i docelowy system Windows, zostanie utworzony plik wykonywalny *word_reader.exe* wraz z *plikiem word_reader.dll*. Podczas kierowania na Linuksa lub macOS tworzony jest plik wykonywalny *word_reader* wraz z *plikiem word_reader.dll*. Aby uzyskać więcej informacji o identyfikatorach RID, zobacz [.NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> .NET Core SDK 2.1 nie tworzy plików wykonywalnych specyficznych dla platformy podczas publikowania aplikacji zależne od czasu wykonywania.

Wieloplatformowy plik binarny aplikacji można `dotnet <filename.dll>` uruchomić za pomocą polecenia i można go uruchomić na dowolnej platformie. Jeśli aplikacja używa pakietu NuGet, który ma implementacje specyficzne dla platformy, zależności wszystkich platform są kopiowane do folderu publikowania wraz z aplikacją.

Można utworzyć plik wykonywalny dla `-r <RID> --self-contained false` określonej platformy, przekazując parametry do [`dotnet publish`](../tools/dotnet-publish.md) polecenia. Gdy `-r` parametr zostanie pominięty, plik wykonywalny jest tworzony dla bieżącej platformy. Wszystkie pakiety NuGet, które mają zależności specyficzne dla platformy dla platformy docelowej są kopiowane do folderu publikowania.

### <a name="advantages"></a>Zalety

- **Małe wdrożenie**\
Dystrybucja jest rozpowszechniana tylko aplikacji i jej zależności. Środowisko uruchomieniowe i biblioteki .NET Core są instalowane przez użytkownika, a wszystkie aplikacje współużytkują środowisko uruchomieniowe.

- **Wieloplatformowy**\
Twoja aplikacja i dowolne . Biblioteka oparta na sieci jest uruchamiana w innych systemach operacyjnych. Nie musisz definiować platformy docelowej dla aplikacji. Aby uzyskać informacje dotyczące formatu pliku .NET, zobacz [Format pliku .NET Assembly](../../standard/assembly/file-format.md).

- **Używa najnowszego poprawionego czasu wykonywania**\
Aplikacja korzysta z najnowszego czasu uruchomieniowego (w ramach docelowej rodziny głównych mniejszych .NET Core) zainstalowanew systemie docelowym. Oznacza to, że aplikacja automatycznie używa najnowszej poprawionej wersji programu runtime .NET Core. To zachowanie domyślne można zastąpić. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od czasu wykonywania przewijają się do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Wady

- **Wymaga wstępnej instalacji programu runtime**\
Aplikacja może działać tylko wtedy, gdy wersja .NET Core, w ramach który aplikacja jest już zainstalowana w systemie hosta. Można skonfigurować zachowanie roll-forward dla aplikacji, aby wymagać określonej wersji programu .NET Core lub zezwolić na nowszą wersję programu .NET Core. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od czasu wykonywania przewijają się do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET Core może ulec zmianie**\
Jest możliwe dla .NET Core runtime i bibliotek, które mają być aktualizowane na komputerze, na którym aplikacja jest uruchamiana. W rzadkich przypadkach może to zmienić zachowanie aplikacji, jeśli używasz bibliotek .NET Core, co większość aplikacji zrobić. Można skonfigurować sposób, w jaki aplikacja korzysta z nowszych wersji programu .NET Core. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od czasu wykonywania przewijają się do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

Poniższa wada dotyczy tylko .NET Core 2.1 SDK.

- **Użyj `dotnet` polecenia, aby uruchomić aplikację**\
Użytkownicy muszą `dotnet <filename.dll>` uruchomić polecenie, aby uruchomić aplikację. Zestaw SDK .NET Core 2.1 nie tworzy plików wykonywalnych specyficznych dla platformy dla aplikacji opublikowanych w zależności od czasu wykonywania.

### <a name="examples"></a>Przykłady

Publikowanie aplikacji współzależnej dla wielu platform. Plik wykonywalny przeznaczony dla bieżącej platformy jest tworzony wraz z plikiem *dll.*

```dotnet
dotnet publish
```

Publikowanie aplikacji współzależnej dla wielu platform. Wraz z plikiem *dll* tworzony jest 64-bitowy plik wykonywalny dla systemu Linux. To polecenie nie działa z zestawem .NET Core SDK 2.1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publikowanie samodzielnych

Publikowanie aplikacji jako niezależne produkuje plik wykonywalny specyficzne dla platformy. Wyjściowy folder publikowania zawiera wszystkie składniki aplikacji, w tym biblioteki .NET Core i docelowy czas wykonywania. Aplikacja jest izolowana od innych aplikacji .NET Core i nie używa lokalnie zainstalowanego udostępnionego programu runtime. Użytkownik aplikacji nie jest wymagany do pobrania i zainstalowania programu .NET Core.

Plik wykonywalny plik binarny jest tworzony dla określonej platformy docelowej. Na przykład jeśli masz aplikację o nazwie **word_reader**i publikujesz samodzielny plik wykonywalny dla systemu Windows, tworzony jest plik *word_reader.exe.* Publikowanie dla systemu Linux lub macOS, *word_reader* plik jest tworzony. Platforma docelowa i architektura `-r <RID>` jest [`dotnet publish`](../tools/dotnet-publish.md) określona z parametrem polecenia. Aby uzyskać więcej informacji o identyfikatorach RID, zobacz [.NET Core RID Catalog](../rid-catalog.md).

Jeśli aplikacja ma zależności specyficzne dla platformy, takich jak pakiet NuGet zawierający zależności specyficzne dla platformy, są one kopiowane do folderu publikowania wraz z aplikacją.

### <a name="advantages"></a>Zalety

- **Sterowanie wersją programu .NET Core**\
Możesz kontrolować, która wersja programu .NET Core jest wdrażana w aplikacji.

- **Kierowanie specyficzne dla platformy**\
Ponieważ musisz opublikować aplikację dla każdej platformy, wiesz, gdzie aplikacja będzie działać. Jeśli program .NET Core wprowadzi nową platformę, użytkownicy nie będą mogli uruchomić aplikacji na tej platformie, dopóki nie wydasz wersji przeznaczonej dla tej platformy. Możesz przetestować aplikację pod kątem problemów ze zgodnością, zanim użytkownicy uruchomią aplikację na nowej platformie.

### <a name="disadvantages"></a>Wady

- **Większe wdrożenia**\
Ponieważ aplikacja zawiera program .NET Core i wszystkie zależności aplikacji, wymagany rozmiar pobierania i miejsce na dysku twardym jest większa niż wersja [zależna od czasu wykonywania.](#publish-runtime-dependent)

  > [!TIP]
  > Rozmiar wdrożenia w systemach Linux można zmniejszyć o około 28 MB przy użyciu [*trybu niezmiennego globalizacji*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).NET Core. Zmusza to aplikację do traktowania wszystkich kultur, takich jak [kultura niezmienna.](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)

- **Trudniejsze zaktualizowanie wersji programu .NET Core**\
Program .NET Core Runtime (dystrybuowany za pomocą aplikacji) można uaktualnić tylko przez wydanie nowej wersji aplikacji. Jesteś odpowiedzialny za dostarczanie zaktualizowanej wersji aplikacji dla poprawek zabezpieczeń do programu .NET Core Runtime.

### <a name="examples"></a>Przykłady

Publikowanie aplikacji w sposób samodzielny. Tworzony jest 64-bitowy plik wykonywalny systemu macOS.

```dotnet
dotnet publish -r osx-x64
```

Publikowanie aplikacji w sposób samodzielny. Tworzony jest 64-bitowy plik wykonywalny systemu Windows.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Zobacz też

- [Wdrażanie aplikacji .NET Core apps z usługą .NET Core CLI.](deploy-with-cli.md)
- [Wdrażanie aplikacji .NET Core apps w programie Visual Studio.](deploy-with-vs.md)
- [Pakiety, metapakiety i struktury.](../packages.md)
- [Wykaz identyfikatora środowiska uruchomienionowego .NET Core .NET.](../rid-catalog.md)
- [Wybierz wersję .NET Core, która ma być używana.](../versions/selection.md)
