---
title: Projektowanie w przypadku typów referencyjnych dopuszczającego wartość null
description: W tym samouczku zaawansowane zawiera wprowadzenie do typów referencyjnych dopuszczającego wartość null. Dowiesz się, że express projektu chcący po wartości odniesienia może mieć wartości null i pozwolić kompilatorowi wymusić, gdy nie może mieć wartości null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 1c0df9b129e9c434eb3b5e6e50144013c2c0462e
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442103"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="e8fde-104">Samouczek: Wyraźniej Express zgodną z planem projektu w przypadku typów referencyjnych dopuszcza wartości null i nie dopuszcza wartości null</span><span class="sxs-lookup"><span data-stu-id="e8fde-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="e8fde-105">C#8 wprowadzono **typy dopuszczające wartości null odwołań**, które odwołania uzupełnieniem typów taki sam sposób, typy o wartości zerowalnej uzupełniają typów wartości.</span><span class="sxs-lookup"><span data-stu-id="e8fde-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="e8fde-106">Zadeklaruj zmienną **typu dopuszczającego wartość null odwołania** , dodając `?` do typu.</span><span class="sxs-lookup"><span data-stu-id="e8fde-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="e8fde-107">Na przykład `string?` reprezentuje dopuszczający wartości null `string`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="e8fde-108">Te nowe typy można użyć, aby wyraźniej express zgodną z planem projektu: niektóre zmienne *zawsze musi mieć wartość*, inne *może brakować wartość*.</span><span class="sxs-lookup"><span data-stu-id="e8fde-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="e8fde-109">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="e8fde-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="e8fde-110">Włączenie typy dopuszczające wartości null i dopuszcza odwołań do projektów</span><span class="sxs-lookup"><span data-stu-id="e8fde-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="e8fde-111">Włącz sprawdzanie typu dopuszczającego wartość null odwołanie w całym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8fde-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="e8fde-112">Napisz kod, w których kompilator wymusza tych decyzji projektowych.</span><span class="sxs-lookup"><span data-stu-id="e8fde-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="e8fde-113">Funkcja odwołanie dopuszczającego wartość null w własnych projektów</span><span class="sxs-lookup"><span data-stu-id="e8fde-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8fde-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e8fde-114">Prerequisites</span></span>

<span data-ttu-id="e8fde-115">Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 beta.</span><span class="sxs-lookup"><span data-stu-id="e8fde-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="e8fde-116">C# 8 kompilatora w wersji beta jest dostępna z [2019 usługi Visual Studio w wersji zapoznawczej 2](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), lub [.NET Core 3.0 w wersji zapoznawczej 2](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="e8fde-116">The C# 8 beta compiler is available with [Visual Studio 2019 preview 2](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), or [.NET Core 3.0 preview 2](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="e8fde-117">W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8fde-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="e8fde-118">Włączenie typy dopuszczające wartości null odwołań do projektów</span><span class="sxs-lookup"><span data-stu-id="e8fde-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="e8fde-119">W tym samouczku utworzysz biblioteki, który modeluje systemem ankiety.</span><span class="sxs-lookup"><span data-stu-id="e8fde-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="e8fde-120">Kod używa typy dopuszczające wartości null odwołań i typy referencyjne nie dopuszcza wartości null w celu przedstawienia koncepcji rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="e8fde-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="e8fde-121">Pytania ankiety nigdy nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-121">The survey questions can never be null.</span></span> <span data-ttu-id="e8fde-122">Respondenta może nie chce uzyskać odpowiedzi na pytanie.</span><span class="sxs-lookup"><span data-stu-id="e8fde-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="e8fde-123">W takim przypadku może mieć wartości null odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e8fde-123">The responses might be null in this case.</span></span>

