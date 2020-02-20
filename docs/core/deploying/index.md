---
title: Publikowanie aplikacji
description: Dowiedz się więcej na temat sposobów publikowania aplikacji platformy .NET Core. Platforma .NET Core może publikować aplikacje zależne od platformy lub dla wielu platform. Aplikację można opublikować jako samodzielny lub jako zależny od środowiska uruchomieniowego. Każdy tryb ma wpływ na sposób uruchamiania aplikacji przez użytkownika.
ms.date: 01/31/2020
ms.openlocfilehash: 696cca436c73601a3e7825033152d43a659a7dce
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448987"
---
# <a name="net-core-application-publishing-overview"></a>Omówienie publikowania aplikacji .NET Core

Aplikacje tworzone za pomocą platformy .NET Core mogą być publikowane w dwóch różnych trybach, a tryb ma wpływ na sposób uruchamiania aplikacji przez użytkownika.

Opublikowanie aplikacji jako *samodzielny* powoduje utworzenie aplikacji obejmującej środowisko uruchomieniowe i biblioteki platformy .NET Core oraz aplikację i jej zależności. Użytkownicy aplikacji mogą uruchomić ją na komputerze, na którym nie zainstalowano środowiska uruchomieniowego .NET Core. 

Opublikowanie aplikacji jako *zależnej od środowiska uruchomieniowego* powoduje utworzenie aplikacji zawierającej tylko samą aplikację i jej zależności. Użytkownicy aplikacji muszą oddzielnie zainstalować środowisko uruchomieniowe programu .NET Core.

Oba tryby publikowania domyślnie generują plik wykonywalny specyficzny dla platformy. Aplikacje zależne od środowiska uruchomieniowego można tworzyć bez pliku wykonywalnego, a te aplikacje są Międzyplatformowe.

Gdy tworzony jest plik wykonywalny, można określić platformę docelową z identyfikatorem czasu wykonywania (RID). Aby uzyskać więcej informacji na temat identyfikatorów RID, zobacz [katalog .NET Core RID Catalog](../rid-catalog.md).

Poniższa tabela zawiera opis poleceń używanych do publikowania aplikacji jako zależnej od środowiska uruchomieniowego lub samodzielnego, na wersję zestawu SDK:

