---
title: Projektowanie w przypadku typów referencyjnych dopuszczającego wartość null
description: W tym samouczku zaawansowane zawiera wprowadzenie do typów referencyjnych dopuszczającego wartość null. Dowiesz się, że express projektu chcący po wartości odniesienia może mieć wartości null i pozwolić kompilatorowi wymusić, gdy nie może mieć wartości null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 97b41574b328c9f6bed60d4bf2943c7a726261d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706172"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Samouczek: Wyraźniej Express zgodną z planem projektu w przypadku typów referencyjnych dopuszcza wartości null i nie dopuszcza wartości null

C#8 wprowadzono **typy dopuszczające wartości null odwołań**, które odwołania uzupełnieniem typów taki sam sposób, typy o wartości zerowalnej uzupełniają typów wartości. Zadeklaruj zmienną **typu dopuszczającego wartość null odwołania** , dodając `?` do typu. Na przykład `string?` reprezentuje dopuszczający wartości null `string`. Te nowe typy można użyć, aby wyraźniej express zgodną z planem projektu: niektóre zmienne *zawsze musi mieć wartość*, inne *może brakować wartość*.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> * Włączenie typy dopuszczające wartości null i dopuszcza odwołań do projektów
> * Włącz sprawdzanie typu dopuszczającego wartość null odwołanie w całym kodzie.
> * Napisz kod, w których kompilator wymusza tych decyzji projektowych.
> * Funkcja odwołanie dopuszczającego wartość null w własnych projektów

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 beta. C# 8 kompilatora w wersji beta jest dostępna z [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), lub r [.NET Core 3.0 w wersji zapoznawczej](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Włączenie typy dopuszczające wartości null odwołań do projektów

W tym samouczku utworzysz biblioteki, który modeluje systemem ankiety. Kod używa typy dopuszczające wartości null odwołań i typy referencyjne nie dopuszcza wartości null w celu przedstawienia koncepcji rzeczywistych. Pytania ankiety nigdy nie może mieć wartości null. Respondenta może nie chce uzyskać odpowiedzi na pytanie. W takim przypadku może mieć wartości null odpowiedzi.

Kod, który Ty napiszesz omawiany w tym przykładzie wyrażenie wskaźnika tym przeznaczeniem, a kompilator wymusza tym przeznaczeniem.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Tworzenie aplikacji i włączanie typów referencyjnych dopuszczającego wartość null

Utwórz nową aplikację konsoli w programie Visual Studio lub z wiersza polecenia przy użyciu `dotnet new console`. Nazwij aplikację `NullableIntroduction`. Po utworzeniu aplikacji, musisz włączyć C# 8 funkcje w wersji beta. Otwórz `csproj` pliku i Dodaj `LangVersion` elementu `PropertyGroup` elementu. Użytkownik musi wyrazić zgodę **typy dopuszczające wartości null odwołań** funkcji, nawet w C# 8 projektów. To dlatego po włączeniu funkcji istniejące deklaracje zmiennych odwołania stają się, że **typów referencyjnych dopuszcza**. Podczas tej decyzji pomogą znaleźć problemy, gdy istniejący kod może nie mieć odpowiednich sprawdzanie wartości null, jego mogą nie odzwierciedla precyzyjnie zgodne z zamiarami użytkownika oryginalnego projektu. Możesz włączyć tę funkcję, ustawiając `NullableContextOptions` elementu `enable`:

```xml
<LangVersion>8.0</LangVersion>
<NullableContextOptions>enable</NullableContextOptions>
```

> [!NOTE]
> Gdy C# wydaniu 8 (nie w wersji zapoznawczej), `NullableContextOptions` element zostanie dodany przez nowe szablony projektów. Do tego czasu należy dodać ją ręcznie.

### <a name="design-the-types-for-the-application"></a>Projektowanie typów dla aplikacji

Ta aplikacja ankiety wymaga, tworząc liczby klas:

- Klasa, która modele listę pytań.
- Klasa, która modele listę osób skontaktować się z ankietę.
- Klasa, która modele odpowiedzi od osoby, która trwała ankiety.

Te typy spowoduje, że wykorzystanie zarówno dopuszczającego wartość null i typy nieprzyjmujące wartości odwołań do wyrażania elementów członkowskich, które są wymagane i elementów członkowskich, które są opcjonalne. Typy dopuszczające wartości null odwołanie do komunikacji, wyraźnie projektowania przeznaczenie:

- Pytania, na które są dostępne w ramach przeglądu nigdy nie może mieć wartość null: Nie ma sensu zadać pytanie puste.
- Respondentów nigdy nie może mieć wartości null. Należy śledzić osób z Tobą, nawet respondentów, które odrzucone do udziału.
- Każda odpowiedź na pytanie może mieć wartości null. Respondentów można odrzucić odpowiedzi na niektóre lub wszystkie pytania.

