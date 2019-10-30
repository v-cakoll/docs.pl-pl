---
title: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null
description: Ten zaawansowany samouczek zawiera wprowadzenie do typów referencyjnych dopuszczających wartość null. Dowiesz się, w jaki sposób projekt zostanie zastosowany, gdy wartości odniesienia mogą mieć wartość null, i że kompilator wymusi, gdy nie mogą mieć wartości null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 9cb9ac1b292e61d6a8a5f84be29a6a6c323725fc
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039686"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Samouczek: Migrowanie istniejącego kodu z typami referencyjnymi Nullable

C#8 wprowadza **typy odwołań do wartości null**, które uzupełniają typy odwołań w taki sam sposób, jak typy wartości null uzupełniają typy wartości. Należy zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null** , dołączając `?` do typu. Na przykład `string?` reprezentuje wartość null `string`. Możesz użyć tych nowych typów, aby dokładniej wyznaczać intencje projektowania: niektóre zmienne *muszą zawsze mieć wartość*, inne *mogą nie mieć wartości*. Wszystkie istniejące zmienne typu referencyjnego byłyby interpretowane jako typ referencyjny, który nie dopuszcza wartości null. 

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> - Włącz sprawdzanie odwołań o wartości null podczas pracy z kodem.
> - Diagnozuj i popraw różne ostrzeżenia związane z wartościami null.
> - Zarządzaj interfejsem pomiędzy włączonymi do dopuszczania wartości null a niedozwolonymi kontekstami.
> - Kontrolowanie kontekstów adnotacji dopuszczających wartość null.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0. C# 8 kompilator jest dostępny w programie [Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="explore-the-sample-application"></a>Eksplorowanie przykładowej aplikacji

Przeprowadzona Przykładowa aplikacja jest aplikacją internetową czytnika kanału informacyjnego RSS. Odczytuje z pojedynczego kanału informacyjnego RSS i wyświetla podsumowania dla najnowszych artykułów. Aby odwiedzić witrynę, możesz kliknąć dowolny z tych artykułów. Aplikacja jest stosunkowo nowa, ale została zapisywana przed udostępnieniem typów referencyjnych dopuszczających wartości null. Decyzje projektowe dotyczące zasad dotyczących dźwięku reprezentowane przez aplikację, ale nie korzystają z tej ważnej funkcji języka.

Przykładowa aplikacja zawiera bibliotekę testów jednostkowych, która sprawdza poprawność głównych funkcji aplikacji. Ten projekt ułatwi bezpieczne uaktualnienie, jeśli zmienisz dowolną implementację w oparciu o wygenerowane ostrzeżenia. Możesz pobrać kod początkowy z repozytorium usługi GitHub [/przykłady](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) .

Celem migrowania projektu powinna być skorzystanie z nowych funkcji języka, aby wyraźnie wyrażać intencję do wartości null zmiennych i zrobić to w taki sposób, aby kompilator nie generował ostrzeżeń w przypadku braku kontekstu adnotacji z dopuszczaniem wartości null i kontekst ostrzegawczy dopuszczający wartość null jest ustawiany na `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Uaktualnij projekty do C# 8

Dobrym pierwszym krokiem jest określenie zakresu zadania migracji. Zacznij od uaktualnienia projektu do C# 8,0 (lub nowszego). Dodaj element `LangVersion` do obu plików csproj dla projektu sieci Web i projektu testów jednostkowych:

```xml
<LangVersion>8.0</LangVersion>
```

Uaktualnienie wersji językowej powoduje C# wybranie 8,0, ale nie włączenie kontekstu adnotacji nullable ani kontekstu ostrzeżenia o wartości null. Skompiluj ponownie projekt, aby upewnić się, że kompiluje się bez ostrzeżeń.

Dobrym następnym krokiem jest włączenie kontekstu adnotacji nullable i zobacz, ile ostrzeżeń jest generowanych. Dodaj następujący element do obu plików csproj w rozwiązaniu bezpośrednio pod elementem `LangVersion`:

```xml
<Nullable>enable</Nullable>
```

Wykonaj kompilację testową i zwróć uwagę na listę ostrzeżeń. W tej małej aplikacji kompilator generuje pięć ostrzeżeń, więc prawdopodobnie pozostawisz kontekst adnotacji z dopuszczaniem wartości null i Rozpocznij naprawianie ostrzeżeń dla całego projektu.

Ta strategia działa tylko w przypadku mniejszych projektów. W przypadku większych projektów liczba ostrzeżeń generowanych przez włączenie kontekstu adnotacji dopuszczających wartość null dla całej bazy kodu utrudnia systematyczne Rozwiązywanie ostrzeżeń. W przypadku większych projektów przedsiębiorstwa często zajdzie potrzeba migracji jednego projektu jednocześnie. W każdym projekcie Przeprowadź migrację jednej klasy lub pliku jednocześnie.

## <a name="warnings-help-discover-original-design-intent"></a>Ostrzeżenia ułatwiają odnajdywanie oryginalnego zamiaru projektu

Istnieją dwie klasy, które generują wiele ostrzeżeń. Zacznij od klasy `NewsStoryViewModel`. Usuń element `Nullable` z obu plików csproj, aby ograniczyć zakres ostrzeżeń do sekcji kodu, z którym pracujesz. Otwórz plik *NewsStoryViewModel.cs* i Dodaj następujące dyrektywy, aby włączyć kontekst adnotacji dopuszczający wartość null dla `NewsStoryViewModel` i przywrócić go po tej definicji klasy:

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

Te dwie dyrektywy pomagają skupić się na zadaniu migracji. Ostrzeżenia dopuszczające wartość null są generowane dla obszaru kodu, nad którym pracujesz. Pozostawisz je do momentu, aż wszystko będzie gotowe do włączenia ostrzeżeń dla całego projektu. Należy używać `restore`, a nie `disable` wartości, aby uniemożliwić przypadkowe wyłączenie tego kontekstu po włączeniu adnotacji do wartości null dla całego projektu. Po włączeniu kontekstu adnotacji do wartości null dla całego projektu można usunąć wszystkie `#nullable` pragm z tego projektu.

