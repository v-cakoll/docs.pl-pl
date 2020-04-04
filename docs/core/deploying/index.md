---
title: Publikowanie aplikacji
description: Dowiedz się więcej o sposobach publikowania aplikacji .NET Core. Program .NET Core może publikować aplikacje specyficzne dla platformy lub aplikacje między platformami. Aplikację można opublikować jako niezależną lub zależną od środowiska wykonawczego. Każdy tryb wpływa na sposób, w jaki użytkownik uruchamia aplikację.
ms.date: 04/01/2020
ms.openlocfilehash: a4e5f9fe048d40c751f582bd49732cb903202db4
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665537"
---
# <a name="net-core-application-publishing-overview"></a>Omówienie publikowania aplikacji .NET Core

Aplikacje utworzone za pomocą platformy .NET Core można publikować w dwóch różnych trybach, a tryb ma wpływ na sposób, w jaki użytkownik uruchamia aplikację.

Publikowanie aplikacji jako *samodzielnej* tworzy aplikację, która zawiera środowisko uruchomieniowe .NET Core i biblioteki oraz aplikację i jej zależności. Użytkownicy aplikacji można uruchomić go na komputerze, który nie ma zainstalowanego środowiska uruchomieniowego .NET Core.

Publikowanie aplikacji jako *zależne od środowiska uruchomieniowego* (wcześniej znane jako *zależne od struktury)* tworzy aplikację, która zawiera tylko samą aplikację i jej zależności. Użytkownicy aplikacji muszą oddzielnie zainstalować środowisko uruchomieniowe .NET Core.

Oba tryby publikowania domyślnie generują plik wykonywalny specyficzny dla platformy. Aplikacje zależne od środowiska wykonawczego można tworzyć bez pliku wykonywalnego, a te aplikacje są wieloplatformowe.

Po wykonaniu pliku wykonywalnego można określić platformę docelową za pomocą identyfikatora środowiska uruchomieniowego (RID). Aby uzyskać więcej informacji na temat identyfikatorów RID, zobacz [.NET Core RID Catalog](../rid-catalog.md).

W poniższej tabeli przedstawiono polecenia używane do publikowania aplikacji jako zależne od środowiska wykonawczego lub samodzielne, dla wersji SDK:

