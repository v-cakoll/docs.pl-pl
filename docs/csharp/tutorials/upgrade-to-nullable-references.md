---
title: Projektowanie w przypadku typów referencyjnych dopuszczającego wartość null
description: W tym samouczku zaawansowane zawiera wprowadzenie do typów referencyjnych dopuszczającego wartość null. Dowiesz się, że express projektu chcący po wartości odniesienia może mieć wartości null i pozwolić kompilatorowi wymusić, gdy nie może mieć wartości null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 289b864aaa0380a31e93ef223fb5b5780e35892a
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195848"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Samouczek: Migrowanie istniejącego kodu w przypadku typów referencyjnych dopuszczającego wartość null

C#8 wprowadzono **typy dopuszczające wartości null odwołań**, które odwołania uzupełnieniem typów taki sam sposób, typy o wartości zerowalnej uzupełniają typów wartości. Zadeklaruj zmienną **typu dopuszczającego wartość null odwołania** , dodając `?` do typu. Na przykład `string?` reprezentuje dopuszczający wartości null `string`. Te nowe typy można użyć, aby wyraźniej express zgodną z planem projektu: niektóre zmienne *zawsze musi mieć wartość*, inne *może brakować wartość*. Żadnych istniejących zmiennych typu odwołania może być interpretowany jako typ odwołania nie dopuszcza wartości null. 

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> * Włącz sprawdzanie odwołania o wartości null, podczas pracy z kodem.
> * Zdiagnozować i rozwiązać inny ostrzeżenia dotyczące wartości null.
> * Zarządzaj interfejs między dopuszczającego wartość null kontekstów wyłączone włączone i dopuszcza wartości null.
> * Kontrolowanie kontekstów annotation dopuszczający wartość null.

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 beta. C# 8 kompilatora w wersji beta jest dostępna z [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), lub r [.NET Core 3.0 w wersji zapoznawczej](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.

## <a name="explore-the-sample-application"></a>Zapoznaj się z przykładowej aplikacji

Przykładowa aplikacja będzie migracji jest czytnik źródła danych RSS aplikacji sieci web. Odczytuje z jednego źródła danych RSS i wyświetla podsumowania dla najnowsze artykuły. Możesz kliknąć dowolny z tych artykułów do witryny. Aplikacja jest stosunkowo nowe, ale zostały zapisane przed typy dopuszczające wartości null odwołań były dostępne. Decyzje dotyczące projektu dla aplikacji reprezentowane dźwięku zasad, ale nie korzystać z zalet tej funkcji języka ważna.

Przykładowa aplikacja zawiera Biblioteka testów jednostkowych, która weryfikuje najważniejsze funkcje aplikacji. Ten projekt ułatwi uaktualnić bezpieczne, jeśli zmienisz jakiekolwiek implementacji, w oparciu o ostrzeżenia wygenerowane. Możesz pobrać kod początkowy, od [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) repozytorium GitHub.

Celem projektu migracji powinno być wykorzystać nowe funkcje języka, dzięki czemu wyraźnie express zgodne z zamiarami użytkownika w dopuszczania wartości null, zmiennych i to zrobić w taki sposób, że kompilator nie generuje ostrzeżenia w przypadku kontekstu annotation dopuszczający wartość null i dopuszcza wartości null kontekstu ostrzeżenie równa `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Uaktualnianie projektów do C# 8

Dobre, pierwszym krokiem jest określenie zakresu zadania migracji. Rozpoczyna się od uaktualnienia projektu C# 8.0 (lub nowsza). Dodaj `LangVersion` elementu, aby oba pliki csproj dla projektu sieci web i projektu testu jednostkowego:

```xml
<LangVersion>8.0</LangVersion>
```

Uaktualnianie wersji językowej wybiera C# 8.0, ale nie uwzględnia kontekst annotation dopuszczający wartość null lub wartość null kontekst ostrzeżenie. Ponownie skompiluj projekt, aby upewnić się, że opiera się bez ostrzeżeń.

Dobre, następnym krokiem jest Włącz kontekstu annotation dopuszczający wartość null i zobacz, jak wiele ostrzeżeń są generowane. Dodaj następujący element w obu plikach csproj w rozwiązaniu bezpośrednio pod `LangVersion` elementu:

```xml
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> `Nullable` Poprzednia nazwa elementu `NullableContextOptions`. Zmień nazwę dostarczany z programem Visual Studio 2019 r, 16.2 p1. 3.0.100-preview5-011568 zestawu .NET Core SDK nie ma tej zmiany. Jeśli używasz interfejsu wiersza polecenia platformy .NET Core, musisz użyć `NullableContextOptions` aż do następnej wersji zapoznawczej.

