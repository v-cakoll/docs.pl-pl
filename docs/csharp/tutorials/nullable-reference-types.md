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
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="49b32-104">Samouczek: Wyraź swój zamiar projektu jaśniej z nullable i non-null typów odwołań</span><span class="sxs-lookup"><span data-stu-id="49b32-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="49b32-105">C# 8.0 wprowadza [nullable typy odwołań](../nullable-references.md), które uzupełniają typy odwołań w taki sam sposób typy wartości nullable uzupełnienia typów wartości.</span><span class="sxs-lookup"><span data-stu-id="49b32-105">C# 8.0 introduces [nullable reference types](../nullable-references.md), which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="49b32-106">Deklarujesz zmienną jako **typ odwołania powodujący wartość null,** dołączając go `?` do typu.</span><span class="sxs-lookup"><span data-stu-id="49b32-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="49b32-107">Na przykład `string?` reprezentuje nullable `string`.</span><span class="sxs-lookup"><span data-stu-id="49b32-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="49b32-108">Można użyć tych nowych typów, aby wyraźniej wyrazić swoje intencje projektowe: niektóre zmienne *muszą zawsze mieć wartość,* inne *mogą brakować wartości.*</span><span class="sxs-lookup"><span data-stu-id="49b32-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="49b32-109">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="49b32-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="49b32-110">Uwzględnianie do swoich projektów typów odwołań, których nie można unieważnić i nie można ich unieważnić</span><span class="sxs-lookup"><span data-stu-id="49b32-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="49b32-111">Włącz sprawdzanie typu odwołania z nullable w całym kodzie.</span><span class="sxs-lookup"><span data-stu-id="49b32-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="49b32-112">Napisz kod, w którym kompilator wymusza te decyzje projektowe.</span><span class="sxs-lookup"><span data-stu-id="49b32-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="49b32-113">Użyj funkcji odniesienia, której można anulować we własnych projektach</span><span class="sxs-lookup"><span data-stu-id="49b32-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49b32-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="49b32-114">Prerequisites</span></span>

<span data-ttu-id="49b32-115">Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilatora C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="49b32-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="49b32-116">Kompilator języka C# 8.0 jest dostępny w [programie Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="49b32-116">The C# 8.0 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="49b32-117">W tym samouczku założono, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="49b32-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="49b32-118">Uwzględnianie typów odwołań, których można anulować, do wzorów</span><span class="sxs-lookup"><span data-stu-id="49b32-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="49b32-119">W tym samouczku utworzysz bibliotekę, która modeluje z udziałem ankiety.</span><span class="sxs-lookup"><span data-stu-id="49b32-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="49b32-120">Kod używa zarówno nullable typów odwołań i typów odwołań nie nullable do reprezentowania rzeczywistych pojęć.</span><span class="sxs-lookup"><span data-stu-id="49b32-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="49b32-121">Pytania ankietowe nigdy nie mogą być zerowe.</span><span class="sxs-lookup"><span data-stu-id="49b32-121">The survey questions can never be null.</span></span> <span data-ttu-id="49b32-122">Respondent może nie odpowiadać na pytanie.</span><span class="sxs-lookup"><span data-stu-id="49b32-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="49b32-123">Odpowiedzi mogą być `null` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="49b32-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="49b32-124">Kod, który napiszesz dla tego przykładu wyraża tę intencję, a kompilator wymusza tę intencję.</span><span class="sxs-lookup"><span data-stu-id="49b32-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="49b32-125">Tworzenie aplikacji i włączanie typów odwołań z dopuszczalną wartością null</span><span class="sxs-lookup"><span data-stu-id="49b32-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="49b32-126">Utwórz nową aplikację konsoli w programie Visual Studio `dotnet new console`lub z wiersza polecenia za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="49b32-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="49b32-127">Nazwij `NullableIntroduction`aplikację .</span><span class="sxs-lookup"><span data-stu-id="49b32-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="49b32-128">Po utworzeniu aplikacji należy określić, że cały projekt kompiluje się w włączonym **kontekście adnotacji z możliwością null.**</span><span class="sxs-lookup"><span data-stu-id="49b32-128">Once you've created the application, you'll need to specify that the entire project compiles in an enabled **nullable annotation context**.</span></span> <span data-ttu-id="49b32-129">Otwórz plik *csproj* i `Nullable` dodaj element `PropertyGroup` do elementu.</span><span class="sxs-lookup"><span data-stu-id="49b32-129">Open the *.csproj* file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="49b32-130">Ustaw dla niej wartość `enable`.</span><span class="sxs-lookup"><span data-stu-id="49b32-130">Set its value to `enable`.</span></span> <span data-ttu-id="49b32-131">Należy wybrać funkcję **typów odwołań, których można anulować,** nawet w projektach języka C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="49b32-131">You must opt into the **nullable reference types** feature, even in C# 8.0 projects.</span></span> <span data-ttu-id="49b32-132">Dzieje się tak dlatego, że po włączeniu funkcji istniejące deklaracje zmiennych referencyjnych stają się **typami odwołań niepodważalnych.**</span><span class="sxs-lookup"><span data-stu-id="49b32-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="49b32-133">Chociaż ta decyzja pomoże znaleźć problemy, w których istniejący kod może nie mieć odpowiednich kontroli zerowych, może nie odzwierciedlać dokładnie oryginalnego zamiaru projektu:</span><span class="sxs-lookup"><span data-stu-id="49b32-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="49b32-134">Projektowanie typów dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="49b32-134">Design the types for the application</span></span>