| Typ                                                                                 | ZESTAW SDK 2,1 | Zestaw SDK 3. x | Polecenie |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [plik wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla bieżącej platformy. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [plik wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla określonej platformy.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [plik binarny dla wielu platform zależnych od środowiska uruchomieniowego](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [samodzielny plik wykonywalny](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Aby uzyskać więcej informacji, zobacz [polecenie .NET Core dotnet Publish](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Generuj plik wykonywalny

Pliki wykonywalne nie są na wielu platformach. Są one specyficzne dla systemu operacyjnego i architektury procesora CPU. Podczas publikowania aplikacji i tworzenia pliku wykonywalnego można opublikować aplikację jako [samodzielną](#publish-self-contained) lub [zależną od środowiska uruchomieniowego](#publish-runtime-dependent). Publikowanie aplikacji jako samodzielnego obejmuje środowisko uruchomieniowe platformy .NET Core z aplikacją, a użytkownicy aplikacji nie muszą martwić się o Instalowanie programu .NET Core przed uruchomieniem aplikacji. Aplikacje publikowane jako zależne od środowiska uruchomieniowego nie obejmują środowiska uruchomieniowego i bibliotek platformy .NET Core; uwzględniane są tylko zależności aplikacji i innych firm.

Następujące polecenia tworzą plik wykonywalny:

| Typ                                                                                 | ZESTAW SDK 2,1 | Zestaw SDK 3. x | Polecenie |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [plik wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla bieżącej platformy. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [plik wykonywalny zależny od środowiska uruchomieniowego](#publish-runtime-dependent) dla określonej platformy.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [samodzielny plik wykonywalny](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Tworzenie danych binarnych dla wielu platform

Pliki binarne dla wielu platform są tworzone podczas publikowania aplikacji jako [zależnej od środowiska uruchomieniowego](#publish-runtime-dependent)w postaci pliku *dll* . Plik *dll* nosi nazwę po projekcie. Na przykład jeśli masz aplikację o nazwie **word_reader**, zostanie utworzony plik o nazwie *word_reader. dll* . Aplikacje publikowane w ten sposób są uruchamiane za pomocą polecenia `dotnet <filename.dll>` i mogą być uruchamiane na dowolnej platformie.

Pliki binarne dla wielu platform można uruchamiać w dowolnym systemie operacyjnym, o ile jest już zainstalowany przeznaczony do środowiska uruchomieniowego platformy .NET Core. Jeśli nie zainstalowano dostosowanego środowiska uruchomieniowego platformy .NET Core, aplikacja może działać w nowszej wersji środowiska uruchomieniowego, jeśli aplikacja jest skonfigurowana do przesyłania dalej. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego przenoszone do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

Następujące polecenie tworzy plik binarny dla wielu platform:

| Typ                                                                                 | ZESTAW SDK 2,1 | Zestaw SDK 3. x | Polecenie |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [plik binarny dla wielu platform zależnych od środowiska uruchomieniowego](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publikowanie zależne od środowiska uruchomieniowego

Aplikacje publikowane jako zależne od środowiska uruchomieniowego są na wielu platformach i nie obejmują środowiska uruchomieniowego .NET Core. Użytkownik aplikacji jest wymagany do zainstalowania środowiska uruchomieniowego platformy .NET Core.

Publikowanie aplikacji jako zależnej od środowiska uruchomieniowego powoduje utworzenie danych [binarnych dla wielu platform](#produce-a-cross-platform-binary) jako pliku *dll* oraz plików [wykonywalnych specyficznych dla platformy](#produce-an-executable) przeznaczonych dla bieżącej platformy. *Biblioteka DLL* jest międzyplatformowa, gdy plik wykonywalny nie jest. Na przykład jeśli opublikujesz aplikację o nazwie **word_reader** i docelowym systemie Windows, tworzony jest plik wykonywalny *word_reader. exe* wraz z *word_reader. dll*. W przypadku określania wartości dla systemu Linux lub macOS tworzony jest plik wykonywalny *word_reader* wraz z *word_reader. dll*. Aby uzyskać więcej informacji na temat identyfikatorów RID, zobacz [katalog .NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> Zestaw .NET Core SDK 2,1 nie produkuje plików wykonywalnych specyficznych dla platformy przy publikowaniu zależnych od środowiska uruchomieniowego aplikacji.

Międzyplatformowe dane binarne aplikacji można uruchomić za pomocą polecenia `dotnet <filename.dll>` i można je uruchomić na dowolnej platformie. Jeśli aplikacja używa pakietu NuGet, który ma implementacje specyficzne dla platformy, wszystkie zależności platformy są kopiowane do folderu publikowania wraz z aplikacją.

Można utworzyć plik wykonywalny dla określonej platformy, przekazując parametry `-r <RID> --self-contained false` do polecenia [`dotnet publish`](../tools/dotnet-publish.md) . Gdy `-r` parametr zostanie pominięty, tworzony jest plik wykonywalny dla bieżącej platformy. Wszystkie pakiety NuGet, które mają zależności specyficzne dla platformy dla platformy przeznaczonej, są kopiowane do folderu publikowanie.

### <a name="advantages"></a>Zalety

- **Małe\ wdrażania**
Dystrybuowana jest tylko aplikacja i jej zależności. Środowisko uruchomieniowe programu .NET Core i biblioteki są instalowane przez użytkownika, a wszystkie aplikacje współużytkują środowisko uruchomieniowe.

- \ **Międzyplatformowe**
Twoja aplikacja i wszystkie. Biblioteka oparta na sieci działa w innych systemach operacyjnych. Nie musisz definiować platformy docelowej dla swojej aplikacji. Aby uzyskać informacje na temat formatu pliku .NET, zobacz [Format pliku zestawu .NET](../../standard/assembly/file-format.md).

- **Używa najnowszej poprawki\ środowiska uruchomieniowego**
Aplikacja używa najnowszej wersji środowiska uruchomieniowego (w ramach docelowej rodziny głównej platformy .NET Core) zainstalowanej w systemie docelowym. Oznacza to, że aplikacja automatycznie używa najnowszej wersji poprawki środowiska uruchomieniowego platformy .NET Core. To zachowanie domyślne można przesłonić. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego przenoszone do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Wady

- **Wymaga wstępnego zainstalowania\ środowiska uruchomieniowego**
Aplikacja może działać tylko wtedy, gdy wersja platformy .NET Core, której dotyczy Twoja aplikacja, jest już zainstalowana w systemie hosta. Można skonfigurować zachowanie funkcji przekazywania do przodu dla aplikacji, aby wymagać określonej wersji platformy .NET Core lub zezwolić na nowszą wersję programu .NET Core. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego przenoszone do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

- Program **.NET Core może zmienić**\
Jest możliwe, aby środowisko uruchomieniowe i biblioteki platformy .NET Core zostały zaktualizowane na komputerze, na którym uruchomiono aplikację. W rzadkich przypadkach może to zmienić zachowanie aplikacji w przypadku używania bibliotek programu .NET Core, które są w większości aplikacji. Można skonfigurować, w jaki sposób aplikacja używa nowszych wersji platformy .NET Core. Aby uzyskać więcej informacji, zobacz [aplikacje zależne od środowiska uruchomieniowego przenoszone do przodu](../versions/selection.md#framework-dependent-apps-roll-forward).

Następująca wada dotyczy tylko zestawu .NET Core 2,1 SDK.

- **Użyj `dotnet` polecenie, aby uruchomić aplikację**\
Aby uruchomić aplikację, użytkownicy muszą uruchomić polecenie `dotnet <filename.dll>`. Zestaw .NET Core 2,1 SDK nie tworzy plików wykonywalnych specyficznych dla platformy dla aplikacji opublikowanych w środowisku uruchomieniowym.

### <a name="examples"></a>Przykłady

Publikowanie aplikacji zależnych od środowiska uruchomieniowego dla wielu platform. Tworzony jest plik wykonywalny, który jest przeznaczony dla bieżącej platformy wraz z plikiem *dll* .

```dotnet
dotnet publish
```

Publikowanie aplikacji zależnych od środowiska uruchomieniowego dla wielu platform. Tworzony jest plik wykonywalny systemu Linux 64-bitowy wraz z plikiem *dll* . To polecenie nie działa z zestaw .NET Core SDK 2,1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publikuj samodzielny

Publikowanie aplikacji jako samodzielnego powoduje utworzenie pliku wykonywalnego specyficznego dla platformy. Folder publikowania danych wyjściowych zawiera wszystkie składniki aplikacji, w tym biblioteki .NET Core i docelowe środowisko uruchomieniowe. Aplikacja jest odizolowana od innych aplikacji platformy .NET Core i nie korzysta z lokalnie zainstalowanego udostępnionego środowiska uruchomieniowego. Użytkownik aplikacji nie jest wymagany do pobrania i zainstalowania platformy .NET Core.

Plik binarny wykonywalny jest generowany dla określonej platformy docelowej. Na przykład jeśli masz aplikację o nazwie **word_reader**i opublikujesz plik wykonywalny samodzielnego dla systemu Windows, zostanie utworzony pliku *word_reader. exe* . Publikowanie dla systemu Linux lub macOS, tworzony jest plik *word_reader* . Docelowa platforma i architektura są określone za pomocą `-r <RID>` parametru dla polecenia [`dotnet publish`](../tools/dotnet-publish.md) . Aby uzyskać więcej informacji na temat identyfikatorów RID, zobacz [katalog .NET Core RID Catalog](../rid-catalog.md).

Jeśli aplikacja ma zależności specyficzne dla platformy, takie jak pakiet NuGet zawierający zależności specyficzne dla platformy, są one kopiowane do folderu publikowania wraz z aplikacją.

### <a name="advantages"></a>Zalety

- **Sterowanie wersjami programu .NET Core**\
Ty określasz, która wersja programu .NET Core jest wdrażana wraz z Twoją aplikacją.

- \ **ukierunkowane specyficzne dla platformy**
Ponieważ musisz opublikować aplikację dla każdej platformy, wiesz, gdzie aplikacja będzie działać. Jeśli program .NET Core wprowadza nową platformę, użytkownicy nie będą mogli uruchamiać aplikacji na tej platformie, dopóki nie zostanie wydana wersja przeznaczona dla tej platformy. Możesz przetestować swoją aplikację pod kątem problemów ze zgodnością, zanim użytkownicy będą mogli uruchamiać aplikację na nowej platformie.

### <a name="disadvantages"></a>Wady

- **Większe wdrożenia**\
Ponieważ aplikacja zawiera środowisko uruchomieniowe platformy .NET Core i wszystkie zależności aplikacji, wymagany rozmiar i ilość miejsca na dysku twardym są większe niż wersja [zależna od środowiska uruchomieniowego](#publish-runtime-dependent) .

  > [!TIP]
  > Możesz zmniejszyć rozmiar wdrożenia w systemach Linux o około 28 MB przy użyciu [*trybu niezmiennej globalizacji*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)platformy .NET Core. Wymusza to aplikacji traktowanie wszystkich kultur, takich jak [Niezmienna kultura](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- **Trudniejsze do zaktualizowania wersji .NET Core**\
Środowisko uruchomieniowe platformy .NET Core (dystrybuowane z aplikacją) można uaktualnić tylko przez wydanie nowej wersji aplikacji. Użytkownik jest odpowiedzialny za dostarczanie zaktualizowanej wersji aplikacji na potrzeby poprawek zabezpieczeń do środowiska uruchomieniowego .NET Core. 

### <a name="examples"></a>Przykłady

Publikuj samodzielną aplikację. Tworzony jest plik wykonywalny macOS 64-bitowy.

```dotnet
dotnet publish -r osx-x64
```

Publikuj samodzielną aplikację. Tworzony jest plik wykonywalny systemu Windows 64-bitowy.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Zobacz też

- [Wdrażanie aplikacji .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core.](deploy-with-cli.md)
- [Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio.](deploy-with-vs.md)
- [Pakiety, aplikacje i struktury.](../packages.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID).](../rid-catalog.md)
- [Wybierz wersję platformy .NET Core do użycia.](../versions/selection.md)