| Typ                                                                                 | Zestaw SDK 2.1 | SDK 3.x | Polecenie |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla bieżącej platformy. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla określonej platformy.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [zależny od środowiska uruchomię wieloplatformowy plik binarny](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [samodzielny plik wykonywalny](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Aby uzyskać więcej informacji, zobacz [polecenie .NET Core dotnet publish](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Tworzenie pliku wykonywalnego

Pliki wykonywalne nie są międzyplatformowe. Są one specyficzne dla systemu operacyjnego i architektury procesora. Podczas publikowania aplikacji i tworzenia pliku wykonywalnego można opublikować aplikację jako [niezależną](#publish-self-contained) lub [zależną od środowiska wykonawczego](#publish-runtime-dependent). Publikowanie aplikacji jako samodzielnej obejmuje środowisko uruchomieniowe .NET Core z aplikacją, a użytkownicy aplikacji nie muszą się martwić o zainstalowanie programu .NET Core przed uruchomieniem aplikacji. Aplikacje opublikowane jako zależne od środowiska wykonawczego nie obejmują środowiska uruchomieniowego i bibliotek .NET Core; uwzględniane są tylko zależności aplikacji i innych firm.

Następujące polecenia generują plik wykonywalny:

| Typ                                                                                 | Zestaw SDK 2.1 | SDK 3.x | Polecenie |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla bieżącej platformy. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla określonej platformy.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [samodzielny plik wykonywalny](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Tworzenie wieloplatformowego pliku binarnego

Pliki binarne między platformami są tworzone podczas publikowania aplikacji jako [zależnej od środowiska wykonawczego](#publish-runtime-dependent)w postaci pliku *DLL.* Nazwa pliku *dll* pochodzi od projektu. Na przykład, jeśli masz aplikację o nazwie **word_reader,** tworzony jest plik o nazwie *word_reader.dll.* Aplikacje opublikowane w ten sposób `dotnet <filename.dll>` są uruchamiane za pomocą polecenia i mogą być uruchamiane na dowolnej platformie.

Pliki binarne między platformami można uruchomić w dowolnym systemie operacyjnym, o ile docelowe środowisko uruchomieniowe .NET Core jest już zainstalowane. Jeśli docelowe środowisko uruchomieniowe .NET Core nie jest zainstalowane, aplikacja może działać przy użyciu nowszego środowiska wykonawczego, jeśli aplikacja jest skonfigurowana do przekazywania do przodu. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego są przewijane do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

Następujące polecenie tworzy binarny między platformami:

| Typ                                                                                 | Zestaw SDK 2.1 | SDK 3.x | Polecenie |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [zależny od środowiska uruchomię wieloplatformowy plik binarny](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publikowanie zależne od środowiska uruchomieniowego

Aplikacje opublikowane jako zależne od środowiska wykonawczego są wieloplatformowe i nie zawierają środowiska uruchomieniowego .NET Core. Użytkownik aplikacji jest wymagany do zainstalowania środowiska uruchomieniowego .NET Core.

Publikowanie aplikacji jako zależnej od środowiska wykonawczego tworzy [plik binarny między platformami](#produce-a-cross-platform-binary) jako plik *DLL* i [plik wykonywalny specyficzny dla platformy,](#produce-an-executable) który jest przeznaczony dla bieżącej platformy. Biblioteka *DLL* jest wieloplatformowa, podczas gdy plik wykonywalny nie jest. Na przykład, jeśli publikujesz aplikację o nazwie **word_reader** i docelową windows, plik wykonywalny *word_reader.exe* jest tworzony wraz z *word_reader.dll*. Podczas kierowania na Linuksa lub macOS tworzony jest plik wykonywalny *word_reader* wraz z *word_reader.dll*. Aby uzyskać więcej informacji na temat identyfikatorów RID, zobacz [.NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> .NET Core SDK 2.1 nie generuje plików wykonywalnych specyficznych dla platformy podczas publikowania aplikacji zależnej od środowiska uruchomieniowego.

Wieloplatformowy plik binarny aplikacji `dotnet <filename.dll>` można uruchomić za pomocą polecenia i można go uruchomić na dowolnej platformie. Jeśli aplikacja używa pakietu NuGet, który ma implementacje specyficzne dla platformy, wszystkie zależności platformy są kopiowane do folderu publikowania wraz z aplikacją.

Można utworzyć plik wykonywalny `-r <RID> --self-contained false` dla określonej platformy, przekazując parametry do [`dotnet publish`](../tools/dotnet-publish.md) polecenia. Po `-r` pominięciu parametru dla bieżącej platformy jest tworzony plik wykonywalny. Wszystkie pakiety NuGet, które mają zależności specyficzne dla platformy docelowej są kopiowane do folderu publikowania.

### <a name="advantages"></a>Zalety

- **Małe wdrożenie**\
Tylko aplikacja i jej zależności są dystrybuowane. Środowisko uruchomieniowe core platformy .NET i biblioteki są instalowane przez użytkownika i wszystkie aplikacje współużytkują środowisko wykonawcze.

- **Międzyplatformowe**\
Twoja aplikacja i dowolna . Biblioteka oparta na sieci działa w innych systemach operacyjnych. Nie musisz definiować platformy docelowej dla aplikacji. Aby uzyskać informacje o formacie pliku .NET, zobacz [Format pliku złożenia .NET](../../standard/assembly/file-format.md).

- **Używa najnowszego poprawionego środowiska uruchomieniowego**\
Aplikacja korzysta z najnowszego środowiska wykonawczego (w ramach docelowej rodziny głównych-podrzędnych .NET Core) zainstalowanych w systemie docelowym. Oznacza to, że aplikacja automatycznie używa najnowszej poprawionej wersji środowiska uruchomieniowego .NET Core. To domyślne zachowanie można zastąpić. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego są przewijane do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Wady

- **Wymaga wstępnej instalacji środowiska wykonawczego**\
Aplikacja może działać tylko wtedy, gdy wersja .NET Core obiektów docelowych aplikacji jest już zainstalowana w systemie hosta. Zachowanie przesyłania dalej aplikacji można skonfigurować w taki sposób, aby wymagało określonej wersji programu .NET Core, albo zezwolić na nowszą wersję programu .NET Core. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego są przewijane do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET Core może ulec zmianie**\
Środowisko uruchomieniowe .NET Core i biblioteki mają być aktualizowane na komputerze, na którym jest uruchamiana aplikacja. W rzadkich przypadkach może to zmienić zachowanie aplikacji, jeśli używasz bibliotek .NET Core, które wykonują większość aplikacji. Można skonfigurować sposób korzystania z nowszych wersji programu .NET Core. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego są przewijane do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

Następująca wada dotyczy tylko sdk .NET Core 2.1.

- **Użyj `dotnet` polecenia, aby uruchomić aplikację**\
Aby uruchomić `dotnet <filename.dll>` aplikację, użytkownicy muszą uruchomić polecenie. .NET Core 2.1 SDK nie tworzy plików wykonywalnych specyficznych dla platformy dla aplikacji opublikowanych w czasie wykonywania zależne.

### <a name="examples"></a>Przykłady

Publikowanie aplikacji zależne od środowiska uruchomieniowego między platformami. Plik wykonywalny przeznaczony dla bieżącej platformy jest tworzony wraz z plikiem *DLL.*

```dotnet
dotnet publish
```

Publikowanie aplikacji zależne od środowiska uruchomieniowego między platformami. Linux 64-bitowy plik wykonywalny jest tworzony wraz z plikiem *DLL.* To polecenie nie działa z .NET Core SDK 2.1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publikowanie samodzielnych

Publikowanie aplikacji jako samodzielnej tworzy plik wykonywalny specyficzny dla platformy. Folder publikowania danych zawiera wszystkie składniki aplikacji, w tym biblioteki .NET Core i docelowy czas wykonywania. Aplikacja jest odizolowana od innych aplikacji .NET Core i nie używa lokalnie zainstalowanego udostępnionego środowiska uruchomieniowego. Użytkownik aplikacji nie jest wymagany do pobierania i instalowania programu .NET Core.

Plik binarny pliku wykonywalnego jest produkowany dla określonej platformy docelowej. Jeśli na przykład masz aplikację o nazwie **word_reader**i publikujesz samodzielny plik wykonywalny dla systemu Windows, tworzony jest plik *word_reader.exe.* Publikując dla systemu Linux lub macOS, tworzony jest plik *word_reader.* Platforma docelowa i architektura `-r <RID>` jest [`dotnet publish`](../tools/dotnet-publish.md) określona z parametrem dla polecenia. Aby uzyskać więcej informacji na temat identyfikatorów RID, zobacz [.NET Core RID Catalog](../rid-catalog.md).

Jeśli aplikacja ma zależności specyficzne dla platformy, takie jak pakiet NuGet zawierający zależności specyficzne dla platformy, są one kopiowane do folderu publikowania wraz z aplikacją.

### <a name="advantages"></a>Zalety

- **Sterowanie wersją .NET Core**\
Można kontrolować, która wersja programu .NET Core jest wdrażana z aplikacją.

- **Kierowanie specyficzne dla platformy**\
Ponieważ musisz opublikować aplikację dla każdej platformy, wiesz, gdzie aplikacja będzie działać. Jeśli program .NET Core wprowadzi nową platformę, użytkownicy nie będą mogli uruchomić aplikacji na tej platformie, dopóki nie wydasz wersji przeznaczonej na tę platformę. Możesz przetestować aplikację pod kątem problemów ze zgodnością, zanim użytkownicy uruchomią aplikację na nowej platformie.

### <a name="disadvantages"></a>Wady

- **Większe wdrożenia**\
Ponieważ aplikacja zawiera środowisko uruchomieniowe .NET Core i wszystkie zależności aplikacji, wymagany rozmiar pobierania i miejsce na dysku twardym jest większa niż wersja [zależna od środowiska uruchomieniowego.](#publish-runtime-dependent)

  > [!TIP]
  > Rozmiar wdrożenia w systemach Linux można zmniejszyć o około 28 MB przy użyciu [*trybu niezmiennego globalizacji*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).NET Core. Zmusza to aplikację do traktowania wszystkich kultur, takich jak [kultura niezmienna.](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)

- **Trudniej zaktualizować wersję .NET Core**\
.NET Core Runtime (rozproszone z aplikacją) można uaktualnić tylko przez zwolnienie nowej wersji aplikacji. Użytkownik jest odpowiedzialny za dostarczanie zaktualizowanej wersji aplikacji dla poprawek zabezpieczeń do środowiska uruchomieniowego .NET Core.

### <a name="examples"></a>Przykłady

Publikowanie aplikacji niezależnej. Tworzony jest 64-bitowy plik wykonywalny systemu macOS.

```dotnet
dotnet publish -r osx-x64
```

Publikowanie aplikacji niezależnej. Tworzony jest 64-bitowy plik wykonywalny systemu Windows.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Zobacz też

- [Wdrażanie aplikacji .NET Core z rdzeniem .NET Core CLI.](deploy-with-cli.md)
- [Wdrażanie aplikacji .NET Core w programie Visual Studio.](deploy-with-vs.md)
- [Pakiety, metapakiety i struktury.](../packages.md)
- [.NET Core Runtime IDentifier (RID) — katalog.](../rid-catalog.md)
- [Wybierz wersję .NET Core, której chcesz użyć.](../versions/selection.md)
