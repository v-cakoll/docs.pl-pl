---
title: Projektowanie z typami odwołań z wartością nullable
description: Ten zaawansowany samouczek zawiera wprowadzenie do typów odwołań nullable. Nauczysz się wyrażać intencji projektu, gdy wartości odwołania mogą być null i kompilator wymusić, gdy nie mogą być null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 54cf9d812999cae837483b48cdedd89d9dc40fc9
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249132"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Samouczek: Wyraź swój zamiar projektu jaśniej z nullable i non-null typów odwołań

C# 8.0 wprowadza [nullable typy odwołań](../nullable-references.md), które uzupełniają typy odwołań w taki sam sposób typy wartości nullable uzupełnienia typów wartości. Deklarujesz zmienną jako **typ odwołania powodujący wartość null,** dołączając go `?` do typu. Na przykład `string?` reprezentuje nullable `string`. Można użyć tych nowych typów, aby wyraźniej wyrazić swoje intencje projektowe: niektóre zmienne *muszą zawsze mieć wartość,* inne *mogą brakować wartości.*

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Uwzględnianie do swoich projektów typów odwołań, których nie można unieważnić i nie można ich unieważnić
> - Włącz sprawdzanie typu odwołania z nullable w całym kodzie.
> - Napisz kod, w którym kompilator wymusza te decyzje projektowe.
> - Użyj funkcji odniesienia, której można anulować we własnych projektach

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilatora C# 8.0. Kompilator języka C# 8.0 jest dostępny w [programie Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W tym samouczku założono, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Uwzględnianie typów odwołań, których można anulować, do wzorów

W tym samouczku utworzysz bibliotekę, która modeluje z udziałem ankiety. Kod używa zarówno nullable typów odwołań i typów odwołań nie nullable do reprezentowania rzeczywistych pojęć. Pytania ankietowe nigdy nie mogą być zerowe. Respondent może nie odpowiadać na pytanie. Odpowiedzi mogą być `null` w tym przypadku.

Kod, który napiszesz dla tego przykładu wyraża tę intencję, a kompilator wymusza tę intencję.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Tworzenie aplikacji i włączanie typów odwołań z dopuszczalną wartością null

Utwórz nową aplikację konsoli w programie Visual Studio `dotnet new console`lub z wiersza polecenia za pomocą programu . Nazwij `NullableIntroduction`aplikację . Po utworzeniu aplikacji należy określić, że cały projekt kompiluje się w włączonym **kontekście adnotacji z możliwością null.** Otwórz plik *csproj* i `Nullable` dodaj element `PropertyGroup` do elementu. Ustaw dla niej wartość `enable`. Należy wybrać funkcję **typów odwołań, których można anulować,** nawet w projektach języka C# 8.0. Dzieje się tak dlatego, że po włączeniu funkcji istniejące deklaracje zmiennych referencyjnych stają się **typami odwołań niepodważalnych.** Chociaż ta decyzja pomoże znaleźć problemy, w których istniejący kod może nie mieć odpowiednich kontroli zerowych, może nie odzwierciedlać dokładnie oryginalnego zamiaru projektu:

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Projektowanie typów dla aplikacji

Ta aplikacja ankietowa wymaga utworzenia wielu klas:

- Klasa, która modeluje listę pytań.
- Klasa, która modeluje listę osób, z którymi skontaktowano się w celu wykonania ankiety.
- Klasa, która modeluje odpowiedzi od osoby, która wzięła udział w ankiecie.

Te typy będą korzystać z typów odwołań nullable i nie nullable wyrazić, które elementy członkowskie są wymagane, a które są opcjonalne. Typy odwołań dopuszczania do wartości null komunikują intencję projektu wyraźnie:

- Pytania, które są częścią badania nigdy nie może być null: Nie ma sensu zadać puste pytanie.
- Respondenci nigdy nie mogą być zerowi. Będziesz chciał śledzić osoby, z którymi się skontaktowałeś, a nawet respondentów, którzy odmówili udziału.
- Każda odpowiedź na pytanie może mieć wartość null. Respondenci mogą odmówić odpowiedzi na niektóre lub wszystkie pytania.

