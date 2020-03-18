---
title: Uaktualnianie do typów odwołań z możliwością null
description: Ten zaawansowany samouczek pokazuje, jak przeprowadzić migrację istniejącego kodu za pomocą typów odwołań z możliwością null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 9767493059623e770cc100b83b9284e8d0bdf0f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156457"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Samouczek: Migracja istniejącego kodu za pomocą typów odwołań podlegających wartości null

C# 8 wprowadza **typy odwołań nullable**, które uzupełniają typy odwołań w ten sam sposób typy wartości null douzupełnienia typów wartości. Deklarujesz zmienną jako typ odwołania z `?` **wartością null,** dołączając do typu. Na przykład `string?` reprezentuje nullable `string`. Można użyć tych nowych typów, aby wyraźniej wyrazić intencję projektu: niektóre zmienne *muszą zawsze mieć wartość,* inne *mogą brakować wartości.* Wszelkie istniejące zmienne typu odwołania będą interpretowane jako typ odwołania niepodlegający null.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Włącz sprawdzanie odwołań zerowych podczas pracy z kodem.
> - Diagnozowanie i poprawianie różnych ostrzeżeń związanych z wartościami null.
> - Zarządzanie interfejsem między kontekstami wyłączonymi z możliwością null a kontekstami wyłączonymi z możliwością null.
> - Kontroluj konteksty adnotacji nullable.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0. Kompilator C# 8 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

W tym samouczku przyjęto założenie, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.

## <a name="explore-the-sample-application"></a>Poznaj przykładową aplikację

Przykładowa aplikacja, która zostanie migrowana jest aplikacją sieci web czytnik aplikacyjny rss. Odczytuje z jednego kanału RSS i wyświetla podsumowania najnowszych artykułów. Możesz wybrać dowolny z artykułów, aby odwiedzić witrynę. Aplikacja jest stosunkowo nowy, ale został napisany przed nullable typy odwołań były dostępne. Decyzje projektowe dla aplikacji reprezentowały solidne zasady, ale nie korzystaj z tej ważnej funkcji języka.

Przykładowa aplikacja zawiera bibliotekę testów jednostkowych, która sprawdza poprawność głównych funkcji aplikacji. Ten projekt ułatwi bezpieczne uaktualnienie, jeśli zmienisz dowolną implementację na podstawie wygenerowanych ostrzeżeń. Kod startowy można pobrać z repozytorium GitHub/sample.You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) GitHub repository.

Celem migracji projektu powinno być wykorzystanie nowych funkcji języka, dzięki czemu wyraźnie wyrazić zamiar na nullability zmiennych i zrobić to w taki sposób, że kompilator nie generuje ostrzeżenia, gdy masz nullable kontekstu adnotacji i nullable kontekście ostrzeżenie ustawione na `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Uaktualnianie projektów do języka C# 8

Dobrym pierwszym krokiem jest określenie zakresu zadania migracji. Rozpocznij od uaktualnienia projektu do języka C# 8.0 (lub nowszego). Dodaj `LangVersion` element do PropertyGroup zarówno w plikach csproj dla projektu sieci web, jak i w projekcie testu jednostkowego:

```xml
<LangVersion>8.0</LangVersion>
```

Uaktualnianie wersji językowej wybiera C# 8.0, ale nie włącza nullable kontekstu adnotacji lub nullable kontekście ostrzeżenia. Odbudować projekt, aby upewnić się, że buduje bez ostrzeżeń.

Dobrym następnym krokiem jest włączenie kontekstu adnotacji nullable i zobaczyć, ile ostrzeżenia są generowane. Dodaj następujący element do obu plików csproj w `LangVersion` rozwiązaniu, bezpośrednio pod elementem:

```xml
<Nullable>enable</Nullable>
```

Wykonaj kompilację testową i zwróć uwagę na listę ostrzeżeń. W tej małej aplikacji kompilator generuje pięć ostrzeżeń, więc prawdopodobnie pozostawisz włączony kontekst adnotacji z możliwością null i rozpocząć naprawianie ostrzeżeń dla całego projektu.

Strategia ta działa tylko w przypadku mniejszych projektów. Dla większych projektów liczba ostrzeżeń generowanych przez włączenie kontekstu adnotacji nullable dla całej bazy kodu utrudnia systematyczne naprawianie ostrzeżeń. W przypadku większych projektów korporacyjnych często chcesz przeprowadzić migrację jednego projektu naraz. W każdym projekcie migruj jedną klasę lub plik naraz.

## <a name="warnings-help-discover-original-design-intent"></a>Ostrzeżenia pomagają odkryć oryginalne intencje projektu

Istnieją dwie klasy, które generują wiele ostrzeżeń. Zacznij od `NewsStoryViewModel` klasy. Usuń `Nullable` element z obu plików csproj, dzięki czemu można ograniczyć zakres ostrzeżeń do sekcji kodu, z którymi pracujesz. Otwórz *plik NewsStoryViewModel.cs* i dodaj następujące dyrektywy, aby włączyć kontekst `NewsStoryViewModel` adnotacji nullable dla i przywrócić go zgodnie z tą definicją klasy:

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

Te dwie dyrektywy pomagają skoncentrować swoje wysiłki migracyjne. Ostrzeżenia nullable są generowane dla obszaru kodu, nad którym aktywnie pracujesz. Pozostawisz je włączone, dopóki nie będziesz gotowy do włączeniu ostrzeżeń dla całego projektu. Należy użyć `restore` `disable` wartości, aby nie przypadkowo wyłączyć kontekst później po włączeniu adnotacji nullable dla całego projektu. Po włączeniu kontekstu adnotacji nullable dla całego projektu, można `#nullable` usunąć wszystkie pragmy z tego projektu.

