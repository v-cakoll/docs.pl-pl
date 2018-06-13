---
title: Eksportowanie do platformy .NET Core - bibliotek
description: Informacje o porcie projektów bibliotek z programu .NET Framework do platformy .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.openlocfilehash: 88513eaee35a82d6424fc2218f8cbbe635a8e02c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218361"
---
# <a name="porting-to-net-core---libraries"></a>Eksportowanie do platformy .NET Core - bibliotek

W tym artykule omówiono przenoszenia biblioteki kodu platformy .NET Core wykonywania wielu platform.

## <a name="prerequisites"></a>Wymagania wstępne

W tym artykule przyjęto założenie, że możesz:

- Program Visual Studio 2017 lub nowszej.
  - Oprogramowanie .NET core nie jest obsługiwane we wcześniejszych wersjach programu Visual Studio
- Zrozumienie [zalecane eksportowanie procesu](index.md).
- Zostały rozwiązane problemy z [zależności innych firm](third-party-deps.md).

Należy również zapoznać się z zawartością w następujących tematach:

[.NET standard](~/docs/standard/net-standard.md)   
W tym temacie opisano formalną specyfikację interfejsów API architektury .NET, które mają być dostępne na wszystkich implementacji .NET.

[Pakiety, Metapackages i platform](~/docs/core/packages.md)   
W tym artykule omówiono sposób definiuje oprogramowanie .NET Core i korzysta z pakietów i obsługi pakietów kodu uruchomionego na wiele implementacji .NET.

[Tworzenie bibliotek z wielu narzędzi platformy](~/docs/core/tutorials/libraries.md)   
W tym temacie wyjaśniono, jak napisać biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia i platform.

[Dodatki do *csproj* format dla platformy .NET Core](~/docs/core/tools/csproj.md)   
W tym artykule opisano zmiany, które zostały dodane do pliku projektu w ramach przejścia *csproj* i MSBuild.

[Eksportowanie do platformy .NET Core - analizowanie zależności innych firm](~/docs/core/porting/third-party-deps.md)   
W tym temacie omówiono przenośność zależności innych firm i co należy zrobić, gdy zależność pakietu NuGet nie działa na .NET Core.

## <a name="net-framework-technologies-unavailable-on-net-core"></a>Niedostępna na .NET Core technologii .NET framework

