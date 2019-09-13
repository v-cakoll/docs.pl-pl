---
title: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null
description: Ten zaawansowany samouczek zawiera wprowadzenie do typów referencyjnych dopuszczających wartość null. Dowiesz się, w jaki sposób projekt zostanie zastosowany, gdy wartości odniesienia mogą mieć wartość null, i że kompilator wymusi, gdy nie mogą mieć wartości null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 0c95065e6c380fab6ba33432a32b3297e78027a3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926628"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Samouczek: Migruj istniejący kod z typami referencyjnymi Nullable

C#8 wprowadza **typy odwołań do wartości null**, które uzupełniają typy odwołań w taki sam sposób, jak typy wartości null uzupełniają typy wartości. Należy zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null** poprzez dołączenie `?` do typu. Na przykład `string?` reprezentuje wartość null `string`. Możesz użyć tych nowych typów, aby dokładniej wyznaczać intencje projektowania: niektóre zmienne *muszą zawsze mieć wartość*, inne *mogą nie mieć wartości*. Wszystkie istniejące zmienne typu referencyjnego byłyby interpretowane jako typ referencyjny, który nie dopuszcza wartości null. 

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> - Włącz sprawdzanie odwołań o wartości null podczas pracy z kodem.
> - Diagnozuj i popraw różne ostrzeżenia związane z wartościami null.
> - Zarządzaj interfejsem pomiędzy włączonymi do dopuszczania wartości null a niedozwolonymi kontekstami.
> - Kontrolowanie kontekstów adnotacji dopuszczających wartość null.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0 beta. Kompilator C# 8-Beta jest dostępny w programie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub najnowszej [wersji zapoznawczej programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="explore-the-sample-application"></a>Eksplorowanie przykładowej aplikacji

Przeprowadzona Przykładowa aplikacja jest aplikacją internetową czytnika kanału informacyjnego RSS. Odczytuje z pojedynczego kanału informacyjnego RSS i wyświetla podsumowania dla najnowszych artykułów. Aby odwiedzić witrynę, możesz kliknąć dowolny z tych artykułów. Aplikacja jest stosunkowo nowa, ale została zapisywana przed udostępnieniem typów referencyjnych dopuszczających wartości null. Decyzje projektowe dotyczące zasad dotyczących dźwięku reprezentowane przez aplikację, ale nie korzystają z tej ważnej funkcji języka.

Przykładowa aplikacja zawiera bibliotekę testów jednostkowych, która sprawdza poprawność głównych funkcji aplikacji. Ten projekt ułatwi bezpieczne uaktualnienie, jeśli zmienisz dowolną implementację w oparciu o wygenerowane ostrzeżenia. Możesz pobrać kod początkowy z repozytorium usługi GitHub [/przykłady](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) .

Celem migrowania projektu powinna być skorzystanie z nowych funkcji języka, aby wyraźnie wyrażać intencję do wartości null zmiennych i zrobić to w taki sposób, aby kompilator nie generował ostrzeżeń w przypadku braku kontekstu adnotacji z dopuszczaniem wartości null i kontekst ostrzegawczy dopuszczający `enabled`wartość null jest ustawiony na wartość.

## <a name="upgrade-the-projects-to-c-8"></a>Uaktualnij projekty do C# 8

Dobrym pierwszym krokiem jest określenie zakresu zadania migracji. Zacznij od uaktualnienia projektu do C# 8,0 (lub nowszego). `LangVersion` Dodaj element do obu plików csproj dla projektu sieci Web i projektu testów jednostkowych:

```xml
<LangVersion>8.0</LangVersion>
```

Uaktualnienie wersji językowej powoduje C# wybranie 8,0, ale nie włączenie kontekstu adnotacji nullable ani kontekstu ostrzeżenia o wartości null. Skompiluj ponownie projekt, aby upewnić się, że kompiluje się bez ostrzeżeń.

Dobrym następnym krokiem jest włączenie kontekstu adnotacji nullable i zobacz, ile ostrzeżeń jest generowanych. Dodaj następujący element do obu plików csproj w rozwiązaniu bezpośrednio pod `LangVersion` elementem:

