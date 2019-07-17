---
title: Narzędzia .NET Portability Analyzer — .NET
description: Dowiedz się, jak ocenić, jak przenośny kod jest między różne implementacje platformy .NET, takich jak .NET Core, .NET Standard, platformy uniwersalnej systemu Windows i Xamarin za pomocą narzędzia .NET Portability Analyzer.
ms.date: 07/10/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 73a9cacbce02880d236f87459673812af9828916
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238557"
---
# <a name="the-net-portability-analyzer"></a>Narzędzia .NET Portability Analyzer

Czy chcesz wprowadzić bibliotek pomocy technicznej dla wielu platform? Chcesz zobaczyć, ile pracy jest wymagane, aby Twoje aplikacje zgodne z innych implementacji platformy .NET i profilów, w tym .NET Core, .NET Standard, platformy uniwersalnej systemu Windows i Xamarin dla systemów iOS, Android i Mac? [Narzędzia .NET Portability Analyzer](https://github.com/microsoft/dotnet-apiport) to narzędzie, które zawiera szczegółowy raport w sposób elastyczny Twój program jest w implementacji platformy .NET, analizując zestawy. Analizator przenośności jest oferowany jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), która analizuje zestawu według projektu, a także jako [aplikacja konsolowa ApiPort](https://aka.ms/apiportdownload), która analizuje zestawy określone pliki lub katalogu.

## <a name="common-targets"></a>Typowe obiekty docelowe

* [.NET Core](../../core/index.md): Modularny projekt ma używającego side-by-side i jest przeznaczony dla scenariuszy dla wielu platform. Side-by-side umożliwia wdrażanie nowych wersji platformy .NET Core bez przerywania innych aplikacji. Jeśli dowiesz się, jak przenieść swoją aplikację do platformy .NET Core, obsługa wielu platform, jest to zalecane docelowego. 
* . [NET Standard](../../standard/net-standard.md): Obejmuje .NET Standard interfejsami API dostępnymi na wszystkich implementacji .NET. Jeśli celem jest zapewnienie biblioteki do uruchamiania na platformie .NET wszystkich obsługiwanych platform, jest to zalecane docelowego.  
* [ASP.NET Core](/aspnet/core): Nowoczesnej sieci web — platforma oparta na module .NET Core. Jeśli dowiesz się, jak przenieść swoją aplikację sieci web do obsługi wielu platform .NET Core, jest to zalecane docelowego.
* .NET core + [rozszerzenia platformy](../../core/porting/windows-compat-pack.md): Obejmuje podstawowe interfejsy API platformy .NET poza pakietu zgodności Windows udostępnia wiele technologii dostępnych w .NET Framework. Jest to zalecane celu przenoszenie aplikacji z .NET Framework i .NET Core w Windows.
* .NET standard + [rozszerzenia platformy](../../core/porting/windows-compat-pack.md): Obejmuje standardowych interfejsów API .NET oprócz pakietu zgodności Windows udostępnia wiele technologii dostępnych w .NET Framework. Jest to zalecane docelowej eksportowaniu biblioteki z .NET Framework i .NET Core w Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Jak używać narzędzia .NET Portability Analyzer

Aby rozpocząć korzystanie z narzędzia .NET Portability Analyzer w programie Visual Studio, należy najpierw pobrać i zainstalować rozszerzenie z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Działa w programie Visual Studio 2017 i nowszych wersjach. Można go skonfigurować w programie Visual Studio za pośrednictwem **analizy** > **Portability Analyzer ustawienia** i wybieranie platform docelowych, czyli platform/wersji .NET, które ma zostać oceniona porównanie z platform/version bieżący zestaw został utworzony za pomocą luki przenoszenia.

![Zrzut ekranu przenośności](./media/portability-analyzer/portability-screenshot.png)

Możesz również użyć ApiPort konsoli aplikacji, pobierz go z [repozytorium ApiPort](http://aka.ms/apiportdownload). Możesz użyć `listTargets` polecenia opcję, aby wyświetlić listę dostępnych docelowego, a następnie wybierz platform docelowych, określając `-t` lub `--target` opcja polecenia. 

### <a name="analyze-portability"></a>Analizowanie przenośności
Aby analizować cały projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **analizowanie przenośności zestawu**. W przeciwnym razie przejdź do **analizy** menu, a następnie wybierz **analizowanie przenośności zestawu**. W tym miejscu wybierz plik wykonywalny projektu lub biblioteki DLL.

![Analizator przenośności w Eksploratorze rozwiązań](./media/portability-analyzer/portability-solution-explorer.png)

Można również użyć [aplikacja konsolowa ApiPort](https://aka.ms/apiportdownload). 

* Wpisz następujące polecenie, aby analizować bieżący katalog: `ApiPort.exe analyze -f .`
* Aby analizować określonych listą plików .dll, wpisz następujące polecenie: `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Uruchom `ApiPort.exe -?` umożliwiające uzyskanie szerszej pomocy

Zaleca się, że zawrzesz wszystkie powiązane exe i dll pliki, które należy do użytkownika i do portu, a następnie wykluczyć pliki, które zależy aplikacja, ale nie jest własnością i portu, nie można. Zapewni to najbardziej istotnych przenośność raportu.  

### <a name="view-and-interpret-portability-result"></a>Wyświetlanie i interpretacji wyników przenośności

Raport uwzględnia tylko interfejsy API, które nie są obsługiwane przez platformę docelową. Po uruchomieniu analizy w programie Visual Studio, zobaczysz, że linku do pliku raportu .NET Portability pojawia się. Jeśli użyto [aplikacja konsolowa ApiPort](https://aka.ms/apiportdownload), .NET Portability raport jest zapisywany jako plik w formacie wskazana. Wartość domyślna to w pliku programu Excel (*xlsx*) w bieżącym katalogu.

#### <a name="portability-summary"></a>Podsumowanie przenośności 

![Podsumowanie przenośności](./media/portability-analyzer/portabilitysummary.png)

Sekcja Podsumowanie przenośność raportu zawiera wartość procentową przenośność dla każdego zestawu uwzględnione w procesie. W poprzednim przykładzie użyto 89.74% interfejsów API programu .NET Framework w `ConsoleAppFramework` aplikacji są dostępne w .NET Core i rozszerzenia platformy w wersji 2.2. Po uruchomieniu narzędzia .NET Portability Analyzer względem wielu zestawów każdego zestawu mają wiersz w raporcie Podsumowanie przenoszenia.

#### <a name="details"></a>Szczegóły

![Szczegóły dotyczące przenośności](./media/portability-analyzer/portabilitydetails.png)

Sekcja szczegółów raportu zawiera interfejsy API brakuje jednego z platform docelowych. 

- Docelowy typ: Typ ma Brak interfejsu API platformy docelowej 
- Docelowy element członkowski: Brak metody platformy docelowej 
- Nazwa zestawu: zestaw .NET Framework, który Brak interfejsu API, który znajduje się w. 
- Każdy z wybranych platformach docelowych jest jedną kolumnę, takich jak ".NET Core": Wartość "Nie jest obsługiwane" oznacza, że interfejs API nie jest obsługiwana na tej platformie docelowej. 
- Zaleca się zmiany: zaleca się interfejsu API lub technologii, aby zmienić. Obecnie to pole jest puste lub nieaktualna dla wielu interfejsów API. Z powodu dużej liczby interfejsów API mamy dużym wyzwaniem, aby utrzymać ją w. Czekamy na alternatywne rozwiązania zawierają informacje przydatne dla klientów.

#### <a name="missing-assemblies"></a>Brak zestawów

![Szczegóły dotyczące przenośności](./media/portability-analyzer/missingassemblies.png)

W raporcie może się okazać sekcji Brak zestawów. Jej informuje, że ta lista zestawów odwołują się zestawy przeanalizowany i nie zostały przeanalizowane. Jeśli jest to zespół, którego jesteś właścicielem, dołączyć analizator przenośności interfejsu Api, uruchamianie, dzięki czemu można uzyskać interfejsu API poziomu przenośność szczegółowy raport dla niego. Jeśli istnieje biblioteki innej firmy, szuka jeśli mają nowszej wersji, obsługa docelowej platformy. Jeśli tak, należy wziąć pod uwagę przeniesienie do nowszej wersji. Po pewnym czasie można oczekiwać, że ta lista zawiera wszystkie zestawów innych firm, które Twoja aplikacja jest zależna od i potwierdza, że wersja docelowej platformy obsługi.  

Aby uzyskać więcej informacji dotyczących narzędzia .NET Portability Analyzer, odwiedź stronę [dokumentację GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i [krótki Przyjrzyj się narzędzia .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) wideo Channel 9.
