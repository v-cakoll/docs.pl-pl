---
title: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null
description: Ten zaawansowany samouczek zawiera wprowadzenie do typów referencyjnych dopuszczających wartość null. Dowiesz się, w jaki sposób projekt zostanie zastosowany, gdy wartości odniesienia mogą mieć wartość null, i że kompilator wymusi, gdy nie mogą mieć wartości null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 5327a9babdf080a535e292cdcefba6da9d0a725b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834070"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Samouczek: wyraźny cel projektowania dokładniej z typami referencyjnymi nullable i niedopuszczających wartości null

C#8 wprowadza **typy odwołań do wartości null**, które uzupełniają typy odwołań w taki sam sposób, jak typy wartości null uzupełniają typy wartości. Należy zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null** , dołączając `?` do typu. Na przykład `string?` reprezentuje wartość null `string`. Możesz użyć tych nowych typów, aby dokładniej wyznaczać intencje projektowania: niektóre zmienne *muszą zawsze mieć wartość*, inne *mogą nie mieć wartości*.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> - Uwzględnianie typów referencyjnych dopuszczających wartości null i niedopuszczających wartości null do Twoich projektów
> - Włącz kontrolę typu odwołania do wartości null w całym kodzie.
> - Napisz kod, w którym kompilator wymusza te decyzje projektowe.
> - Używanie funkcji referencyjnej nullable we własnych projektach

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0. Kompilator C# 8-Beta jest dostępny w programie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Dołączanie typów odwołań do wartości null do projektów

W tym samouczku utworzysz bibliotekę, w której będą wykonywane ankiety. Kod używa zarówno typów referencyjnych dopuszczających wartości null, jak i niedopuszczających wartości null typy odwołań do reprezentowania rzeczywistych koncepcji. Pytania dotyczące ankiety nigdy nie mogą mieć wartości null. Respondent może preferować nie odpowiedzieć na pytanie. W takim przypadku odpowiedzi mogą mieć wartość null.

Kod, który napiszesz dla tego przykładu, oznacza, że zamiar, a kompilator wymusza ten cel.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Tworzenie aplikacji i włączanie typów referencyjnych dopuszczających wartość null

Utwórz nową aplikację konsolową w programie Visual Studio lub z wiersza polecenia, używając `dotnet new console`. Nadaj aplikacji nazwę `NullableIntroduction`. Po utworzeniu aplikacji należy włączyć C# 8 funkcji w wersji beta. Otwórz plik `csproj` i Dodaj element `LangVersion` do elementu `PropertyGroup`. Należy wybrać funkcję **typów referencyjnych dopuszczających wartość null** , nawet C# w 8 projektach. Dzieje się tak, ponieważ po włączeniu tej funkcji istniejące deklaracje zmiennej odwołania stają się **typami odwołań niedopuszczających wartości null**. Chociaż ta decyzja pomoże w znalezieniu problemów, w których istniejący kod może nie mieć odpowiednich testów o wartości null, może nie dokładnie odzwierciedlać pierwotny cel projektowania. Aby włączyć tę funkcję, należy ustawić `Nullable` elementu na `enable`:

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Projektowanie typów aplikacji

Ta aplikacja do ankiety wymaga utworzenia szeregu klas:

- Klasa, która modeluje listę pytań.
- Klasa, która modeluje listę osób, którym kontaktowali się na potrzeby ankiety.
- Klasa, która modeluje odpowiedzi od osoby, która przeprowadziła ankietę.

Te typy będą używały typów referencyjnych dopuszczających wartości null i niedopuszczających wartości null do wyznaczania, które elementy członkowskie są wymagane i które są opcjonalne. Typy referencyjne dopuszczające wartość null komunikują się, że projekt zamierzenia

- Pytania, które są częścią ankiety, nie mogą mieć wartości null: nie ma sensu, aby zadać puste pytanie.
- Respondenci nie mogą być puste. Użytkownik chce śledzić osoby, którym nastąpi kontakt, nawet respondentów, którzy odrzucili uczestnictwo.
- Każda odpowiedź na pytanie może mieć wartość null. Respondenci mogą odrzucić niektóre lub wszystkie pytania.

Jeśli zaznaczono program w programie C#, można go przywołać do typów referencyjnych, które zezwalają na wartości null, które mogły pominąć inne możliwości deklarowania wystąpień niedopuszczających wartości null:

- Kolekcje pytań nie mogą dopuszczać wartości null.
- Kolekcja respondentów nie powinna być dopuszczana do wartości null.