Jeśli został zaprogramowany w C#, można więc przyzwyczajeni do odwołania typów, które akceptuje wartości null, które mogły zostać pominięte innymi możliwościami do deklarowania dopuszcza wystąpień:

- Kolekcji pytań, powinna być wartość null.
- Kolekcja respondentów powinna być wartość null.

Podczas pisania kodu, zobaczysz, że typ odwołania nie dopuszcza wartości null jako domyślne dla odwołania pozwala uniknąć typowych pomyłek, które mogą prowadzić do wyjątków odwołanie o wartości null. Lekcja jeden z tego samouczka jest podjęliśmy decyzje, o których zmiennych może lub nie może mieć wartości null. Język nie dostarczył składni wyrażenia te decyzje. Teraz robi.

Aplikację, którą utworzysz będzie wykonywać następujące czynności:

1. Tworzą ankietę i dodać pytania do niego.
1. Utwórz zestaw pseudolosową respondentów ankietę.
1. Skontaktuj się z respondentów, dopóki numer celem osiągnie rozmiar przeprowadzone badania.
1. Zapisać ważnych statystyk w odpowiedzi na ankietę.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Tworzenie przeglądu z typu dopuszczającego wartość null i nie dopuszcza wartości null

Pierwszy kod, który Ty napiszesz tworzy ankietę. Przedstawiono tworzenie klas modelu pytania ankiety i ankiety, uruchom. Ankiety ma trzy rodzaje pytań związanych z rozróżnianych na podstawie formatu odpowiedzi: Tak/nie odbierze odpowiedzi numer i tekst odpowiedzi. Tworzenie `public` `SurveyQuestion` klasy:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilator interpretuje co deklaracji zmiennych typu odwołania jako **dopuszcza** odwołania do typu dla kodu w kontekście włączone dopuszczającego wartość null. Można wyświetlić swoje pierwsze ostrzeżenie przez dodanie właściwości tekst pytania i rodzaju pytania, jak pokazano w poniższym kodzie:

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

Ponieważ jeszcze nie zainicjowany `QuestionText`, kompilator generuje ostrzeżenie właściwości niedopuszczającej nie zostało zainicjowane. Projekt wymaga tekst pytania, aby mieć wartości null, więc dodać konstruktora, aby go zainicjować i `QuestionType` również wartość. Definicja klasy Zakończono wygląda podobnie do poniższego kodu:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Dodanie konstruktora powoduje usunięcie ostrzeżenia. Argument konstruktora jest również typem referencyjnym dopuszcza kompilator nie generuje żadnych ostrzeżeń.

Następnie należy utworzyć `public` klasę o nazwie `SurveyRun`. Ta klasa zawiera listę `SurveyQuestion` obiektów i metod, aby dodać pytania ankiety, jak pokazano w poniższym kodzie:

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

Tak jak poprzednio należy zainicjować obiekt listy, do wartości innej niż null lub kompilator generuje ostrzeżenie. Nie ma żadnych sprawdzanie wartości null w drugie przeciążenie `AddQuestion` , ponieważ nie są one potrzebne: Został zadeklarowany tej zmiennej jako wartości null. Jego wartość nie może być `null`.