Jeśli masz zaprogramowane w języku C#, może być tak `null` przyzwyczajony do typów odwołań, które pozwalają na wartości, które mogą mieć pominięte inne możliwości deklarowania wystąpienia nienastępne do null:

- Zbieranie pytań powinno być nie można anulować.
- Zbieranie respondentów powinno być niedościwidalne.

Podczas pisania kodu zobaczysz, że typ odwołania nienależytego do wartości null jako domyślny <xref:System.NullReferenceException>dla odwołań pozwala uniknąć typowych błędów, które mogą prowadzić do s. Jedną z lekcji z tego samouczka jest to, że `null`podjąłeś decyzje o tym, które zmienne mogą lub nie mogą być . Język nie podał składni, aby wyrazić te decyzje. Teraz tak.

Aplikacja, którą skompilujesz, wykonuje następujące czynności:

1. Tworzy ankietę i dodaje do niej pytania.
1. Tworzy pseudolosowy zestaw respondentów do badania.
1. Kontaktuje się z respondentami, dopóki wypełniony rozmiar ankiety nie osiągnie numeru celu.
1. Zapisuje ważne statystyki dotyczące odpowiedzi na ankietę.

## <a name="build-the-survey-with-nullable-and-non-nullable-reference-types"></a>Tworzenie ankiety z typami odwołań z których można anulować i nienastępującym do wartości null

Pierwszy kod, który napiszesz, tworzy ankietę. Będziesz pisać klasy do modelowania pytania ankiety i badania. Ankieta zawiera trzy rodzaje pytań, wyróżniające się formatem odpowiedzi: Tak/Nie odpowiedzi, odpowiedzi liczbowe i odpowiedzi tekstowe. Tworzenie `public SurveyQuestion` klasy:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilator interpretuje każdą deklarację zmiennej typu odwołania jako typ odwołania **niepodważalny** dla kodu w włączonym kontekście adnotacji z możliwością null. Pierwsze ostrzeżenie można wyświetlić, dodając właściwości tekstu pytania i typu pytania, jak pokazano w poniższym kodzie:

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

Ponieważ nie zostały zainicjowane, `QuestionText`kompilator generuje ostrzeżenie, że właściwość nie można anulować nie została zainicjowana. Projekt wymaga, aby tekst pytania był nietrwały, więc należy dodać `QuestionType` konstruktora, aby zainicjować go i wartość, jak również. Definicja gotowej klasy wygląda następująco:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Dodanie konstruktora usuwa ostrzeżenie. Argument konstruktora jest również typem odwołania, którego nie można unieważnić, więc kompilator nie wydaje żadnych ostrzeżeń.

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

Tak jak poprzednio, należy zainicjować obiekt listy do wartości innej niż null lub kompilator generuje ostrzeżenie. Nie ma żadnych kontroli null w `AddQuestion` drugim przeciążenie, ponieważ nie są one potrzebne: Zadeklarowałeś, że zmienna jest nie można anulować. Jego wartość nie `null`może być .

Przełącz się na *Program.cs* w edytorze `Main` i zastąp zawartość następujących wierszy kodu:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Ponieważ cały projekt znajduje się w włączonym kontekście adnotacji z `null` możliwością null, otrzymasz ostrzeżenia po przejściu do dowolnej metody oczekującej typu odwołania, którego nie można anulować. Spróbuj, dodając następujący wiersz `Main`do:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Tworzenie respondentów i uzyskiwanie odpowiedzi na ankietę

Następnie napisz kod, który generuje odpowiedzi na ankietę. Proces ten obejmuje kilka małych zadań:

1. Tworzenie metody, która generuje respondenta obiektów. Reprezentują one osoby proszone o wypełnienie ankiety.
1. Tworzenie logiki do symulowania zadawania pytań do respondenta i zbierania odpowiedzi lub zauważyć, że respondent nie odpowiedział.
1. Powtarzaj, aż wystarczająca liczba respondentów odpowie na ankietę.

Będziesz potrzebować klasy do reprezentowania odpowiedzi na ankietę, więc dodaj ją teraz. Włącz obsługę można anulować. Dodaj `Id` właściwość i konstruktora, który inicjuje go, jak pokazano w poniższym kodzie:

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