Podczas pisania kodu zobaczysz, że typ referencyjny niedopuszczający wartości null jako domyślny dla odwołań pozwala uniknąć częstych błędów, które mogą prowadzić do wyjątków odwołania o wartości null. Jedną z lekcji w tym samouczku jest to, że podjęto decyzję o tym, które zmienne mogły lub nie mogą mieć wartości null. Język nie dostarczył składni do wyrażania tych decyzji. Teraz.

Aplikacja, którą utworzysz, wykona następujące czynności:

1. Utwórz ankietę i Dodaj do niej pytania.
1. Utwórz pseudo-losowy zbiór respondentów dla ankiety.
1. Skontaktuj się z respondentami do momentu, aż ukończony rozmiar ankiety osiągnie numer celu.
1. Zapisuj ważne dane statystyczne odpowiedzi na ankiety.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Kompilowanie ankiety przy użyciu typów dopuszczających wartości null i nie dopuszczających wartości null

Pierwszy kod, który napiszesz, tworzy ankietę. Należy napisać klasy do modelowania pytania ankietowego i uruchomienia ankiety. Ankieta zawiera trzy typy pytań, które różnią się formatem odpowiedzi: tak/nie odpowiedzi, odpowiedzi na liczbę i odpowiedzi tekstowe. Utwórz klasę `public` `SurveyQuestion`:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilator interpretuje każdą deklarację zmiennej typu odwołania jako typ referencyjny **niedopuszczający wartości null** dla kodu w kontekście, w którym włączono wartość null. Pierwsze ostrzeżenie można zobaczyć, dodając właściwości dla tekstu pytania i typ pytania, jak pokazano w poniższym kodzie:

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

Ponieważ nie zainicjowano `QuestionText`, kompilator generuje ostrzeżenie, że nie zainicjowano właściwości, która nie dopuszcza wartości null. Projekt wymaga, aby tekst pytania miał wartość różną od null, więc można dodać konstruktora, aby go zainicjować, i wartości `QuestionType`. Gotowa definicja klasy wygląda podobnie do następującego kodu:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Dodanie konstruktora spowoduje usunięcie ostrzeżenia. Argument konstruktora jest również typem referencyjnym, który nie dopuszcza wartości null, więc kompilator nie wystawia żadnych ostrzeżeń.

Następnie Utwórz klasę `public` o nazwie `SurveyRun`. Ta klasa zawiera listę obiektów i metod `SurveyQuestion` w celu dodania pytań do ankiety, jak pokazano w poniższym kodzie:

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

Tak jak wcześniej, należy zainicjować obiekt listy w wartości innej niż null lub kompilator generuje ostrzeżenie. W drugim przeciążeniu `AddQuestion` nie ma sprawdzania wartości null, ponieważ nie są one potrzebne: zadeklarowano, że zmienna nie dopuszcza wartości null. Wartość nie może być `null`.