Przełącz się do `Program.cs` w edytorze i Zastąp zawartość `Main` z następującymi wierszami kodu:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Ponieważ cały projekt jest w kontekście włączone dopuszczającego wartość null, otrzymasz ostrzeżenia, jeśli przekazujesz `null` do dowolnej metody, oczekiwano typu odwołania nie dopuszcza wartości null. Wypróbuj je, dodając następujący wiersz do `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Utwórz respondentów i Uzyskaj odpowiedzi na ankietę

Następnie napisz kod, który generuje odpowiedzi na ankietę. Ten proces obejmuje kilka małych zadań:

1. Tworzenie metody, która generuje obiekty respondentów. Reprezentują one zadawane Wypełnij ankietę.
1. Twórz logikę do symulacji udzielenia odpowiedzi na pytania respondentom i zbieranie odpowiedzi lub biorąc pod uwagę, że respondenta nie odpowiedzieć.
1. Powtórz wystarczająco dużo respondentów Uzyskaj odpowiedzi na ankietę.

Potrzebna będzie klasy do reprezentowania odpowiedź na ankietę, więc teraz dodać. Włącz obsługę dopuszczającego wartość null. Dodaj `Id` właściwość i Konstruktor, który inicjuje go, jak pokazano w poniższym kodzie:

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

Następnie dodaj `static` metodę w celu utworzenia nowych uczestników, generując losowy identyfikator:

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Podstawowa odpowiedzialność tej klasy jest do generowania odpowiedzi dla uczestników na pytania ankiety. Ta odpowiedzialność składa się z kilku kroków:

1. Prosić o udział w ankiecie. Jeśli dana osoba nie zgodę, zwróć odpowiedź (wartość null lub nie).
1. Zadawaj pytania i Zapisz odpowiedź. Wszystkie odpowiedzi jest także (wartość null lub nie).

Dodaj następujący kod, aby Twoje `SurveyResponse` klasy:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Magazyn odpowiedzi udział w ankiecie jest `Dictionary<int, string>?`, wskazujący, że może mieć wartości null. Zadeklaruj zamiar projektu, kompilator i kto czyta swój kod w dalszej części za pomocą nowej funkcji języka. Jeśli kiedykolwiek wyłuskania `surveyResponses` bez uprzedniego sprawdzania pod zawiera wartości null, zostanie wyświetlone ostrzeżenie kompilatora. Nie pojawi się ostrzeżenie `AnswerSurvey` metody ponieważ kompilator może określić `surveyResponses` zmienna została ustawiona na wartość inną niż null powyżej.

Za pomocą `null` dla Brak odpowiedzi wyróżnia punkt klucza do pracy w przypadku typów referencyjnych dopuszczającego wartość null: cel nie jest, aby usunąć wszystkie `null` wartości z programu. Celem użytkownika jest raczej, upewnij się, że kod, który napiszesz wyraża celem projektu. Brak wartości są niezbędne pojęcia, aby wyrazić w kodzie. `null` Wartość jest jasny sposób wyrażania te brakujące wartości. Próby usunięcia wszystkich `null` tylko prowadzi do definiowania niektóre sposobu, aby te brakujące wartości bez wartości `null`.

Następnie należy napisać `PerformSurvey` method in Class metoda `SurveyRun` klasy. Dodaj następujący kod w `SurveyRun` klasy:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Ponownie w tym miejscu, wybór dopuszczający wartości null `List<SurveyResponse>?` wskazuje odpowiedzi może mieć wartości null. Wskazuje, że udział w ankiecie nie zostały przypisane do żadnych respondentów jeszcze. Należy zauważyć, że respondentów są dodawane do momentu wystarczająco wyrażono zgodę.

Ostatni krok, aby uruchomić udział w ankiecie jest dodanie wywołanie przeprowadzić ankietę na końcu `Main` metody:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Sprawdź odpowiedzi na ankietę

Ostatnim krokiem jest do wyświetlania wyników ankiety. Następnie dodasz kod do wielu klas, które zostały zapisane. Ten kod przedstawia wartość rozróżniania typów referencyjnych dopuszcza wartości null i nie dopuszcza wartości null. Rozpocznij, dodając następujące dwa elementy członkowskie z wyrażeniem do `SurveyResponse` klasy:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Ponieważ `surveyResponses` jest typem niedopuszczającym odwołania żadne testy nie są niezbędne przed do odwoływania się do niego. `Answer` Metoda zwraca ciąg z innych niż null, więc wybierz przeciążenia `GetValueOrDefault` przyjmującej drugi argument dla wartości domyślnej.

Następnie dodaj te trzy elementy członkowskie z wyrażeniem do `SurveyRun` klasy:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

`AllParticipants` Element członkowski należy wziąć pod uwagę, `respondents` zmienna może mieć wartości null, ale wartość zwracana nie może mieć wartości null. Jeśli zmienisz to wyrażenie, usuwając `??` i pustej sekwencji, który następuje po kompilatora ostrzega, metoda może zwrócić `null` i jeho signatura zwracany zwraca typ niedopuszczający.

Na koniec Dodaj następującą pętlę w dolnej części `Main` metody:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Nie potrzebujesz żadnej `null` sprawdza w tym kodzie, ponieważ został zaprojektowany podstawowych interfejsów, tak, aby wszystkie one zwracane typy nieprzyjmujące wartości odwołania.

## <a name="get-the-code"></a>Pobierz kod

Możesz też uzyskać kod Zakończono samouczek z naszych [przykłady](https://github.com/dotnet/samples) repozytorium w [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folderu.

Eksperymentować, zmieniając deklaracje typu między typami dopuszczającego wartość null i wartości null. Zobacz, jak generujący różnych ostrzeżenia, aby upewnić się, przypadkowo nie wykonuj dereferencji `null`.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej, migrując istniejących aplikacji na używanie typów referencyjnych dopuszczającego wartość null:
> [!div class="nextstepaction"]
> [Uaktualnianie aplikacji na używanie typów nullable odwołań](upgrade-to-nullable-references.md)