1. Poproś o udział w ankiecie. Jeśli dana osoba nie wyrazi zgody, zwróć brakującą (lub null) odpowiedź.
1. Zadaj każde pytanie i zapisz odpowiedź. Każda odpowiedź może również brakować (lub null).

Dodaj następujący kod `SurveyResponse` do swojej klasy:

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Magazyn odpowiedzi na ankietę `Dictionary<int, string>?`jest , wskazując, że może być null. Używasz nowej funkcji języka, aby zadeklarować intencji projektu, zarówno do kompilatora i dla każdego, kto czyta kod później. Jeśli kiedykolwiek wyłuskania `surveyResponses` bez `null` sprawdzania wartości po raz pierwszy, otrzymasz ostrzeżenie kompilatora. Nie otrzymasz ostrzeżenia w `AnswerSurvey` metodzie, ponieważ kompilator może `surveyResponses` określić, że zmienna została ustawiona na wartość nie null powyżej.

Używanie `null` brakujących odpowiedzi wyróżnia kluczowy punkt do pracy z typami odwołań, `null` których można anulować: celem nie jest usunięcie wszystkich wartości z programu. Zamiast tego Twoim celem jest zapewnienie, że kod, który piszesz wyraża intencję projektu. Brakujące wartości są niezbędne pojęcie do wyrażenia w kodzie. Wartość `null` jest jasnym sposobem wyrażania tych brakujących wartości. Próba usunięcia `null` wszystkich wartości prowadzi tylko do zdefiniowania innego `null`sposobu wyrażania brakujących wartości bez .

Następnie należy napisać `PerformSurvey` metodę w `SurveyRun` klasie. Dodaj następujący kod `SurveyRun` w klasie:

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

W tym miejscu ponownie, `List<SurveyResponse>?` wybór nullable wskazuje odpowiedź może być null. Oznacza to, że ankieta nie została jeszcze przekazana żadnym respondentom. Należy zauważyć, że respondenci są dodawane, dopóki nie wystarczająco wyrazisz na to zgodę.

Ostatnim krokiem do uruchomienia ankiety jest dodanie połączenia w celu `Main` przeprowadzenia ankiety na końcu metody:

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Sprawdzanie odpowiedzi na ankietę

Ostatnim krokiem jest wyświetlenie wyników ankiety. Dodasz kod do wielu napisanych klas. Ten kod pokazuje wartość rozróżniania typów odwołań nullable i non-nullable. Zacznij od dodania następujących dwóch członków zabudowanych wyrażeniami `SurveyResponse` do klasy:

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Ponieważ `surveyResponses` jest typu odwołania nullable, null kontroli są niezbędne przed odsyłanie go. Metoda `Answer` zwraca ciąg nienastępujący do wartości null, więc musimy omówić przypadek brakującej odpowiedzi przy użyciu operatora scalania wartości null.

Następnie dodaj te trzy elementy członkowskie zabudowane wyrażeniami `SurveyRun` do klasy:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Element `AllParticipants` członkowski musi wziąć `respondents` pod uwagę, że zmienna może mieć wartość null, ale wartość zwracana nie może być null. Jeśli zmienisz to wyrażenie, `??` usuwając i puste sekwencji, która następuje, kompilator ostrzega, że metoda może powrócić `null` i jego podpis zwraca typ nie nullable.

Na koniec dodaj następującą pętlę `Main` u dołu metody:

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Nie trzeba żadnych `null` kontroli w tym kodzie, ponieważ zostały zaprojektowane interfejsów bazowych, tak aby wszystkie one zwracają typy odwołania bez null.

## <a name="get-the-code"></a>Uzyskiwanie kodu

Możesz pobrać kod gotowego samouczka z naszego repozytorium [próbek](https://github.com/dotnet/samples) w folderze [csharp/NullIntroduction.](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction)

Eksperymentuj, zmieniając deklaracje typów między typami odwołań, których można anulować i nie można anulować. Zobacz, jak to generuje różne ostrzeżenia, aby upewnić `null`się, że nie przypadkowo wyłuskać .

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej, migrując istniejącą aplikację w celu użycia typów odwołań powodujących wartość null:
> [!div class="nextstepaction"]
> [Uaktualnianie aplikacji w celu użycia typów odwołań z dopuszczalną wartością null](upgrade-to-nullable-references.md)