<span data-ttu-id="e8fde-124">Kod, który Ty napiszesz omawiany w tym przykładzie wyrażenie wskaźnika tym przeznaczeniem, a kompilator wymusza tym przeznaczeniem.</span><span class="sxs-lookup"><span data-stu-id="e8fde-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="e8fde-125">Tworzenie aplikacji i włączanie typów referencyjnych dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="e8fde-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="e8fde-126">Utwórz nową aplikację konsoli w programie Visual Studio lub z wiersza polecenia przy użyciu `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="e8fde-127">Nazwij aplikację `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="e8fde-128">Po utworzeniu aplikacji, musisz włączyć C# 8 funkcje w wersji beta.</span><span class="sxs-lookup"><span data-stu-id="e8fde-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="e8fde-129">Otwórz `csproj` pliku i Dodaj `LangVersion` elementu `PropertyGroup` elementu.</span><span class="sxs-lookup"><span data-stu-id="e8fde-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="e8fde-130">Użytkownik musi wyrazić zgodę **typy dopuszczające wartości null odwołań** funkcji, nawet w C# 8 projektów.</span><span class="sxs-lookup"><span data-stu-id="e8fde-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="e8fde-131">To dlatego po włączeniu funkcji istniejące deklaracje zmiennych odwołania stają się, że **typów referencyjnych dopuszcza**.</span><span class="sxs-lookup"><span data-stu-id="e8fde-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="e8fde-132">Podczas tej decyzji pomogą znaleźć problemy, gdy istniejący kod może nie mieć odpowiednich sprawdzanie wartości null, jego mogą nie odzwierciedla precyzyjnie zgodne z zamiarami użytkownika oryginalnego projektu.</span><span class="sxs-lookup"><span data-stu-id="e8fde-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="e8fde-133">Możesz włączyć tę funkcję, ustawiając `NullableContextOptions` elementu `enable`:</span><span class="sxs-lookup"><span data-stu-id="e8fde-133">You turn on the feature by setting the `NullableContextOptions` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<NullableContextOptions>enable</NullableContextOptions>
```

> [!NOTE]
> <span data-ttu-id="e8fde-134">Gdy C# wydaniu 8 (nie w wersji zapoznawczej), `NullableContextOptions` element zostanie dodany przez nowe szablony projektów.</span><span class="sxs-lookup"><span data-stu-id="e8fde-134">When C# 8 is released (not in preview mode), the `NullableContextOptions` element will be added by new project templates.</span></span> <span data-ttu-id="e8fde-135">Do tego czasu należy dodać ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="e8fde-135">Until then, you'll need to add it manually.</span></span>


### <a name="design-the-types-for-the-application"></a><span data-ttu-id="e8fde-136">Projektowanie typów dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="e8fde-136">Design the types for the application</span></span>

<span data-ttu-id="e8fde-137">Ta aplikacja ankiety wymaga, tworząc liczby klas:</span><span class="sxs-lookup"><span data-stu-id="e8fde-137">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="e8fde-138">Klasa, która modele listę pytań.</span><span class="sxs-lookup"><span data-stu-id="e8fde-138">A class that models the list of questions.</span></span>
- <span data-ttu-id="e8fde-139">Klasa, która modele listę osób skontaktować się z ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-139">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="e8fde-140">Klasa, która modele odpowiedzi od osoby, która trwała ankiety.</span><span class="sxs-lookup"><span data-stu-id="e8fde-140">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="e8fde-141">Te typy spowoduje, że wykorzystanie zarówno dopuszczającego wartość null i typy nieprzyjmujące wartości odwołań do wyrażania elementów członkowskich, które są wymagane i elementów członkowskich, które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e8fde-141">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="e8fde-142">Typy dopuszczające wartości null odwołanie do komunikacji, wyraźnie projektowania przeznaczenie:</span><span class="sxs-lookup"><span data-stu-id="e8fde-142">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="e8fde-143">Pytania, na które są dostępne w ramach przeglądu nigdy nie może mieć wartość null: Nie ma sensu zadać pytanie puste.</span><span class="sxs-lookup"><span data-stu-id="e8fde-143">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="e8fde-144">Respondentów nigdy nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-144">The respondents can never be null.</span></span> <span data-ttu-id="e8fde-145">Należy śledzić osób z Tobą, nawet respondentów, które odrzucone do udziału.</span><span class="sxs-lookup"><span data-stu-id="e8fde-145">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="e8fde-146">Każda odpowiedź na pytanie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-146">Any response to a question may be null.</span></span> <span data-ttu-id="e8fde-147">Respondentów można odrzucić odpowiedzi na niektóre lub wszystkie pytania.</span><span class="sxs-lookup"><span data-stu-id="e8fde-147">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="e8fde-148">Jeśli został zaprogramowany w C#, można więc przyzwyczajeni do odwołania typów, które akceptuje wartości null, które mogły zostać pominięte innymi możliwościami do deklarowania dopuszcza wystąpień:</span><span class="sxs-lookup"><span data-stu-id="e8fde-148">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="e8fde-149">Kolekcji pytań, powinna być wartość null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-149">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="e8fde-150">Kolekcja respondentów powinna być wartość null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-150">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="e8fde-151">Podczas pisania kodu, zobaczysz, że typ odwołania nie dopuszcza wartości null jako domyślne dla odwołania pozwala uniknąć typowych pomyłek, które mogą prowadzić do wyjątków odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-151">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="e8fde-152">Lekcja jeden z tego samouczka jest podjęliśmy decyzje, o których zmiennych może lub nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-152">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="e8fde-153">Język nie dostarczył składni wyrażenia te decyzje.</span><span class="sxs-lookup"><span data-stu-id="e8fde-153">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="e8fde-154">Teraz robi.</span><span class="sxs-lookup"><span data-stu-id="e8fde-154">Now it does.</span></span>

<span data-ttu-id="e8fde-155">Aplikację, którą utworzysz będzie wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e8fde-155">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="e8fde-156">Tworzą ankietę i dodać pytania do niego.</span><span class="sxs-lookup"><span data-stu-id="e8fde-156">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="e8fde-157">Utwórz zestaw pseudolosową respondentów ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-157">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="e8fde-158">Skontaktuj się z respondentów, dopóki numer celem osiągnie rozmiar przeprowadzone badania.</span><span class="sxs-lookup"><span data-stu-id="e8fde-158">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="e8fde-159">Zapisać ważnych statystyk w odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-159">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="e8fde-160">Tworzenie przeglądu z typu dopuszczającego wartość null i nie dopuszcza wartości null</span><span class="sxs-lookup"><span data-stu-id="e8fde-160">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="e8fde-161">Pierwszy kod, który Ty napiszesz tworzy ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-161">The first code you'll write creates the survey.</span></span> <span data-ttu-id="e8fde-162">Przedstawiono tworzenie klas modelu pytania ankiety i ankiety, uruchom.</span><span class="sxs-lookup"><span data-stu-id="e8fde-162">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="e8fde-163">Ankiety ma trzy rodzaje pytań związanych z rozróżnianych na podstawie formatu odpowiedzi: Tak/nie odbierze odpowiedzi numer i tekst odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e8fde-163">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="e8fde-164">Tworzenie `public` `SurveyQuestion` klasy:</span><span class="sxs-lookup"><span data-stu-id="e8fde-164">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="e8fde-165">Kompilator interpretuje co deklaracji zmiennych typu odwołania jako **dopuszcza** odwołania do typu dla kodu w kontekście włączone dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-165">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="e8fde-166">Można wyświetlić swoje pierwsze ostrzeżenie przez dodanie właściwości tekst pytania i rodzaju pytania, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e8fde-166">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="e8fde-167">Ponieważ jeszcze nie zainicjowany `QuestionText`, kompilator generuje ostrzeżenie właściwości niedopuszczającej nie zostało zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="e8fde-167">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="e8fde-168">Projekt wymaga tekst pytania, aby mieć wartości null, więc dodać konstruktora, aby go zainicjować i `QuestionType` również wartość.</span><span class="sxs-lookup"><span data-stu-id="e8fde-168">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="e8fde-169">Definicja klasy Zakończono wygląda podobnie do poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="e8fde-169">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="e8fde-170">Dodanie konstruktora powoduje usunięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="e8fde-170">Adding the constructor removes the warning.</span></span> <span data-ttu-id="e8fde-171">Argument konstruktora jest również typem referencyjnym dopuszcza kompilator nie generuje żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="e8fde-171">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="e8fde-172">Następnie należy utworzyć `public` klasę o nazwie `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-172">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="e8fde-173">Ta klasa zawiera listę `SurveyQuestion` obiektów i metod, aby dodać pytania ankiety, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e8fde-173">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="e8fde-174">Tak jak poprzednio należy zainicjować obiekt listy, do wartości innej niż null lub kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="e8fde-174">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="e8fde-175">Nie ma żadnych sprawdzanie wartości null w drugie przeciążenie `AddQuestion` , ponieważ nie są one potrzebne: Został zadeklarowany tej zmiennej jako wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-175">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="e8fde-176">Jego wartość nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-176">Its value can't be `null`.</span></span>