Klasa `NewsStoryViewModel` jest obiektem transferu danych (DTO), a dwie właściwości są ciągami odczytu/zapisu:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Te dwie właściwości powodują `CS8618`"Właściwość niebędąca dopuszczaniem wartości null jest niezainicjowana". Jest to wystarczająco jasne: obie `string` właściwości mają wartość domyślną `null` podczas konstruowania `NewsStoryViewModel`. Ważne do odnajdowania to sposób konstruowania obiektów `NewsStoryViewModel`. Patrząc na tę klasę, nie można stwierdzić, czy wartość `null` jest częścią projektu lub czy te obiekty są ustawione na wartości inne niż null, gdy zostanie utworzony jeden. Historie wiadomości są tworzone w metodzie `GetNews` klasy `NewsService`:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

W poprzednim bloku kodu jest już w toku. Ta aplikacja używa pakietu NuGet [automapowania](https://automapper.org/) do konstruowania elementu wiadomości z `ISyndicationItem`. Wykryto, że są konstruowane elementy historii wiadomości i właściwości są ustawiane w jednej instrukcji. Oznacza to, że projekt `NewsStoryViewModel` wskazuje, że te właściwości nigdy nie powinny mieć wartości `null`. Te właściwości powinny mieć **niezerowe typy odwołań**. To najlepiej reprezentuje pierwotny cel projektowania. W rzeczywistości wszystkie `NewsStoryViewModel` *są* poprawnie tworzone przy użyciu wartości innych niż null. Powoduje to, że następujący kod inicjujący ma prawidłową poprawkę:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Przypisanie `Title` i `Uri` do `default` `null` dla typu `string` nie zmienia zachowania programu w czasie wykonywania. `NewsStoryViewModel` nadal jest zbudowana z wartościami null, ale teraz kompilator nie zgłasza ostrzeżeń. **Operator łagodniejszej o wartości null**, znak `!` po wyrażeniu `default` informuje kompilator, że poprzednie wyrażenie nie ma wartości null. Ta technika może być taka, gdy inne zmiany wymuszają znacznie większe zmiany w bazie kodu, ale w tej aplikacji istnieje stosunkowo szybkie i lepsze rozwiązanie: uczyń `NewsStoryViewModel` niezmiennym typem, gdzie wszystkie właściwości są ustawiane w konstruktorze. Wprowadź następujące zmiany w `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Po wykonaniu tej czynności należy zaktualizować kod, który konfiguruje automapowanie, tak aby używał konstruktora zamiast ustawiania właściwości. Otwórz `NewsService.cs` i Wyszukaj następujący kod w dolnej części pliku:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Ten kod mapuje właściwości obiektu `ISyndicationItem` na właściwości `NewsStoryViewModel`. Chcesz, aby automapowanie zapewniało mapowanie przy użyciu konstruktora. Zastąp powyższy kod następującym konfiguracją automapowania:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Zwróć uwagę, że ponieważ ta klasa jest mała i uważnie sprawdzona, należy włączyć dyrektywę `#nullable enable` powyżej tej deklaracji klasy. Zmiana w konstruktorze mogła spowodować uszkodzenie elementu, więc jest wartościowa do uruchamiania wszystkich testów i testowania aplikacji przed przechodzeniem.

Pierwszy zestaw zmian przedstawia sposób odnajdywania, gdy oryginalny projekt wskazał, że zmienne nie powinny być ustawione na `null`. Technika jest określana jako **poprawna przez konstrukcję**. Deklaruje, że obiekt i jego właściwości nie mogą być `null`, gdy jest konstruowany. Analiza przepływu kompilatora zapewnia gwarancję, że te właściwości nie są ustawione na `null` po przygotowaniu. Należy zauważyć, że ten konstruktor jest wywoływany przez kod zewnętrzny, a ten kod **dopuszcza wartość null Oblivious**. Nowa składnia nie zapewnia sprawdzania środowiska uruchomieniowego. Kod zewnętrzny może obejść analizę przepływu kompilatora. 

W innych przypadkach struktura klasy zawiera różne wskazówki dotyczące zamiaru. Otwórz plik *Error.cshtml.cs* w folderze *Pages* . `ErrorViewModel` zawiera następujący kod:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Dodaj dyrektywę `#nullable enable` przed deklaracją klasy i `#nullable restore` dyrektywą. Otrzymasz jedno ostrzeżenie, że `RequestId` nie zostanie zainicjowany. Przeglądając klasę, należy zdecydować, że w niektórych przypadkach Właściwość `RequestId` powinna mieć wartość null. Obecność właściwości `ShowRequestId` wskazuje, że brakujące wartości są możliwe. Ponieważ `null` jest prawidłowy, Dodaj `?` do typu `string`, aby wskazać, że właściwość `RequestId` jest *typem referencyjnym dopuszczającym wartość null*. Ostatnia Klasa wygląda podobnie do poniższego przykładu:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Sprawdź, czy są używane właściwości i czy na skojarzonej stronie właściwość jest sprawdzana pod kątem wartości null przed renderowaniem w znaczniku. Jest to bezpieczne użycie typu referencyjnego dopuszczającego wartość null, więc należy wykonać tę klasę.

## <a name="fixing-nulls-causes-change"></a>Naprawianie wartości null powoduje zmianę

Często poprawka jednego zestawu ostrzeżeń tworzy nowe ostrzeżenia w powiązanym kodzie. Zobaczmy ostrzeżenia w akcji, rozwiązując klasę `index.cshtml.cs`. Otwórz plik `index.cshtml.cs` i zapoznaj się z kodem. Ten plik zawiera kod związany ze stroną indeksu:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Dodaj dyrektywę `#nullable enable`, a zobaczysz dwa ostrzeżenia. Nie zainicjowano ani właściwości `ErrorText`, ani właściwości `NewsItems`. Badanie tej klasy doprowadziłoby do tego, że obie właściwości powinny mieć typ referencyjny dopuszczający wartości null: oba mają prywatne metody ustawiające. W metodzie `OnGet` jest przypisywany dokładnie jeden. Przed wprowadzeniem zmian należy zapoznać się z użytkownikami obu właściwości. Na samej stronie `ErrorText` jest sprawdzana pod kątem wartości null przed wygenerowaniem znaczników pod kątem błędów. Kolekcje `NewsItems` są sprawdzane pod kątem `null`i sprawdzane, aby upewnić się, że kolekcja zawiera elementy. Szybką poprawką byłoby najęcie obu właściwości typów referencyjnych dopuszczających wartość null. Lepszym rozwiązaniem jest udostępnienie kolekcji jako typu referencyjnego, który nie ma wartości null, i dodanie elementów do istniejącej kolekcji przy pobieraniu wiadomości. Pierwszą poprawkę jest dodanie `?` do typu `string` dla `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Ta zmiana nie będzie miała wpływu na inny kod, ponieważ każdy dostęp do właściwości `ErrorText` został już chroniony przez sprawdzanie wartości null. Następnie zainicjuj listę `NewsItems` i Usuń metodę ustawiającą właściwość, ustawiając ją jako właściwość tylko do odczytu:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Naprawiono ostrzeżenie, ale wprowadzono błąd. Lista `NewsItems` jest teraz **poprawna przez konstrukcję**, ale kod ustawiający listę w `OnGet` musi ulec zmianie, aby pasował do nowego interfejsu API. Zamiast przypisania, wywołaj `AddRange`, aby dodać elementy wiadomości do istniejącej listy:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Użycie `AddRange` zamiast przypisania oznacza, że metoda `GetNews` może zwrócić `IEnumerable` zamiast `List`. Powoduje to zapisanie jednej alokacji. Zmień podpis metody i Usuń wywołanie `ToList`, jak pokazano w następującym przykładzie kodu:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Zmiana podpisu spowoduje również przerwanie jednego z testów. Otwórz plik `NewsServiceTests.cs` w folderze `Services` projektu `SimpleFeedReader.Tests`. Przejdź do testu `Returns_News_Stories_Given_Valid_Uri` i Zmień typ zmiennej `result` na `IEnumerable<NewsItem>`. Zmiana typu oznacza, że właściwość `Count` nie jest już dostępna, więc Zastąp Właściwość `Count` w `Assert` z wywołaniem do `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Należy również dodać instrukcję `using System.Linq` na początku pliku.

Ten zestaw zmian wyróżnia szczególną uwagę podczas aktualizowania kodu, który zawiera ogólne wystąpienia. Zarówno lista, jak i elementy na liście typów niedopuszczających wartości null. Oba typy mogą być dopuszczane do wartości null. Dozwolone są wszystkie następujące deklaracje:

- `List<NewsStoryViewModel>`: Lista niemająca wartości null dla modeli widoku nonullabled.
- `List<NewsStoryViewModel?>`: niemożliwa do null lista modeli widoku dopuszczających wartości null.
- `List<NewsStoryViewModel>?`: dopuszczająca wartość null lista niezerowych modeli widoku.
- `List<NewsStoryViewModel?>?`: dopuszczająca wartość null lista modeli widoku dopuszczających wartość null.

## <a name="interfaces-with-external-code"></a>Interfejsy z kodem zewnętrznym

Wprowadzono zmiany w klasie `NewsService`, więc Włącz `#nullable enable` adnotację dla tej klasy. Nie spowoduje to wygenerowania żadnych nowych ostrzeżeń. Jednak dokładne badanie klasy ułatwia zilustrowanie niektórych ograniczeń analizy przepływu kompilatora. Badanie konstruktora:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

Parametr `IMapper` jest typem odwołania, które nie ma wartości null. Jest on wywoływany przez ASP.NET Core kod infrastruktury, więc kompilator nie wie, że `IMapper` nigdy nie będzie mieć wartości null. ASP.NET Core domyślny kontener iniekcji zależności (DI) zgłasza wyjątek, jeśli nie może rozpoznać wymaganej usługi, więc kod jest poprawny. Kompilator nie może sprawdzić poprawności wszystkich wywołań publicznych interfejsów API, nawet jeśli kod jest kompilowany z włączonym kontekstem adnotacji dopuszczający wartość null. Ponadto biblioteki mogą być używane przez projekty, które nie wybrały jeszcze użycia typów referencyjnych dopuszczających wartość null. Sprawdź poprawność danych wejściowych do publicznych interfejsów API, mimo że zostały zadeklarowane jako typy niemające wartości null.

## <a name="get-the-code"></a>Pobierz kod

Zostały naprawione ostrzeżenia, które zostały zidentyfikowane podczas wstępnego kompilowania testów, dlatego teraz można włączyć kontekst adnotacji dopuszczający wartości null dla obu projektów. Kompiluj ponownie projekty; Kompilator zgłasza Brak ostrzeżeń. Możesz uzyskać kod dla gotowego projektu w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished)