<span data-ttu-id="49b32-135">Ta aplikacja ankietowa wymaga utworzenia wielu klas:</span><span class="sxs-lookup"><span data-stu-id="49b32-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="49b32-136">Klasa, która modeluje listę pytań.</span><span class="sxs-lookup"><span data-stu-id="49b32-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="49b32-137">Klasa, która modeluje listę osób, z którymi skontaktowano się w celu wykonania ankiety.</span><span class="sxs-lookup"><span data-stu-id="49b32-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="49b32-138">Klasa, która modeluje odpowiedzi od osoby, która wzięła udział w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="49b32-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="49b32-139">Te typy będą korzystać z typów odwołań nullable i nie nullable wyrazić, które elementy członkowskie są wymagane, a które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="49b32-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="49b32-140">Typy odwołań dopuszczania do wartości null komunikują intencję projektu wyraźnie:</span><span class="sxs-lookup"><span data-stu-id="49b32-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="49b32-141">Pytania, które są częścią badania nigdy nie może być null: Nie ma sensu zadać puste pytanie.</span><span class="sxs-lookup"><span data-stu-id="49b32-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="49b32-142">Respondenci nigdy nie mogą być zerowi.</span><span class="sxs-lookup"><span data-stu-id="49b32-142">The respondents can never be null.</span></span> <span data-ttu-id="49b32-143">Będziesz chciał śledzić osoby, z którymi się skontaktowałeś, a nawet respondentów, którzy odmówili udziału.</span><span class="sxs-lookup"><span data-stu-id="49b32-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="49b32-144">Każda odpowiedź na pytanie może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="49b32-144">Any response to a question may be null.</span></span> <span data-ttu-id="49b32-145">Respondenci mogą odmówić odpowiedzi na niektóre lub wszystkie pytania.</span><span class="sxs-lookup"><span data-stu-id="49b32-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="49b32-146">Jeśli masz zaprogramowane w języku C#, może być tak `null` przyzwyczajony do typów odwołań, które pozwalają na wartości, które mogą mieć pominięte inne możliwości deklarowania wystąpienia nienastępne do null:</span><span class="sxs-lookup"><span data-stu-id="49b32-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="49b32-147">Zbieranie pytań powinno być nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="49b32-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="49b32-148">Zbieranie respondentów powinno być niedościwidalne.</span><span class="sxs-lookup"><span data-stu-id="49b32-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="49b32-149">Podczas pisania kodu zobaczysz, że typ odwołania nienależytego do wartości null jako domyślny <xref:System.NullReferenceException>dla odwołań pozwala uniknąć typowych błędów, które mogą prowadzić do s.</span><span class="sxs-lookup"><span data-stu-id="49b32-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="49b32-150">Jedną z lekcji z tego samouczka jest to, że `null`podjąłeś decyzje o tym, które zmienne mogą lub nie mogą być .</span><span class="sxs-lookup"><span data-stu-id="49b32-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="49b32-151">Język nie podał składni, aby wyrazić te decyzje.</span><span class="sxs-lookup"><span data-stu-id="49b32-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="49b32-152">Teraz tak.</span><span class="sxs-lookup"><span data-stu-id="49b32-152">Now it does.</span></span>