```xml
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> Element miał wcześniej nazwę `NullableContextOptions`. `Nullable` Zmiana nazwy jest dostarczana z programem Visual Studio 2019, 16,2-P1. Ta zmiana nie ma zestaw .NET Core SDK 3.0.100-preview5-011568. Jeśli używasz interfejs wiersza polecenia platformy .NET Core, musisz użyć `NullableContextOptions` do momentu udostępnienia kolejnej wersji zapoznawczej.

Wykonaj kompilację testową i zwróć uwagę na listę ostrzeżeń. W tej małej aplikacji kompilator generuje pięć ostrzeżeń, więc prawdopodobnie pozostawisz kontekst adnotacji z dopuszczaniem wartości null i Rozpocznij naprawianie ostrzeżeń dla całego projektu.

Ta strategia działa tylko w przypadku mniejszych projektów. W przypadku większych projektów liczba ostrzeżeń generowanych przez włączenie kontekstu adnotacji dopuszczających wartość null dla całej bazy kodu utrudnia systematyczne Rozwiązywanie ostrzeżeń. W przypadku większych projektów przedsiębiorstwa często zajdzie potrzeba migracji jednego projektu jednocześnie. W każdym projekcie Przeprowadź migrację jednej klasy lub pliku jednocześnie.

## <a name="warnings-help-discover-original-design-intent"></a>Ostrzeżenia ułatwiają odnajdywanie oryginalnego zamiaru projektu

Istnieją dwie klasy, które generują wiele ostrzeżeń. Zacznij od `NewsStoryViewModel` klasy. `Nullable` Usuń element z obu plików csproj, aby ograniczyć zakres ostrzeżeń do sekcji kodu, z którym pracujesz. Otwórz plik *NewsStoryViewModel.cs* i Dodaj następujące dyrektywy, aby włączyć kontekst adnotacji dopuszczający wartość null `NewsStoryViewModel` dla i przywrócić go po tej definicji klasy:

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

Te dwie dyrektywy pomagają skupić się na zadaniu migracji. Ostrzeżenia dopuszczające wartość null są generowane dla obszaru kodu, nad którym pracujesz. Pozostawisz je do momentu, aż wszystko będzie gotowe do włączenia ostrzeżeń dla całego projektu. Należy użyć `restore` `disable` wartości zamiast, aby uniemożliwić przypadkowe wyłączenie tego kontekstu po włączeniu adnotacji dopuszczających wartości null dla całego projektu. Po włączeniu kontekstu adnotacji do wartości null dla całego projektu można usunąć wszystkie `#nullable` dyrektywy pragma z tego projektu.

`NewsStoryViewModel` Klasa jest obiektem transferu danych (DTO), a dwie właściwości są ciągami odczytu/zapisu:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Te dwie właściwości powodują `CS8618`, że właściwość "niedopuszczający wartości null" jest niezainicjowana ". Jest to wystarczająco jasne: obie `string` właściwości mają `null` wartość domyślną, gdy `NewsStoryViewModel` jest konstruowany. Ważne do odnalezienia to sposób `NewsStoryViewModel` konstruowania obiektów. Na tej klasie nie można stwierdzić, czy `null` wartość jest częścią projektu lub czy te obiekty są ustawione na wartości inne niż null, gdy zostanie utworzony jeden. Historie wiadomości są tworzone w `GetNews` metodzie `NewsService` klasy:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

