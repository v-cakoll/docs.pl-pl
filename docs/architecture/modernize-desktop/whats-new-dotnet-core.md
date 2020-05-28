---
title: Co nowego w programie .NET Core for Desktop?
description: Dowiedz się więcej na temat platformy .NET Core, różnic między platformą .NET Core i .NET Framework oraz nowych funkcji, które zostały dodane.
ms.date: 05/12/2020
ms.openlocfilehash: b4fc0cb2841fe13b000223aefc5eaf63bd911994
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144264"
---
# <a name="whats-new-with-net-core-for-desktop"></a>Co nowego w programie .NET Core for Desktop?

Począwszy od platformy .NET Core 3,0, .NET Core obsługuje Windows Forms i WPF. Teraz możesz wybrać między .NET Framework i .NET Core dla aplikacji klasycznych. W tym rozdziale opisano, co to jest .NET Core i jakie są korzyści dla aplikacji klasycznych.

## <a name="the-motivation-behind-net-core"></a>Motywacja pod kątem platformy .NET Core

Od momentu jego uruchomienia w 2002, .NET Framework został rozwijający przez lata do obsługi wielu technologii, takich jak Windows Forms, ASP.NET, Entity Framework, Sklep Windows i wiele innych. Wszystkie z nich różnią się charakterem. W związku z tym firma Microsoft zbliża się do tego ewolucji, pobierając części .NET Framework i tworząc inny stos aplikacji dla każdej technologii. Dzięki temu możliwości programistyczne mogą być dostosowane do potrzeb określonego stosu, co maksymalizuje potencjał każdej platformy. Prowadzi to do fragmentacji wersji .NET Framework, które są obsługiwane przez różne niezależne zespoły. Wszystkie te stosy mają wspólną strukturę obejmującą model aplikacji, strukturę i środowisko uruchomieniowe, ale różnią się w implementacji każdej z tych części.

Jeśli masz tylko jedną z tych platform, możesz użyć tego modelu. Jednak w wielu przypadkach może być potrzebna więcej niż jedna platforma docelowa w tym samym rozwiązaniu. Na przykład aplikacja może mieć część administratora pulpitu, czyli witrynę sieci Web, która udostępnia logikę zaplecza działającą na serwerze, a nawet klienta mobilnego. W takim przypadku konieczne jest ujednolicone środowisko kodowania, które może obejmować wszystkie te pionowe środowiska .NET.