Nowe funkcje, które obsługują typy referencyjne dopuszczające wartość null, ułatwiają znajdowanie i rozwiązywanie potencjalnych błędów w sposobie obsługi `null` wartości w kodzie. Włączenie kontekstu adnotacji z dopuszczaniem wartości null pozwala na wyrażenie zamiaru projektu: niektóre zmienne nigdy nie powinny mieć wartości null, inne zmienne mogą zawierać wartości null. Te funkcje ułatwiają deklarowanie zamiaru projektowania. Podobnie, kontekst ostrzegawczy wartości null instruuje kompilator, aby wydawał ostrzeżenia w przypadku naruszenia tego celu. Te ostrzeżenia przeprowadzą Cię przez proces aktualizacji, które sprawiają, że kod będzie bardziej odporny na błędy i mniej, co może spowodować wygenerowanie `NullReferenceException` podczas wykonywania. Można kontrolować zakres tych kontekstów, aby można było skupić się na lokalnych obszarach kodu do migracji, gdy pozostała baza kodu jest nienaruszona. W tym celu zadanie migracji jest częścią regularnej konserwacji klas. W tym samouczku przedstawiono proces migrowania aplikacji w celu używania typów referencyjnych dopuszczających wartość null. Możesz zapoznać się z większym rzeczywistym przykładem tego procesu, sprawdzając, czy element PR [Jan Skeet](https://github.com/jskeet) miał zostać uwzględniony w [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