W poprzednim bloku kodu jest już w toku. Ta aplikacja używa pakietu NuGet [automapowania](https://automapper.org/) do konstruowania elementu wiadomości z `ISyndicationItem`. Wykryto, że są konstruowane elementy historii wiadomości i właściwości są ustawiane w jednej instrukcji. Oznacza to, że projekt `NewsStoryViewModel` wskazuje, że te właściwości nigdy nie powinny `null` mieć wartości. Te właściwości powinny mieć **niezerowe typy odwołań**. To najlepiej reprezentuje pierwotny cel projektowania. W rzeczywistości wszystkie `NewsStoryViewModel` wystąpienia *są* poprawnie tworzone przy użyciu wartości innych niż null. Powoduje to, że następujący kod inicjujący ma prawidłową poprawkę:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Przypisanie `Title` i `Uri` do`default`danegotypunie zmienia zachowania programu w czasie wykonywania. `string` `null` `NewsStoryViewModel` Jest nadal zbudowany z wartościami null, ale teraz kompilator nie zgłasza ostrzeżeń. **Operator łagodniejszej null**, `!` znak następujący po `default` wyrażeniu informuje kompilator, że poprzednie wyrażenie nie ma wartości null. Ta technika może być celowa, gdy inne zmiany wymuszają znacznie większe zmiany w bazie kodu, ale w tej aplikacji istnieje stosunkowo szybkie i lepsze rozwiązanie: Utwórz niemodyfikowalny typ, `NewsStoryViewModel` w którym wszystkie właściwości są ustawione w konstruktorze. Wprowadź następujące zmiany `NewsStoryViewModel`w:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Po wykonaniu tej czynności należy zaktualizować kod, który konfiguruje automapowanie, tak aby używał konstruktora zamiast ustawiania właściwości. Otwórz `NewsService.cs` i Wyszukaj następujący kod w dolnej części pliku:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Ten kod mapuje właściwości `ISyndicationItem` obiektu `NewsStoryViewModel` na właściwości. Chcesz, aby automapowanie zapewniało mapowanie przy użyciu konstruktora. Zastąp powyższy kod następującym konfiguracją automapowania:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Zwróć uwagę, że ponieważ ta klasa jest mała i uważnie sprawdzona, należy włączyć `#nullable enable` dyrektywę powyżej tej deklaracji klasy. Zmiana w konstruktorze mogła spowodować uszkodzenie elementu, więc jest wartościowa do uruchamiania wszystkich testów i testowania aplikacji przed przechodzeniem.

Pierwszy zestaw zmian przedstawia sposób odnajdowania, gdy oryginalny projekt wskazał, że zmienne nie powinny być ustawiane na `null`. Technika jest określana jako **poprawna przez konstrukcję**. Deklaruje, że obiekt i jego właściwości nie mogą `null` być, gdy jest konstruowany. Analiza przepływu kompilatora zapewnia gwarancję, że te właściwości nie są ustawione `null` na wartość po konstrukcji. Należy zauważyć, że ten konstruktor jest wywoływany przez kod zewnętrzny, a ten kod **dopuszcza wartość null Oblivious**. Nowa składnia nie zapewnia sprawdzania środowiska uruchomieniowego. Kod zewnętrzny może obejść analizę przepływu kompilatora. 

W innych przypadkach struktura klasy zawiera różne wskazówki dotyczące zamiaru. Otwórz plik *Error.cshtml.cs* w folderze *Pages* . `ErrorViewModel` Zawiera następujący kod:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Dodaj dyrektywę przed deklaracją klasy `#nullable restore` i po niej. `#nullable enable` Otrzymasz jedno ostrzeżenie, które `RequestId` nie zostało zainicjowane. Przeglądając klasę, należy zdecydować, że `RequestId` w niektórych przypadkach właściwość powinna mieć wartość null. Istnienie `ShowRequestId` właściwości wskazuje, że brakujące wartości są możliwe. Ponieważ `null` jest prawidłowy, `?` Dodaj `string` do typu, aby wskazać, że `RequestId` właściwość jest *typem referencyjnym dopuszczającym wartość null*. Ostatnia Klasa wygląda podobnie do poniższego przykładu:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Sprawdź, czy są używane właściwości i czy na skojarzonej stronie właściwość jest sprawdzana pod kątem wartości null przed renderowaniem w znaczniku. Jest to bezpieczne użycie typu referencyjnego dopuszczającego wartość null, więc należy wykonać tę klasę.

## <a name="fixing-nulls-causes-change"></a>Naprawianie wartości null powoduje zmianę

Często poprawka jednego zestawu ostrzeżeń tworzy nowe ostrzeżenia w powiązanym kodzie. Zobaczmy ostrzeżenia w akcji, rozwiązując `index.cshtml.cs` klasę. `index.cshtml.cs` Otwórz plik i zapoznaj się z kodem. Ten plik zawiera kod związany ze stroną indeksu:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

`#nullable enable` Dodaj dyrektywę i zobaczysz dwa ostrzeżenia. Nie została zainicjowana `NewsItems` ani Właściwość,aniwłaściwość.`ErrorText` Badanie tej klasy doprowadziłoby do tego, że obie właściwości powinny mieć typ referencyjny dopuszczający wartości null: Oba mają prywatne metody ustawiające. W `OnGet` metodzie jest przypisywany dokładnie jeden. Przed wprowadzeniem zmian należy zapoznać się z użytkownikami obu właściwości. Na samej `ErrorText` stronie jest sprawdzana pod kątem wartości null przed wygenerowaniem znaczników dla błędów. Kolekcja jest sprawdzana pod `null`kątem i sprawdza, czy kolekcja zawiera elementy. `NewsItems` Szybką poprawką byłoby najęcie obu właściwości typów referencyjnych dopuszczających wartość null. Lepszym rozwiązaniem jest udostępnienie kolekcji jako typu referencyjnego, który nie ma wartości null, i dodanie elementów do istniejącej kolekcji przy pobieraniu wiadomości. Pierwsza poprawka to dodanie `?` `string` do typu dla `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Ta zmiana nie będzie miała wpływu na inny kod, ponieważ każdy dostęp `ErrorText` do właściwości został już chroniony przez kontrole o wartości null. Następnie zainicjuj `NewsItems` listę i Usuń metodę ustawiającą właściwość, ustawiając ją jako właściwość tylko do odczytu:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Naprawiono ostrzeżenie, ale wprowadzono błąd. Lista jest teraz **poprawna przez konstrukcję**, ale kod, który ustawia listę w `OnGet` , musi zmienić się, aby pasował do nowego interfejsu API. `NewsItems` Zamiast przypisania, należy wywołać `AddRange` , aby dodać elementy wiadomości do istniejącej listy:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Użycie `AddRange` zamiast przypisania oznacza `GetNews` , że metoda może `List`zwracać `IEnumerable` zamiast. Powoduje to zapisanie jednej alokacji. Zmień podpis metody i Usuń `ToList` wywołanie, jak pokazano w następującym przykładzie kodu:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Zmiana podpisu spowoduje również przerwanie jednego z testów. `NewsServiceTests.cs` Otwórz plik`Services` w folderze`SimpleFeedReader.Tests` projektu. Przejdź do `Returns_News_Stories_Given_Valid_Uri` testu i Zmień typ `result` zmiennej na `IEnumerable<NewsItem>`. Zmiana typu oznacza, że `Count` właściwość nie jest już dostępna, więc `Count` Zastąp właściwość w `Assert` wywołaniu `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Należy również dodać `using System.Linq` instrukcję do początku pliku.

Ten zestaw zmian wyróżnia szczególną uwagę podczas aktualizowania kodu, który zawiera ogólne wystąpienia. Zarówno lista, jak i elementy na liście typów niedopuszczających wartości null. Oba typy mogą być dopuszczane do wartości null. Dozwolone są wszystkie następujące deklaracje:

- `List<NewsStoryViewModel>`: Lista niemająca wartości null dla modeli widoku nonullabled.
- `List<NewsStoryViewModel?>`: niemożliwa do null lista niedopuszczających modeli widoku.
- `List<NewsStoryViewModel>?`: Lista dopuszcza wartość null dla niezerowych modeli widoku.
- `List<NewsStoryViewModel?>?`: dopuszczająca wartość null dla modeli widoku dopuszczającego wartość null.

## <a name="interfaces-with-external-code"></a>Interfejsy z kodem zewnętrznym

Wprowadzono zmiany w `NewsService` klasie, dlatego należy włączyć `#nullable enable` adnotację dla tej klasy. Nie spowoduje to wygenerowania żadnych nowych ostrzeżeń. Jednak dokładne badanie klasy ułatwia zilustrowanie niektórych ograniczeń analizy przepływu kompilatora. Badanie konstruktora:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

`IMapper` Parametr jest typu jako odwołanie, które nie ma wartości null. Jest on wywoływany przez ASP.NET Core kod infrastruktury, więc kompilator nie wie, że `IMapper` nigdy nie będzie mieć wartości null. ASP.NET Core domyślny kontener iniekcji zależności (DI) zgłasza wyjątek, jeśli nie może rozpoznać wymaganej usługi, więc kod jest poprawny. Kompilator nie może sprawdzić poprawności wszystkich wywołań publicznych interfejsów API, nawet jeśli kod jest kompilowany z włączonym kontekstem adnotacji dopuszczający wartość null. Ponadto biblioteki mogą być używane przez projekty, które nie wybrały jeszcze użycia typów referencyjnych dopuszczających wartość null. Sprawdź poprawność danych wejściowych do publicznych interfejsów API, mimo że zostały zadeklarowane jako typy niemające wartości null.

## <a name="get-the-code"></a>Pobierz kod

Zostały naprawione ostrzeżenia, które zostały zidentyfikowane podczas wstępnego kompilowania testów, dlatego teraz można włączyć kontekst adnotacji dopuszczający wartości null dla obu projektów. Kompiluj ponownie projekty; Kompilator zgłasza Brak ostrzeżeń. Możesz uzyskać kod dla gotowego projektu w repozytorium GitHub [/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished)

Nowe funkcje, które obsługują typy odwołań dopuszczające wartość null, ułatwiają znajdowanie i rozwiązywanie potencjalnych `null` błędów w sposobie obsługi wartości w kodzie. Włączenie kontekstu adnotacji z dopuszczaniem wartości null pozwala na wyrażenie zamiaru projektu: niektóre zmienne nigdy nie powinny mieć wartości null, inne zmienne mogą zawierać wartości null. Te funkcje ułatwiają deklarowanie zamiaru projektowania. Podobnie, kontekst ostrzegawczy wartości null instruuje kompilator, aby wydawał ostrzeżenia w przypadku naruszenia tego celu. Te ostrzeżenia przeprowadzą Cię przez proces aktualizacji, które sprawiają, że kod będzie bardziej odporny `NullReferenceException` na błędy i mniej, co może zgłosić podczas wykonywania. Można kontrolować zakres tych kontekstów, aby można było skupić się na lokalnych obszarach kodu do migracji, gdy pozostała baza kodu jest nienaruszona. W tym celu zadanie migracji jest częścią regularnej konserwacji klas. W tym samouczku przedstawiono proces migrowania aplikacji w celu używania typów referencyjnych dopuszczających wartość null. Możesz zapoznać się z większym rzeczywistym przykładem tego procesu, sprawdzając, czy element PR [Jan Skeet](https://github.com/jskeet) miał zostać uwzględniony w [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
