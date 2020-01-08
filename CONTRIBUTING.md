---
ms.openlocfilehash: 469be53e14c42775f21ef1ef815becd5cad03a97
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336724"
---
# <a name="contributing"></a>Współtworzenie

Dziękujemy za zainteresowanie współtworzeniem dokumentacji platformy .NET.

> Jesteśmy w trakcie przechodzenia naszych wytycznych do przewodnika po całej lokacji.
> Aby zapoznać się z nowymi wskazówkami, odwiedź stronę [Microsoft docs przewodnika współautora](https://docs.microsoft.com/contribute/).

W dokumencie omówiono proces współtworzenia artykułów i przykładów kodu, które są hostowane w [witrynie dokumentacji programu .NET](https://docs.microsoft.com/dotnet). Współtworzyć można na różne sposoby, od poprawiania literówek po pisanie nowych artykułów.

- [DOs i podstawowe](#dos-and-donts)
- [Proces współtworzenia](#process-for-contributing)
- [Środowisko C# interaktywne](#the-c-interactive-experience)
- [Umowa licencyjna współautora](#contributor-license-agreement)

To repozytorium zawiera dokumentację koncepcyjną dla platformy .NET. Witryna dokumentacji programu .NET została utworzona na podstawie wielu repozytoriów, a także do tego:

- [Przykłady i fragmenty kodu](https://github.com/dotnet/samples) Problemy i zadania dla tego repozytorium są śledzone w usłudze [dotnet/docs/problemy](https://github.com/dotnet/docs/issues).
- [Dokumentacja interfejsu API platformy .NET](https://github.com/dotnet/dotnet-api-docs) Problemy i zadania dla tego repozytorium są śledzone w programie [dotnet/dotnet-API-docs/problemy](https://github.com/dotnet/dotnet-api-docs/issues).
- [Dokumentacja zestawu SDK .NET compiler platform](https://github.com/dotnet/roslyn-api-docs) Problemy i zadania dla tego repozytorium są śledzone w usłudze [dotnet/docs/problemy](https://github.com/dotnet/docs/issues).

## <a name="dos-and-donts"></a>DOs i podstawowe

Poniższa lista przedstawia pewne wskazówki, o których należy pamiętać podczas współtworzenia dokumentacji platformy .NET:

- **NIE ZASKAKUJ NAS** dużymi żądaniami ściągnięcia. Zamiast tego zgłoś problem i rozpocznij dyskusję, abyśmy uzgodnili kierunek zanim zainwestujesz dużo czasu. W przypadku zmian zbiorczych należy przerwać działanie w mniejszych żądań ściągnięcia (do 100 plików). Te wytyczne są zdecydowanie zalecane, jeśli żądanie ściągnięcia nie postępuje zgodnie z poniższymi wskazówkami.
- **Zapoznaj się** z bieżącą usługą [w celu](https://github.com/dotnet/docs/labels/up-for-grabs) dołączania problemów związanych z sugestiami dotyczącymi zadań.
- **Utwórz jedną** żądanie ściągnięcia dla każdego zadania. Żądań ściągnięcia, które obejmują wiele niepowiązanych zmian, są znacznie trudniejsze do przejrzenia. To opóźnia przeglądy i scalanie żądań ściągnięcia. Te wytyczne dotyczą również przeglądów: staramy się, aby nie sugerowały niezwiązanych zmian w przeglądach; Firma Microsoft zaleca, aby Recenzje społeczności przestrzegać tych wytycznych.
- **Podaj jasny** opis pracy w ramach żądania ściągnięcia. Powiedz nam, co zmieniono i dlaczego. Domyślny opis "Update article.md" nie jest pomocny dla recenzentów.
- **Nie** przesyłaj żądań ściągnięcia wyłącznie do stylów bez wcześniejszej dyskusji. Te żądań ściągnięcia pomogą Ci uzyskać więcej czasu na sprawdzenie dokładności i scalanie ich często powoduje konflikty scalania z innymi ważnymi aktualizacjami. Pracujemy nad spójnym stylem, ale firma Microsoft gwarantuje, że pracujemy nad innymi zadaniami. Artykuły są zgodne ze stylem, gdy wprowadzamy najważniejsze aktualizacje z innych przyczyn.
- **Przeczytaj** [Przewodnik po stylu](./styleguide/template.md) i wskazówki dotyczące [głosu i tonu](./styleguide/voice-tone.md) . Nowe dodatki powinny być zgodne z tymi wskazówkami.
- **UTWÓRZ** oddzielną gałąź swojego rozwidlenia zanim zaczniesz pracę przy artykułach.
- **POSTĘPUJ** zgodnie z [przepływem pracy usługi GitHub Flow](https://guides.github.com/introduction/flow/).
- **PISZ** bloga i tweety (lub coś innego) o swoim wkładzie, i rób to często!

Te wskazówki pomagają nam w zaszanowaniu czasu. Wiele osób współtworzy te repozytoria. Postępując zgodnie z tymi wskazówkami, można ułatwić nam przeglądanie i scalanie żądania ściągnięcia. Te praktyki minimalizują konflikty z żądań ściągnięcia od innych członków społeczności i naszego zespołu. Ponieważ żądań ściągnięcia, które nie są zgodne z tymi wytycznymi często, powodują, że firma Microsoft i członkowie społeczności mogą je odrzucić. Jeśli chcesz utworzyć wyjątek, Zacznij od utworzenia problemu.

> Uwaga: możesz zauważyć, że niektóre tematy nie są obecnie zgodne ze wszystkimi wytycznymi określonymi tutaj i w [przewodniku po stylu](./styleguide/template.md) . Pracujemy nad osiągnięciem spójności w ramach witryny.

## <a name="process-for-contributing"></a>Proces współtworzenia

Potrzebna jest podstawowa znajomość usługi [git i GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Pomiń ten krok w przypadku małych zmian (na przykład w przypadku korygowania literówki lub natychmiastowego otwarcia żądania ściągnięcia w celu rozwiązania problemu znalezionego w dokumentacji). Jeśli interesuje Cię pisanie nowej zawartości lub gruntowna korekta istniejącej zawartości, otwórz [problem](https://github.com/dotnet/docs/issues), opisując, co chcesz zrobić.
Zawartość w folderze *docs* jest podzielona na sekcje, które zostały odzwierciedlone w spisie treści. Określ, gdzie w spisie treści będzie się znajdował temat. Uzyskaj opinie na temat swojej propozycji.

lub

Możesz też wybierać spośród istniejących problemów, dla których współtworzenie w ramach społeczności jest mile widziane. [Projekty dla współautorów społeczności .NET](https://github.com/dotnet/docs/projects/35) wyświetlają wiele elementów roboczych, które są dostępne dla współautorów społecznościowych. W zależności od zainteresowań i poziomu zaangażowania możesz wybierać spośród problemów w następujących kategoriach:

- **Konserwacja**. Ta kategoria obejmuje dosyć prosty wkład, taki jak naprawianie uszkodzonych lub niepoprawnych linków, dodawanie brakujących przykładów kodu lub rozwiązywanie ograniczonych problemów z zawartością. W niektórych przypadkach te problemy mogą dotyczyć bardzo wielu plików. W takim przypadku powiadom nas, nad czym chcesz pracować, zanim zaczniesz.

- **Aktualizacje zawartości**. Biorąc pod uwagę ogrom zbioru dokumentów, zawartość łatwo staje się przestarzała i wymaga poprawy. Ponadto, z wielu powodów, pewna zawartość została zduplikowana lub nawet triplicated. Aktualizowanie zawartości wymaga upewnienia się, że poszczególne tematy są aktualne lub poprawiają treść w obszarze funkcji w celu wyeliminowania duplikacji i zapewnienia, że cała unikatowa zawartość jest zachowana w mniejszym zbiorze dokumentacji.

- **Tworzenie nowych treści**. Jeśli interesuje Cię tworzenie własnego tematu, następujące problemy zawierają listę tematów, o których wiemy, że chcemy je dodać do naszego zestawu dokumentów. Poinformuj nas jednak, zanim zaczniesz pracować nad tematem. Jeśli interesuje Cię napisanie tematu, który nie został tu wymieniony, otwórz problem.

Możesz też obejrzeć naszą listę [otwartych problemów](https://github.com/dotnet/docs/issues) i zgłosić się na ochotnika do pracy przy tych, które Cię interesują. Używamy etykiety [up-for-](https://github.com/dotnet/docs/labels/up-for-grabs) dodaliśmy do tagów problemów otwartych dla udziału.

**Krok 2:** Rozwidlenie `dotnet/docs`, `dotnet/samples` lub `dotnet/dotnet-api-docs` repozytoriów w razie potrzeby i utworzenie gałęzi dla zmian.

W przypadku małych zmian można użyć interfejsu internetowego usługi GitHub. Po prostu kliknij pozycję **Edytuj plik w rozwidleniu tego projektu** w pliku, który chcesz zmienić. W witrynie GitHub zostanie utworzona nowa gałąź po przesłaniu zmian.

**Krok 3.** Wprowadzaj zmiany w tej nowej gałęzi.

Jeśli jest to nowy temat, jako punktu początkowego możesz użyć tego [pliku szablonu](./styleguide/template.md). Zawiera on wytyczne dotyczące pisania, jak również objaśnia metadane wymagane dla każdego artykułu, takie jak informacje o autorze.

W kroku 1 przejdź do folderu odpowiadającego lokalizacji w spisie treści określonej dla Twojego artykułu.
Ten folder zawiera pliki Markdown dla wszystkich artykułów w tej sekcji.
W razie potrzeby utwórz nowy folder na pliki dla Twojej zawartości. Główny artykuł w tej sekcji nosi nazwę *index.md*.
W przypadku obrazów i innych zasobów statycznych utwórz podfolder o nazwie *media* wewnątrz folderu zawierającego Twój artykuł, jeśli jeszcze nie istnieje. Wewnątrz folderu *media* utwórz podfolder mający nazwę artykułu (z wyjątkiem pliku indeksu).
Uwzględnij większe próbki w folderze *Samples* w katalogu głównym repozytorium.

Należy pamiętać o przestrzeganiu składni Markdown. Aby uzyskać więcej informacji, zobacz [Przewodnik po stylu](./styleguide/template.md).

### <a name="example-structure"></a>Struktura przykładu

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

**Krok 4.** Prześlij żądanie ściągnięcia z gałęzi do `dotnet/docs/master`, `dotnet/dotnet-api-docs/master`lub `dotnet/samples/master`.

Żądanie ściągnięcia powinno *zawsze* wskazywać domyślną gałąź repozytorium (chyba że Pracujesz w gałęzi wydania). W przypadku dotnet/docs gałąź główna jest gałęzią domyślną. W przypadku zlokalizowanych repozytoriów aktywna gałąź jest domyślną. *Nigdy nie* należy otwierać żądania ściągnięcia, które jest przeznaczone dla aktywnej gałęzi w programie dotnet/docs.

Każde żądanie ściągnięcia zazwyczaj powinno dotyczyć jednego rozwiązania problemu naraz. Żądanie ściągnięcia może modyfikować jeden lub więcej plików. Jeśli wprowadzasz wiele poprawek do różnych plików, zalecane są różne żądania ściągnięcia.

Jeśli żądanie ściągnięcia dotyczy istniejącego problemu, Dodaj słowo kluczowe `Fixes #Issue_Number` do komunikatu zatwierdzenia lub opisu żądania ściągnięcia. Dzięki temu problem zostanie automatycznie zamknięty po scaleniu żądania ściągnięcia. Aby uzyskać więcej informacji, zobacz [Zamykanie problemów za pomocą komunikatów zatwierdzania](https://help.github.com/articles/closing-issues-via-commit-messages/).

Zespół platformy .NET sprawdzi Twoje żądanie ściągnięcia i da Ci znać, czy do jego zatwierdzenia są konieczne jakiekolwiek inne aktualizacje/zmiany.

**Krok 5.** Wprowadź wszelkie niezbędne aktualizacje do swojej gałęzi w sposób omówiony z zespołem.

Osoby odpowiedzialne za obsługę scalą Twoje żądanie ściągnięcia z gałęzią główną, gdy opinia zostanie zastosowana i Twoja zmiana zostanie zatwierdzona.

W przypadku niektórych erze wszystkie zatwierdzenia z gałęzi głównej są przekazywane do aktywnej gałęzi, a następnie będzie można zobaczyć swój udział na żywo w https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Współtworzenie przykładów

Wprowadzamy następujące rozróżnienie dla kodu istniejącego w naszym repozytorium:

- Przykłady: czytelnicy mogą pobrać i uruchomić przykłady. Wszystkie przykłady powinny być kompletnymi aplikacjami lub bibliotekami. Gdy przykład tworzy bibliotekę, powinien on zawierać testy jednostkowe lub aplikację, która umożliwi czytelnikom uruchomienie kodu.

- Fragmenty kodu: ilustrują mniejszą koncepcję lub zadanie. Można je skompilować, ale nie mają one być kompletnymi aplikacjami.

Cały kod znajduje się w repozytorium [dotnet/samples](https://github.com/dotnet/samples). Pracujemy nad modelem, w którym struktura naszego folderu przykładów będzie pasować do struktury naszego folderu dokumentów. Do standardów, których przestrzegamy, należą:

- Folder *snippets* najwyższego poziomu zawiera fragmenty kodu dla małych, konkretnych przykładów.
- Przykłady referencyjne interfejsu API znajdują się w folderze następującym po tym wzorcu: *fragmenty kodu/\<language >/api/\<przestrzeni nazw >/\<apiname >* .
- Inne foldery najwyższego poziomu są zgodne z folderami najwyższego poziomu w repozytorium *docs*. Na przykład w repozytorium docs jest folder *machine-learning/tutorials*, a przykłady dotyczące samouczków uczenia maszynowego są w folderze *samples/machine-learning/tutorials*.

Ponadto wszystkie przykłady w folderach *core* i *standard* powinny się skompilować i uruchomić na wszystkich platformach obsługiwanych przez platformę .NET Core. Nasz system kompilacji ciągłej integracji wymusi to. Folder najwyższego poziomu *framework* zawiera przykłady, które są kompilowane i weryfikowane tylko w systemie Windows.

Firma Microsoft może rozszerzyć te katalogi, ponieważ repozytorium docs dodaje nową zawartość. Na przykład dodamy katalogi platformy Xamarin, takie jak `xamarin-ios` i `xamarin-android` katalogi.

Każdy kompletny przykład, który tworzysz, powinien zawierać plik *readme.md*. Ten plik powinien zawierać krótki opis przykładu (jeden lub dwa akapity). Plik *readme.md* powinien informować czytelników o tym, czego się dowiedzą, analizując ten przykład. Plik *readme.md* powinien też zawierać link do opublikowanego dokumentu w [witrynie dokumentacji platformy .NET](https://docs.microsoft.com/dotnet/welcome).
Aby ustalić, gdzie dany plik w repozytorium jest zamapowany na daną witrynę, zastąp fragment `/docs` w ścieżce repozytorium fragmentem `https://docs.microsoft.com/dotnet`.

Twój temat będzie też zawierał linki do przykładu. Link powinien prowadzić bezpośrednio do folderu przykładu w usłudze GitHub.

Aby uzyskać więcej informacji, zobacz [plik Readme przykładów](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Interaktywna platforma języka C#

Krótkie przykłady kodu w języku C# mogą używać tagu języka `csharp-interactive` do określenia przykładu w języku C# uruchomionego w przeglądarce. (Wbudowane przykłady kodu używają znacznika `csharp-interactive`, w przypadku wstawek zawartych ze źródła, Użyj tagu `code-csharp-interactive`). Te przykłady kodu zawierają okno kod i okno dane wyjściowe w artykule. Okno wyjściowe pokazuje wszelkie dane wyjściowe po wykonaniu interaktywnego kodu, gdy użytkownik uruchomił przykład.

Interaktywna platforma języka C# zmienia sposób pracy z przykładami. Goście mogą uruchomić przykład, aby zobaczyć wyniki. Wiele czynników pomaga ustalić, czy przykład lub odpowiadający mu tekst ma zawierać informacje o danych wyjściowych.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kiedy wyświetlić oczekiwane dane wyjściowe bez uruchamiania przykładu

- Artykuły przeznaczone dla początkujących powinny udostępniać dane wyjściowe, aby czytelnicy mogli porównać dane wyjściowe swojej pracy z oczekiwaną odpowiedzią.
- Dane wyjściowe powinny być prezentowane dla przykładów, w których dane wyjściowe są integralną częścią tematu. Na przykład artykuły na temat sformatowanego tekstu powinny pokazywać format tekstu bez uruchamiania przykładu.
- Gdy zarówno przykład, jak i oczekiwane dane wyjściowe są krótkie, rozważ pokazanie danych wyjściowych. Zaoszczędzi to trochę czasu.
- Artykuły objaśniające, jak bieżąca kultura lub kultura niezmienna wpływają na dane wyjściowe, powinny objaśniać oczekiwane dane wyjściowe. Interaktywna pętla REPL (Read Evaluate Print Loop) działa na hostach opartych na systemie Linux. Domyślna kultura i kultura niezmienna tworzą inne dane wyjściowe dla różnych systemów operacyjnych i maszyn. Artykuł powinien objaśniać dane wyjściowe w systemach Windows, Linux i Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kiedy wykluczać oczekiwane dane wyjściowe z przykładu

- Artykuły, gdzie przykład generuje większe dane wyjściowe, nie powinny zawierać ich w komentarzach. Przesłania to kod, gdy przykład zostanie uruchomiony.
- Artykuły, gdzie przykład jest ilustracją tematu, ale dane wyjściowe nie są konieczne do jego zrozumienia. Na przykład kod uruchamiający zapytanie LINQ w celu wyjaśnienia składni zapytania, a następnie wyświetlający każdy element z kolekcji wyjściowej.

## <a name="contributor-license-agreement"></a>Umowa licencyjna współautora

Zanim Twoje żądanie ściągnięcia zostanie scalone, musisz podpisać [Umowę licencyjną współautora platformy .NET Foundation (CLA)](https://cla.dotnetfoundation.org). Jest to jednorazowe wymaganie dla projektów na platformie .NET Foundation. Więcej na temat [umów licencyjnych współautora (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) możesz przeczytać w Wikipedii.

Umowa: [net-foundation-contribution-license-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Nie musisz z góry podpisywać umowy. Możesz sklonować, rozwidlić i przekazać swoje żądanie ściągnięcia w zwykły sposób. Gdy Twoje żądanie ściągnięcia jest tworzone, jest ono klasyfikowane przez bota CLA. Jeśli zmiana jest prosta (na przykład Naprawiono literówki), żądanie ściągnięcia jest oznaczone `cla-not-required`. W przeciwnym razie jest ono klasyfikowane jako `cla-required`. Po podpisaniu umowy CLA bieżące i wszystkie przyszłe żądania ściągnięcia będą oznaczone jako `cla-signed`.
