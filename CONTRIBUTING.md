---
ms.openlocfilehash: 303d6790f1e4a42b021de3a214e3e7b44e1a4320
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104631"
---
# <a name="contributing"></a>Udział

Dziękujemy za zainteresowanie korzystaniem z dokumentacji platformy .NET.

> Jesteśmy w trakcie przechodzenia naszych wytycznych do przewodnika po całej lokacji. 
> Aby zapoznać się z nowymi wskazówkami, odwiedź stronę [Microsoft docs przewodnika](https://docs.microsoft.com/contribute/)współautora.

W dokumencie omówiono proces współtworzenia artykułów i przykładów kodu, które są hostowane w [witrynie dokumentacji programu .NET](https://docs.microsoft.com/dotnet). Wkłady mogą być bardzo proste jako poprawki literówki lub złożone jako nowe artykuły.

- [Proces współtworzenia](#process-for-contributing)
- [Środowisko C# interaktywne](#the-c-interactive-experience)
- [DOs i podstawowe](#dos-and-donts)
- [Umowa licencyjna współautora](#contributor-license-agreement)

To repozytorium zawiera dokumentację koncepcyjną dla platformy .NET. Witryna dokumentacji programu .NET została utworzona na podstawie wielu repozytoriów, a także do tego:

- [Przykłady i fragmenty kodu](https://github.com/dotnet/samples)
- [Dokumentacja interfejsu API](https://github.com/dotnet/dotnet-api-docs)
- [Dokumentacja zestawu SDK .NET Compiler Platform](https://github.com/dotnet/roslyn-api-docs)

Problemy i zadania dla wszystkich tych repozytoriów są śledzone w tym miejscu.

## <a name="process-for-contributing"></a>Proces współtworzenia

Potrzebna jest podstawowa znajomość usługi [git i GitHub.com](https://guides.github.com/activities/hello-world/).

**Krok 1:** Pomiń ten krok w przypadku małych zmian (na przykład w przypadku korygowania literówki lub natychmiastowego otwarcia żądania ściągnięcia w celu rozwiązania problemu znalezionego w dokumentacji). Jeśli interesuje Cię Pisanie nowej zawartości lub dokładne poprawianie istniejącej zawartości, Otwórz [problem](https://github.com/dotnet/docs/issues) z opisem tego, co chcesz zrobić.
Zawartość w folderze **docs** jest zorganizowana w sekcje, które są odzwierciedlone w spisie treści (TOC). Zdefiniuj, gdzie temat będzie znajdował się w spisie treści. Uzyskaj opinię na temat propozycji.

—lub—

Możesz również wybrać spośród istniejących problemów, dla których wkłady społecznościowe są powitane. [Projekty dla współautorów społeczności .NET](https://github.com/dotnet/docs/projects/35) wyświetlają wiele elementów roboczych, które są dostępne dla współautorów społecznościowych. W zależności od zainteresowań i poziomu zobowiązań możesz wybierać spośród problemów w następujących kategoriach:

- **Konserwacja**. Ta kategoria obejmuje dość proste wkłady, takie jak Naprawianie uszkodzonych lub nieprawidłowych linków, Dodawanie brakujących przykładów kodu lub Rozwiązywanie problemów z zawartością. W niektórych przypadkach te problemy mogą dotyczyć dużej liczby plików. W takim przypadku należy poinformować nas, co chcesz zrobić, zanim zaczniesz.

- **Aktualizacje zawartości**. Po enormity zestawu dokumentów zawartość jest łatwo przestarzała i wymaga poprawki. Ponadto z różnych przyczyn część zawartości została zduplikowana lub nawet triplicated. Aktualizacja zawartości polega na tym, że poszczególne tematy są aktualne lub poprawiają zawartość w obszarze funkcji w celu wyeliminowania duplikatów i zapewnienia, że cała unikatowa zawartość jest zachowywana w mniejszych zestawach dokumentacji.

- **Tworzenie nowej zawartości**. Jeśli interesuje Cię Tworzenie własnego tematu, te problemy mogą zostać dodane do naszego zestawu dokumentów. Daj nam znać przed rozpoczęciem pracy z tematem. Jeśli interesuje Cię pisanie tematu, którego nie ma na liście, Otwórz problem. 

Możesz również zapoznać się z naszą listą [problemów otwartych](https://github.com/dotnet/docs/issues) i od osoby zależnej, aby zacząć korzystać z interesujących Cię elementów. Używamy etykiety [up-for-](https://github.com/dotnet/docs/labels/up-for-grabs) dodaliśmy do tagów problemów otwartych dla udziału. 

**Krok 2:** Rozwidlenie lub`dotnet/dotnet-api-docs` repozytoria w razie potrzeby i utworzenie gałęzi dla zmian. `dotnet/samples` `dotnet/docs`

W przypadku małych zmian można użyć interfejsu internetowego usługi GitHub. Po prostu kliknij pozycję **Edytuj plik w rozwidleniu tego projektu** w pliku, który chcesz zmienić. W witrynie GitHub zostanie utworzona nowa gałąź po przesłaniu zmian.

**Krok 3.** Wprowadź zmiany w tej nowej gałęzi.

Jeśli jest to nowy temat, możesz użyć tego [pliku szablonu](./styleguide/template.md) jako punktu początkowego. Zawiera wytyczne dotyczące pisania i objaśnia metadane wymagane dla każdego artykułu, takie jak informacje o autorze.

Przejdź do folderu, który odpowiada lokalizacji spisu treści określonego dla artykułu w kroku 1.
Ten folder zawiera pliki promocji dla wszystkich artykułów w tej sekcji.
W razie potrzeby utwórz nowy folder, aby umieścić pliki dla zawartości. Główny artykuł dotyczący tej sekcji nosi nazwę *index.MD*.
W przypadku obrazów i innych zasobów statycznych utwórz podfolder o nazwie **multimedia** w folderze zawierającym artykuł, jeśli jeszcze nie istnieje. W folderze **Media** utwórz podfolder o nazwie artykułu (z wyjątkiem pliku indeksu).
Uwzględnij większe próbki w folderze Samples w katalogu głównym repozytorium.

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

**Krok 4.** Prześlij żądanie ściągnięcia z gałęzi do `dotnet/docs/master`.

Żądanie ściągnięcia powinno *zawsze* wskazywać główną gałąź. *Nigdy nie* należy otwierać żądania ściągnięcia, które jest przeznaczone dla aktywnej gałęzi.

Każdy element żądania ściągnięcia powinien zwykle dotyczyć jednego problemu w danym momencie. Żądanie ściągnięcia może zmodyfikować jeden lub wiele plików. W przypadku rozwiązywania wielu poprawek w różnych plikach preferowane są osobne żądań ściągnięcia.

Jeśli żądanie ściągnięcia dotyczy istniejącego problemu, Dodaj `Fixes #Issue_Number` słowo kluczowe do komunikatu zatwierdzenia lub opisu żądania ściągnięcia. W ten sposób problem zostanie automatycznie zamknięty po scaleniu żądania ściągnięcia. Aby uzyskać więcej informacji, zobacz [zamykanie problemów za pomocą komunikatów zatwierdzania](https://help.github.com/articles/closing-issues-via-commit-messages/).

Zespół platformy .NET sprawdzi swój stan żądania ściągnięcia i poinformuje o tym, czy istnieją inne aktualizacje/zmiany niezbędne do zatwierdzenia.

**Krok 5.** Wykonaj wszelkie niezbędne aktualizacje gałęzi, jak to opisano w zespole.

W przypadku, gdy zastosowana została opinia i zostanie zatwierdzona zmiana zostanie scalona żądanie ściągnięcia z gałęzią główną.

W przypadku niektórych erze wszystkie zatwierdzenia z gałęzi głównej są przekazywane do aktywnej gałęzi, a następnie będzie można zobaczyć swój udział na https://docs.microsoft.com/dotnet/ żywo.

### <a name="contributing-to-samples"></a>Współtworzenie przykładów

Dla kodu, który istnieje w naszym repozytorium, wprowadzimy następujące rozróżnienia:

- Przykłady: czytelnicy mogą pobrać i uruchomić przykłady. Wszystkie przykłady powinny być kompletnymi aplikacjami lub bibliotekami. Gdzie przykład tworzy bibliotekę, powinna obejmować testy jednostkowe lub aplikację, która umożliwia czytelnikom uruchamianie kodu.

- Fragmenty kodu: ilustrują mniejszą koncepcję lub zadanie. Są one kompilowane, ale nie są przeznaczone do kompletnych aplikacji.

Kod wszystkie są przechowywane w repozytorium [dotnet/Samples](https://github.com/dotnet/samples) . Pracujemy nad modelem, w którym nasze przykłady struktury folderów są zgodne z naszą strukturą folderów docs. Stosowane są następujące standardy:

- Folder *wstawek* najwyższego poziomu zawiera fragmenty kodu dla małych, ukierunkowanych próbek.
- Przykłady referencyjne interfejsu API znajdują się w folderze następującym po tym wzorcu: *fragmenty\<kodu/język >\</API/\<przestrzeni nazw >/apiname >* .
- Inne foldery najwyższego poziomu są zgodne z folderami najwyższego poziomu w repozytorium *docs* . Na przykład repozytorium docs zawiera folder uczenie *maszynowego/samouczków* , a przykłady samouczków dotyczących uczenia maszynowego znajdują się w folderze *Samples/Machine-Learning/samouczki* .

Ponadto wszystkie przykłady w folderach *podstawowe* i *standardowe* powinny być kompilowane i uruchamiane na wszystkich platformach obsługiwanych przez platformę .NET Core. Nasz system kompilacji elementu konfiguracji będzie wymuszać to. Folder *struktury* najwyższego poziomu zawiera przykłady, które są kompilowane i sprawdzane tylko w systemie Windows.

Firma Microsoft może rozszerzyć te katalogi, ponieważ repozytorium docs dodaje nową zawartość. Na przykład dodamy katalogi platformy Xamarin, jak `xamarin-ios` i `xamarin-android` katalogi.

Każdy kompletny przykład tworzony przez Ciebie powinien zawierać plik *README.MD* . Ten plik powinien zawierać Krótki opis przykładu (jeden lub dwa akapity). Twoja *README.MD* powinna poinformować czytelników, co pouczy się, eksplorowanie tego przykładu. Plik *README.MD* powinien również zawierać link do dokumentu na żywo w [witrynie dokumentacji programu .NET](https://docs.microsoft.com/dotnet/welcome).
Aby określić, gdzie dany plik w repozytorium jest mapowany na tę lokację, `/docs` Zastąp ciąg `https://docs.microsoft.com/dotnet`ścieżką.

Temat zawiera również linki do przykładu. Połącz bezpośrednio z folderem przykładu w usłudze GitHub.

Aby uzyskać więcej informacji, zobacz [plik Readme przykładów](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Środowisko C# interaktywne

Krótkie przykłady kodu w C# programie mogą użyć `csharp-interactive` znacznika języka, aby określić C# próbkę, która jest uruchamiana w przeglądarce. (Wbudowane przykłady kodu używają `csharp-interactive` znacznika, w przypadku fragmentów zawartych ze źródła, `code-csharp-interactive` Użyj tagu). Te przykłady kodu zawierają okno kod i okno dane wyjściowe w artykule. W oknie dane wyjściowe są wyświetlane wszystkie dane wyjściowe z wykonywania kodu interaktywnego, gdy użytkownik uruchomi przykład. 

C# Interaktywny proces zmienia sposób pracy z przykładami. Odwiedzający mogą uruchomić przykład, aby zobaczyć wyniki. Wiele czynników pomaga ustalić, czy próbka lub odpowiedni tekst powinien zawierać informacje o danych wyjściowych.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Kiedy mają być wyświetlane oczekiwane dane wyjściowe bez uruchamiania przykładu

- Artykuły przeznaczone dla początkujących powinny dostarczyć dane wyjściowe, dzięki czemu czytelnicy mogą porównać wyniki pracy z oczekiwaną odpowiedzią.
- Próbki, w których dane wyjściowe są integralne względem tematu, powinny wyświetlać te dane wyjściowe. Na przykład artykuły na sformatowanym tekście powinny zawierać format tekstu bez uruchamiania przykładu.
- Gdy zarówno próbka, jak i oczekiwane dane wyjściowe są krótkie, należy rozważyć wyświetlanie danych wyjściowych. Oszczędza czas.
- Artykuły objaśniające, w jaki sposób bieżąca kultura lub Niezmienna kultura ma wpływ na dane wyjściowe powinny wyjaśnić oczekiwane dane wyjściowe. Interaktywna REPL (odczyt) jest uruchamiana na hoście opartym na systemie Linux. Kultura domyślna i Niezmienna kultura tworzą różne dane wyjściowe w różnych systemach operacyjnych i komputerach. W tym artykule wyjaśniono dane wyjściowe w systemach Windows, Linux i Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Kiedy należy wykluczyć oczekiwane dane wyjściowe z przykładu 

- Artykuły, w których próbka generuje większe dane wyjściowe nie powinny uwzględniać tego w komentarzach. Po uruchomieniu próbki program zasłania kod.
- Artykuły, w których przykład ilustruje temat, ale dane wyjściowe nie są integralną częścią tego tematu. Na przykład kod, który uruchamia zapytanie LINQ, aby wyjaśnić składnię zapytania, a następnie wyświetlić każdy element w kolekcji wyjściowej.

## <a name="dos-and-donts"></a>DOs i podstawowe

Na poniższej liście przedstawiono niektóre reguły identyfikatorów GUID, które należy wziąć pod uwagę podczas korzystania z dokumentacji programu .NET:

- **Nie ryzykuj** nas z dużymi żądaniami ściągnięcia. Zamiast tego należy rozwiązać problem i zacząć dyskusję, dzięki czemu możemy wyrazić zgodę na kierunek przed zainwestowaniem dużej ilości czasu.
- Przeczytaj [Przewodnik po stylu](./styleguide/template.md) i wskazówki dotyczące [głosu i tonu](./styleguide/voice-tone.md) .
- Użyj pliku [szablonu](./styleguide/template.md) jako punktu początkowego pracy.
- Przed rozpoczęciem pracy z artykułami utwórz oddzielną gałąź w rozwidleniu.
- Postępuj zgodnie z [przepływem pracy przepływu usługi GitHub](https://guides.github.com/introduction/flow/).
- Bądź na blogu i Tweety (lub niezależnie od tego) o Twoje wkłady — często!

> Uwaga: możesz zauważyć, że niektóre tematy nie są obecnie zgodne ze wszystkimi wytycznymi określonymi tutaj i w przewodniku po [stylu](./styleguide/template.md) . Pracujemy nad osiągnięciem spójności w całej lokacji. Sprawdź listę [otwartych problemów](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) , które obecnie są śledzone dla tego konkretnego celu.

## <a name="contributor-license-agreement"></a>Umowa licencyjna współautora

Przed scaleniem żądania ściągnięcia należy podpisać [umowę licencyjną programu .NET Foundation (CLA)](https://cla.dotnetfoundation.org) . Jest to jednorazowe wymaganie dla projektów w programie .NET Foundation. Więcej informacji na temat [umów licencyjnych dotyczących udziałów (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) można znaleźć w witrynie Wikipedia.

Umowa: [NET-Foundation-Contribution-License-Agreement. PDF](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Nie musisz podpisać umowy z góry. Można klonować, rozwidlenie i przesłać żądanie ściągnięcia w zwykły sposób. Po utworzeniu żądania ściągnięcia jest ono klasyfikowane przez CLA bot. Jeśli zmiana jest prosta (na przykład Naprawiono literówki), żądanie ściągnięcia jest oznaczone etykietą `cla-not-required`. W przeciwnym razie jest sklasyfikowany `cla-required`jako. Po podpisaniu CLA bieżące i wszystkie przyszłe żądania ściągnięcia są oznaczone jako `cla-signed`.