Czy kompilacja testowa i zwróć uwagę na liście ostrzeżenie. W małych aplikacji kompilator generuje ostrzeżenia pięć, więc prawdopodobnie spowoduje pozostawienie kontekstu annotation dopuszczający wartość null włączone i rozpocząć rozwiązywanie ostrzeżenia dla całego projektu.

Taka strategia działa tylko w przypadku mniejszych projektów. Dla wszystkich projektów, większe, liczba ostrzeżeń generowanych przez włączenie kontekstu annotation dopuszczający wartość null w całej bazie kodu utrudnia ustalenie ostrzeżenia systematycznie. Dla większych projektów w przedsiębiorstwie często należy przeprowadzić migrację jeden projekt naraz. W każdym projekcie migrację jednej klasy lub pliku w danym momencie.

## <a name="warnings-help-discover-original-design-intent"></a>Ostrzeżenia ułatwić, wykrywanie oryginalne założenia projektowe

Istnieją dwie klasy, które generują wiele ostrzeżeń. Rozpoczynać `NewsStoryViewModel` klasy. Usuń `Nullable` elementu z obu plików csproj dzięki czemu można ograniczyć zakres ostrzeżeń w sekcjach dotyczących pracy z kodem. Otwórz *NewsStoryViewModel.cs* pliku i dodaj następujące dyrektywy, aby umożliwić kontekst annotation dopuszczający wartość null dla `NewsStoryViewModel` i przywrócić ją po tej definicji klasy:

```csharp
#nullable enable
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; }
    public string Uri { get; set; }
}
#nullable restore
```

Te dwa dyrektywy pomóc Ci skoncentrować się na migracji. Ostrzeżenia dopuszcza wartości null są generowane dla obszaru kodu aktywnie pracuje. Opuścisz je na aż wszystko będzie gotowe włączyć ostrzeżenia dla całego projektu. Należy używać `restore` zamiast `disable` wartości, tak aby nie przypadkowo wyłączysz kontekście później po włączeniu adnotacje dopuszczającego wartość null dla całego projektu. Po włączeniu kontekstu annotation dopuszczający wartość null dla całego projektu można usunąć wszystkich `#nullable` pragm z tego projektu.