Klasa `NewsStoryViewModel` jest obiektem transferu danych (DTO), a dwie właściwości są ciągami odczytu/zapisu:

[!code-csharp[InitialViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Te dwie właściwości `CS8618`powodują , "Właściwość niepodlegająca null jest uninitialized". To dość jasne: `string` obie właściwości mają domyślną `null` `NewsStoryViewModel` wartość, gdy a jest skonstruowany. Ważne jest, aby odkryć, jak `NewsStoryViewModel` obiekty są konstruowane. Patrząc na tę klasę, nie można `null` stwierdzić, czy wartość jest częścią projektu lub jeśli te obiekty są ustawione na wartości inne niż null, gdy jest tworzony. Wiadomości są tworzone w `GetNews` metodzie `NewsService` klasy:

[!code-csharp[StarterCreateNewsItem](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

W poprzednim bloku kodu dzieje się sporo. Ta aplikacja używa [automapper](https://automapper.org/) nuget pakiet do `ISyndicationItem`konstruowania elementu wiadomości z . Odkryto, że elementy wątku wiadomości są konstruowane i właściwości są ustawione w tej jednej instrukcji. Oznacza to, że `NewsStoryViewModel` projekt wskazuje, że te `null` właściwości nigdy nie powinny mieć wartość. Właściwości te powinny być **nieunieważnionymi typami odwołań**. To najlepiej wyraża pierwotny zamiar projektu. W rzeczywistości `NewsStoryViewModel` każdy *jest* poprawnie tworzone z wartościami innych niż null. To sprawia, że następujący kod inicjalizacji prawidłową poprawkę:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

Przypisanie `Title` i `Uri` `default` do `null` którego `string` jest dla typu nie zmienia zachowanie wykonywania programu. Nadal `NewsStoryViewModel` jest skonstruowany z wartościami null, ale teraz kompilator zgłasza żadnych ostrzeżeń. Operator **wyrozumiały**null `!` , `default` znak następujący po wyrażeniu informuje kompilator, że poprzednie wyrażenie nie jest null. Ta technika może być celowe, gdy inne zmiany wymuszają znacznie większe zmiany do bazy kodu, ale `NewsStoryViewModel` w tej aplikacji istnieje stosunkowo szybkie i lepsze rozwiązanie: Make niezmiennego typu, gdzie wszystkie właściwości są ustawione w konstruktorze. Wyconajmi `NewsStoryViewModel`w :

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Gdy to zrobisz, należy zaktualizować kod, który konfiguruje AutoMapper tak, aby używa konstruktora, a nie ustawienie właściwości. Otwórz `NewsService.cs` i poszukaj następującego kodu u dołu pliku:

[!code-csharp[StarterAutoMapper](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Ten kod mapuje `ISyndicationItem` właściwości obiektu `NewsStoryViewModel` do właściwości. Chcesz AutoMapper, aby zapewnić mapowanie przy użyciu konstruktora zamiast. Zamień powyższy kod na następującą konfigurację automapy:

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Należy zauważyć, że ponieważ ta klasa jest mała i zostały `#nullable enable` dokładnie zbadane, należy włączyć dyrektywy powyżej tej deklaracji klasy. Zmiana konstruktora mogła coś ułamać, więc warto uruchomić wszystkie testy i przetestować aplikację przed przejściem dalej.

Pierwszy zestaw zmian pokazał, jak odkryć, kiedy oryginalny projekt wskazał, że `null`zmienne nie powinny być ustawione na . Technika ta jest określana jako **poprawna przez konstrukcję**. Deklarujesz, że obiekt i `null` jego właściwości nie mogą być po skonstruowaniu. Analiza przepływu kompilatora zapewnia pewność, że `null` te właściwości nie są ustawione po zakończeniu budowy. Należy zauważyć, że ten konstruktor jest wywoływana przez kod zewnętrzny, a ten kod jest **nullable oblivious**. Nowa składnia nie zapewnia sprawdzania czasu wykonywania. Kod zewnętrzny może obejść analizę przepływu kompilatora.

Innym razem struktura klasy zapewnia różne wskazówki do intencji. Otwórz plik *Error.cshtml.cs* w folderze *Strony.* Zawiera `ErrorViewModel` następujący kod:

[!code-csharp[StarterErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Dodaj `#nullable enable` dyrektywy przed deklaracją `#nullable restore` klasy i dyrektywy po nim. Otrzymasz jedno ostrzeżenie, `RequestId` które nie jest inicjowane. Patrząc na klasę, należy zdecydować, że `RequestId` właściwość powinna być null w niektórych przypadkach. Istnienie `ShowRequestId` właściwości wskazuje, że brakujące wartości są możliwe. Ponieważ `null` jest `?` prawidłowy, `string` dodaj typ, `RequestId` aby wskazać, że właściwość jest *typem odwołania z wartością null*. Klasa końcowa wygląda jak w poniższym przykładzie:

[!code-csharp[FinishedErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Sprawdź, czy nie ma zastosowań właściwości, a zobaczysz, że na skojarzonej stronie właściwość jest sprawdzana pod kątem wartości null przed renderowaniem jej w znacznikach. Jest to bezpieczne użycie typu odwołania z wartością null, więc gotowe z tej klasy.

## <a name="fixing-nulls-causes-change"></a>Naprawianie wartości null powoduje zmianę

Często poprawka dla jednego zestawu ostrzeżeń tworzy nowe ostrzeżenia w powiązanym kodzie. Zobaczmy ostrzeżenia w akcji, naprawiając `index.cshtml.cs` klasę. Otwórz `index.cshtml.cs` plik i sprawdź kod. Ten plik zawiera kod za dla strony indeksu:

[!code-csharp[StarterIndexModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Dodaj `#nullable enable` dyrektywę, a zobaczysz dwa ostrzeżenia. Ani właściwość, `ErrorText` ani `NewsItems` właściwość nie są inicjowane. Badanie tej klasy prowadzi do przekonania, że obie właściwości powinny być typy odwołań nullable: Oba mają private setters. Dokładnie jeden jest przypisany w metodzie. `OnGet` Przed wprowadzeniem zmian, spójrz na konsumentów obu właściwości. Na samej stronie `ErrorText` jest sprawdzana na null przed wygenerowaniem znaczników dla błędów. Kolekcja `NewsItems` jest sprawdzana `null`i sprawdzana, aby upewnić się, że kolekcja ma przedmioty. Szybka poprawka będzie, aby obie właściwości nullable typy odwołań. Lepszą poprawką byłoby uczynienie kolekcji typem odwołania nieunieważnialnym i dodawanie elementów do istniejącej kolekcji podczas pobierania wiadomości. Pierwszą poprawką jest `?` dodanie `string` do `ErrorText`typu :

[!code-csharp[UpdateErrorText](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Ta zmiana nie będzie tętnić przez inny `ErrorText` kod, ponieważ każdy dostęp do właściwości był już strzeżony przez kontrole zerowe. Następnie zainicjować `NewsItems` listę i usunąć setter właściwości, co czyni go readonly właściwość:

[!code-csharp[InitializeNewsItems](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

To naprawił ostrzeżenie, ale wprowadzono błąd. Lista `NewsItems` jest teraz **poprawna według konstrukcji,** ale `OnGet` kod, który ustawia listę, musi zostać zmienił, aby pasował do nowego interfejsu API. Zamiast przypisania, `AddRange` zadzwoń, aby dodać elementy wiadomości do istniejącej listy:

[!code-csharp[AddRange](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Użycie `AddRange` zamiast przypisania oznacza, że `GetNews` `IEnumerable` metoda może `List`zwrócić zamiast . To oszczędza jedną alokację. Zmień podpis metody i usuń `ToList` wywołanie, jak pokazano w poniższym przykładzie kodu:

[!code-csharp[GetNews](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

Zmiana podpisu przerywa również jeden z testów. Otwórz `NewsServiceTests.cs` plik w `Services` folderze `SimpleFeedReader.Tests` projektu. Przejdź do `Returns_News_Stories_Given_Valid_Uri` testu i zmień `result` typ `IEnumerable<NewsItem>`zmiennej na . Zmiana typu `Count` oznacza, że właściwość nie jest `Count` już `Assert` dostępna, więc `Any()`zamień właściwość w wywołaniu:

[!code-csharp[FixTests](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Należy również dodać instrukcję `using System.Linq` na początku pliku.

Ten zestaw zmian podkreśla szczególną uwagę podczas aktualizowania kodu, który zawiera ogólne wystąpienia. Zarówno lista, jak i elementy na liście typów niepodlegających zerwanym. Typy z możliwością odmienne lub oba mogą być typami z możliwością null. Dozwolone są wszystkie następujące deklaracje:

- `List<NewsStoryViewModel>`: nieunieważniona lista nieunieważnialnych modeli widoku.
- `List<NewsStoryViewModel?>`: nieunieważnialna lista modeli widoku unieważnianego.
- `List<NewsStoryViewModel>?`: lista widoków niepodlegających unieważnieniu.
- `List<NewsStoryViewModel?>?`: lista widoków nullable.

## <a name="interfaces-with-external-code"></a>Interfejsy z kodem zewnętrznym

Wprowadzono zmiany w `NewsService` klasie, więc włącz `#nullable enable` adnotację dla tej klasy. Nie spowoduje to wygenerowania żadnych nowych ostrzeżeń. Jednak dokładne zbadanie klasy pomaga zilustrować niektóre ograniczenia analizy przepływu kompilatora. Sprawdź konstruktora:

[!code-csharp[ServiceConstructor](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

Parametr `IMapper` jest wpisywany jako odwołanie niepodlegające unieważnieniu. Jest wywoływana przez ASP.NET core kod infrastruktury, więc kompilator tak naprawdę nie wie, że nigdy nie `IMapper` będzie null. Domyślny ASP.NET Core dependency injection (DI) kontener zgłasza wyjątek, jeśli nie można rozwiązać niezbędne usługi, więc kod jest poprawny. Kompilator nie może sprawdzić poprawności wszystkich wywołań publicznych interfejsów API, nawet jeśli kod jest kompilowany z włączonymi kontekstami adnotacji nullable. Ponadto biblioteki mogą być używane przez projekty, które nie zostały jeszcze włączone do używania typów odwołań nullable. Sprawdź poprawność danych wejściowych do publicznych interfejsów API, nawet jeśli zostały zadeklarowane jako typy niepodlegające unieważnieniu.

## <a name="get-the-code"></a>Uzyskiwanie kodu

Poprawiono ostrzeżenia zidentyfikowane w kompilacji testu początkowego, więc teraz można włączyć kontekst adnotacji nullable dla obu projektów. Odbudować projekty; kompilator nie zgłasza żadnych ostrzeżeń. Kod gotowego projektu można uzyskać w repozytorium [githubdodot/próbki dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished)

Nowe funkcje, które obsługują typy odwołań nullable pomóc `null` znaleźć i naprawić potencjalne błędy w sposobie obsługi wartości w kodzie. Włączenie kontekstu adnotacji nullable umożliwia wyrażenie intencji projektu: niektóre zmienne nigdy nie powinny być null, inne zmienne mogą zawierać wartości null. Te funkcje ułatwiają deklarowanie intencji projektu. Podobnie kontekst ostrzeżenia nullins kompilator do wydawania ostrzeżeń, gdy zostały naruszone tego zamiaru. Te ostrzeżenia prowadzą do tworzenia aktualizacji, które sprawiają, że `NullReferenceException` kod bardziej odporne i mniej prawdopodobne, aby zgłosić podczas wykonywania. Można kontrolować zakres tych kontekstów, dzięki czemu można skupić się na lokalnych obszarach kodu do migracji, podczas gdy pozostała baza kodu jest nietknięta. W praktyce można zrobić to zadanie migracji częścią regularnej konserwacji do klas. W tym samouczku pokazano proces migracji aplikacji do używania typów odwołań nullable. Można zbadać większy rzeczywisty przykład tego procesu, badając PR [Jon Skeet](https://github.com/jskeet) wykonane w celu włączenia typów odwołań nullable do [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits). Lub po prostu Ponadto można nauczyć się technik używania typów odwołań nullable z entity framework core w [jednostce Framework Core — praca z typami odwołań nullable](/ef/core/miscellaneous/nullable-reference-types).
