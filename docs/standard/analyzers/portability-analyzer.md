---
title: Analizator przenośności .NET — .NET
description: Dowiedz się, jak używać narzędzia analizatora przenośności platformy .NET do oceniania sposobu, w jaki przenośny kod znajduje się wśród różnych implementacji platformy .NET, w tym .NET Core, .NET Standard, platformy UWP i Xamarin.
ms.date: 07/18/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 32b4f980061b0975c413a8cde436074f76cfabc9
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433952"
---
# <a name="the-net-portability-analyzer"></a>Analizator przenośności platformy .NET

Czy chcesz, aby biblioteki obsługiwały wiele platform? Chcesz zobaczyć, ile pracy jest wymagane, aby aplikacja była zgodna z innymi implementacjami i profilami .NET, w tym .NET Core, .NET Standard, platformy UWP i Xamarin dla systemów iOS, Android i Mac? [Analizator przenośności platformy .NET](https://github.com/microsoft/dotnet-apiport) to narzędzie, które udostępnia szczegółowy raport dotyczący sposobu, w jaki program jest elastyczny od implementacji platformy .NET przez analizowanie zestawów. Analizator przenośności jest oferowany jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), które analizuje zestaw na projekt, oraz jako [aplikację konsolową ApiPort](https://aka.ms/apiportdownload), która analizuje zestawy według określonych plików lub katalogów.

## <a name="common-targets"></a>Wspólne elementy docelowe

* [.NET Core](../../core/index.md): Program ma projektowanie modularne, wykorzystuje równolegle i ukierunkowane scenariusze dla wielu platform. Obok siebie można zastosować nowe wersje platformy .NET Core bez przerywania innych aplikacji. Jeśli chcesz przenieść aplikację do platformy .NET Core obsługującej wiele platform, jest to zalecany element docelowy. 
* . [Standard NET](../../standard/net-standard.md): Obejmuje interfejsy API .NET Standard dostępne we wszystkich implementacjach platformy .NET. Jeśli chcesz, aby Twoja biblioteka działała na wszystkich platformach obsługiwanych przez platformę .NET, jest to zalecane.  
* [ASP.NET Core](/aspnet/core): Nowoczesne środowisko sieci Web oparte na platformie .NET Core. Jeśli chcesz przenieść aplikację sieci Web do programu .NET Core w celu obsługi wielu platform, jest to zalecane miejsce docelowe.
* [Rozszerzenia platformy](../../core/porting/windows-compat-pack.md).NET Core +: Zawiera interfejsy API platformy .NET Core oprócz pakietu zgodności systemu Windows, który zapewnia wiele .NET Framework dostępnych technologii. Jest to zalecany element docelowy do przenoszenia aplikacji z .NET Framework do platformy .NET Core w systemie Windows.
* .NET Standard i [rozszerzenia platformy](../../core/porting/windows-compat-pack.md): Program zawiera .NET Standard interfejsy API oprócz pakietu zgodności systemu Windows, który zapewnia wiele .NET Framework dostępnych technologii. Jest to zalecany element docelowy do przenoszenia biblioteki z .NET Framework do platformy .NET Core w systemie Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak używać analizatora przenośności platformy .NET

Aby rozpocząć korzystanie z analizatora przenośności platformy .NET w programie Visual Studio, należy najpierw pobrać i zainstalować rozszerzenie z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Działa on w programie Visual Studio 2017 i nowszych wersjach. Można skonfigurować je w programie Visual Studio za pomocą funkcji **Analizuj** > **Ustawienia analizatora przenośności** i wybrać Platformy docelowe, które są platformami/wersjami platformy .NET, które mają oszacować przerwy w korzystaniu z platformy/ wersja, z którą jest zbudowany bieżący zestaw.

![Zrzut ekranu z przenośnością](./media/portability-analyzer/portability-screenshot.png)

Możesz również użyć aplikacji konsolowej ApiPort, pobrać ją z [repozytorium ApiPort](https://aka.ms/apiportdownload). Można użyć `listTargets` opcji polecenia, aby wyświetlić listę dostępnych obiektów docelowych, a następnie wybrać Platformy docelowe przez `-t` określenie `--target` lub opcję polecenia. 

### <a name="analyze-portability"></a>Analiza przenośności
Aby analizować cały projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz pozycję **Analizuj przenośność zestawu**. W przeciwnym razie przejdź do menu **Analizuj** i wybierz pozycję **Analizuj przenośność zestawu**. Z tego miejsca wybierz plik wykonywalny lub DLL projektu.

![Analizator przenośności z Eksplorator rozwiązań](./media/portability-analyzer/portability-solution-explorer.png)

Możesz również użyć [aplikacji konsolowej ApiPort](https://aka.ms/apiportdownload). 

* Wpisz następujące polecenie, aby przeanalizować bieżący katalog:`ApiPort.exe analyze -f .`
* Aby przeanalizować określoną listę plików DLL, wpisz następujące polecenie:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Uruchom `ApiPort.exe -?` , aby uzyskać więcej pomocy

Zaleca się zawrzeć wszystkie powiązane pliki exe i dll, które mają być używane, i które mają być używane do portów, a także wykluczenie plików, od których zależy aplikacja, ale nie do portów. Zapewni to najbardziej odpowiedni raport dotyczący przenośności.  

### <a name="view-and-interpret-portability-result"></a>Wyświetl i Interpretuj wyniki przenośności

W raporcie są wyświetlane tylko interfejsy API, które nie są obsługiwane przez platformę docelową. Po uruchomieniu analizy w programie Visual Studio zostanie wyświetlony link do pliku raportu przenośności platformy .NET. Jeśli użyto [aplikacji konsolowej ApiPort](https://aka.ms/apiportdownload), raport dotyczący przenośności platformy .NET jest zapisywany jako plik w określonym formacie. Wartość domyślna to w pliku programu Excel (*xlsx*) w bieżącym katalogu.

#### <a name="portability-summary"></a>Podsumowanie przenośności 

![Podsumowanie przenośności](./media/portability-analyzer/portabilitysummary.png)

Sekcja podsumowania przenośności raportu przedstawia wartość procentową przenośności każdego zestawu zawartego w przebiegu. W poprzednim przykładzie 71,24% interfejsów API .NET Framework używanych w `svcutil` aplikacji są dostępne w rozszerzeniach platformy .NET Core + platform. Po uruchomieniu narzędzia analizatora przenośności platformy .NET dla wielu zestawów każdy zestaw powinien mieć wiersz w raporcie podsumowującym przenośność.

#### <a name="details"></a>Szczegóły

![Szczegóły przenośności](./media/portability-analyzer/portabilitydetails.png)

Sekcja szczegóły raportu zawiera listę interfejsów API, których brakuje na jednej z platform docelowych. 

- Typ docelowy: typ ma brakujący interfejs API z platformy docelowej 
- Docelowy element członkowski: brak metody z platformy docelowej 
- Nazwa zestawu: zestaw .NET Framework, w którym znajduje się brakujący interfejs API. 
- Każda z wybranych platform docelowych jest jedną kolumną, na przykład ".NET Core": Wartość "nieobsługiwana" oznacza, że interfejs API nie jest obsługiwany na tej platformie docelowej. 
- Zalecane zmiany: zalecany interfejs API lub technologia do zmiany. Obecnie to pole jest puste lub nieaktualne z dużą ilością interfejsów API. Ze względu na dużą liczbę interfejsów API mamy do nich duże wyzwanie. Przeglądamy alternatywne rozwiązania, aby zapewnić klientom przydatne informacje.

#### <a name="missing-assemblies"></a>Brakujące Zestawy

![Szczegóły przenośności](./media/portability-analyzer/missingassemblies.png)

W raporcie można znaleźć sekcję brakujące zestawy. Informuje o tym, że ta lista zestawów odwołuje się do przeanalizowanych zestawów i nie została przeanalizowana. Jeśli jest to zestaw, którego jesteś własnym, dołącz go do przebiegu analizatora przenośności interfejsu API, aby można było uzyskać dla niego szczegółowy raport dotyczący poziomu interfejsu API. Jeśli jest to biblioteka innej firmy, sprawdź, czy ma ona nowszą wersję obsługującą platformę docelową. Jeśli tak, rozważ przejście do nowszej wersji. Na koniec należy oczekiwać, że ta lista zawiera wszystkie zestawy innych firm, od których zależy aplikacja, i potwierdzenie, że mają wersję obsługującą platformę docelową.  

Aby uzyskać więcej informacji na temat analizatora przenośności platformy .NET, zapoznaj się z [dokumentacją dotyczącą usługi GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i zapoznaj się z tematem wideo dotyczącego kanału 9 usługi [.NET przenośności](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) .