Przełącz się do `Program.cs` w edytorze i Zastąp zawartość `Main` następującymi wierszami kodu:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Ponieważ cały projekt jest w kontekście, w którym włączono wartość null, podczas przekazywania `null` do dowolnej metody oczekiwano typu referencyjnego, który nie dopuszcza wartości null. Wypróbuj go, dodając następujący wiersz do `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Twórz respondenci i uzyskuj odpowiedzi na ankietę

Następnie napisz kod, który generuje odpowiedzi na ankietę. Ten proces obejmuje kilka małych zadań:

1. Kompiluj metodę generującą obiekty respondentów. Reprezentują one osoby, które poprosiły o wypełnienie ankiety.
1. Utwórz logikę, aby symulować pytania do respondenta i zbierać odpowiedzi lub zauważyć, że respondent nie odpowiedział.
1. Powtarzaj do momentu, aż wystarczające respondenci przepowieli ankietę.

Potrzebujesz klasy do reprezentowania odpowiedzi ankiety, więc Dodaj ją teraz. Włącz obsługę dopuszczania wartości null. Dodaj właściwość `Id` i konstruktora, która go inicjuje, jak pokazano w poniższym kodzie:

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

Następnie Dodaj metodę `static`, aby utworzyć nowych uczestników przez wygenerowanie losowego identyfikatora:

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Główną odpowiedzialnością tej klasy jest generowanie odpowiedzi dla uczestnika na pytania w ankiecie. Ta odpowiedzialność obejmuje kilka kroków:

1. Poproś o uczestnictwo w ankiecie. Jeśli osoba nie wyraża zgody, zwróć odpowiedź o brakującą wartość (lub null).
1. Zadawaj każde pytanie i zanotuj odpowiedź. Każda odpowiedź może być również brakująca (lub mieć wartość null).

Dodaj następujący kod do klasy `SurveyResponse`:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Magazyn dla odpowiedzi na ankiety to `Dictionary<int, string>?`, co oznacza, że może mieć wartość null. Używasz nowej funkcji języka do deklarowania zamiaru projektu, zarówno do kompilatora, jak i do każdego, kto czyta kod później. Jeśli kiedykolwiek utworzysz odwołanie `surveyResponses` bez uprzedniego sprawdzenia wartości null, otrzymasz ostrzeżenie kompilatora. Nie otrzymasz ostrzeżenia w metodzie `AnswerSurvey`, ponieważ kompilator może określić zmienną `surveyResponses` została ustawiona na wartość różną od null.

Użycie `null` w przypadku brakujących odpowiedzi podświetla kluczowy punkt do pracy z typami referencyjnymi nullable: nie można usunąć wszystkich wartości `null` z programu. Zamiast tego celem jest upewnienie się, że napisany kod wyraża zamiar Twojego projektu. Brakujące wartości są koniecznym pojęciem do wyrażania w kodzie. Wartość `null` to oczywisty sposób wyrażenia brakujących wartości. Próba usunięcia wszystkich wartości `null` prowadzi tylko do definiowania niektórych innych metod, aby wyrazić te brakujące wartości bez `null`.

Następnie należy napisać metodę `PerformSurvey` w klasie `SurveyRun`. Dodaj następujący kod do klasy `SurveyRun`:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

W tym miejscu możesz wybrać wartość null `List<SurveyResponse>?` wskazuje, że odpowiedź może mieć wartość null. Oznacza to, że ankieta nie została jeszcze udzielona żadnym respondentom. Zwróć uwagę, że respondenci są dodawani, dopóki nie zostanie osiągnięta wystarczająca liczba.

Ostatnim krokiem do uruchomienia ankiety jest dodanie wywołania do wykonania ankiety na końcu metody `Main`:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Zbadaj odpowiedzi na ankietę

Ostatnim krokiem jest wyświetlenie wyników ankiety. Dodasz kod do wielu utworzonych klas. Ten kod demonstruje wartość odróżniania typów referencyjnych dopuszczających wartości null i niedopuszczających wartości null. Zacznij od dodania następujących dwóch składowych wyrażeń do klasy `SurveyResponse`:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Ponieważ `surveyResponses` to typ referencyjny dopuszczający wartości null są wymagane przed cofnięciem odwołania. Metoda `Answer` zwraca ciąg niedopuszczający wartości null, dlatego musimy uwzględnić przypadek brakującej odpowiedzi przy użyciu operatora łączenia wartości null.

Następnie Dodaj te trzy składowe z wyrażeniami do klasy `SurveyRun`:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Członek `AllParticipants` musi wziąć pod uwagę, że zmienna `respondents` może mieć wartość null, ale zwracana wartość nie może być równa null. Jeśli zmienisz to wyrażenie, usuwając `??` i pustą sekwencję, która następuje, kompilator ostrzega o tym, że metoda może zwrócić `null`, a jej sygnatura zwrotna zwraca typ, który nie dopuszcza wartości null.

Na koniec Dodaj następującą pętlę w dolnej części metody `Main`:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Nie jest potrzebne żadne `null` checks w tym kodzie, ponieważ zostały zaprojektowane podstawowe interfejsy, aby wszystkie zwracały typy odwołań niedopuszczające wartości null.

## <a name="get-the-code"></a>Pobierz kod

Możesz uzyskać kod gotowego samouczka z naszego repozytorium [przykładów](https://github.com/dotnet/samples) w folderze [CSharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) .

Eksperymentowanie, zmieniając deklaracje typu między typami odwołań dopuszczających wartości null i niedopuszczające wartości null. Zobacz, jak generuje różne ostrzeżenia, aby zapobiec przypadkowemu wykorzystaniu `null`.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej przez Migrowanie istniejącej aplikacji w celu używania typów referencyjnych dopuszczających wartości null:
> [!div class="nextstepaction"]
> [Uaktualnianie aplikacji w celu używania typów referencyjnych dopuszczających wartości null](upgrade-to-nullable-references.md)
