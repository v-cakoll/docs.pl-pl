---
ms.openlocfilehash: 25615dd43f1ae4f56c7bced7f79a0612093a21fb
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191697"
---
# <a name="contributing"></a>Udział

Dziękujemy za zainteresowanie korzystaniem z dokumentacji platformy .NET.

> Jesteśmy w trakcie przechodzenia naszych wytycznych do przewodnika po całej lokacji.
> Aby zapoznać się z nowymi wskazówkami, odwiedź stronę [Microsoft docs przewodnika współautora](https://docs.microsoft.com/contribute/).

W dokumencie omówiono proces współtworzenia artykułów i przykładów kodu, które są hostowane w [witrynie dokumentacji programu .NET](https://docs.microsoft.com/dotnet). Wkłady mogą być bardzo proste jako poprawki literówki lub złożone jako nowe artykuły.

- [DOs i podstawowe](#dos-and-donts)
- [Proces współtworzenia](#process-for-contributing)
- [Środowisko C# interaktywne](#the-c-interactive-experience)
- [Umowa licencyjna współautora](#contributor-license-agreement)

To repozytorium zawiera dokumentację koncepcyjną dla platformy .NET. Witryna dokumentacji programu .NET została utworzona na podstawie wielu repozytoriów, a także do tego:

- [Przykłady i fragmenty kodu](https://github.com/dotnet/samples)  
    Problemy i zadania dla tego repozytorium są śledzone w usłudze [dotnet/docs/problemy](https://github.com/dotnet/docs/issues).
- [Dokumentacja interfejsów API platformy .NET](https://github.com/dotnet/dotnet-api-docs)  
    Problemy i zadania dla tego repozytorium są śledzone w programie [dotnet/dotnet-API-docs/problemy](https://github.com/dotnet/dotnet-api-docs/issues).
- [Dokumentacja zestawu SDK .NET Compiler Platform](https://github.com/dotnet/roslyn-api-docs)  
    Problemy i taks dla tego repozytorium są śledzone w usłudze [dotnet/docs/problemy](https://github.com/dotnet/docs/issues).

## <a name="dos-and-donts"></a>DOs i podstawowe

Na poniższej liście przedstawiono niektóre reguły identyfikatorów GUID, które należy wziąć pod uwagę podczas korzystania z dokumentacji programu .NET:

- **Nie ryzykuj** nas z dużymi żądaniami ściągnięcia. Zamiast tego należy rozwiązać problem i zacząć dyskusję, dzięki czemu możemy wyrazić zgodę na kierunek przed zainwestowaniem dużej ilości czasu. W przypadku zmian zbiorczych należy przerwać działanie w mniejszych żądań ściągnięcia (do 100 plików). Te wytyczne są zdecydowanie zalecane, jeśli żądanie ściągnięcia nie postępuje zgodnie z poniższymi wskazówkami.
- **Zapoznaj się** z bieżącą usługą [w celu](https://github.com/dotnet/docs/labels/up-for-grabs) dołączania problemów związanych z sugestiami dotyczącymi zadań.
- **Utwórz jedną** żądanie ściągnięcia dla każdego zadania. Żądań ściągnięcia, które obejmują wiele niepowiązanych zmian, są znacznie trudniejsze do przejrzenia. To opóźnia przeglądy i scalanie żądań ściągnięcia. Te wytyczne dotyczą również przeglądów: staramy się, aby nie sugerowały niezwiązanych zmian w przeglądach; Firma Microsoft zaleca, aby Recenzje społeczności przestrzegać tych wytycznych.
- **Podaj jasny** opis pracy w ramach żądania ściągnięcia. Powiedz nam, co zmieniono i dlaczego. Domyślny opis "Update article.md" nie jest pomocny dla recenzentów.
- **Nie** przesyłaj żądań ściągnięcia wyłącznie do stylów bez wcześniejszej dyskusji. Te żądań ściągnięcia pomogą Ci uzyskać więcej czasu na sprawdzenie dokładności i scalanie ich często powoduje konflikty scalania z innymi ważnymi aktualizacjami. Pracujemy nad spójnym stylem, ale firma Microsoft gwarantuje, że pracujemy nad innymi zadaniami. Artykuły są zgodne ze stylem, gdy wprowadzamy najważniejsze aktualizacje z innych przyczyn. 
- **Przeczytaj** [Przewodnik po stylu](./styleguide/template.md) i wskazówki dotyczące [głosu i tonu](./styleguide/voice-tone.md) . Nowe dodatki powinny być zgodne z tymi wskazówkami.
- Przed rozpoczęciem pracy z artykułami utwórz oddzielną gałąź w rozwidleniu.
- **Postępuj zgodnie z** [przepływem pracy przepływu usługi GitHub](https://guides.github.com/introduction/flow/).
- Bądź **na blogu i** tweety (lub niezależnie od tego) o Twoje wkłady — często!

Te wskazówki pomagają nam w zaszanowaniu czasu. Wiele osób współtworzy te repozytoria. Postępując zgodnie z tymi wskazówkami, można ułatwić nam przeglądanie i scalanie żądania ściągnięcia. Te praktyki minimalizują konflikty z żądań ściągnięcia od innych członków społeczności i naszego zespołu. Ponieważ żądań ściągnięcia, które nie są zgodne z tymi wytycznymi często, powodują, że firma Microsoft i członkowie społeczności mogą je odrzucić. Jeśli chcesz utworzyć wyjątek, Zacznij od utworzenia problemu.

> Uwaga: możesz zauważyć, że niektóre tematy nie są obecnie zgodne ze wszystkimi wytycznymi określonymi tutaj i w [przewodniku po stylu](./styleguide/template.md) . Pracujemy nad osiągnięciem spójności w całej lokacji.

## <a name="process-for-contributing"></a>Proces współtworzenia

Potrzebna jest podstawowa znajomość usługi [git i GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Pomiń ten krok w przypadku małych zmian (na przykład w przypadku korygowania literówki lub natychmiastowego otwarcia żądania ściągnięcia w celu rozwiązania problemu znalezionego w dokumentacji). Jeśli interesuje Cię Pisanie nowej zawartości lub dokładne poprawianie istniejącej zawartości, Otwórz [problem](https://github.com/dotnet/docs/issues) z opisem tego, co chcesz zrobić.
Zawartość w folderze *docs* jest zorganizowana w sekcje, które są odzwierciedlone w spisie treści (TOC). Zdefiniuj, gdzie temat będzie znajdował się w spisie treści. Uzyskaj opinię na temat propozycji.

—lub—

Możesz również wybrać spośród istniejących problemów, dla których wkłady społecznościowe są powitane. [Projekty dla współautorów społeczności .NET](https://github.com/dotnet/docs/projects/35) wyświetlają wiele elementów roboczych, które są dostępne dla współautorów społecznościowych. W zależności od zainteresowań i poziomu zobowiązań możesz wybierać spośród problemów w następujących kategoriach:

- **Konserwacja**. Ta kategoria obejmuje dość proste wkłady, takie jak Naprawianie uszkodzonych lub nieprawidłowych linków, Dodawanie brakujących przykładów kodu lub Rozwiązywanie problemów z zawartością. W niektórych przypadkach te problemy mogą dotyczyć dużej liczby plików. W takim przypadku należy poinformować nas, co chcesz zrobić, zanim zaczniesz.

- **Aktualizacje zawartości**. Po enormity zestawu dokumentów zawartość jest łatwo przestarzała i wymaga poprawki. Ponadto, z wielu powodów, pewna zawartość została zduplikowana lub nawet triplicated. Aktualizacja zawartości polega na tym, że poszczególne tematy są aktualne lub poprawiają zawartość w obszarze funkcji w celu wyeliminowania duplikatów i zapewnienia, że cała unikatowa zawartość jest zachowywana w mniejszych zestawach dokumentacji.

- **Tworzenie nowej zawartości**. Jeśli interesuje Cię Tworzenie własnego tematu, te problemy mogą zostać dodane do naszego zestawu dokumentów. Daj nam znać przed rozpoczęciem pracy z tematem. Jeśli interesuje Cię pisanie tematu, którego nie ma na liście, Otwórz problem.

Możesz również zapoznać się z naszą listą [problemów otwartych](https://github.com/dotnet/docs/issues) i od osoby zależnej, aby zacząć korzystać z interesujących Cię elementów. Używamy etykiety [up-for-](https://github.com/dotnet/docs/labels/up-for-grabs) dodaliśmy do tagów problemów otwartych dla udziału. 

**Krok 2:** Rozwidlenie `dotnet/docs`, `dotnet/samples` lub `dotnet/dotnet-api-docs` repozytoriów w razie potrzeby i utworzenie gałęzi dla zmian.

W przypadku małych zmian można użyć interfejsu internetowego usługi GitHub. Po prostu kliknij pozycję **Edytuj plik w rozwidleniu tego projektu** w pliku, który chcesz zmienić. W witrynie GitHub zostanie utworzona nowa gałąź po przesłaniu zmian.

**Krok 3.** Wprowadź zmiany w tej nowej gałęzi.

Jeśli jest to nowy temat, możesz użyć tego [pliku szablonu](./styleguide/template.md) jako punktu początkowego. Zawiera wytyczne dotyczące pisania i objaśnia metadane wymagane dla każdego artykułu, takie jak informacje o autorze.

Przejdź do folderu, który odpowiada lokalizacji spisu treści określonego dla artykułu w kroku 1.
Ten folder zawiera pliki promocji dla wszystkich artykułów w tej sekcji.
W razie potrzeby utwórz nowy folder, aby umieścić pliki dla zawartości. Główny artykuł dotyczący tej sekcji nosi nazwę *index.MD*.
W przypadku obrazów i innych zasobów statycznych utwórz podfolder o nazwie *multimedia* w folderze zawierającym artykuł, jeśli jeszcze nie istnieje. W folderze *Media* utwórz podfolder o nazwie artykułu (z wyjątkiem pliku indeksu).
Uwzględnij większe próbki w folderze *Samples* w katalogu głównym repozytorium.

Upewnij się, że przestrzegasz odpowiedniej składni promocji. Aby uzyskać więcej informacji, zobacz [Przewodnik po stylu](./styleguide/template.md).

### <a name="example-structure"></a>Przykładowa struktura

```
docs
  /about
  /core
    /porting
      porting-overview.md
      /media
        /porting-overview
            portability_report.png
```

**Krok 4.** Prześlij żądanie ściągnięcia z gałęzi do `dotnet/docs/master`, `dotnet/dotnet-api-docs/master` lub `dotnet/samples/master`.

Żądanie ściągnięcia powinno *zawsze* wskazywać domyślną gałąź repozytorium (chyba że Pracujesz w gałęzi wydania). W przypadku dotnet/docs gałąź główna jest gałęzią domyślną. W przypadku zlokalizowanych repozytoriów aktywna gałąź jest domyślną. *Nigdy nie* należy otwierać żądania ściągnięcia, które jest przeznaczone dla aktywnej gałęzi w programie dotnet/docs.

Każdy element żądania ściągnięcia powinien zwykle dotyczyć jednego problemu w danym momencie. Żądanie ściągnięcia może zmodyfikować jeden lub wiele plików. W przypadku rozwiązywania wielu poprawek w różnych plikach preferowane są osobne żądań ściągnięcia.

Jeśli żądanie ściągnięcia dotyczy istniejącego problemu, Dodaj słowo kluczowe `Fixes #Issue_Number` do komunikatu zatwierdzenia lub opisu żądania ściągnięcia. W ten sposób problem zostanie automatycznie zamknięty po scaleniu żądania ściągnięcia. Aby uzyskać więcej informacji, zobacz [zamykanie problemów za pomocą komunikatów zatwierdzania](https://help.github.com/articles/closing-issues-via-commit-messages/).

Zespół platformy .NET sprawdzi swój stan żądania ściągnięcia i poinformuje o tym, czy istnieją inne aktualizacje/zmiany niezbędne do zatwierdzenia.

**Krok 5.** Wykonaj wszelkie niezbędne aktualizacje gałęzi, jak to opisano w zespole.

W przypadku, gdy zastosowana została opinia i zostanie zatwierdzona zmiana zostanie scalona żądanie ściągnięcia z gałęzią główną.

W przypadku niektórych erze wszystkie zatwierdzenia z gałęzi głównej są przekazywane do aktywnej gałęzi, a następnie będzie można zobaczyć swój udział na żywo w https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Współtworzenie przykładów

Dla kodu, który istnieje w naszym repozytorium, wprowadzimy następujące rozróżnienia:

- Przykłady: czytelnicy mogą pobrać i uruchomić przykłady. Wszystkie przykłady powinny być kompletnymi aplikacjami lub bibliotekami. Gdzie przykład tworzy bibliotekę, powinna obejmować testy jednostkowe lub aplikację, która umożliwia czytelnikom uruchamianie kodu.

- Fragmenty kodu: ilustrują mniejszą koncepcję lub zadanie. Są one kompilowane, ale nie są przeznaczone do kompletnych aplikacji.

Kod wszystkie są przechowywane w repozytorium [dotnet/Samples](https://github.com/dotnet/samples) . Pracujemy nad modelem, w którym nasze przykłady struktury folderów są zgodne z naszą strukturą folderów docs. Stosowane są następujące standardy:

- Folder *wstawek* najwyższego poziomu zawiera fragmenty kodu dla małych, ukierunkowanych próbek.
- Przykłady referencyjne interfejsu API znajdują się w folderze następującym po tym wzorcu: *fragmenty kodu/\<language >/api/\<namespace >/\<apiname >* .
- Inne foldery najwyższego poziomu są zgodne z folderami najwyższego poziomu w repozytorium *docs* . Na przykład repozytorium docs zawiera folder *uczenie maszynowego/samouczków* , a przykłady samouczków dotyczących uczenia maszynowego znajdują się w folderze *Samples/Machine-Learning/samouczki* .

Ponadto wszystkie przykłady w folderach *podstawowe* i *standardowe* powinny być kompilowane i uruchamiane na wszystkich platformach obsługiwanych przez platformę .NET Core. Nasz system kompilacji elementu konfiguracji będzie wymuszać to. Folder *struktury* najwyższego poziomu zawiera przykłady, które są kompilowane i sprawdzane tylko w systemie Windows.

Firma Microsoft może rozszerzyć te katalogi, ponieważ repozytorium docs dodaje nową zawartość. Na przykład dodamy katalogi platformy Xamarin, takie jak `xamarin-ios` i `xamarin-android`.

Każdy kompletny przykład tworzony przez Ciebie powinien zawierać plik *README.MD* . Ten plik powinien zawierać Krótki opis przykładu (jeden lub dwa akapity). Twoja *README.MD* powinna poinformować czytelników, co pouczy się, eksplorowanie tego przykładu. Plik *README.MD* powinien również zawierać link do dokumentu na żywo w [witrynie dokumentacji programu .NET](https://docs.microsoft.com/dotnet/welcome).
Aby określić, gdzie dany plik w repozytorium jest mapowany do tej lokacji, Zastąp `/docs` w ścieżce repozytorium `https://docs.microsoft.com/dotnet`.

Temat zawiera również linki do przykładu. Połącz bezpośrednio z folderem przykładu w usłudze GitHub.

Aby uzyskać więcej informacji, zobacz [plik Readme przykładów](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Środowisko C# interaktywne

Krótkie przykłady kodu w C# programie mogą użyć znacznika języka `csharp-interactive`, aby określić C# przykład, który działa w przeglądarce. (Wbudowane przykłady kodu używają tagu `csharp-interactive`, dla wstawek zawartych ze źródła, Użyj znacznika `code-csharp-interactive`). Te przykłady kodu zawierają okno kod i okno dane wyjściowe w artykule. W oknie dane wyjściowe są wyświetlane wszystkie dane wyjściowe z wykonywania kodu interaktywnego, gdy użytkownik uruchomi przykład. 

C# Interaktywny proces zmienia sposób pracy z przykładami. Odwiedzający mogą uruchomić przykład, aby zobaczyć wyniki. Wiele czynników pomaga ustalić, czy próbka lub odpowiedni tekst powinien zawierać informacje o danych wyjściowych.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kiedy mają być wyświetlane oczekiwane dane wyjściowe bez uruchamiania przykładu

- Artykuły przeznaczone dla początkujących powinny dostarczyć dane wyjściowe, dzięki czemu czytelnicy mogą porównać wyniki pracy z oczekiwaną odpowiedzią.
- Próbki, w których dane wyjściowe są integralne względem tematu, powinny wyświetlać te dane wyjściowe. Na przykład artykuły na sformatowanym tekście powinny zawierać format tekstu bez uruchamiania przykładu.
- Gdy zarówno próbka, jak i oczekiwane dane wyjściowe są krótkie, należy rozważyć wyświetlanie danych wyjściowych. Oszczędza czas.
- Artykuły objaśniające, w jaki sposób bieżąca kultura lub Niezmienna kultura ma wpływ na dane wyjściowe powinny wyjaśnić oczekiwane dane wyjściowe. Interaktywna REPL (odczyt) jest uruchamiana na hoście opartym na systemie Linux. Kultura domyślna i Niezmienna kultura tworzą różne dane wyjściowe w różnych systemach operacyjnych i komputerach. W tym artykule wyjaśniono dane wyjściowe w systemach Windows, Linux i Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kiedy należy wykluczyć oczekiwane dane wyjściowe z przykładu 

- Artykuły, w których próbka generuje większe dane wyjściowe nie powinny uwzględniać tego w komentarzach. Po uruchomieniu próbki program zasłania kod.
- Artykuły, w których przykład ilustruje temat, ale dane wyjściowe nie są integralną częścią tego tematu. Na przykład kod, który uruchamia zapytanie LINQ, aby wyjaśnić składnię zapytania, a następnie wyświetlić każdy element w kolekcji wyjściowej.

## <a name="contributor-license-agreement"></a>Umowa licencyjna współautora

Przed scaleniem żądania ściągnięcia należy podpisać [umowę licencyjną programu .NET Foundation (CLA)](https://cla.dotnetfoundation.org) . Jest to jednorazowe wymaganie dla projektów w programie .NET Foundation. Więcej informacji na temat [umów licencyjnych dotyczących udziałów (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) można znaleźć w witrynie Wikipedia.

Umowa: [NET-Foundation-Contribution-License-Agreement. PDF](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Nie musisz podpisać umowy z góry. Można klonować, rozwidlenie i przesłać żądanie ściągnięcia w zwykły sposób. Po utworzeniu żądania ściągnięcia jest ono klasyfikowane przez CLA bot. Jeśli zmiana jest prosta (na przykład Naprawiono literówki), żądanie ściągnięcia jest oznaczone `cla-not-required`. W przeciwnym razie jest sklasyfikowany jako `cla-required`. Po podpisaniu CLA bieżące i wszystkie przyszłe żądania ściągnięcia są oznaczone jako `cla-signed`.