<span data-ttu-id="e8fde-177">Przełącz się do `Program.cs` w edytorze i Zastąp zawartość `Main` z następującymi wierszami kodu:</span><span class="sxs-lookup"><span data-stu-id="e8fde-177">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="e8fde-178">Ponieważ cały projekt jest w kontekście włączone dopuszczającego wartość null, otrzymasz ostrzeżenia, jeśli przekazujesz `null` do dowolnej metody, oczekiwano typu odwołania nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-178">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="e8fde-179">Wypróbuj je, dodając następujący wiersz do `Main`:</span><span class="sxs-lookup"><span data-stu-id="e8fde-179">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="e8fde-180">Utwórz respondentów i Uzyskaj odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="e8fde-180">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="e8fde-181">Następnie napisz kod, który generuje odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-181">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="e8fde-182">Ten proces obejmuje kilka małych zadań:</span><span class="sxs-lookup"><span data-stu-id="e8fde-182">This process involves several small tasks:</span></span>

1. <span data-ttu-id="e8fde-183">Tworzenie metody, która generuje obiekty respondentów.</span><span class="sxs-lookup"><span data-stu-id="e8fde-183">Build a method that generates respondent objects.</span></span> <span data-ttu-id="e8fde-184">Reprezentują one zadawane Wypełnij ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-184">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="e8fde-185">Twórz logikę do symulacji udzielenia odpowiedzi na pytania respondentom i zbieranie odpowiedzi lub biorąc pod uwagę, że respondenta nie odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="e8fde-185">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="e8fde-186">Powtórz wystarczająco dużo respondentów Uzyskaj odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-186">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="e8fde-187">Potrzebna będzie klasy do reprezentowania odpowiedź na ankietę, więc teraz dodać.</span><span class="sxs-lookup"><span data-stu-id="e8fde-187">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="e8fde-188">Włącz obsługę dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-188">Enable nullable support.</span></span> <span data-ttu-id="e8fde-189">Dodaj `Id` właściwość i Konstruktor, który inicjuje go, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e8fde-189">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="e8fde-190">Następnie dodaj `static` metodę w celu utworzenia nowych uczestników, generując losowy identyfikator:</span><span class="sxs-lookup"><span data-stu-id="e8fde-190">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="e8fde-191">Podstawowa odpowiedzialność tej klasy jest do generowania odpowiedzi dla uczestników na pytania ankiety.</span><span class="sxs-lookup"><span data-stu-id="e8fde-191">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="e8fde-192">Ta odpowiedzialność składa się z kilku kroków:</span><span class="sxs-lookup"><span data-stu-id="e8fde-192">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="e8fde-193">Prosić o udział w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="e8fde-193">Ask for participation in the survey.</span></span> <span data-ttu-id="e8fde-194">Jeśli dana osoba nie zgodę, zwróć odpowiedź (wartość null lub nie).</span><span class="sxs-lookup"><span data-stu-id="e8fde-194">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="e8fde-195">Zadawaj pytania i Zapisz odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="e8fde-195">Ask each question and record the answer.</span></span> <span data-ttu-id="e8fde-196">Wszystkie odpowiedzi jest także (wartość null lub nie).</span><span class="sxs-lookup"><span data-stu-id="e8fde-196">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="e8fde-197">Dodaj następujący kod, aby Twoje `SurveyResponse` klasy:</span><span class="sxs-lookup"><span data-stu-id="e8fde-197">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="e8fde-198">Magazyn odpowiedzi udział w ankiecie jest `Dictionary<int, string>?`, wskazujący, że może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-198">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="e8fde-199">Zadeklaruj zamiar projektu, kompilator i kto czyta swój kod w dalszej części za pomocą nowej funkcji języka.</span><span class="sxs-lookup"><span data-stu-id="e8fde-199">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="e8fde-200">Jeśli kiedykolwiek wyłuskania `surveyResponses` bez uprzedniego sprawdzania pod zawiera wartości null, zostanie wyświetlone ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e8fde-200">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="e8fde-201">Nie pojawi się ostrzeżenie `AnswerSurvey` metody ponieważ kompilator może określić `surveyResponses` zmienna została ustawiona na wartość inną niż null powyżej.</span><span class="sxs-lookup"><span data-stu-id="e8fde-201">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="e8fde-202">Za pomocą `null` dla Brak odpowiedzi wyróżnia punkt klucza do pracy w przypadku typów referencyjnych dopuszczającego wartość null: cel nie jest, aby usunąć wszystkie `null` wartości z programu.</span><span class="sxs-lookup"><span data-stu-id="e8fde-202">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="e8fde-203">Celem użytkownika jest raczej, upewnij się, że kod, który napiszesz wyraża celem projektu.</span><span class="sxs-lookup"><span data-stu-id="e8fde-203">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="e8fde-204">Brak wartości są niezbędne pojęcia, aby wyrazić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8fde-204">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="e8fde-205">`null` Wartość jest jasny sposób wyrażania te brakujące wartości.</span><span class="sxs-lookup"><span data-stu-id="e8fde-205">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="e8fde-206">Próby usunięcia wszystkich `null` tylko prowadzi do definiowania niektóre sposobu, aby te brakujące wartości bez wartości `null`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-206">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="e8fde-207">Następnie należy napisać `PerformSurvey` method in Class metoda `SurveyRun` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8fde-207">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="e8fde-208">Dodaj następujący kod w `SurveyRun` klasy:</span><span class="sxs-lookup"><span data-stu-id="e8fde-208">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="e8fde-209">Ponownie w tym miejscu, wybór dopuszczający wartości null `List<SurveyResponse>?` wskazuje odpowiedzi może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-209">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="e8fde-210">Wskazuje, że udział w ankiecie nie zostały przypisane do żadnych respondentów jeszcze.</span><span class="sxs-lookup"><span data-stu-id="e8fde-210">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="e8fde-211">Należy zauważyć, że respondentów są dodawane do momentu wystarczająco wyrażono zgodę.</span><span class="sxs-lookup"><span data-stu-id="e8fde-211">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="e8fde-212">Ostatni krok, aby uruchomić udział w ankiecie jest dodanie wywołanie przeprowadzić ankietę na końcu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="e8fde-212">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="e8fde-213">Sprawdź odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="e8fde-213">Examine survey responses</span></span>