<span data-ttu-id="49b32-153">Aplikacja, którą skompilujesz, wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="49b32-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="49b32-154">Tworzy ankietę i dodaje do niej pytania.</span><span class="sxs-lookup"><span data-stu-id="49b32-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="49b32-155">Tworzy pseudolosowy zestaw respondentów do badania.</span><span class="sxs-lookup"><span data-stu-id="49b32-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="49b32-156">Kontaktuje się z respondentami, dopóki wypełniony rozmiar ankiety nie osiągnie numeru celu.</span><span class="sxs-lookup"><span data-stu-id="49b32-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="49b32-157">Zapisuje ważne statystyki dotyczące odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="49b32-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="49b32-158">Tworzenie ankiety z typami odwołań z których można anulować i nienastępującym do wartości null</span><span class="sxs-lookup"><span data-stu-id="49b32-158">Build the survey with nullable and non-nullable reference types</span></span>

<span data-ttu-id="49b32-159">Pierwszy kod, który napiszesz, tworzy ankietę.</span><span class="sxs-lookup"><span data-stu-id="49b32-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="49b32-160">Będziesz pisać klasy do modelowania pytania ankiety i badania.</span><span class="sxs-lookup"><span data-stu-id="49b32-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="49b32-161">Ankieta zawiera trzy rodzaje pytań, wyróżniające się formatem odpowiedzi: Tak/Nie odpowiedzi, odpowiedzi liczbowe i odpowiedzi tekstowe.</span><span class="sxs-lookup"><span data-stu-id="49b32-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="49b32-162">Tworzenie `public SurveyQuestion` klasy:</span><span class="sxs-lookup"><span data-stu-id="49b32-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="49b32-163">Kompilator interpretuje każdą deklarację zmiennej typu odwołania jako typ odwołania **niepodważalny** dla kodu w włączonym kontekście adnotacji z możliwością null.</span><span class="sxs-lookup"><span data-stu-id="49b32-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in an enabled nullable annotation context.</span></span> <span data-ttu-id="49b32-164">Pierwsze ostrzeżenie można wyświetlić, dodając właściwości tekstu pytania i typu pytania, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="49b32-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="49b32-165">Ponieważ nie zostały zainicjowane, `QuestionText`kompilator generuje ostrzeżenie, że właściwość nie można anulować nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="49b32-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="49b32-166">Projekt wymaga, aby tekst pytania był nietrwały, więc należy dodać `QuestionType` konstruktora, aby zainicjować go i wartość, jak również.</span><span class="sxs-lookup"><span data-stu-id="49b32-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="49b32-167">Definicja gotowej klasy wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="49b32-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="49b32-168">Dodanie konstruktora usuwa ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="49b32-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="49b32-169">Argument konstruktora jest również typem odwołania, którego nie można unieważnić, więc kompilator nie wydaje żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="49b32-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="49b32-170">Następnie utwórz `public` klasę `SurveyRun`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="49b32-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="49b32-171">Ta klasa zawiera `SurveyQuestion` listę obiektów i metod dodawania pytań do ankiety, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="49b32-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="49b32-172">Tak jak poprzednio, należy zainicjować obiekt listy do wartości innej niż null lub kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="49b32-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="49b32-173">Nie ma żadnych kontroli null w `AddQuestion` drugim przeciążenie, ponieważ nie są one potrzebne: Zadeklarowałeś, że zmienna jest nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="49b32-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="49b32-174">Jego wartość nie `null`może być .</span><span class="sxs-lookup"><span data-stu-id="49b32-174">Its value can't be `null`.</span></span>