`NewsStoryViewModel` Klasy jest obiekt transferu danych (DTO), a dwie właściwości są ciągami odczyt/zapis:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Te dwie właściwości spowodować `CS8618`, "nieprzyjmujące właściwość została zainicjowana". Który ma wystarczająco dużo, wyczyść: zarówno `string` właściwości mają wartość domyślną `null` podczas `NewsStoryViewModel` jest konstruowany. Co to jest ważne dowiedzieć się, jest sposób `NewsStoryViewModel` obiekty są konstruowane. Patrząc tej klasy, nie wiadomo, jeśli `null` wartość jest częścią projektu lub jeśli te obiekty są skonfigurowane do innych niż null wartości w każdym przypadku, gdy jeden jest tworzony. Wątki wiadomości są tworzone w `GetNews` metody `NewsService` klasy:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Brak znacznej w poprzednim bloku kodu. Ta aplikacja używa [AutoMapper](https://automapper.org/) pakiet NuGet do skonstruowania elementu wiadomości z `ISyndicationItem`. Już znasz, że elementów historii wiadomości są zbudowane i właściwości są ustawione w tym jednej instrukcji. Oznacza to, że projekt `NewsStoryViewModel` wskazuje, że te właściwości nigdy nie powinny mieć `null` wartość. Te właściwości powinny być **typów referencyjnych kolumną**. Najlepiej wyraża oryginalne założenia projektowe. W rzeczywistości wszystkie `NewsStoryViewModel` *jest* poprawnie utworzone za pomocą wartości innych niż null. Sprawia to, że następująca Inicjalizacja prawidłową poprawkę kodu:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Przypisywanie `Title` i `Uri` do `default` czyli `null` dla `string` typu nie zmienia zachowanie środowiska uruchomieniowego programu. `NewsStoryViewModel` Nadal jest konstruowany przy użyciu wartości null, ale teraz kompilator nie zgłasza żadnych ostrzeżeń. **Null forgiving operator**, `!` następujący znak `default` wyrażenie informuje kompilator, że poprzedniego wyrażenia nie ma wartości null. Ta technika może być wskazane, gdy inne zmiany wymusić znacznie większe zmiany do bazy kodu, ale w tej aplikacji jest stosunkowo szybko i lepsze rozwiązania: Wprowadź `NewsStoryViewModel` typem niezmienne, gdzie wszystkie właściwości są ustawiane w konstruktorze. Wprowadź następujące zmiany do `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Po zakończeniu tej operacji musisz zaktualizować kod, który konfiguruje AutoMapper, tak aby używał konstruktora, a nie ustawienie właściwości. Otwórz `NewsService.cs` i znajdź następujący kod w dolnej części pliku:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Mapy właściwości w kodu `ISyndicationItem` obiekt `NewsStoryViewModel` właściwości. Chcesz, aby AutoMapper zapewnienie mapowania przy użyciu konstruktora, zamiast tego. Zastąp kod powyżej, o następującej konfiguracji automapper:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Należy zauważyć, że ponieważ ta klasa jest mały i uważnie zbadane, należy włączyć `#nullable enable` dyrektywy powyżej tej deklaracji klasy. Zmiany do konstruktora może przerwane, więc warto uruchomić wszystkie testy i testowanie aplikacji przed kontynuowaniem.

Pierwszy zestaw zmian pokazuje, jak wykryć kiedy oryginalnego projektu wskazane, nie należy ustawiać zmienne `null`. Technika nazywa się **poprawne wynikające z konstrukcji**. Możesz zadeklarować obiekt i jego właściwości nie może być `null` gdy jest konstruowany. Analizę przepływu kompilatora zapewnia pewność, że te właściwości nie są ustawione na `null` po konstrukcji. Należy pamiętać, że ten konstruktor jest wywoływany przez kod zewnętrzny, a kod **nullable oblivious**. Nowa składnia nie dostarcza sprawdzanie w czasie wykonywania. Kod zewnętrzny mogą ominąć analizę przepływu kompilatora. 

W innych sytuacjach strukturę klasy zawiera różne wskazówki do intencji. Otwórz *Error.cshtml.cs* w pliku *stron* folderu. `ErrorViewModel` Zawiera następujący kod:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Dodaj `#nullable enable` dyrektywy przed deklaracją klasy i `#nullable restore` dyrektywy po nim. Uzyskasz jeden ostrzeżenie, że `RequestId` nie został zainicjowany. Patrząc na klasy, należy zdecydować, że `RequestId` właściwość powinna mieć wartość null. w niektórych przypadkach. Istnienie `ShowRequestId` właściwość wskazuje, czy możliwe brakujące wartości. Ponieważ `null` jest prawidłowy, Dodaj `?` na `string` typu, aby wskazać `RequestId` właściwość *typu dopuszczającego wartość null odwołania*. Ostatnią klasę wygląda następująco:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Sprawdź, czy używa właściwości i zobacz, czy w skojarzona strona właściwości jest sprawdzana pod kątem wartości null przed renderowaniem go w znacznikach. Dzięki zakończeniu korzystania z tej klasy jest bezpieczne użycie typu dopuszczającego wartość null odwołania.

## <a name="fixing-nulls-causes-change"></a>Naprawianie wartości null powoduje, że zmiany

Często rozwiązać jeden zestaw ostrzeżeń, które tworzy nowe ostrzeżenia w kod pokrewny. Zobaczmy, ostrzeżeń w akcji napraw `index.cshtml.cs` klasy. Otwórz `index.cshtml.cs` pliku i poszukaj w kodzie. Ten plik zawiera kod związany z strony indeksu:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Dodaj `#nullable enable` dyrektywy, aby zobaczyć dwa ostrzeżenia. Ani `ErrorText` właściwości ani `NewsItems` właściwość jest inicjowana. Badanie tej klasy doprowadziłoby wrażenie, że obie te właściwości powinny być typy dopuszczające wartości null odwołań: Obie mieć prywatnych metod ustawiających. Dokładnie jeden jest przypisany w `OnGet` metody. Przed wprowadzeniem zmian, Przyjrzyj się konsumentów obie te właściwości. Na stronie, `ErrorText` jest sprawdzana względem wartości null, przed wygenerowaniem znaczników pod kątem błędów. `NewsItems` Kolekcji jest sprawdzana względem `null`, sprawdzona, aby upewnić się, kolekcja ma elementy. Szybka poprawka będzie zapewnienie oba typy dopuszczające wartości null odwołanie do właściwości. Poprawka lepiej byłoby że kolekcja jest kolumną typu referencyjnego i dodać elementy do istniejącej kolekcji podczas jej odczytywania wiadomości. Pierwsze rozwiązanie polega na dodawanie `?` do `string` wpisz `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Czy zmiana nie będzie rozprzestrzeniają się na inny kod, ponieważ żadnego dostępu do `ErrorText` właściwość została już chroniony przez sprawdzanie wartości null. Następnie zainicjuj `NewsItems` listy i Usuń metoda ustawiająca właściwości, dzięki czemu właściwość tylko do odczytu:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Który stałej ostrzeżenie, ale błąd. `NewsItems` Lista staje się **poprawne wynikające z konstrukcji**, ale kod, który umożliwia określenie listy w `OnGet` musi zmianie, aby dopasować nowego interfejsu API. Zamiast przypisania, wywołania `AddRange` do dodawania elementów wiadomości do istniejącej listy:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Za pomocą `AddRange` zamiast przypisania oznacza, że `GetNews` metoda może zwracać `IEnumerable` zamiast `List`. Który zapisuje jednej alokacji. Zmień sygnaturę metody i Usuń `ToList` wywołać, jak pokazano w następującym przykładzie kodu:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Zmienianie podpisu dzieli jedną również testy. Otwórz `NewsServiceTests.cs` w pliku `Services` folderu `SimpleFeedReader.Tests` projektu. Przejdź do `Returns_News_Stories_Given_Valid_Uri` testu i zmienić typ `result` zmienną `IEnumerable<NewsItem>`. Zmiana typu oznacza `Count` właściwość nie jest już dostępna, więc Zastąp `Count` właściwości w `Assert` wywołaniem `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Musisz dodać `using System.Linq` instrukcji na początku pliku, jak również.

Ten zbiór zmian wyróżnia szczególną ostrożność podczas aktualizowania kodu, który zawiera ogólnych instancji. Lista i elementy na liście typów innych niż null. Jeden lub oba, może być typy dopuszczające wartości null. Dozwolone są następujące deklaracje:

- `List<NewsStoryViewModel>`: listy modeli widoków nonullable kolumną.
- `List<NewsStoryViewModel?>`: kolumną lista modeli widoków dopuszczającego wartość null.
- `List<NewsStoryViewModel>?`: nullable lista modeli widoków niedopuszczające wartości null.
- `List<NewsStoryViewModel?>?`: dopuszczającego wartość null lista modeli widoków dopuszczającego wartość null.

## <a name="interfaces-with-external-code"></a>Interfejsy z kodu zewnętrznego

Wprowadzono zmiany do `NewsService` klasy, więc włączyć `#nullable enable` adnotacji dla tej klasy. Nie będzie to wygenerowanie nowego ostrzeżenia. Jednak dokładne badanie klasy pomaga w celu wyłącznie zilustrowanie niektórych ograniczeń analizę przepływu kompilatora. Sprawdź konstruktora:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` Jako odwołanie kolumną jest wpisana nazwa parametru. Jest wywoływana przez kod infrastruktury platformy ASP.NET Core, dzięki czemu kompilator tak naprawdę nie wie, że `IMapper` nigdy nie będzie mieć wartości null. Domyślny kontener iniekcji (DI) zależności platformy ASP.NET Core zgłasza wyjątek, jeśli nie można rozpoznać wymaganej usługi, dzięki czemu kod jest poprawny. Kompilator nie można zweryfikować wszystkie wywołania do publicznych interfejsów API, nawet wtedy, gdy kod jest kompilowany z kontekstami annotation dopuszczający wartość null, włączone. Ponadto bibliotek mogą być używane przez projekty, które nie zostały jeszcze wyrażania zgody na używanie typów nullable odwołania. Sprawdzanie poprawności danych wejściowych do publicznych interfejsów API, nawet po ich zadeklarowane jako typy kolumną.

## <a name="get-the-code"></a>Pobierz kod

Problem został rozwiązany ostrzeżeń został zidentyfikowany w kompilacji testu wstępnego, więc można włączyć w kontekście annotation dopuszczający wartość null w obu projektach. Ponowna kompilacja projektów; Kompilator nie zgłasza żadnych ostrzeżeń. Możesz też uzyskać kod zakończony projekt w [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished) repozytorium GitHub.

Nowe funkcje obsługujące pomagające w znajdowaniu i rozwiązać ewentualne błędy, w jaki sposób obsługiwać typów referencyjnych nullable `null` wartości w kodzie. Włączanie kontekstu annotation dopuszczający wartość null, umożliwia wyrażanie zgodną z planem projektu: niektóre zmienne nigdy nie powinien mieć wartość null, inne zmienne mogą zawierać wartości null. Te funkcje ułatwiają zadeklarować zgodną z planem projektu. Podobnie kontekst ostrzeżenie dopuszczającego wartość null nakazuje kompilatorowi problem ostrzeżenia, gdy spowodować naruszenie tym przeznaczeniem. Tych ostrzeżeń przewodnik dotyczyć wprowadzenia aktualizacji, które sprawić, że kod bardziej odporne na błędy i mniej prawdopodobnie zgłaszany `NullReferenceException` podczas wykonywania. Można kontrolować zakres tych kontekstach, dzięki czemu można skupić się na lokalnych obszarów kodu, aby przeprowadzić migrację, podczas gdy pozostałe bazy kodu nie została zmieniona. W praktyce istnieje możliwość migracji zadań w ramach regularnej konserwacji do swoich klas. W tym samouczku przedstawiono proces migracji aplikacji na używanie typów nullable odwołań. Możesz zapoznać się z większego przykładu rzeczywistych tego procesu, sprawdzając żądania Ściągnięcia [Jon Skeet](https://github.com/jskeet) wprowadzone zestawowi typy dopuszczające wartości null odwołań do [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
