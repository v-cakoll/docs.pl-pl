# <a name="contributing"></a>Współtworzenie

Dziękujemy za zainteresowanie Współtworzenie dokumentacji platformy .NET!

> Jesteśmy w trakcie przenoszenia nasze wskazówki w przewodniku po współtworzeniu całej lokacji. 
> Aby zobaczyć nowe wskazówki, odwiedź stronę [przewodnik współautora Microsoft Docs — omówienie](https://docs.microsoft.com/contribute/).

Dokument obejmuje procesu współtworzenia artykułów i przykłady kodu, które są hostowane na [witrynie dokumentacji .NET](https://docs.microsoft.com/dotnet). Wkład może być tak proste, jak Literówka poprawki lub tak złożonego jak nowe artykuły.

* [Proces przekazywania](#process-for-contributing)
* [C# Interaktywnego środowiska](#the-c-interactive-experience)
* [Zalecenia i zakazy](#dos-and-donts)
* [Umowę licencyjną współautora](#contributor-license-agreement)

To repozytorium zawiera dokumentacji koncepcyjnego dla platformy .NET. Witrynie dokumentacji .NET składa się z wieloma repozytoriami, oprócz tego:

- [Przykłady kodu i fragmentów kodu](https://github.com/dotnet/samples)
- [Dokumentacja interfejsu API](https://github.com/dotnet/dotnet-api-docs)
- [Odwołanie do zestawu SDK platformy kompilatora .NET](https://github.com/dotnet/roslyn-api-docs)

Zagadnienia i zadania dla tych repozytoriów są śledzone w tym miejscu.

## <a name="process-for-contributing"></a>Proces przekazywania

Potrzebujesz podstawową wiedzę na temat [Git i GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Pomiń ten krok w przypadku niewielkich zmian. Jeśli interesują w pisaniu nowych treści lub dokładnie zmieniającego istniejącej zawartości, należy otworzyć [problem](https://github.com/dotnet/docs/issues) opisujący, co chcesz zrobić.
Zawartość wewnątrz **docs** folderu jest podzielona na sekcje, które są odzwierciedlone w tabeli z treści (TOC). Zdefiniuj lokalizację tematu w spisie treści. Uzyskiwanie opinii na temat swojej propozycji.

—lub—

Możesz również z istniejących problemów dla społeczności, które obejmują powitalnej. [Projekty dla platformy .NET społeczności](https://github.com/dotnet/docs/projects/35) zawiera wiele elementów roboczych, które są dostępne dla społeczności. W zależności od zainteresowań i poziomu zobowiązania można wybrać problemów w następujących kategoriach:

- **Konserwacja**. Ta kategoria obejmuje dość proste wkładów, takie jak ustalania uszkodzone lub nieprawidłowe linki, dodanie brakujących przykładów kodu lub adresowania ograniczone zawartości problemów. W niektórych przypadkach te problemy mogą dotyczyć dużą liczbę plików. W takiej sytuacji należy Daj nam znać, co chcesz pracować nad przed przystąpieniem do wykonywania.

- **Aktualizacje zawartości**. Biorąc pod uwagę enormity zestawu dokumentacji, zawartość łatwo stają się nieaktualne i wymaga poprawek. Ponadto z różnych przyczyn część zawartości została zduplikowana lub nawet triplicated. Aktualizowanie zawartości obejmuje upewnienie się, że poszczególne tematy są bieżące lub zmieniającego zawartość obszaru funkcji, aby nie zawierała dublowania i upewnij się, że cała zawartość unikatowy jest zachowywany w mniejszych dokumentacji zestawu.

- **Nowe tworzenia zawartości**. Jeśli interesuje Cię Tworzenie własnego tematu, te problemy listę tematów, w których wiemy, że chcemy dodać do naszego zestawu dokumentacji. Daj nam znać przed rozpoczęciem pracy z tematem, mimo że. Jeśli interesuje Cię pisania tematu, który nie ma na liście, otwórz problem. 

Można także przyjrzeć się nasze [zgłaszanie problemów](https://github.com/dotnet/docs/issues) listy i volunteer do pracy nad tymi interesuje Cię. Używamy [w górę do chwyty](https://github.com/dotnet/docs/labels/up-for-grabs) etykietę do tagu problemy otwarte dla udziału. 

**Krok 2:** Rozwidlenia `dotnet/docs`, `dotnet/samples` lub `dotnet/dotnet-api-docs` repozytoriów jako potrzebne i utwórz gałąź dla Twoich zmian.

Dla niewielkich zmian można użyć interfejsu sieci web usługi GitHub. Po prostu kliknij **Edytuj plik w Twoim rozwidleniu ten projekt** w pliku, czy chcesz zmienić. GitHub tworzy nową gałąź dla Ciebie, po przesłaniu zmian.

**Krok 3:** Wprowadź zmiany w tej nowej gałęzi.

Jeśli jest to nowy temat, możesz użyć tej funkcji [plik szablonu](./styleguide/template.md) jako punktu początkowego. Zawiera wskazówki dotyczące pisania i wyjaśniono również metadane wymagane dla każdego artykułu, takie jak informacje o autorze.

Przejdź do folderu, który odnosi się do lokalizacji spisu treści dla artykułu w kroku 1.
Ten folder zawiera pliki Markdown wszystkie artykuły w tej sekcji.
Jeśli to konieczne, Utwórz nowy folder do umieszczenia plików zawartości. Główny artykuł w tej sekcji jest nazywany *index.md*.
W przypadku obrazów i inne zasoby statyczne, utworzyć podfolder o nazwie **media** wewnątrz folderu, który zawiera artykuł, jeśli jeszcze nie istnieje. Wewnątrz **media** folderze utwórz podfolder o nazwie artykułu (z wyjątkiem pliku indeksu).
Obejmują większych próbek w *przykłady* folder w katalogu głównym repozytorium.

Pamiętaj wykonać poprawnej składni języka Markdown. Aby uzyskać więcej informacji, zobacz [przewodnik stylistyczny](./styleguide/template.md).

### <a name="example-structure"></a>Przykład struktury

    docs
      /about
      /core
        /porting
          porting-overview.md
          /media
            /porting-overview
                portability_report.png

**Krok 4:** Prześlij ściągnięcia żądania (PR) z gałęzi `dotnet/docs/master`.

Żądanie Ściągnięcia powinno *zawsze* docelowych gałęzi głównej. Należy *nigdy nie* Otwórz żądania Ściągnięcia, który jest przeznaczony dla gałęzi aktywnej.

Każdego żądania Ściągnięcia powinien zwykle adres jednym problemem w danym momencie. Żądania Ściągnięcia można zmodyfikować jeden lub wiele plików. Jeśli masz adresowania wiele poprawek dla innych plików, oddzielne żądania ściągnięcia są preferowane.

Jeśli żądanie Ściągnięcia jest adresowanie istniejący problem, Dodaj `Fixes #Issue_Number` — słowo kluczowe komunikat dotyczący zatwierdzenia lub opis żądania Ściągnięcia. W ten sposób ten problem zostanie zamknięty automatycznie po scaleniu żądania Ściągnięcia. Aby uzyskać więcej informacji, zobacz [zamyka problemy za pośrednictwem wiadomości z zatwierdzeń](https://help.github.com/articles/closing-issues-via-commit-messages/).

Zespół .NET przejrzy żądanie Ściągnięcia i powiadomienie Cię o tym, czy istnieją inne aktualizacje/zmiany niezbędne, aby można było ją zatwierdzić.

**Krok 5:** Wprowadź wymagane zmiany w gałęzi, zgodnie z opisem z zespołem.

Maintainers spowoduje scalenie żądania Ściągnięcia z gałęzią główną, po zastosowaniu opinii i zmiana zostaje zatwierdzona.

W erze przesuwamy wszystkich zatwierdzeń z głównej gałęzi do gałęzi aktywnej, a następnie będzie można wyświetlić Twój wkład Konferencję https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Współtworzenie przykłady

Ułatwiamy rozróżnienie następujący kod, który znajduje się w naszym repozytorium:

- Przykłady: czytelnicy pobierania i uruchamiania przykładów. Wszystkie przykłady powinna być pełną aplikacji lub biblioteki. W przypadku, gdy przykładowa aplikacja tworzy bibliotekę, powinien zawierać, testy jednostkowe lub aplikacji, która umożliwia czytelnicy wykonywania kodu.

- fragmenty kodu: ilustrują mniejszych koncepcji lub zadania. Skompilować one, ale nie mają one być ukończone aplikacje.

Kod wszystkie powiązane z nimi [dotnet/samples](https://github.com/dotnet/samples) repozytorium. Pracujemy nad na model, w których nasze przykłady strukturę folderów odpowiada naszych docs strukturę folderów. Dostępne są następujące standardy, które możemy wykonać:

- Najwyższego poziomu *fragmenty* folder zawiera fragmenty małe, ukierunkowane przykładów.
- Przykłady dokumentacja interfejsu API zostały w folderze, zgodnie z tego wzorca: *fragmenty /\<języka > /api/\<przestrzeni nazw > /\<apiname >*.
- Inne foldery najwyższego poziomu dopasowania foldery najwyższego poziomu w *docs* repozytorium. Na przykład repozytorium dokumentów ma *machine-learning/samouczki* folder i przykłady, machine learning samouczki znajdują się w *samples /-learning/samouczki na temat maszyny* folderu.

Ponadto wszystkie przykłady w obszarze *core* i *standardowa* folderów należy skompilować i uruchomić na wszystkich platformach obsługiwanych przez platformy .NET Core. Nasz system kompilacji CI będzie wymuszać który. Najwyższego poziomu *framework* folder zawiera przykłady, które są kompilowane i tylko sprawdzone na Windows.

Możemy rozwinąć te katalogi jako repozytorium dokumentów dodaje nową zawartość. Na przykład dodamy katalogów platformy Xamarin, takie jak `xamarin-ios` i `xamarin-android` katalogów.

Pełny przykład, z którą tworzysz powinien zawierać *readme.md* pliku. Ten plik powinien zawierać krótki opis przykładu (jednej lub dwóch akapitów). Twoje *readme.md* powinien poinformować czytelnicy, co przedstawiono eksplorując ten przykład. *Readme.md* plik powinien również zawierać łącze do dokumentu na żywo na [witrynie dokumentacji .NET](https://docs.microsoft.com/dotnet/welcome).
Aby określić, gdzie dany plik w repozytorium jest mapowany na tę lokację, należy zastąpić `/docs` w ścieżce repozytorium za pomocą `https://docs.microsoft.com/dotnet`.

Twój temat zawiera również linki do przykładu. Link bezpośrednio do folderu przykładu, w witrynie GitHub.

Aby uzyskać więcej informacji, zobacz [Readme przykłady](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>C# Interaktywnego środowiska #

Krótkie przykłady kodu w C# służy `csharp-interactive` tagu języka, aby określić C# próbki, która działa w przeglądarce. (Użyj przykłady kodu wbudowanego `csharp-interactive` tag fragmenty uwzględnione ze źródła do używania `code-csharp-interactive` tagu.) Te przykłady kodu wyświetlenia okna Kod i dane wyjściowe w artykule. W oknie danych wyjściowych Wyświetla wszelkie dane wyjściowe wykonania kodu interaktywnego po użytkownik ma uruchomienia przykładu. 

C# Interaktywnego środowiska zmieni się, jak pracujemy z przykładów. Osoby odwiedzające można uruchomić przykład, aby zobaczyć wyniki. Wiele czynników pomóc określić, jeśli próbka lub odpowiedni tekst powinien zawierać informacje o danych wyjściowych.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kiedy należy wyświetlić oczekiwane dane wyjściowe bez konieczności uruchamiania przykładu

- Artykuły, przeznaczone dla początkujących powinny dostarczyć dane wyjściowe, tak, aby czytelnicy mogą porównasz dane wyjściowe swojej pracy oczekiwanej odpowiedzi.
- Przykłady, których wynikiem jest integralną częścią tematu powinno wyświetlać te dane wyjściowe. Na przykład artykuły dotyczące sformatowany tekst powinien być wyświetlony format tekstu bez konieczności uruchamiania przykładu.
- W przypadku zarówno próbkę, jak i oczekiwanych danych wyjściowych jest krótki, należy rozważyć, wyświetlanie danych wyjściowych. Można zaoszczędzić trochę czasu.
- Artykuły objaśniające sposób bieżącej kultury lub niezmiennej kultury mogą wpłynąć na dane wyjściowe powinny wyjaśnić oczekiwanych danych wyjściowych. Interaktywna pętla REPL (pętli drukowania oceny odczytu) działa na hoście z systemem Linux. Domyślnej kultury i kultury niezmiennej dawać różne wyniki w różnych systemach operacyjnych i na maszynach. Artykuł powinien opisano dane wyjściowe w systemach Windows, Linux i Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kiedy należy wykluczyć oczekiwane dane wyjściowe z przykładu 

- Artykuły, gdzie przykład generuje większe dane wyjściowe nie powinien zawierać, komentarze. Po uruchomieniu przykładu, ukrywa kod.
- Artykuły, gdzie w przykładzie pokazano tematu, ale wynik nie jest integralną częścią zrozumienia. Na przykład kod, który uruchamia zapytanie LINQ, aby wyjaśnić składni zapytań, a następnie Wyświetl każdego elementu w kolekcji danych wyjściowych.

## <a name="dos-and-donts"></a>Zalecenia i zakazy

Poniższa lista zawiera pewne wskazówki reguł, które należy mieć na uwadze, gdy masz Współtworzenie dokumentacji platformy .NET:

- **Nie** zaskakującymi nas o dużych żądań ściągnięcia. Zamiast tego należy zgłosić problem i Rozpocznij dyskusję, dzięki czemu można firma Microsoft zobowiązuje się w kierunku, zanim inwestować dużą ilość czasu.
- **CZY** odczytu [przewodnik stylistyczny](./styleguide/template.md) i [połączeń głosowych i ton](./styleguide/voice-tone.md) wytycznych.
- **CZY** użyj [szablonu](./styleguide/template.md) pliku jako punktu początkowego swoją pracę.
- **CZY** tworzenie oddzielnej gałęzi w rozwidleniu przed rozpoczęciem pracy w artykułach.
- **CZY** wykonaj [przepływu pracy przepływu usługi GitHub](https://guides.github.com/introduction/flow/).
- **CZY** blogu i tweet (lub niezależnie od rodzaju) o współtworzeniu, często!

> Uwaga: możesz mogą zauważyć, że niektóre tematy są obecnie następujące wszystkie wskazówki, które są określone w tym miejscu i na [przewodnik stylistyczny](./styleguide/template.md) także. Pracujemy nad do osiągnięcia spójności w całej lokacji. Sprawdź listę [zgłaszanie problemów](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) firma Microsoft obecnie śledzonych dla tego określonego celu.

## <a name="contributor-license-agreement"></a>Umowę licencyjną współautora

Musisz zalogować się [.NET Foundation wkład internetowej umowy licencyjnej (CLA)](https://cla.dotnetfoundation.org) przed scaleniu żądania Ściągnięcia. Jest to jednorazowe wymaganie dla projektów w .NET Foundation. Przeczytaj więcej o [internetowej umowy licencyjnej współautorstwa (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) w witrynie Wikipedia.

Umowa: [net-foundation wkład licencji agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Nie masz w celu podpisania Umowy z góry. Można sklonować, rozwidlenia i przesyłania żądania Ściągnięcia w zwykły sposób. Po utworzeniu żądania Ściągnięcia jest klasyfikowana przez bota CLA. Jeśli ta zmiana jest prosta (na przykład naprawiono błąd pisowni), a następnie żądanie Ściągnięcia jest oznaczony `cla-not-required`. W przeciwnym razie jest klasyfikowana jako `cla-required`. Po zalogowaniu CLA, żądań ściągnięcia bieżących i przyszłych wszystkie są oznaczone jako `cla-signed`.
