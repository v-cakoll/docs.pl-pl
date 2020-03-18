---
title: Analizator przenośności .NET - .NET
description: Dowiedz się, jak używać narzędzia Analizator przenośności .NET do oceny, jak przenośny kod jest jednym z różnych implementacji .NET, w tym .NET Core, .NET Standard, UWP i Xamarin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: e0a5c791926b36fe5a35c5446471c3dcdb75cd7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72774389"
---
# <a name="the-net-portability-analyzer"></a>Analizator przenośności .NET

Chcesz, aby twoje biblioteki obsługiwać wiele platform? Chcesz zobaczyć, ile pracy jest wymagane, aby aplikacja .NET Framework działała na platformie .NET Core? [Analizator przenośności .NET](https://github.com/microsoft/dotnet-apiport) jest narzędziem, które analizuje zestawy i udostępnia szczegółowy raport o interfejsach API platformy .NET, których brakuje dla aplikacji lub bibliotek, które mają być przenośne na określonych platformach .NET. Analizator przenośności jest oferowany jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), które analizuje jeden zestaw na projekt, oraz jako aplikacja konsoli [ApiPort](https://aka.ms/apiportdownload), która analizuje zestawy według określonych plików lub katalogu.

Po przekonwertowaniu projektu na nową platformę, taką jak .NET Core, można użyć [narzędzia Analizator interfejsu API](api-analyzer.md) opartego na interfejsie Roslyn do identyfikowania interfejsów API zgłaszających <xref:System.PlatformNotSupportedException> wyjątki i inne problemy ze zgodnością.

## <a name="common-targets"></a>Wspólne cele

- [.NET Core](../../core/index.md): Ma modułową konstrukcję, wykorzystuje scenariusze międzyplatformowe i jest przeznaczony dla wielu platform. Side-by-side umożliwia przyjęcie nowych wersji .NET Core bez przerywania innych aplikacji. Jeśli twoim celem jest przeniesienie aplikacji do .NET Core obsługujących platformy międzyplatformowe, jest to zalecany obiekt docelowy.
- . [Standard NETTO:](../../standard/net-standard.md)Zawiera standardowe interfejsy API .NET dostępne we wszystkich implementacjach .NET. Jeśli twoim celem jest, aby biblioteki do uruchomienia na wszystkich platformach obsługiwanych platformy .NET, jest to zalecane miejsce docelowe.
- [ASP.NET Core:](/aspnet/core)Nowoczesna struktura internetowa zbudowana na platformie .NET Core. Jeśli twoim celem jest przeniesienie aplikacji sieci web do platformy .NET Core do obsługi wielu platform, jest to zalecany cel.
- .NET Core + [Rozszerzenia platformy:](../../core/porting/windows-compat-pack.md)Oprócz pakietów Zgodności systemu Windows, który udostępnia wiele dostępnych technologii .NET Framework, zawiera podstawowe interfejsy API .NET Core. Jest to zalecany obiekt docelowy do przenoszenia aplikacji z platformy .NET Framework do platformy .NET Core w systemie Windows.
- .NET Standard + [Rozszerzenia platformy:](../../core/porting/windows-compat-pack.md)Oprócz standardowych interfejsów API .NET oprócz pakietu zgodności systemu Windows, który udostępnia wiele dostępnych technologii .NET Framework. Jest to zalecany obiekt docelowy do przenoszenia biblioteki z .NET Framework do .NET Core w systemie Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak korzystać z analizatora przenośności .NET

Aby rozpocząć korzystanie z analizatora przenośności .NET w programie Visual Studio, należy najpierw pobrać i zainstalować rozszerzenie z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Działa w programie Visual Studio 2017 i nowszych wersjach. Można skonfigurować go w programie Visual Studio za pomocą **analizowania** > **ustawień analizatora portności** i wybrać platformy docelowe, która jest platformy .NET/ wersje, które mają ocenić luki przenośności w porównaniu z platformą/wersją, że bieżący zestaw jest zbudowany z.

![Zrzut ekranu przedstawiający analizator przenośności.](./media/portability-analyzer/portability-screenshot.png)

Możesz również skorzystać z aplikacji konsoli ApiPort, pobrać ją z [repozytorium ApiPort.](https://aka.ms/apiportdownload) Można użyć `listTargets` opcji polecenia, aby wyświetlić dostępną listę docelową, a następnie wybrać platformy docelowe, określając lub `-t` `--target` polecą opcję.

### <a name="analyze-portability"></a>Analizowanie przenośności
Aby przeanalizować cały projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Analizuj przenośność zestawu**. W przeciwnym razie przejdź do menu **Analizuj** i wybierz **pozycję Analizuj przenośność złożenia**. W tym miejscu wybierz plik wykonywalny projektu lub dll.

![Zrzut ekranu przedstawiający analizator przenośności z Eksploratora rozwiązań.](./media/portability-analyzer/portability-solution-explorer.png)

Możesz również użyć [aplikacji konsoli ApiPort](https://aka.ms/apiportdownload).

- Wpisz następujące polecenie do analizy bieżącego katalogu:`ApiPort.exe analyze -f .`
- Aby przeanalizować określoną listę plików dll, wpisz następujące polecenie:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Uruchom, `ApiPort.exe -?` aby uzyskać więcej pomocy

Zaleca się dołączenie wszystkich powiązanych plików exe i dll, które są twoim i które chcesz przenieść, oraz wykluczenie plików, od których zależy aplikacja, ale nie jesteś właścicielem i nie możesz ich portować. To daje najbardziej odpowiedni raport przenośności.

### <a name="view-and-interpret-portability-result"></a>Wyświetlanie i interpretowanie wyniku przenośności

W raporcie są wyświetlane tylko interfejsy API, które nie są obsługiwane przez platformę docelową.
Po uruchomieniu analizy w programie Visual Studio zostanie wyświetlone łącze pliku raportu przenoszenia .NET. Jeśli użyto [aplikacji konsoli ApiPort,](https://aka.ms/apiportdownload)raport przenoszenia .NET jest zapisywany jako plik w określonym formacie. Wartość domyślna znajduje się w pliku programu Excel (*xlsx*) w bieżącym katalogu.

#### <a name="portability-summary"></a>Podsumowanie przenośności

![Zrzut ekranu przedstawiający podsumowanie przenośności.](./media/portability-analyzer/api-catalog-portablility-summary.png)

Sekcja Podsumowanie przenośności raportu zawiera procent przenośności dla każdego zestawu uwzględnionego w przebiegu. W poprzednim przykładzie 71,24% interfejsów API platformy `svcutil` .NET Framework używanych w aplikacji jest dostępnych w rozszerzeniach platformy .NET Core +. Po uruchomieniu narzędzia Analizator przenośności .NET względem wielu zestawów każdy zestaw powinien mieć wiersz w raporcie Podsumowanie przenośności.

#### <a name="details"></a>Szczegóły

![Zrzut ekranu przedstawiający szczegóły przenośności.](./media/portability-analyzer/api-catalog-portablility-details.png)

Sekcja **Szczegóły** raportu zawiera listę interfejsów API brakujących w dowolnej z wybranych **platform docelowych**.

- Typ docelowy: typ ma brak interfejsu API z platformy docelowej
- Element członkowski obiektu docelowego: brakuje metody na platformie docelowej
- Nazwa zestawu: zestaw .NET Framework, w których mieszka brakujący interfejs API.
- Każda z wybranych platform docelowych jest jedną kolumną, na przykład ".NET Core": Wartość "Nieobsługiwana" oznacza, że interfejs API nie jest obsługiwany na tej platformie docelowej.
- Zalecane zmiany: zalecane interfejsy API lub technologia do zmiany. Obecnie to pole jest puste lub nieaktualne dla wielu interfejsów API. Ze względu na dużą liczbę interfejsów API, mamy duże wyzwanie, aby go utrzymać. Szukamy alternatywnych rozwiązań, aby zapewnić przydatne informacje dla klientów.

#### <a name="missing-assemblies"></a>Brakujące zestawy

![Zrzut ekranu przedstawiający brakujące zestawy.](./media/portability-analyzer/api-catalog-missing-assemblies.png)

Sekcja Brakujące zestawy może znaleźć się w raporcie. Informuje, że ta lista zestawów odwołuje się do analizowanych zestawów i nie zostały przeanalizowane. Jeśli jest to zestaw, który należy, dołącz go do uruchamiania analizatora przenośności interfejsu Api, aby można było uzyskać szczegółowy raport przenośności poziomu interfejsu API. Jeśli jest to biblioteka innej firmy, wyszcem, jeśli mają nowszą wersję obsługjącą platformę docelową. Jeśli tak, rozważ przejście do nowszej wersji. Po pewnym czasie można oczekiwać, że ta lista zawiera wszystkie zestawy innych firm, od których zależy aplikacja, i potwierdziła, że mają wersję obsługjącą platformę docelową.

Aby uzyskać więcej informacji na temat analizatora przenośności .NET, odwiedź [dokumentację usługi GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i krótkie spojrzenie na wideo [.NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9.
