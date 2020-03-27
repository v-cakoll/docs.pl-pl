---
title: Analizator przenośności .NET - .NET
description: Dowiedz się, jak używać narzędzia .NET Portability Analyzer do oceny, jak przenośny kod znajduje się wśród różnych implementacji platformy .NET, w tym .NET Core, .NET Standard, platformy uniwersalnej systemu Windows i platformy Xamarin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 397d9f08a0dd28f80d653ac5044d6acfa2418727
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344311"
---
# <a name="the-net-portability-analyzer"></a>Analizator przenośności .NET

Chcesz, aby Twoje biblioteki obsługiwać wiele platform? Chcesz zobaczyć, ile pracy jest wymagane, aby aplikacja .NET Framework działała na programie .NET Core? [Analizator przenośności platformy .NET](https://github.com/microsoft/dotnet-apiport) jest narzędziem, które analizuje zestawy i udostępnia szczegółowy raport na temat interfejsów API platformy .NET, których brakuje dla aplikacji lub bibliotek, które mają być przenośne na określonych platformach docelowych .NET. Analizator przenośności jest oferowany jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), które analizuje jeden zestaw na projekt i jako aplikacja konsoli [ApiPort](https://aka.ms/apiportdownload), która analizuje zestawy przez określone pliki lub katalog.

Po przekonwertowaniu projektu na nową platformę, taką jak .NET Core, można użyć [narzędzia analizatora interfejsu API](api-analyzer.md) opartego na roslyn do identyfikowania interfejsów API zgłaszających <xref:System.PlatformNotSupportedException> wyjątki i inne problemy ze zgodnością.

## <a name="common-targets"></a>Wspólne cele

- [.NET Core:](../../core/index.yml)Ma modułową konstrukcję, wykorzystuje side-by-side i cele scenariuszy między platformami. Side-by-side umożliwia przyjęcie nowych wersji .NET Core bez przerywania innych aplikacji. Jeśli twoim celem jest przeniesienie aplikacji do platformy .NET Core obsługującej między platformami, jest to zalecany obiekt docelowy.
- . [Standard NET:](../../standard/net-standard.md)Zawiera standardowe interfejsy API platformy .NET dostępne we wszystkich implementacjach platformy .NET. Jeśli twoim celem jest, aby biblioteka do uruchomienia na wszystkich platformach obsługiwanych przez platformy .NET, jest to zalecane miejsce docelowe.
- [ASP.NET Core:](/aspnet/core)Nowoczesna struktura internetowa oparta na programie .NET Core. Jeśli twoim celem jest przeniesienie aplikacji sieci web do platformy .NET Core do obsługi wielu platform, jest to zalecany obiekt docelowy.
- .NET Core + [Rozszerzenia platformy:](../../core/porting/windows-compat-pack.md)Zawiera interfejsy API .NET Core oprócz pakietu zgodności systemu Windows, który zapewnia wiele dostępnych technologii programu .NET Framework. Jest to zalecany obiekt docelowy przenoszenia aplikacji z programu .NET Framework do platformy .NET Core w systemie Windows.
- .NET Standard + [Rozszerzenia platformy:](../../core/porting/windows-compat-pack.md)Zawiera interfejsy API .NET Standard oprócz pakietu zgodności systemu Windows, który zapewnia wiele dostępnych technologii programu .NET Framework. Jest to zalecany cel przenoszenia biblioteki z programu .NET Framework do platformy .NET Core w systemie Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak korzystać z analizatora przenośności .NET

Aby rozpocząć korzystanie z analizatora przenoszenia .NET w programie Visual Studio, należy najpierw pobrać i zainstalować rozszerzenie z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Działa na programie Visual Studio 2017 i nowszych wersjach. Można go skonfigurować w programie Visual Studio za pomocą **analizy** > **ustawienia analizowania przenośności** i wybierz platformy docelowe, który jest platform .NET/wersje, które chcesz ocenić luki w przenośni w porównaniu z platform/wersji, które bieżącego zestawu jest zbudowany z.

![Zrzut ekranu przedstawiający analizator przenośności.](./media/portability-analyzer/portability-screenshot.png)

Możesz również użyć aplikacji konsoli ApiPort, pobrać ją z [repozytorium ApiPort](https://aka.ms/apiportdownload). Można użyć `listTargets` opcji polecenia, aby wyświetlić dostępną listę `-t` docelową, a następnie wybrać platformy docelowe, określając lub `--target` polecając opcję.

### <a name="analyze-portability"></a>Analizowanie przenośności
Aby przeanalizować cały projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz pozycję **Analizuj przenośność zestawu**. W przeciwnym razie przejdź do menu **Analizuj** i wybierz polecenie **Analizuj przenośność złożenia**. W tym miejscu wybierz plik wykonywalny lub bibliotekę DLL projektu.

![Zrzut ekranu przedstawiający analizator przenośności z Eksploratora rozwiązań.](./media/portability-analyzer/portability-solution-explorer.png)

Można również użyć [aplikacji konsoli ApiPort](https://aka.ms/apiportdownload).

- Wpisz następujące polecenie, aby przeanalizować bieżący katalog:`ApiPort.exe analyze -f .`
- Aby przeanalizować określoną listę plików dll, wpisz następujące polecenie:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Biegnij, `ApiPort.exe -?` aby uzyskać więcej pomocy

Zaleca się uwzględnienie wszystkich powiązanych plików exe i dll, które są własnością i chcesz port, i wykluczyć pliki, które zależy od aplikacji, ale nie jesteś właścicielem i nie można port. To daje najbardziej odpowiedni raport przenoszenia.

### <a name="view-and-interpret-portability-result"></a>Wyświetlanie i interpretowanie wyniku przenoszenia

Tylko interfejsy API, które nie są obsługiwane przez platformę docelową są wyświetlane w raporcie.
Po uruchomieniu analizy w programie Visual Studio zostanie wyświetlene łącze do pliku raportu o przenośności .NET. Jeśli używano [aplikacji konsoli ApiPort,](https://aka.ms/apiportdownload)raport .NET Portability jest zapisywany jako plik w określonym formacie. Wartość domyślna znajduje się w pliku programu Excel (*xlsx*) w bieżącym katalogu.

#### <a name="portability-summary"></a>Podsumowanie przenoszenia

![Zrzut ekranu przedstawiający podsumowanie przenośności.](./media/portability-analyzer/api-catalog-portablility-summary.png)

Sekcja Podsumowanie przenoszenia raportu pokazuje procent przenoszenia dla każdego zestawu uwzględnionego w przebiegu. W poprzednim przykładzie 71,24% interfejsów API programu .NET Framework używanych w `svcutil` aplikacji są dostępne w .NET Core + rozszerzenia platformy. Po uruchomieniu narzędzia .NET Analizator przenośności dla wielu zestawów, każdy zestaw powinien mieć wiersz w raporcie Podsumowanie przenoszenia.

#### <a name="details"></a>Szczegóły

![Zrzut ekranu przedstawiający szczegóły przenoszenia.](./media/portability-analyzer/api-catalog-portablility-details.png)

Sekcja **Szczegóły** raportu zawiera listę interfejsów API, których brakuje w dowolnej z wybranych **platform docelowych**.

- Typ obiektu docelowego: typ ma brak interfejsu API z platformy docelowej
- Element członkowski docelowy: brakuje metody na platformie docelowej
- Nazwa zestawu: .NET Framework zestawu, w których mieszka brakujący interfejs API.
- Każda z wybranych platform docelowych jest jedna kolumna, takich jak ".NET Core": "Nie obsługiwane" wartość oznacza, że interfejs API nie jest obsługiwany na tej platformie docelowej.
- Zalecane zmiany: zalecany interfejs API lub technologia do zmiany. Obecnie to pole jest puste lub nieaktualne dla wielu interfejsów API. Ze względu na dużą liczbę interfejsów API, mamy duże wyzwanie, aby go utrzymać. Szukamy alternatywnych rozwiązań, aby zapewnić klientom pomocne informacje.

#### <a name="missing-assemblies"></a>Brakujące złoża

![Zrzut ekranu przedstawiający brakujące zestawy.](./media/portability-analyzer/api-catalog-missing-assemblies.png)

W raporcie może znajdować się sekcja Brakujące zestawy. Informuje, że ta lista zestawów odwołuje się do analizowanych zestawów i nie zostały przeanalizowane. Jeśli jest to zestaw, który jesteś właścicielem, dołącz go w analizatora przenoszenia interfejsu API, aby uzyskać szczegółowy raport przenośności na poziomie interfejsu API. Jeśli jest to biblioteka innej firmy, wyszukuje, czy mają nowszą wersję obsługującą platformę docelową. Jeśli tak, rozważ przejście do nowszej wersji. Po pewnym czasie można oczekiwać, że ta lista zawiera wszystkie zestawy innych firm, które zależy od aplikacji i potwierdził, że mają wersję obsługującą platformę docelową.

Aby uzyskać więcej informacji na temat analizatora przenoszenia .NET, odwiedź [dokumentację usługi GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i krótkie spojrzenie na wideo [.NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9.