<span data-ttu-id="49b32-175">Przełącz się na *Program.cs* w edytorze `Main` i zastąp zawartość następujących wierszy kodu:</span><span class="sxs-lookup"><span data-stu-id="49b32-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="49b32-176">Ponieważ cały projekt znajduje się w włączonym kontekście adnotacji z `null` możliwością null, otrzymasz ostrzeżenia po przejściu do dowolnej metody oczekującej typu odwołania, którego nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="49b32-176">Because the entire project is in an enabled nullable annotation context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="49b32-177">Spróbuj, dodając następujący wiersz `Main`do:</span><span class="sxs-lookup"><span data-stu-id="49b32-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="49b32-178">Tworzenie respondentów i uzyskiwanie odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="49b32-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="49b32-179">Następnie napisz kod, który generuje odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="49b32-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="49b32-180">Proces ten obejmuje kilka małych zadań:</span><span class="sxs-lookup"><span data-stu-id="49b32-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="49b32-181">Tworzenie metody, która generuje respondenta obiektów.</span><span class="sxs-lookup"><span data-stu-id="49b32-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="49b32-182">Reprezentują one osoby proszone o wypełnienie ankiety.</span><span class="sxs-lookup"><span data-stu-id="49b32-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="49b32-183">Tworzenie logiki do symulowania zadawania pytań do respondenta i zbierania odpowiedzi lub zauważyć, że respondent nie odpowiedział.</span><span class="sxs-lookup"><span data-stu-id="49b32-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="49b32-184">Powtarzaj, aż wystarczająca liczba respondentów odpowie na ankietę.</span><span class="sxs-lookup"><span data-stu-id="49b32-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="49b32-185">Będziesz potrzebować klasy do reprezentowania odpowiedzi na ankietę, więc dodaj ją teraz.</span><span class="sxs-lookup"><span data-stu-id="49b32-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="49b32-186">Włącz obsługę można anulować.</span><span class="sxs-lookup"><span data-stu-id="49b32-186">Enable nullable support.</span></span> <span data-ttu-id="49b32-187">Dodaj `Id` właściwość i konstruktora, który inicjuje go, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="49b32-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="49b32-188">Następnie dodaj `static` metodę tworzenia nowych uczestników, generując losowy identyfikator:</span><span class="sxs-lookup"><span data-stu-id="49b32-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="49b32-189">Głównym obowiązkiem tej klasy jest generowanie odpowiedzi dla uczestnika na pytania w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="49b32-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="49b32-190">Odpowiedzialność ta ma kilka kroków:</span><span class="sxs-lookup"><span data-stu-id="49b32-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="49b32-191">Poproś o udział w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="49b32-191">Ask for participation in the survey.</span></span> <span data-ttu-id="49b32-192">Jeśli dana osoba nie wyrazi zgody, zwróć brakującą (lub null) odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="49b32-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="49b32-193">Zadaj każde pytanie i zapisz odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="49b32-193">Ask each question and record the answer.</span></span> <span data-ttu-id="49b32-194">Każda odpowiedź może również brakować (lub null).</span><span class="sxs-lookup"><span data-stu-id="49b32-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="49b32-195">Dodaj następujący kod `SurveyResponse` do swojej klasy:</span><span class="sxs-lookup"><span data-stu-id="49b32-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="49b32-196">Magazyn odpowiedzi na ankietę `Dictionary<int, string>?`jest , wskazując, że może być null.</span><span class="sxs-lookup"><span data-stu-id="49b32-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="49b32-197">Używasz nowej funkcji języka, aby zadeklarować intencji projektu, zarówno do kompilatora i dla każdego, kto czyta kod później.</span><span class="sxs-lookup"><span data-stu-id="49b32-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="49b32-198">Jeśli kiedykolwiek wyłuskania `surveyResponses` bez `null` sprawdzania wartości po raz pierwszy, otrzymasz ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="49b32-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="49b32-199">Nie otrzymasz ostrzeżenia w `AnswerSurvey` metodzie, ponieważ kompilator może `surveyResponses` określić, że zmienna została ustawiona na wartość nie null powyżej.</span><span class="sxs-lookup"><span data-stu-id="49b32-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="49b32-200">Używanie `null` brakujących odpowiedzi wyróżnia kluczowy punkt do pracy z typami odwołań, `null` których można anulować: celem nie jest usunięcie wszystkich wartości z programu.</span><span class="sxs-lookup"><span data-stu-id="49b32-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="49b32-201">Zamiast tego Twoim celem jest zapewnienie, że kod, który piszesz wyraża intencję projektu.</span><span class="sxs-lookup"><span data-stu-id="49b32-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="49b32-202">Brakujące wartości są niezbędne pojęcie do wyrażenia w kodzie.</span><span class="sxs-lookup"><span data-stu-id="49b32-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="49b32-203">Wartość `null` jest jasnym sposobem wyrażania tych brakujących wartości.</span><span class="sxs-lookup"><span data-stu-id="49b32-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="49b32-204">Próba usunięcia `null` wszystkich wartości prowadzi tylko do zdefiniowania innego `null`sposobu wyrażania brakujących wartości bez .</span><span class="sxs-lookup"><span data-stu-id="49b32-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="49b32-205">Następnie należy napisać `PerformSurvey` metodę w `SurveyRun` klasie.</span><span class="sxs-lookup"><span data-stu-id="49b32-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="49b32-206">Dodaj następujący kod `SurveyRun` w klasie:</span><span class="sxs-lookup"><span data-stu-id="49b32-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="49b32-207">W tym miejscu ponownie, `List<SurveyResponse>?` wybór nullable wskazuje odpowiedź może być null.</span><span class="sxs-lookup"><span data-stu-id="49b32-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="49b32-208">Oznacza to, że ankieta nie została jeszcze przekazana żadnym respondentom.</span><span class="sxs-lookup"><span data-stu-id="49b32-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="49b32-209">Należy zauważyć, że respondenci są dodawane, dopóki nie wystarczająco wyrazisz na to zgodę.</span><span class="sxs-lookup"><span data-stu-id="49b32-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="49b32-210">Ostatnim krokiem do uruchomienia ankiety jest dodanie połączenia w celu `Main` przeprowadzenia ankiety na końcu metody:</span><span class="sxs-lookup"><span data-stu-id="49b32-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="49b32-211">Sprawdzanie odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="49b32-211">Examine survey responses</span></span>

