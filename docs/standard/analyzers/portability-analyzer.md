---
title: Analizator przenośności .NET — .NET
description: Dowiedz się, jak używać narzędzia analizatora przenośności platformy .NET do oceniania sposobu, w jaki przenośny kod znajduje się wśród różnych implementacji platformy .NET, w tym .NET Core, .NET Standard, platformy UWP i Xamarin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 815ac8e0f0c4392a3d89530947b0739d06a0b95d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278366"
---
# <a name="the-net-portability-analyzer"></a>Analizator przenośności platformy .NET

Czy chcesz, aby biblioteki obsługiwały wiele platform? Chcesz sprawdzić, ile pracy jest wymagane do uruchomienia aplikacji .NET Framework na platformie .NET Core? [Analizator przenośności .NET](https://github.com/microsoft/dotnet-apiport) to narzędzie, które analizuje zestawy i udostępnia szczegółowy raport dotyczący interfejsów API platformy .NET, których brakuje w przypadku aplikacji lub bibliotek, które mają być przenośne na określonych przeznaczonych dla Ciebie platformach platformy .NET. Analizator przenośności jest oferowany jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), które analizuje jeden zestaw na każdy projekt i jako [aplikację konsolową ApiPort](https://aka.ms/apiportdownload), która analizuje zestawy według określonych plików lub katalogów.

Po przeprowadzeniu konwersji projektu na nową platformę, taką jak .NET Core, można użyć [Narzędzia analizatora interfejsów API](api-analyzer.md) Roslyn, aby identyfikować interfejsy API zgłaszające <xref:System.PlatformNotSupportedException> wyjątki i inne problemy ze zgodnością.

## <a name="common-targets"></a>Wspólne elementy docelowe

- [.NET Core](../../core/index.yml): ma model modularny, obsługuje instalację równoległą i kieruje scenariusze dla wielu platform. Instalacja równoczesna pozwala na zastosowanie nowych wersji platformy .NET Core bez przerywania innych aplikacji. Jeśli chcesz przenieść aplikację do platformy .NET Core i obsługiwać wiele platform, jest to zalecany element docelowy.
- . [Net Standard](../net-standard.md): zawiera interfejsy API .NET Standard dostępne we wszystkich implementacjach platformy .NET. Jeśli chcesz, aby Twoja biblioteka działała na wszystkich platformach obsługiwanych przez platformę .NET, jest to zalecane.
- [ASP.NET Core](/aspnet/core): nowoczesne środowisko sieci Web oparte na platformie .NET Core. Jeśli chcesz przenieść aplikację sieci Web do programu .NET Core w celu obsługi wielu platform, jest to zalecane miejsce docelowe.
- Rozszerzenia platformy .NET Core + [platform](../../core/porting/windows-compat-pack.md): zawierają interfejsy API platformy .NET Core oprócz pakietu zgodności systemu Windows, który zapewnia wiele .NET Framework dostępnych technologii. Jest to zalecany element docelowy do przenoszenia aplikacji z .NET Framework do platformy .NET Core w systemie Windows.
- Rozszerzenia .NET Standard i [platformy](../../core/porting/windows-compat-pack.md): zawierają interfejsy API .NET Standard oprócz pakietu zgodności systemu Windows, który zapewnia wiele .NET Framework dostępnych technologii. Jest to zalecany element docelowy do przenoszenia biblioteki z .NET Framework do platformy .NET Core w systemie Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak używać analizatora przenośności platformy .NET

Aby rozpocząć korzystanie z analizatora przenośności platformy .NET w programie Visual Studio, należy najpierw pobrać i zainstalować rozszerzenie z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Działa on w programie Visual Studio 2017 i nowszych wersjach. Skonfiguruj je w programie Visual Studio za pomocą funkcji **Analizuj**  >  **Ustawienia analizatora przenośności** i wybierz Platformy docelowe, które są platformami/wersjami platformy .NET, które mają oszacować przerwy w przenośności porównujące z platformą/wersją, z których korzysta bieżący zestaw.

![Zrzut ekranu analizatora przenośności.](./media/portability-analyzer/portability-screenshot.png)

Możesz również użyć aplikacji konsolowej ApiPort, pobrać ją z [repozytorium ApiPort](https://aka.ms/apiportdownload). Można użyć `listTargets` opcji polecenia, aby wyświetlić listę dostępnych obiektów docelowych, a następnie wybrać Platformy docelowe przez określenie `-t` lub `--target` opcję polecenia.

### <a name="analyze-portability"></a>Analiza przenośności
Aby analizować cały projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz pozycję **Analizuj przenośność zestawu**. W przeciwnym razie przejdź do menu **Analizuj** i wybierz pozycję **Analizuj przenośność zestawu**. Z tego miejsca wybierz plik wykonywalny lub DLL projektu.

![Zrzut ekranu analizatora przenośności z Eksplorator rozwiązań.](./media/portability-analyzer/portability-solution-explorer.png)

Możesz również użyć [aplikacji konsolowej ApiPort](https://aka.ms/apiportdownload).

- Wpisz następujące polecenie, aby przeanalizować bieżący katalog:`ApiPort.exe analyze -f .`
- Aby przeanalizować określoną listę plików DLL, wpisz następujące polecenie:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Uruchom `ApiPort.exe -?` , aby uzyskać więcej pomocy

Zaleca się zawrzeć wszystkie powiązane pliki exe i dll, które mają być używane, i które mają być używane do portów, a także wykluczenie plików, od których zależy aplikacja, ale nie do portów. Zapewni to najbardziej odpowiedni raport dotyczący przenośności.

### <a name="view-and-interpret-portability-result"></a>Wyświetl i Interpretuj wyniki przenośności

W raporcie są wyświetlane tylko interfejsy API, które nie są obsługiwane przez platformę docelową.
Po uruchomieniu analizy w programie Visual Studio zostanie wyświetlony link do pliku raportu przenośności platformy .NET. Jeśli użyto [aplikacji konsolowej ApiPort](https://aka.ms/apiportdownload), raport dotyczący przenośności platformy .NET jest zapisywany jako plik w określonym formacie. Wartość domyślna to w pliku programu Excel (*xlsx*) w bieżącym katalogu.

#### <a name="portability-summary"></a>Podsumowanie przenośności

![Zrzut ekranu przedstawiający podsumowanie przenośności.](./media/portability-analyzer/api-catalog-portablility-summary.png)

Sekcja podsumowania przenośności raportu przedstawia wartość procentową przenośności każdego zestawu zawartego w przebiegu. W poprzednim przykładzie 71,24% interfejsów API .NET Framework używanych w `svcutil` aplikacji są dostępne w rozszerzeniach platformy .NET Core + platform. Po uruchomieniu narzędzia analizatora przenośności platformy .NET dla wielu zestawów każdy zestaw powinien mieć wiersz w raporcie podsumowującym przenośność.

#### <a name="details"></a>Szczegóły

![Zrzut ekranu przedstawiający szczegóły dotyczące przenośności.](./media/portability-analyzer/api-catalog-portablility-details.png)

Sekcja **szczegóły** raportu zawiera listę interfejsów API, których brakuje na żadnej z wybranych **platform**.

- Typ docelowy: typ ma brakujący interfejs API z platformy docelowej
- Docelowy element członkowski: brak metody z platformy docelowej
- Nazwa zestawu: zestaw .NET Framework, w którym znajduje się brakujący interfejs API.
- Każda z wybranych platform docelowych jest jedną kolumną, taką jak ".NET Core": "nieobsługiwana" oznacza, że interfejs API nie jest obsługiwany na tej platformie docelowej.
- Zalecane zmiany: zalecany interfejs API lub technologia do zmiany. Obecnie to pole jest puste lub nieaktualne w przypadku wielu interfejsów API. Ze względu na dużą liczbę interfejsów API mamy duże wyzwanie, aby zachować aktualność. Przeglądamy alternatywne rozwiązania, aby zapewnić klientom przydatne informacje.

#### <a name="missing-assemblies"></a>Brakujące Zestawy

![Zrzut ekranu przedstawiający brakujące zestawy.](./media/portability-analyzer/api-catalog-missing-assemblies.png)

W raporcie można znaleźć sekcję brakujące zestawy. Ta sekcja zawiera listę zestawów, do których odwołują się analizowane zestawy i które nie zostały przeanalizowane. Jeśli jest to zestaw, którego jesteś własnym, dołącz go do przebiegu analizatora przenośności interfejsu API, dzięki czemu możesz uzyskać szczegółowy raport dla tego poziomu interfejsu API. Jeśli jest to biblioteka innych firm, sprawdź, czy jest dostępna nowsza wersja, która obsługuje platformę docelową, i rozważ przejście do nowszej wersji. Ostatecznie lista powinna obejmować wszystkie zestawy innych firm, od których zależy aplikacja, która ma wersję obsługującą platformę docelową.

Aby uzyskać więcej informacji na temat analizatora przenośności platformy .NET, zapoznaj się z [dokumentacją dotyczącą usługi GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i zapoznaj się z tematem wideo dotyczącego kanału 9 usługi [.NET przenośności](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) .