<span data-ttu-id="e8fde-214">Ostatnim krokiem jest do wyświetlania wyników ankiety.</span><span class="sxs-lookup"><span data-stu-id="e8fde-214">The last step is to display survey results.</span></span> <span data-ttu-id="e8fde-215">Następnie dodasz kod do wielu klas, które zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="e8fde-215">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="e8fde-216">Ten kod przedstawia wartość rozróżniania typów referencyjnych dopuszcza wartości null i nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-216">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="e8fde-217">Rozpocznij, dodając następujące dwa elementy członkowskie z wyrażeniem do `SurveyResponse` klasy:</span><span class="sxs-lookup"><span data-stu-id="e8fde-217">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="e8fde-218">Ponieważ `surveyResponses` jest typem niedopuszczającym odwołania żadne testy nie są niezbędne przed do odwoływania się do niego.</span><span class="sxs-lookup"><span data-stu-id="e8fde-218">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="e8fde-219">`Answer` Metoda zwraca ciąg z innych niż null, więc wybierz przeciążenia `GetValueOrDefault` przyjmującej drugi argument dla wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="e8fde-219">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="e8fde-220">Następnie dodaj te trzy elementy członkowskie z wyrażeniem do `SurveyRun` klasy:</span><span class="sxs-lookup"><span data-stu-id="e8fde-220">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="e8fde-221">`AllParticipants` Element członkowski należy wziąć pod uwagę, `respondents` zmienna może mieć wartości null, ale wartość zwracana nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-221">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="e8fde-222">Jeśli zmienisz to wyrażenie, usuwając `??` i pustej sekwencji, który następuje po kompilatora ostrzega, metoda może zwrócić `null` i jeho signatura zwracany zwraca typ niedopuszczający.</span><span class="sxs-lookup"><span data-stu-id="e8fde-222">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="e8fde-223">Na koniec Dodaj następującą pętlę w dolnej części `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="e8fde-223">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="e8fde-224">Nie potrzebujesz żadnej `null` sprawdza w tym kodzie, ponieważ został zaprojektowany podstawowych interfejsów, tak, aby wszystkie one zwracane typy nieprzyjmujące wartości odwołania.</span><span class="sxs-lookup"><span data-stu-id="e8fde-224">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="e8fde-225">Pobierz kod</span><span class="sxs-lookup"><span data-stu-id="e8fde-225">Get the code</span></span>

<span data-ttu-id="e8fde-226">Możesz też uzyskać kod Zakończono samouczek z naszych [przykłady](https://github.com/dotnet/samples) repozytorium w [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folderu.</span><span class="sxs-lookup"><span data-stu-id="e8fde-226">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="e8fde-227">Eksperymentować, zmieniając deklaracje typu między typami dopuszczającego wartość null i wartości null.</span><span class="sxs-lookup"><span data-stu-id="e8fde-227">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="e8fde-228">Zobacz, jak generujący różnych ostrzeżenia, aby upewnić się, przypadkowo nie wykonuj dereferencji `null`.</span><span class="sxs-lookup"><span data-stu-id="e8fde-228">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e8fde-229">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e8fde-229">Next steps</span></span>

<span data-ttu-id="e8fde-230">Dowiedz się więcej, migrując istniejących aplikacji na używanie typów referencyjnych dopuszczającego wartość null:</span><span class="sxs-lookup"><span data-stu-id="e8fde-230">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e8fde-231">Uaktualnianie aplikacji na używanie typów nullable odwołań</span><span class="sxs-lookup"><span data-stu-id="e8fde-231">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