<span data-ttu-id="49b32-212">Ostatnim krokiem jest wyświetlenie wyników ankiety.</span><span class="sxs-lookup"><span data-stu-id="49b32-212">The last step is to display survey results.</span></span> <span data-ttu-id="49b32-213">Dodasz kod do wielu napisanych klas.</span><span class="sxs-lookup"><span data-stu-id="49b32-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="49b32-214">Ten kod pokazuje wartość rozróżniania typów odwołań nullable i non-nullable.</span><span class="sxs-lookup"><span data-stu-id="49b32-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="49b32-215">Zacznij od dodania następujących dwóch członków zabudowanych wyrażeniami `SurveyResponse` do klasy:</span><span class="sxs-lookup"><span data-stu-id="49b32-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="49b32-216">Ponieważ `surveyResponses` jest typu odwołania nullable, null kontroli są niezbędne przed odsyłanie go.</span><span class="sxs-lookup"><span data-stu-id="49b32-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="49b32-217">Metoda `Answer` zwraca ciąg nienastępujący do wartości null, więc musimy omówić przypadek brakującej odpowiedzi przy użyciu operatora scalania wartości null.</span><span class="sxs-lookup"><span data-stu-id="49b32-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="49b32-218">Następnie dodaj te trzy elementy członkowskie zabudowane wyrażeniami `SurveyRun` do klasy:</span><span class="sxs-lookup"><span data-stu-id="49b32-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="49b32-219">Element `AllParticipants` członkowski musi wziąć `respondents` pod uwagę, że zmienna może mieć wartość null, ale wartość zwracana nie może być null.</span><span class="sxs-lookup"><span data-stu-id="49b32-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="49b32-220">Jeśli zmienisz to wyrażenie, `??` usuwając i puste sekwencji, która następuje, kompilator ostrzega, że metoda może powrócić `null` i jego podpis zwraca typ nie nullable.</span><span class="sxs-lookup"><span data-stu-id="49b32-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="49b32-221">Na koniec dodaj następującą pętlę `Main` u dołu metody:</span><span class="sxs-lookup"><span data-stu-id="49b32-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="49b32-222">Nie trzeba żadnych `null` kontroli w tym kodzie, ponieważ zostały zaprojektowane interfejsów bazowych, tak aby wszystkie one zwracają typy odwołania bez null.</span><span class="sxs-lookup"><span data-stu-id="49b32-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="49b32-223">Uzyskiwanie kodu</span><span class="sxs-lookup"><span data-stu-id="49b32-223">Get the code</span></span>

<span data-ttu-id="49b32-224">Możesz pobrać kod gotowego samouczka z naszego repozytorium [próbek](https://github.com/dotnet/samples) w folderze [csharp/NullIntroduction.](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction)</span><span class="sxs-lookup"><span data-stu-id="49b32-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="49b32-225">Eksperymentuj, zmieniając deklaracje typów między typami odwołań, których można anulować i nie można anulować.</span><span class="sxs-lookup"><span data-stu-id="49b32-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="49b32-226">Zobacz, jak to generuje różne ostrzeżenia, aby upewnić `null`się, że nie przypadkowo wyłuskać .</span><span class="sxs-lookup"><span data-stu-id="49b32-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="49b32-227">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="49b32-227">Next steps</span></span>

<span data-ttu-id="49b32-228">Dowiedz się więcej, migrując istniejącą aplikację w celu użycia typów odwołań powodujących wartość null:</span><span class="sxs-lookup"><span data-stu-id="49b32-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="49b32-229">Uaktualnianie aplikacji w celu użycia typów odwołań z dopuszczalną wartością null</span><span class="sxs-lookup"><span data-stu-id="49b32-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