Kilka technologie dostępne do bibliotek .NET Framework nie są dostępne do użycia z programem .NET Core, takich jak domen aplikacji, usług zdalnych zabezpieczeń dostępu kodu (CAS) i przezroczystość zabezpieczeń. Jeśli bibliotek zależą od tego, co najmniej jeden z tych technologii, należy wziąć pod uwagę alternatywnych metod opisanych poniżej. Aby uzyskać więcej informacji o zgodności interfejsu API utrzymuje zespołu CoreFX [listy podziałów zmiany zachowania/compat i przestarzałe/legacy interfejsów API](https://github.com/dotnet/corefx/wiki/ApiCompat) w witrynie GitHub.

Tak, ponieważ nie jest obecnie zaimplementowana interfejsu API lub technologii nie oznacza, że celowo ma nieobsługiwany. Problem w pliku [problemy z repozytorium dotnet/corefx](https://github.com/dotnet/corefx/issues) w witrynie GitHub, aby poprosić o określonych interfejsów API i technologii. [Eksportowanie żądań w problemy](https://github.com/dotnet/corefx/labels/port-to-core) są oznaczone ikoną z `port-to-core` etykiety.

### <a name="appdomains"></a>Domen aplikacji

Elementami AppDomain izolowania aplikacji od siebie nawzajem. Domen wymagają obsługi środowiska uruchomieniowego i zazwyczaj są stosunkowo drogie. Nie jest zaimplementowana w .NET Core. Nie planujemy dodanie tej funkcji w przyszłości. Kod izolacji, zaleca się osobne procesy lub przy użyciu kontenery alternatywnym. Dynamiczne ładowanie zestawów, zaleca się nowe <xref:System.Runtime.Loader.AssemblyLoadContext> klasy.

Ułatwia migrację kodu z .NET Framework, firma Microsoft już widoczne niektóre <xref:System.AppDomain> powierzchni interfejsu API w .NET Core. Niektóre z interfejsu API działa normalnie (na przykład <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), nic nie rób niektóre elementy członkowskie (na przykład <xref:System.AppDomain.SetCachePath%2A>), i niektóre z nich <xref:System.PlatformNotSupportedException> (na przykład <xref:System.AppDomain.CreateDomain%2A>). Sprawdź typy używane przed [ `System.AppDomain` źródło odwołania](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) w [repozytorium GitHub dotnet/corefx](https://github.com/dotnet/corefx) zapewnienie Wybierz gałąź zgodna z wersją zaimplementowany.

### <a name="remoting"></a>Usługi zdalne

.NET remoting został zidentyfikowany jako architektura powodować problemy. Służy do komunikacji między AppDomain nie jest już obsługiwana. Obsługa środowiska uruchomieniowego, która jest kosztowna zachować wymaga również, usług zdalnych. Z tego względu funkcji zdalnych .NET nie jest obsługiwana na .NET Core, a nie planujemy dodanie obsługi dla niego w przyszłości.

Do komunikacji między procesami, należy wziąć pod uwagę mechanizmy komunikacji międzyprocesowej (IPC) zamiast z usługami zdalnymi, takich jak <xref:System.IO.Pipes> lub <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> klasy.

Na komputerach zamiast za pomocą rozwiązania opartego na sieci. Najlepiej używać protokołu niskiego obciążenia zwykłego tekstu, takich jak HTTP. [Serwera sieci web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), używane przez program ASP.NET Core, serwer sieci web jest opcją w tym miejscu. Należy również rozważyć przy użyciu <xref:System.Net.Sockets> dla scenariuszy opartych na sieci, między komputerami. Aby wyświetlić więcej opcji, zobacz [otwarcia projektów Developer źródła .NET: wiadomości](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

### <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

Sandboxing, który jest zależne od środowiska uruchomieniowego lub platformę, aby ograniczyć zasoby zarządzaną aplikację lub biblioteki używa lub jest uruchamiana, [nie jest obsługiwany w programie .NET Framework](~/docs/framework/misc/code-access-security.md) i dlatego też nie jest obsługiwane na .NET Core. Mamy nadzieję, że istnieją zbyt wiele przypadków w .NET Framework i środowiska uruchomieniowego gdzie podniesienie uprawnień występuje, aby kontynuować, traktując urzędów certyfikacji jako granic zabezpieczeń. Ponadto urzędy certyfikacji sprawia, że implementacja jest bardziej skomplikowany i często ma wpływ poprawności wydajności dla aplikacji, które nie będą z niego korzystać.

Użyj granic zabezpieczeń dostarczane przez system operacyjny, takich jak konta użytkowników, kontenery i wirtualizacji dla uruchomionych procesów o najmniejszej zestaw uprawnień.

### <a name="security-transparency"></a>Przezroczystość zabezpieczeń

Podobnie jak urzędy certyfikacji, przezroczystość zabezpieczeń umożliwia oddzielenie kodu w trybie piaskownicy od kodu krytycznego dla zabezpieczeń w sposób deklaratywne, ale jest [nie jest już obsługiwany jako granic zabezpieczeń](~/docs/framework/misc/security-transparent-code.md). Ta funkcja jest silnie używany przez program Silverlight. 

Użyj granic zabezpieczeń dostarczane przez system operacyjny, takich jak konta użytkowników, kontenery i wirtualizacji dla uruchomionych procesów o najmniejszej zestaw uprawnień.

### <a name="globaljson"></a>global.json

*Global.json* plik jest opcjonalny plik, który umożliwia ustawienie wersji narzędzi platformy .NET Core projektu. Jeśli używasz co noc kompilacje .NET Core i chcesz określić określoną wersję zestawu SDK, określ wersję z *global.json* pliku. Zazwyczaj znajduje się on w bieżącym katalogu roboczym lub jeden z jego katalogi nadrzędne. 

```json
{
  "sdk": {
    "version": "2.1.0-preview1-006491"
  }
}
```

## <a name="converting-a-pcl-project"></a>Konwertowanie projektu PCL

Elementy docelowe projektu PCL można przekonwertować na .NET Standard przez ładowanie biblioteki w programie Visual Studio 2017 i wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy w pliku projektu i wybierz **właściwości**.
1. W obszarze **biblioteki**, wybierz pozycję **docelowej platformy .NET Standard**.

Jeśli pakiety obsługuje NuGet 3.0, projekt retargets do .NET Standard.

Jeśli pakiety nie obsługuje NuGet 3.0, pojawi się okno dialogowe z programu Visual Studio, monit o odinstalowanie bieżącej pakietów. Jeśli zostanie wyświetlony tego komunikatu, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy projekt, wybierz **Zarządzaj pakietami NuGet**.
1. Zanotuj pakietów projektu.
1. Odinstalowania pakietów jeden po drugim.
1. Może być konieczne ponowne uruchomienie programu Visual Studio, aby ukończyć proces dezinstalacji. Jeśli tak, **Uruchom ponownie** przycisk są prezentowane w **Menedżera pakietów NuGet** okna.
1. Ponowne załadowanie projektu, dotyczy .NET Standard. Dodawanie pakietów, które są wymagane do odinstalowania.

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>Kod .NET Framework .NET Framework 4.6.2 przekierowania

Jeśli kod nie jest przeznaczony dla platformy .NET Framework 4.6.2, zaleca się zmiany celu .NET Framework 4.6.2. Zapewnia to dostępność najnowszych rozwiązań alternatywnych interfejsu API w przypadkach, gdy .NET Standard nie obsługuje istniejących interfejsów API.

Dla każdego z projektów programu Visual Studio do portu wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie Właściwości.
1. W **platformy docelowej** listy rozwijanej wybierz **.NET Framework 4.6.2**.
1. Skompiluj ponownie swoje projekty.

Ponieważ projekty są teraz celem .NET Framework 4.6.2, należy użyć tej wersji programu .NET Framework jako podstawowym przy eksportowaniu kodu.

## <a name="determining-the-portability-of-your-code"></a>Określanie przenośność kodu

Następnym krokiem jest do uruchamiania analizatora przenośność interfejsu API (ApiPort), aby wygenerować raport przenośność do analizy.

Upewnij się, że rozumiesz [interfejsu API przenośność Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) i sposób generowania raportów przenośność dla przeznaczonych dla platformy .NET Core. Jak wykonać w tym prawdopodobnie w zależności od smaków osobistych i potrzeb użytkowników. Jaki sposób jest kilka różnych metod. Może się okazać się mieszanie kroki z tych metod w zależności od struktury kodu.

### <a name="dealing-primarily-with-the-compiler"></a>Przede wszystkim zajmujących kompilatora

Ta metoda może być najlepsze dla małych projektów lub projektów, które nie używają wielu interfejsów API Framework .NET. Podejście jest prosty:

1. Opcjonalnie możesz uruchomić ApiPort w projekcie. Po uruchomieniu ApiPort poznanie raportu na problemy, które będą potrzebne do adresu.
1. Skopiuj cały kod nad do nowego projektu platformy .NET Core.
1. Podczas odwoływania się do raportu przenośność (jeśli generowany), należy rozwiązać błędy kompilatora do momentu pełni kompiluje projektu.

Mimo że ta metoda jest niestrukturalnych, podejście fokus kodu często prowadzi do szybkie rozwiązywanie problemów i może być dobrym rozwiązaniem dla mniejszych projektów lub biblioteki. Projekt, który zawiera tylko modeli danych może być idealne kandydatem do tej metody.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Pozostaje w programie .NET Framework, dopóki zostaną rozwiązane problemy związane z przenośnością

Takie podejście może być najlepiej, jeśli wolisz kod, który kompiluje w trakcie całego procesu. Podejście jest następujący:

1. Uruchom ApiPort w projekcie.
1. Rozwiąż problemy przy użyciu różnych interfejsów API, które można przenosić.
1. Zwróć uwagę na obszary, gdzie masz możliwości używana zamiast bezpośredniego.
1. Powtórz poprzednie kroki dla wszystkich projektów, które są eksportowanie do momentu masz pewność, że każdy jest gotowy do być kopiowane do nowego projektu platformy .NET Core.
1. Skopiuj kod do nowego projektu platformy .NET Core.
1. Praca ewentualnych problemów, gdzie zanotowaną, że zamiast bezpośredniego nie istnieje.

To dokładne podejście jest bardziej ustrukturyzowanymi niż po prostu wypracowania błędy kompilatora, ale jest nadal stosunkowo fokus kodu i ma o konieczności zawsze kodu, który kompiluje się. Różny sposób rozwiązywanie niektórych problemów, które nie dotyczy tylko przy użyciu innego interfejsu API. Może się okazać, trzeba utworzyć więcej kompleksowe planowanie dla niektórych projektów, którego dotyczy jako podejście dalej.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Utworzenie planu dotyczącego kompleksowe ataku

Ta metoda może być najbardziej większej i bardziej złożonej projektów, gdzie restrukturyzacji kodu lub całkowicie ponowne zapisanie niektórych obszarach kodu mogą być niezbędne do obsługi platformy .NET Core. Podejście jest następujący:

1. Uruchom ApiPort w projekcie.
1. Dowiedz się, gdy jest używany każdego typu nieprzenośne i który wpływ na ogólną przenośność.
   - Zrozumienie natury tych typów. Są one niewielka liczba, ale używany często? Są one dużych wiele, ale używane rzadko? Ich użycie jest skoncentrowany lub zostanie rozmieszczona w całym kodzie?
   - Jest łatwy do izolowania kodu, który nie przenośnym, dzięki czemu można efektywniej postępowania z nim?
   - Czy trzeba zrefaktoryzuj kod?
   - Dla typów, które nie są przenośnych są alternatywne interfejsów API, które wykonania tego samego zadania? Na przykład jeśli używasz <xref:System.Net.WebClient> klasy, można używać <xref:System.Net.Http.HttpClient> zamiast klasy.
   - Istnieją różne przenośnych interfejsów API do wykonania zadania, nawet jeśli nie jest zastąpienie dzięki wsuwanej konstrukcji? Na przykład jeśli używasz <xref:System.Xml.Schema.XmlSchema> do analizy kodu XML, ale nie wymagają XML schematu odnajdowania, można użyć <xref:System.Xml.Linq> interfejsów API i wdrożenie analizowania samodzielnie zamiast polegania na interfejs API.
1. Jeśli masz zestawy, które są trudne do portu jest warto pozostawienie ich w środowisku .NET Framework teraz? Poniżej przedstawiono niektóre czynności, które należy uwzględnić:
   - Niektóre funkcje może mieć w bibliotece, który jest niezgodny z platformą .NET Core, ponieważ zbyt intensywnie opiera się na funkcje .NET Framework lub właściwe dla systemu Windows. Jest warte pozostawiając te funkcje na razie i wydanie wersji platformy .NET Core biblioteki z mniej funkcji tymczasowo aż do portu funkcji dostępnych zasobów?
   - Zrefaktoryzuj może pomóc?
1. Jest to uzasadnione zapisu implementacji niedostępny interfejsu API Framework .NET?
   Można rozważyć kopiowania, modyfikowania i przy użyciu kodu z [źródła .NET Framework odwołanie](https://github.com/Microsoft/referencesource). Kod źródłowy odwołania jest objęte [licencji MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), dlatego ma znaczący swobody korzysta ze źródła jako podstawa własnego kodu. Pamiętaj tylko prawidłowo atrybutu firmy Microsoft w kodzie.
1. Powtórz ten proces dla różnych projektów.
 
Faza analizy może potrwać pewien czas zależnie od wielkości baza kodu. W dłuższej perspektywie poświęcany czas na tym etapie, aby dokładnie zapoznać się z zakresu, wymagane zmiany i aby opracować plan zwykle pozwala czasu, szczególnie w przypadku złożonych codebase.

Plan może obejmować wprowadzeniu istotnych zmian do Twojej codebase podczas nadal przeznaczonych dla środowiska .NET Framework 4.6.2, co to bardziej ustrukturyzowanymi wersji poprzedniej podejścia. Jak przejść o wykonywanych plan jest zależna od baza kodu.

### <a name="mixing-approaches"></a>Mieszanie metod

Istnieje prawdopodobieństwo, że będzie mieszać powyżej metod na podstawie na projekt. Należy wykonać, co sprawia, że najbardziej odpowiednie dla Ciebie i baza kodu.

## <a name="porting-your-tests"></a>Eksportowanie testów

Najlepszym sposobem upewnij się, że wszystko działa, gdy zostały przeniesione kodu jest do testowania kodu jako porcie .NET Core. Aby to zrobić, należy użyć testowania platforma, która kompiluje i uruchamia testy dla platformy .NET Core. Obecnie dostępne są trzy opcje:

- [xUnit](https://xunit.github.io/)
  * [Wprowadzenie](http://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Narzędzie, aby przekonwertować projekt MSTest xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](http://www.nunit.org/)
  * [Wprowadzenie](https://github.com/nunit/docs/wiki/Installation)
  * [Wpis w blogu dotyczące migrowania MSTest do NUnit](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Zalecane podejście do Eksportowanie

Ostatecznie przenoszenia nakładu zależy od silnie struktury kodu .NET Framework. Dobrym sposobem na porcie kodu jest rozpoczynać się od znaku *podstawowej* biblioteki, które są podstawowych składników kodu. Może to być modeli danych lub niektórych klas podstawowych i metod, które używa wszystkich pozostałych bezpośrednio lub pośrednio.

1. Port projekt testowy, który umożliwia sprawdzenie warstwy biblioteki jest obecnie eksportowanie.
1. Skopiuj podstawowy biblioteki do nowego projektu platformy .NET Core i wybierz wersję programu .NET Standard chcesz obsługiwać.
1. Wprowadź wszelkie zmiany, konieczne jest uzyskanie kodu do kompilacji. Większość to może wymagać Dodawanie zależności pakietu NuGet, aby Twoje *csproj* pliku.
1. Uruchom testy i wprowadzić wymagane zmiany.
1. Wybierz kolejna warstwa kodu do portu za pośrednictwem i powtórz poprzednie kroki.

Uruchomienie z podstawowej biblioteki i przenieść na zewnątrz od podstawy i przetestować każda warstwa zgodnie z potrzebami, eksportowanie jest procesem systematyczne, gdy problemy odizolowanych do warstw kodu w czasie.