Po wydaniu systemu Windows 8 podaliśmy koncepcję bibliotek klas przenośnych (PCLs). Początkowo .NET Framework został zaprojektowany wokół założeń, że zawsze będzie ona wdrażana jako jedna jednostka [, więc nie](https://wikipedia.org/wiki/Decomposition_(computer_science)) ma obaw. Aby sprostać problemom z współdzieleniem kodu między pionowymi, siła jazdy polega na sposobie refaktoryzacji struktury. Pomysłem jest zapewnienie dobrze przeczynnika powierzchni interfejsu API. Kontrakty są po prostu zestawami, które są kompilowane i są zaprojektowane z odpowiednim czynnikiem do wzięcia pod uwagę zależności między nimi.

Prowadzi to do uzyskania informacji o różnicach interfejsu API między pionowymi na poziomie zestawu, a nie na poziomie poszczególnych interfejsów API. Ten aspekt włącza środowisko biblioteki klas, które może być ukierunkowane na wiele pionowych, znanych również jako przenośne biblioteki klas.

![Historia wydania .NET Framework](./media/whats-new-dotnet-core/release-history.png)

Dzięki funkcji PCL środowisko projektowania jest ujednolicone w pionie na podstawie kształtu interfejsu API. Należy również rozważyć, aby utworzyć biblioteki działające na różnych pionowych. Jednak istnieje doskonałe wyzwanie: interfejsy API są przenośne tylko wtedy, gdy implementacja została przeniesiona do przodu między wszystkimi pionowymi.

Lepszym rozwiązaniem jest ujednolicenie implementacji w pionie, zapewniając spójną implementację zamiast widoku dobrze. Jest to znacznie prostsze dla każdego zespołu, który jest właścicielem określonego składnika, aby myśleć o tym, jak ich interfejsy API działają we wszystkich pionowych, niż próba wstecznego zapewnienia spójnego stosu interfejsów API na górze. Jest to miejsce, w którym .NET Standard. Szczegółowe informacje znajdują się w następnej sekcji.

Inne duże wyzwanie należy wykonać w celu wdrożenia .NET Framework. .NET Framework jest strukturą dla całego komputera. Wszelkie zmiany wprowadzone do niego wpływają na wszystkie aplikacje, na których jest ona zależna. Chociaż ten model wdrażania ma wiele korzyści, takich jak zmniejszenie miejsca na dysku i scentralizowany dostęp do usług, przedstawia pewne pułapek.

Aby zacząć od, trudno jest, aby deweloperzy aplikacji korzystali z niedawno wydanej struktury. Muszą one być zależne od najnowszego systemu operacyjnego lub udostępniać Instalatora aplikacji, który instaluje .NET Framework wraz z aplikacją. Jeśli jesteś deweloperem sieci Web, możesz nie mieć nawet tej opcji, ponieważ dział IT ustala wersję obsługiwaną przez serwer.

Nawet jeśli chcesz przejść przez problemy z podawaniem Instalatorowi łańcucha w konfiguracji .NET Framework, może się okazać, że uaktualnienie .NET Framework może spowodować przerwanie innych aplikacji.

Pomimo wysiłków związanych z zapewnianiem zgodności z poprzednimi wersjami platformy istnieją zgodne zmiany, które mogą spowodować przerwanie działania aplikacji. Na przykład dodanie interfejsu do istniejącego typu może zmienić sposób serializacji tego typu i spowodować problemy z przerywaniem w zależności od istniejącego kodu. Ze względu na to, że platforma .NET Framework jest ogromna, walka z tymi scenariuszami przerywania spowalnia tempo innowacji w .NET Framework.

Aby rozwiązać wszystkie te problemy, firma Microsoft opracowała platformę .NET Core w celu podejścia do ewolucji platformy .NET.

## <a name="introduction-to-net-core"></a>Wprowadzenie do platformy .NET Core

.NET Core to ewolucja technologii .NET firmy Microsoft do modularnej, wieloplatformowej, typu open source i gotowej do użycia w chmurze platformy. Jest ona uruchamiana w systemach Windows, macOS i Linux z planami do uruchamiania na architekturach opartych na architekturze ARM, takich jak Android i IoT.

Celem platformy .NET Core jest zapewnienie ujednoliconej platformy dla wszystkich typów aplikacji, w tym aplikacji dla systemu Windows, międzyplatformowego i mobilnego. [.NET Standard](../../standard/net-standard.md) umożliwia to dzięki udostępnieniu współużytkowanych interfejsów API, które są wymagane przez każdy model aplikacji oraz z wykluczeniem wszystkich interfejsów API specyficznych dla modelu aplikacji.

Ta struktura zapewnia aplikacjom wiele korzyści w zakresie wydajności i wydajności, upraszczając pakowanie i wdrażanie na różnych obsługiwanych platformach.

Zalety platformy .NET Core pochodzą z następujących trzech cech:

- Na **wielu platformach:** Umożliwia wykonywanie aplikacji na różnych platformach (Windows, macOS i Linux).
- **Open Source:** platforma .NET Core jest platformą Open Source i jest dostępna za poorednictwem usługi GitHub, sprzyjania przejrzystości i wkładów społecznościowych.
- **Obsługiwane:** Firma Microsoft oficjalnie obsługuje platformę .NET Core.

Począwszy od platformy .NET Core 3,0, oprócz istniejącej obsługi sieci Web i chmury, obsługiwane są również domeny dla komputerów stacjonarnych, IoT i AI. Celem tej struktury jest imponujące: aby kierować każdy typ rozwoju platformy .NET i przyszłości. Firma Microsoft planuje wykonać tę wizję na platformie .NET 5 na końcu 2020. Nazwa "Core" została usunięta, aby wzmocnić swoją unikatowość w środowisku .NET World.

![Wszystkie domeny programu .NET 5](./media/whats-new-dotnet-core/all-domains-of-dotnet5.png)

## <a name="net-framework-vs-net-core"></a>.NET Framework a .NET Core

Teraz, gdy zrozumiesz znaczenie platformy .NET Core w ramach strategii firmy Microsoft dla platformy .NET, możesz zastanawiać się, co się dzieje z .NET Framework. Możesz zadawać pytania, takie jak: czy musisz zrezygnować? Czy będzie on znikał? Jakie są moje wybory, aby przeprowadzić modernizację aplikacji, które znajdują się w .NET Framework?

W 2019 wydano ostatnią wersję **.NET Framework – 4,8** . Uwzględniono trzy główne ulepszenia aplikacji klasycznych:

- **Nowoczesne przeglądarki i formanty multimedialne**: obecnie aplikacje klasyczne platformy .NET używają programu Internet Explorer i systemu Windows Media Player do wyświetlania kodu HTML i odtwarzania plików multimedialnych. Ponieważ te starsze kontrolki nie wyświetlają najnowszego kodu HTML lub nie odtwarzają najnowszych plików multimedialnych, dodano nowe kontrolki korzystające z programu Microsoft Edge i nowszych graczy multimedialnych, które obsługują najnowsze standardy.
- **Dostęp do kontrolek platformy UWP**: platformy UWP zawiera nowe kontrolki, które korzystają z najnowszych funkcji systemu Windows i wyświetlania dotykowego. Nie musisz ponownie pisać aplikacji, aby korzystać z tych nowych funkcji i kontrolek, dzięki czemu możesz korzystać z nowych funkcji w istniejącym środowisku WPF lub Windows Forms kodzie.
- **Ulepszenia o wysokiej rozdzielczości DPI**: rozdzielczość wyświetlania jest zwiększana do 4 k i rozdzielczości 8K. Dlatego .NET Framework 4,8 dodaje nowe udoskonalenia HDPI, aby upewnić się, że istniejące Windows Forms i aplikacje WPF mogą wyglądać doskonale na nowych ekranach.

Ponieważ .NET Framework jest zainstalowana na milionach maszyn, firma Microsoft będzie nadal ją obsługiwać, ale nie będzie dodawać nowych funkcji.

.NET Core to platforma typu "open source", międzyplatformowa i szybka wersja platformy .NET. Ze względu na swój charakter równoległy może wprowadzić zmiany bez obaw związanych z uszkodzeniem aplikacji. Oznacza to, że platforma .NET Core uzyska nowe interfejsy API i funkcje językowe w czasie, który .NET Framework nie będzie. Ponadto program **.NET Core** ma już funkcje, które były niemożliwe dla .NET Framework, na przykład:

- **Równoległe wersje platformy .NET obsługujące Windows Forms i WPF**: rozwiązanie to rozwiązuje problem z efektami ubocznymi podczas aktualizowania wersji platformy maszyny. Na tym samym komputerze można zainstalować wiele wersji platformy .NET Core, a każda aplikacja określa wersję platformy .NET Core, która ma być używana. Jeszcze więcej, teraz możesz opracowywać i uruchamiać Windows Forms i WPF na platformie .NET Core.
- **Osadź platformę .NET bezpośrednio w aplikacji**: program .NET Core można wdrożyć w ramach pakietu aplikacji. Dzięki temu można korzystać z najnowszej wersji, funkcji i interfejsów API bez konieczności oczekiwania na zainstalowanie określonej wersji na komputerze.
- **Korzystanie z funkcji platformy .NET Core**: .NET Core to szybka, przenoszona wersja platformy .NET typu open source. Jego charakter równoległy umożliwia szybkie wprowadzenie nowych innowacyjnych interfejsów API i udoskonaleń bibliotek klas podstawowych (BCL) bez ryzyka naruszenia zgodności. Teraz Windows Forms i aplikacje WPF mogą korzystać z najnowszych funkcji platformy .NET Core, które obejmują również bardziej podstawowe poprawki dotyczące wydajności środowiska uruchomieniowego, wysokiej rozdzielczości DPI i tak dalej.

Istotną częścią planu dla firmy Microsoft było ułatwienie deweloperom przenoszenia aplikacji do platformy .NET Core i w przyszłości do programu .NET 5. Jeśli jednak masz istniejące .NET Framework aplikacje, nie należy naciskać się na przejście do platformy .NET Core. .NET Framework będą w pełni obsługiwane i zawsze będą częścią systemu Windows. Jeśli jednak chcesz użyć najnowszych funkcji języka i interfejsów API w przyszłości, musisz przenieść aplikacje do programu .NET Core.

W przypadku nowych aplikacji klasycznych zalecamy rozpoczęcie od platformy .NET Core. Jest ona lekkim i międzyplatformowym, działa obok siebie, ma wysoką wydajność i idealnie napasuje do kontenerów i architektury mikrousług.

![Możesz aktualizować aplikacje .NET Framework przy użyciu najnowszej wersji .NET Framework lub portów aplikacji do platformy .NET Core](./media/whats-new-dotnet-core/framework-vs-core.png)

## <a name="net-standard-vs-pcl"></a>.NET Standard a PCL

[.NET Standard](../../standard/net-standard.md) to formalna Specyfikacja interfejsów API platformy .NET, które mają być dostępne we wszystkich implementacjach platformy .NET. Uzasadnienie związane z .NET Standardem jest ustanowienie większej jednorodności w ekosystemie platformy .NET. .NET Standard to specyfikacja interfejsów API platformy .NET, które tworzą jednolity zestaw umów do kompilowania kodu. Te kontrakty są implementowane w każdej wersji platformy .NET, co pozwala na przenoszenie różnych implementacji platformy .NET.

.NET Standard włącza następujące kluczowe scenariusze:

- Definiuje jednolity zestaw interfejsów API bibliotek klas podstawowych dla wszystkich implementacji platformy .NET do implementacji, niezależnie od obciążenia.
- Umożliwia deweloperom tworzenie przenośnych bibliotek, których można użyć w implementacjach platformy .NET, przy użyciu tego samego zestawu interfejsów API.

.NET Standard to ewolucja PCLs, a na poniższej liście przedstawiono podstawowe różnice między .NET Standard i PCLs:

- .NET Standard to zbiór nadzorowanych interfejsów API, które zostały pobrane przez firmę Microsoft. Nie PCLs.
- Interfejsy API, które zawiera interfejs PCL, są zależne od platform wybranych podczas tworzenia. Dzięki temu można tylko udostępniać PCL dla konkretnych wybranych obiektów docelowych.
- .NET Standard jest platformą niezależny od, można uruchamiać w dowolnym miejscu, w systemach Windows, macOS, Linux i tak dalej.
- PCLs może również uruchamiać wiele platform, ale mają one bardziej ograniczone zasięg. PCLs może dotyczyć tylko ograniczonego zestawu Platform.

## <a name="new-desktop-features-in-net-core"></a>Nowe funkcje pulpitu w programie .NET Core

### <a name="support-for-windows-forms-and-wpf"></a>Obsługa Windows Forms i WPF

Windows Forms i WPF są częścią platformy .NET Core od wersji 3,0. Obie struktury prezentacji są przeznaczone tylko dla systemu Windows, więc nie są one na wielu platformach. Możesz traktować platformę WPF jako rozbudowaną warstwę za pośrednictwem programu DirectX i Windows Forms jako cieńszą warstwę za pośrednictwem interfejsu GDI+. WPF i Windows Forms to doskonałe zadanie ujawniania i wykonywania większości funkcji aplikacji klasycznych w systemie Windows. Dlatego Windows Forms i WPF są dostępne dla platform .NET Core i .NET Framework. Teraz można uruchamiać nowe aplikacje klasyczne przeznaczone dla platformy .NET Core i migrować istniejące z .NET Framework do programu .NET Core.

Nowa wersja .NET Standard w wersji 2,1 została wydana w tym samym czasie co program .NET Core 3,0. Zgodnie z oczekiwaniami wersje programu .NET Core 3. x obsługują .NET Standard 2,1 i wcześniejszych wersjach.

Należy również zwrócić uwagę, że zarówno implementacja Windows Forms, jak i WPF dla platformy .NET Core to "open source".

### <a name="xaml-islands"></a>Wyspy XAML

[Wyspy XAML](/windows/apps/desktop/modernize/xaml-islands) to zestaw składników przeznaczonych dla deweloperów do używania nowych kontrolek systemu Windows 10 (platformy UWP w kontrolkach XAML) w ich bieżącej platformie WPF, Windows Forms i natywnych aplikacjach Win32 (takich jak MFC). W dowolnym miejscu w aplikacjach Win32 można korzystać z "wysp" platformy UWPowych kontrolek XAML.

Te wyspy XAML są możliwe, ponieważ system Windows 10 w wersji 1903 wprowadza zestaw interfejsów API, które umożliwiają hostowanie zawartości XAML platformy UWP w systemie Win32 przy użyciu programów obsługi systemu Windows (HWnd). Należy zauważyć, że tylko aplikacje działające w systemie Windows 10 1903 i nowszych mogą korzystać z wysp XAML.

Aby ułatwić tworzenie wysp XAML dla deweloperów Windows Forms i WPF, zestaw narzędzi Community dla systemu Windows wprowadza zestaw otok platformy .NET w kilku pakietach NuGet. Te otoki są formantami opakowanymi i hostingu:

- Kontrolki w [widokach WebView](/windows/communitytoolkit/controls/wpf-winforms/webview), [WebViewCompatible](/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible), [InkCanvas](/windows/communitytoolkit/controls/wpf-winforms/inkcanvas), [MediaPlayerElement](/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement)i [MapControl](/windows/communitytoolkit/controls/wpf-winforms/mapcontrol) zawijają Niektóre platformy uwpe kontrolki XAML do formantów Windows Forms lub WPF, ukrywając platformy UWP koncepcje dla tych deweloperów.
- Kontrolka [WindowsXamlHost](/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) dla Windows Forms i WPF umożliwia innym nieopakowanym platformy UWP kontrolek XAML i formantów niestandardowych na wyspa XAML.

### <a name="access-to-all-windows-10-apis"></a>Dostęp do wszystkich interfejsów API systemu Windows 10

System Windows 10 ma doskonały dostęp do interfejsu API dla deweloperów. Te interfejsy API zapewniają dostęp do różnorodnych funkcji, takich jak uwierzytelnianie, Bluetooth, terminy i kontakty. Teraz te interfejsy API są udostępniane za pomocą platformy .NET Core i umożliwiają deweloperom systemu Windows tworzenie zaawansowanych aplikacji dla komputerów stacjonarnych wykorzystujących funkcje dostępne w systemie Windows 10.

### <a name="side-by-side-support-and-self-contained-exes"></a>Obsługa Side-by-Side i samodzielna exe

Model wdrażania platformy .NET Core jest jednym z największych korzyści, które są używane przez deweloperów klasycznych dla systemu Windows przy użyciu platformy .NET Core. Możliwość globalnej instalacji programu .NET Core zapewnia wiele takich samych centralnych zalet instalacji i obsługi .NET Framework, ale nie wymaga aktualizacji w miejscu.

Po wydaniu nowej wersji platformy .NET Core można w razie potrzeby zaktualizować każdą aplikację na maszynie bez obaw o wpływ na inne aplikacje. Nowe wersje programu .NET Core są instalowane w ich własnych katalogach i istnieją "obok siebie".

W przypadku konieczności wdrożenia z izolacją można wdrożyć platformę .NET Core przy użyciu aplikacji. Platforma .NET Core będzie powiązać aplikację z środowiskiem uruchomieniowym platformy .NET Core jako pojedynczym plikiem wykonywalnym.

Te opcje wdrażania zostały zażądane przez deweloperów przez dość długi czas, ale trudno było osiągnąć przy użyciu .NET Framework. Architektura modularna używana przez platformę .NET Core zapewnia te elastyczne opcje wdrażania.

### <a name="performance"></a>Wydajność

Od momentu jego uruchomienia, który jest przeznaczony dla obciążeń sieci Web i w chmurze, platforma .NET Core ma wydajność podłączona do swojej DNA. Kod po stronie serwera musi być wystarczająco wydajny, aby można było zrealizować scenariusze o wysokiej współbieżności i wyniki platformy .NET Core już dzisiaj jako platforma sieci Web najlepszej wydajności na rynku.

W przypadku korzystania z platformy .NET Core do tworzenia nowej generacji aplikacji klasycznych można wykorzystać te ulepszenia wydajności.

## <a name="benefits-of-open-source"></a>Zalety platformy Open Source

Zaledwie kilka wyrazów dotyczących środowiska .NET Core będącego źródłem Open Source. Tworzenie wieloplatformowego stosu to coś złożonego, które wymaga interakcji wyspecjalizowanych zespołów na każdej z platform dostosowanych. Ten nakład pracy wymaga dużej współpracy od firmy Microsoft i spoza niej. Dzięki wykorzystaniu usługi IT Open Source i w związku z tym otwartym do współpracy publicznej można uzyskać ostateczny styl programowania Agile, aby podnieść poziom jakości, ponieważ problemy są wykrywane przez ogromną i aktywną społeczność deweloperów.

Jest to kluczowy współczynnik sukcesu platformy .NET Core, który będzie kontynuował przyspieszenie wcześniej wymienionego planu: aby być pojedynczą platformą .NET, którą każdy deweloper będzie musiał utworzyć dowolną aplikację.

>[!div class="step-by-step"]
>[Poprzedni](why-modern-applications.md) 
> [Dalej](migrate-modern-applications.md)
