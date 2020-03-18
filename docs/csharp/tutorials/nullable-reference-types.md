---
title: Projekt z typami odwołań z wartością null
description: Ten zaawansowany samouczek zawiera wprowadzenie do typów odwołań nullable. Nauczysz się wyrażać zamiar projektu, gdy wartości odwołania może być null i kompilator wymusić, gdy nie mogą być null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: b00050c1d151b95e330f94eb9393a4031e47d5a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240070"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Samouczek: Wyraźniejsze wyrażanie intencji projektu za pomocą typów odwołań niepodlegających unieważnieniu i niepodlegających unieważnieniu

C# 8.0 wprowadza [typy odwołań nullable](../nullable-references.md), które uzupełniają typy odwołań w ten sam sposób typy wartości null douzupełnienia typów wartości. Deklarujesz zmienną jako typ odwołania z `?` **wartością null,** dołączając do typu. Na przykład `string?` reprezentuje nullable `string`. Można użyć tych nowych typów, aby wyraźniej wyrazić intencję projektu: niektóre zmienne *muszą zawsze mieć wartość,* inne *mogą brakować wartości.*

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Uwzględnianie typów odwołań z możliwością null i niepodlegających zerowym wartości do projektów
> - Włącz sprawdzanie typu odwołania z możliwością null w całym kodzie.
> - Napisz kod, w którym kompilator wymusza te decyzje projektowe.
> - Użyj funkcji odwołania unieważnialnej we własnych projektach

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0. Kompilator C# 8.0 jest dostępny w [programie Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W tym samouczku przyjęto założenie, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Uwzględnianie typów odwołań z możliwością null do swoich projektów

W tym samouczku stworzysz bibliotekę, która modeluje uruchamianie ankiety. Kod używa zarówno typów odwołań nullable i typy odwołań niedopuszczających do wartości null do reprezentowania rzeczywistych pojęć. Pytania ankiety nigdy nie mogą być zerowe. Respondent może nie chcieć odpowiadać na pytanie. Odpowiedzi mogą `null` być w tym przypadku.

Kod, który napiszesz dla tego przykładu wyraża ten zamiar, a kompilator wymusza ten zamiar.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Tworzenie aplikacji i włączanie typów odwołań możliwych do przemiennego

Utwórz nową aplikację konsoli w programie Visual `dotnet new console`Studio lub z wiersza polecenia przy użyciu . Nazwij `NullableIntroduction`aplikację . Po utworzeniu aplikacji należy określić, że cały projekt kompiluje się w włączonym **kontekście adnotacji nullable**. Otwórz plik *csproj* i `Nullable` dodaj element `PropertyGroup` do elementu. Ustaw dla niej wartość `enable`. Należy zdecydować się na **nullable funkcji typów odwołań,** nawet w projektach C# 8.0. Dzieje się tak, ponieważ po włączeniu funkcji istniejące deklaracje zmiennych referencyjnych stają się **typami odwołań niepodlegających wartości null.** Chociaż ta decyzja pomoże znaleźć problemy, w których istniejący kod może nie mieć odpowiednich kontroli null, może nie dokładnie odzwierciedlać oryginalny zamiar projektu:

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Projektowanie typów aplikacji

Ta aplikacja ankiety wymaga utworzenia kilku klas:

- Klasa, która modeluje listę pytań.
- Klasa, która modeluje listę osób, z którymi skontaktowano się w celu uzyskania ankiety.
- Klasa, która modeluje odpowiedzi od osoby, która wzięła udział w ankiecie.

Typy te będą korzystać z typów odwołań nullable i niedopuszczający do wartości null do wyrażenia, które elementy członkowskie są wymagane, a które elementy członkowskie są opcjonalne. Typy odwołań niedotensowywalne wyraźnie komunikują, że intencja projektu:

- Pytania, które są częścią ankiety nigdy nie może być null: Nie ma sensu zadawać puste pytanie.
- Respondenci nigdy nie mogą być nieważności. Warto śledzić osoby, z którymi się skontaktowałeś, nawet respondentów, którzy odmówili udziału.
- Każda odpowiedź na pytanie może być nieważna. Respondenci mogą odmówić odpowiedzi na niektóre lub wszystkie pytania.

Jeśli programujesz w języku C#, możesz być tak przyzwyczajony `null` do typów odwołań, które zezwalają na wartości, które mogły zostać pominięte inne szanse sprzedaży, aby zadeklarować wystąpienia niepodlegające wartości null:

- Zbieranie pytań powinno być niedopuszczające wartości null.
- Zbiór respondentów nie powinien być unieważniony.

Podczas pisania kodu zobaczysz, że typ odwołania niedopuszczający wartości null jako domyślny dla <xref:System.NullReferenceException>odwołań pozwala uniknąć typowych błędów, które mogą prowadzić do s. Jedną z lekcji z tego samouczka jest to, że `null`podjąłeś decyzje o tym, które zmienne mogą lub nie mogą być . Język nie dostarczył składni do wyrażania tych decyzji. Teraz tak.

Aplikacja, którą stworzysz, wykonuje następujące czynności:

1. Tworzy ankietę i dodaje do niej pytania.
1. Tworzy pseudolosowy zestaw respondentów do ankiety.
1. Kontaktuje się z respondentami, dopóki rozmiar wypełnionej ankiety nie osiągnie numeru celu.
1. Zapisuje ważne statystyki odpowiedzi na ankiety.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Tworzenie ankiety przy pomocą typów z wartością null i niepodlegających zerowym wartościnull

Pierwszy kod, który napiszesz, tworzy ankietę. Będziesz pisać klasy do modelowania pytania ankiety i przebiegu ankiety. Ankieta zawiera trzy rodzaje pytań, wyróżnione formatem odpowiedzi: Odpowiedzi tak/nie, odpowiedzi liczbowe i odpowiedzi tekstowe. Utwórz `public SurveyQuestion` klasę:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilator interpretuje każdą deklarację zmiennej typu odwołania jako typ odwołania **niemożliwy do unieważnienia** dla kodu w włączonym kontekście adnotacji nullable. Pierwsze ostrzeżenie można wyświetlić, dodając właściwości tekstu pytania i typ pytania, jak pokazano w poniższym kodzie:

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

Ponieważ nie zostały zainicjowane, `QuestionText`kompilator wystawia ostrzeżenie, że właściwość nie podlegające null nie została zainicjowana. Projekt wymaga, aby tekst pytania był niezerowy, więc należy dodać konstruktora, aby zainicjować go i `QuestionType` wartość, jak również. Definicja ukończonej klasy wygląda jak następujący kod:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Dodanie konstruktora usuwa ostrzeżenie. Argument konstruktora jest również typem odwołania niedopuszczającym do wartości null, więc kompilator nie wydaje żadnych ostrzeżeń.

Następnie utwórz `public` klasę `SurveyRun`o nazwie . Ta klasa zawiera `SurveyQuestion` listę obiektów i metod dodawania pytań do ankiety, jak pokazano w poniższym kodzie:

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

Tak jak poprzednio, należy zainicjować obiekt listy do wartości innych niż null lub kompilator wydaje ostrzeżenie. Nie ma żadnych kontroli null w `AddQuestion` drugim przeciążenia, ponieważ nie są one potrzebne: Zadeklarowano, że zmienna jest nienullable. Jego wartość nie `null`może być .

Przełącz się do *Program.cs* w edytorze i zastąp zawartość następujących wierszy `Main` kodu:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Ponieważ cały projekt znajduje się w włączonym kontekście adnotacji nullable, otrzymasz ostrzeżenia po przekazaniu `null` do dowolnej metody oczekujące niedopuszczającej wartości null typu odwołania. Spróbuj, dodając następujący wiersz `Main`do:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Tworzenie respondentów i uzyskanie odpowiedzi na ankietę

Następnie napisz kod, który generuje odpowiedzi na ankietę. Proces ten obejmuje kilka małych zadań:

1. Tworzenie metody, która generuje obiekty respondenta. Reprezentują one osoby poproszone o wypełnienie ankiety.
1. Zbuduj logikę, aby symulować zadawanie pytań respondentowi i zbieranie odpowiedzi lub odnotowując, że respondent nie odpowiedział.
1. Powtarzaj tę czynność, aż wystarczająca liczba respondentów odpowie na ankietę.

Będziesz potrzebować klasy do reprezentowania odpowiedzi na ankietę, więc dodaj to teraz. Włącz obsługę z możliwością null. Dodaj `Id` właściwość i konstruktora, który inicjuje go, jak pokazano w następującym kodzie:

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

Następnie dodaj `static` metodę tworzenia nowych uczestników, generując losowy identyfikator:

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Głównym obowiązkiem tej klasy jest generowanie odpowiedzi dla uczestnika na pytania w ankiecie. Odpowiedzialność ta ma kilka kroków:

1. Poproś o udział w ankiecie. Jeśli dana osoba nie wyrazi zgody, zwróć brakjącą (lub null) odpowiedź.
1. Zadaj każde pytanie i zapisz odpowiedź. Każda odpowiedź może również brakować (lub null).

Dodaj następujący kod `SurveyResponse` do swojej klasy:

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Magazyn odpowiedzi na ankietę `Dictionary<int, string>?`jest , wskazując, że może być null. Używasz nowej funkcji języka, aby zadeklarować zamiar projektu, zarówno do kompilatora, jak i dla każdego, kto czyta kod później. Jeśli kiedykolwiek wyłuskbez wątpienia `surveyResponses` `null` bez sprawdzania wartości po raz pierwszy, otrzymasz ostrzeżenie kompilatora. Nie otrzymasz ostrzeżenia w `AnswerSurvey` metodzie, ponieważ kompilator można określić `surveyResponses` zmienna została ustawiona na wartość nienull powyżej.

Używanie `null` brakujących odpowiedzi wyróżnia kluczowy punkt pracy z typami odwołań z `null` możliwością unieważnienia: celem nie jest usunięcie wszystkich wartości z programu. Raczej twoim celem jest zapewnienie, że kod, który piszesz wyraża intencje projektu. Brakujące wartości są niezbędne pojęcie do wyrażenia w kodzie. Wartość `null` jest jasnym sposobem wyrażania tych brakujących wartości. Próba usunięcia `null` wszystkich wartości prowadzi tylko do zdefiniowania `null`innego sposobu wyrażania brakujących wartości bez .

Następnie należy napisać `PerformSurvey` metodę w `SurveyRun` klasie. Dodaj następujący kod `SurveyRun` w klasie:

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

W tym przypadku wybór nullable `List<SurveyResponse>?` wskazuje, że odpowiedź może być null. Oznacza to, że ankieta nie została jeszcze przekazana żadnym respondentom. Należy zauważyć, że respondenci są dodawani, dopóki nie wyrazi zgody.

Ostatnim krokiem do uruchomienia ankiety jest dodanie połączenia do wykonania `Main` ankiety na końcu metody:

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Badanie odpowiedzi na ankiety

Ostatnim krokiem jest wyświetlenie wyników ankiety. Dodasz kod do wielu napisanych klas. Ten kod demonstruje wartość rozróżniania typów odwołań nullable i niedopuszczający do wartości null. Zacznij od dodania następujących dwóch elementów `SurveyResponse` członkowskich zabudowanych wyrażeniem do klasy:

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Ponieważ `surveyResponses` jest typem odwołania null, kontrole wartości null są niezbędne przed odwiązaniem go. Metoda `Answer` zwraca ciąg niedający się do null, więc musimy pokryć przypadek brakującej odpowiedzi przy użyciu operatora łączenia wartości null.

Następnie dodaj te trzy elementy członkowskie `SurveyRun` zabudowane wyrażeniem do klasy:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Element `AllParticipants` członkowski musi `respondents` wziąć pod uwagę, że zmienna może być null, ale wartość zwracana nie może być null. Jeśli zmienisz to wyrażenie, usuwając `??` i pusta sekwencja, która następuje, kompilator ostrzega, że metoda może zwrócić, `null` a jej podpis zwrotny zwraca typ niepodlegający null.

Na koniec dodaj następującą pętlę u dołu `Main` metody:

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Nie trzeba żadnych `null` kontroli w tym kodzie, ponieważ zostały zaprojektowane interfejsów źródłowych, tak aby wszystkie zwracać typy odwołań niedopuszczające wartości null.

## <a name="get-the-code"></a>Uzyskiwanie kodu

Kod gotowego samouczka można uzyskać z naszego repozytorium [próbek](https://github.com/dotnet/samples) w folderze [csharp/NullableIntroduction.](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction)

Eksperymentuj, zmieniając deklaracje typów między typami odwołań z wartością null i niepodlegającymi zerowym. Zobacz, jak to generuje różne ostrzeżenia, aby upewnić się, że nie przypadkowo wyłudzać . `null`

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej, migrując istniejącą aplikację, aby użyć typów odwołań z możliwością null:
> [!div class="nextstepaction"]
> [Uaktualnianie aplikacji w celu użycia typów odwołań z możliwością null](upgrade-to-nullable-references.md)
