---
ms.openlocfilehash: e5da9a98e8725880223df3737dc60f773db8d20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79141136"
---
# <a name="contributing"></a>Współtworzenie

Dziękujemy za zainteresowanie współtworzeniem dokumentacji platformy .NET.

> Jesteśmy w trakcie przenoszenia naszych wytycznych do przewodnika o wkładzie w całej witrynie.
> Aby zapoznać się z nowymi wskazówkami, odwiedź [przewodnik po współautorach dokumentów firmy Microsoft](https://docs.microsoft.com/contribute/).

Dokument obejmuje proces współtworzenia artykułów i próbek kodu, które są hostowane w [witrynie dokumentacji .NET](https://docs.microsoft.com/dotnet). Współtworzyć można na różne sposoby, od poprawiania literówek po pisanie nowych artykułów.

- [OS i DON'Ts](#dos-and-donts)
- [Proces wnoszenia wkładu](#process-for-contributing)
- [Interaktywna platforma języka C#](#the-c-interactive-experience)
- [Umowa licencyjna współautora](#contributor-license-agreement)

To repozytorium zawiera dokumentację koncepcyjną dla .NET. Witryna dokumentacji .NET jest zbudowana z wielu repozytoriów oprócz tego:

- [Przykłady kodu i urywki](https://github.com/dotnet/samples) Problemy i zadania dla tego repozytorium są śledzone w [dotnet/docs/issues](https://github.com/dotnet/docs/issues).
- [Odwołanie interfejsu API .NET](https://github.com/dotnet/dotnet-api-docs) Problemy i zadania dla tego repozytorium są śledzone w [dotnet/dotnet-api-docs/issues](https://github.com/dotnet/dotnet-api-docs/issues).
- [Odwołanie sdk platformy kompilatora .NET](https://github.com/dotnet/roslyn-api-docs) Problemy i zadania dla tego reppo są śledzone w [dotnet/docs/issues](https://github.com/dotnet/docs/issues).

### <a name="contributing-to-international-content"></a>Przyczynianie się do treści międzynarodowych

Składki na zawartość przetłumaczoną maszynowo (MT) nie są obecnie akceptowane. W celu poprawy jakości zawartości MT, przeszliśmy do silnika MT neuronalnej. Akceptujemy i zachęcamy do udziału w treściach tłumaczonych przez człowieka (HT), która służy do szkolenia silnika MT neuronalnej. Tak więc z biegiem czasu, wkład w zawartość HT poprawi jakość zarówno HT, jak i MT. Tematy MT będą miały zastrzeżenie stwierdzające, że część tematu może być MT, a przycisk **Edit** nie będzie wyświetlany jako wyłączony.

## <a name="dos-and-donts"></a>OS i DON'Ts

Poniższa lista przedstawia pewne wskazówki, o których należy pamiętać podczas współtworzenia dokumentacji platformy .NET:

- **NIE ZASKAKUJ NAS** dużymi żądaniami ściągnięcia. Zamiast tego zgłoś problem i rozpocznij dyskusję, abyśmy uzgodnili kierunek zanim zainwestujesz dużo czasu. W przypadku zmian zbiorczych podziel pracę na mniejsze pr (do 100 plików). Zdecydowanie zaleca się stosowanie tych wytycznych, jeśli program pr nie jest zgodny z poniższymi wskazówkami.
- **CZY** spojrzeć na bieżące [do zgarnięcia](https://github.com/dotnet/docs/labels/up-for-grabs) problemów dla sugestii dotyczących zadań.
- **CZY** utworzyć jeden PR dla każdego zadania. PRs, które zawierają wiele niepowiązanych zmian są znacznie trudniejsze do przejrzenia. To opóźnia przeglądy i łączenie prs. Niniejsze wytyczne dotyczą również opinii: staramy się nie sugerować niepowiązanych zmian w recenzjach; prosimy, aby opinie społeczności były zgodne z tymi wytycznymi.
- **CZY** podać jasny opis pracy w PR. Powiedz nam, co się zmieniło i dlaczego. Domyślny opis "aktualizuj article.md" nie jest przydatny dla recenzentów.
- **NIE** przesyłaj prs dla zmian tylko do stylu bez uprzedniej dyskusji. Te prs zająć więcej czasu, aby przejrzeć dokładność i scalanie ich często powoduje konflikty korespondencji scalania z innymi ważnymi aktualizacjami. Pracujemy nad podążaniem za spójnym stylem, ale równoważymy tę pracę z innymi zadaniami. Artykuły są wprowadzane w stylu zgodności, gdy robimy poważne aktualizacje z innych powodów.
- **CZY** przeczytać [przewodnik stylu](./styleguide/template.md) i głos i [tonu](./styleguide/voice-tone.md) wytyczne. Nowe dodatki powinny być zgodne z tymi wytycznymi.
- **UTWÓRZ** oddzielną gałąź swojego rozwidlenia zanim zaczniesz pracę przy artykułach.
- **POSTĘPUJ** zgodnie z [przepływem pracy usługi GitHub Flow](https://guides.github.com/introduction/flow/).
- **PISZ** bloga i tweety (lub coś innego) o swoim wkładzie, i rób to często!

Wytyczne te pomagają nam szanować czas każdego z nas. Wiele osób przyczynia się do tych repozytoriów. Przestrzeganie tych wytycznych ułatwia nam przeglądanie i łączenie twojego PR w odpowiednim czasie. Te praktyki minimalizują konflikty z prs od innych członków społeczności i naszego zespołu. Ponieważ prs, które nie są zgodne z tymi wytycznymi często powodują dodatkową pracę dla nas i członków społeczności, te PRs mogą zostać odrzucone. Jeśli chcesz wyjątek, zacznij od utworzenia problemu.

> Uwaga: można zauważyć, że niektóre tematy nie są obecnie po wszystkich wytycznych określonych tutaj i w [przewodniku po stylu,](./styleguide/template.md) jak również. Pracujemy nad osiągnięciem spójności w ramach witryny.

## <a name="process-for-contributing"></a>Proces wnoszenia wkładu

Potrzebujesz podstawowego zrozumienia [Git i GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Pomiń ten krok w przypadku niewielkich zmian (na przykład, jeśli poprawiasz literówkę lub natychmiast otwierasz żądanie ściągnięcia, aby rozwiązać problem, który znajdujesz w docs). Jeśli interesuje Cię pisanie nowej zawartości lub gruntowna korekta istniejącej zawartości, otwórz [problem](https://github.com/dotnet/docs/issues), opisując, co chcesz zrobić.
Zawartość w folderze *docs* jest podzielona na sekcje, które zostały odzwierciedlone w spisie treści. Określ, gdzie w spisie treści będzie się znajdował temat. Uzyskaj opinie na temat swojej propozycji.

— lub —

Możesz też wybierać spośród istniejących problemów, dla których współtworzenie w ramach społeczności jest mile widziane. [Projekty dla współautorów społeczności .NET](https://github.com/dotnet/docs/projects/35) zawiera listę wielu elementów pracy, które są dostępne dla współautorów społeczności. W zależności od zainteresowań i poziomu zaangażowania możesz wybierać spośród problemów w następujących kategoriach:

- **Konserwacja**. Ta kategoria obejmuje dosyć prosty wkład, taki jak naprawianie uszkodzonych lub niepoprawnych linków, dodawanie brakujących przykładów kodu lub rozwiązywanie ograniczonych problemów z zawartością. W niektórych przypadkach te problemy mogą dotyczyć bardzo wielu plików. W takim przypadku powiadom nas, nad czym chcesz pracować, zanim zaczniesz.

- **Aktualizacje zawartości**. Biorąc pod uwagę ogrom zbioru dokumentów, zawartość łatwo staje się przestarzała i wymaga poprawy. Ponadto, z różnych powodów, niektóre treści zostały zduplikowane lub nawet potrójne. Aktualizowanie zawartości wymaga upewnienia się, że poszczególne tematy są aktualne lub poprawiają treść w obszarze funkcji w celu wyeliminowania duplikacji i zapewnienia, że cała unikatowa zawartość jest zachowana w mniejszym zbiorze dokumentacji.

- **Tworzenie nowych treści**. Jeśli interesuje Cię tworzenie własnego tematu, następujące problemy zawierają listę tematów, o których wiemy, że chcemy je dodać do naszego zestawu dokumentów. Poinformuj nas jednak, zanim zaczniesz pracować nad tematem. Jeśli interesuje Cię napisanie tematu, który nie został tu wymieniony, otwórz problem.

Możesz też obejrzeć naszą listę [otwartych problemów](https://github.com/dotnet/docs/issues) i zgłosić się na ochotnika do pracy przy tych, które Cię interesują. Używamy [etykiety up-for-grabs,](https://github.com/dotnet/docs/labels/up-for-grabs) aby oznaczyć problemy otwarte dla wkładu.

**Krok 2:** `dotnet/docs`Rozwidlić `dotnet/samples` `dotnet/dotnet-api-docs` , lub repo w razie potrzeby i utworzyć gałąź dla zmian.

W przypadku niewielkich zmian można użyć interfejsu internetowego usługi GitHub. Wystarczy kliknąć **pozycję Zmień plik w rozwidliku tego projektu** w pliku, który chcesz zmienić. GitHub tworzy nową gałąź po przesłaniu zmian.

**Krok 3.** Wprowadzaj zmiany w tej nowej gałęzi.

Jeśli jest to nowy temat, jako punktu początkowego możesz użyć tego [pliku szablonu](./styleguide/template.md). Zawiera on wytyczne dotyczące pisania, jak również objaśnia metadane wymagane dla każdego artykułu, takie jak informacje o autorze.

W kroku 1 przejdź do folderu odpowiadającego lokalizacji w spisie treści określonej dla Twojego artykułu.
Ten folder zawiera pliki Markdown dla wszystkich artykułów w tej sekcji.
W razie potrzeby utwórz nowy folder na pliki dla Twojej zawartości. Główny artykuł w tej sekcji nosi nazwę *index.md*.
W przypadku obrazów i innych zasobów statycznych utwórz podfolder o nazwie *media* wewnątrz folderu zawierającego Twój artykuł, jeśli jeszcze nie istnieje. Wewnątrz folderu *media* utwórz podfolder mający nazwę artykułu (z wyjątkiem pliku indeksu).
Dołącz większe próbki do folderu *próbek* pod katalogiem głównym repów.

Należy pamiętać o przestrzeganiu składni Markdown. Aby uzyskać więcej informacji, zobacz [przewodnik po stylu](./styleguide/template.md).

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

**Krok 4:** Prześlij żądanie ściągnięcia (PR) `dotnet/dotnet-api-docs/master`z `dotnet/samples/master`oddziału do `dotnet/docs/master`, lub .

Program PR powinien *zawsze* kierować reklamy na domyślną gałąź repozytorium (chyba że pracujesz nad gałęzią wydania). W przypadku dotnet/docs gałąź główna jest gałęzią domyślną. W przypadku zlokalizowanych repozytoriów gałąź na żywo jest gałęzią domyślną. Nigdy *nie* należy otwierać pr, który jest przeznaczony dla gałęzi na żywo na dotnet/docs.

Każde żądanie ściągnięcia zazwyczaj powinno dotyczyć jednego rozwiązania problemu naraz. Żądanie ściągnięcia może modyfikować jeden lub więcej plików. Jeśli wprowadzasz wiele poprawek do różnych plików, zalecane są różne żądania ściągnięcia.

Jeśli twój program pr rozwiązuje istniejący `Fixes #Issue_Number` problem, dodaj słowo kluczowe do wiadomości zatwierdzającej lub opisu PR. Dzięki temu problem zostanie automatycznie zamknięty po scaleniu żądania ściągnięcia. Aby uzyskać więcej informacji, zobacz [Zamykanie problemów za pomocą komunikatów zatwierdzania](https://help.github.com/articles/closing-issues-via-commit-messages/).

Zespół platformy .NET sprawdzi Twoje żądanie ściągnięcia i da Ci znać, czy do jego zatwierdzenia są konieczne jakiekolwiek inne aktualizacje/zmiany.

**Krok 5.** Wprowadź wszelkie niezbędne aktualizacje do swojej gałęzi w sposób omówiony z zespołem.

Osoby odpowiedzialne za obsługę scalą Twoje żądanie ściągnięcia z gałęzią główną, gdy opinia zostanie zastosowana i Twoja zmiana zostanie zatwierdzona.

W pewnym czasie wypychamy wszystkie commity z gałęzi głównej do żywej gałęzi, https://docs.microsoft.com/dotnet/a następnie będziesz mógł zobaczyć swój wkład na żywo w .

### <a name="contributing-to-samples"></a>Współtworzenie przykładów

Wprowadzamy następujące rozróżnienie dla kodu istniejącego w naszym repozytorium:

- Przykłady: czytelnicy mogą pobrać i uruchomić przykłady. Wszystkie przykłady powinny być kompletnymi aplikacjami lub bibliotekami. Gdy przykład tworzy bibliotekę, powinien on zawierać testy jednostkowe lub aplikację, która umożliwi czytelnikom uruchomienie kodu.

- Fragmenty kodu: ilustrują mniejszą koncepcję lub zadanie. Można je skompilować, ale nie mają one być kompletnymi aplikacjami.

Cały kod znajduje się w repozytorium [dotnet/samples](https://github.com/dotnet/samples). Pracujemy nad modelem, w którym struktura naszego folderu przykładów będzie pasować do struktury naszego folderu dokumentów. Do standardów, których przestrzegamy, należą:

- Folder *snippets* najwyższego poziomu zawiera fragmenty kodu dla małych, konkretnych przykładów.
- Przykłady referencyjne interfejsu API zostały w folderze następującym po tym wzorze: *urywki\</ język>/api/\<obszar nazw> /\<apiname>*.
- Inne foldery najwyższego poziomu są zgodne z folderami najwyższego poziomu w repozytorium *docs*. Na przykład w repozytorium docs jest folder *machine-learning/tutorials*, a przykłady dotyczące samouczków uczenia maszynowego są w folderze *samples/machine-learning/tutorials*.

Ponadto wszystkie przykłady w folderach *core* i *standard* powinny się skompilować i uruchomić na wszystkich platformach obsługiwanych przez platformę .NET Core. Nasz system kompilacji ciągłej integracji wymusi to. Folder najwyższego poziomu *framework* zawiera przykłady, które są kompilowane i weryfikowane tylko w systemie Windows.

Możemy rozszerzyć te katalogi, ponieważ repozytorium dokumentów dodaje nową zawartość. Na przykład dodamy katalogi Xamarin, takie jak `xamarin-ios` i `xamarin-android` katalogi.

Każdy kompletny przykład, który tworzysz, powinien zawierać plik *readme.md*. Ten plik powinien zawierać krótki opis przykładu (jeden lub dwa akapity). Plik *readme.md* powinien informować czytelników o tym, czego się dowiedzą, analizując ten przykład. Plik *readme.md* powinien też zawierać link do opublikowanego dokumentu w [witrynie dokumentacji platformy .NET](https://docs.microsoft.com/dotnet/welcome).
Aby ustalić, gdzie dany plik w repozytorium jest zamapowany na daną witrynę, zastąp fragment `/docs` w ścieżce repozytorium fragmentem `https://docs.microsoft.com/dotnet`.

Twój temat będzie też zawierał linki do przykładu. Link powinien prowadzić bezpośrednio do folderu przykładu w usłudze GitHub.

Aby uzyskać więcej informacji, zobacz [Przykłady Readme](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Interaktywna platforma języka C#

Krótkie przykłady kodu w języku C# mogą używać tagu języka `csharp-interactive` do określenia przykładu w języku C# uruchomionego w przeglądarce. (W przypadku fragmentów `csharp-interactive` kodu źródłowego należy użyć `code-csharp-interactive` znacznika w przypadku fragmentów kodu ze źródła). Te przykłady kodu wyświetlają okno kodu i okno wyjściowe w artykule. Okno wyjściowe pokazuje wszelkie dane wyjściowe po wykonaniu interaktywnego kodu, gdy użytkownik uruchomił przykład.

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

Nie musisz z góry podpisywać umowy. Możesz sklonować, rozwidlić i przekazać swoje żądanie ściągnięcia w zwykły sposób. Gdy Twoje żądanie ściągnięcia jest tworzone, jest ono klasyfikowane przez bota CLA. Jeśli zmiana jest trywialna (na przykład naprawiłeś literówkę), wówczas pr jest oznaczony etykietą `cla-not-required`. W przeciwnym razie jest ono klasyfikowane jako `cla-required`. Po podpisaniu umowy CLA bieżące i wszystkie przyszłe żądania ściągnięcia będą oznaczone jako `cla-signed`.
