---
title: Projektowanie w przypadku typów referencyjnych dopuszczającego wartość null
description: W tym samouczku zaawansowane zawiera wprowadzenie do typów referencyjnych dopuszczającego wartość null. Dowiesz się, że express projektu chcący po wartości odniesienia może mieć wartości null i pozwolić kompilatorowi wymusić, gdy nie może mieć wartości null.
ms.date: 12/03/2018
ms.custom: mvc
ms.openlocfilehash: eec0c54c041db98595202ab982494df6ae3f743c
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204772"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="bee36-104">Samouczek: Wyraźniej Express zgodną z planem projektu w przypadku typów referencyjnych dopuszcza wartości null i nie dopuszcza wartości null</span><span class="sxs-lookup"><span data-stu-id="bee36-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="bee36-105">C#8 wprowadzono **typy dopuszczające wartości null odwołań**, które odwołania uzupełnieniem typów taki sam sposób, typy o wartości zerowalnej uzupełniają typów wartości.</span><span class="sxs-lookup"><span data-stu-id="bee36-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="bee36-106">Zadeklaruj zmienną **typu dopuszczającego wartość null odwołania** , dodając `?` do typu.</span><span class="sxs-lookup"><span data-stu-id="bee36-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="bee36-107">Na przykład `string?` reprezentuje dopuszczający wartości null `string`.</span><span class="sxs-lookup"><span data-stu-id="bee36-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="bee36-108">Te nowe typy można użyć, aby wyraźniej express zgodną z planem projektu: niektóre zmienne *zawsze musi mieć wartość*, inne *może brakować wartość*.</span><span class="sxs-lookup"><span data-stu-id="bee36-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="bee36-109">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="bee36-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="bee36-110">Włączenie typy dopuszczające wartości null i dopuszcza odwołań do projektów</span><span class="sxs-lookup"><span data-stu-id="bee36-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="bee36-111">Włącz sprawdzanie typu dopuszczającego wartość null odwołanie w całym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bee36-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="bee36-112">Napisz kod, w których kompilator wymusza tych decyzji projektowych.</span><span class="sxs-lookup"><span data-stu-id="bee36-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="bee36-113">Funkcja odwołanie dopuszczającego wartość null w własnych projektów</span><span class="sxs-lookup"><span data-stu-id="bee36-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bee36-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bee36-114">Prerequisites</span></span>

<span data-ttu-id="bee36-115">Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 beta.</span><span class="sxs-lookup"><span data-stu-id="bee36-115">You’ll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="bee36-116">C# 8 kompilatora w wersji beta jest dostępna z [2019 usługi Visual Studio w wersji zapoznawczej 1](https://visualstudio.microsoft.com/vs/preview/), lub [.NET Core 3.0 w wersji zapoznawczej 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="bee36-116">The C# 8 beta compiler is available with [Visual Studio 2019 preview 1](https://visualstudio.microsoft.com/vs/preview/), or [.NET Core 3.0 preview 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="bee36-117">W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bee36-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="bee36-118">Włączenie typy dopuszczające wartości null odwołań do projektów</span><span class="sxs-lookup"><span data-stu-id="bee36-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="bee36-119">W tym samouczku utworzysz biblioteki, który modeluje systemem ankiety.</span><span class="sxs-lookup"><span data-stu-id="bee36-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="bee36-120">Kod używa typy dopuszczające wartości null odwołań i typy referencyjne nie dopuszcza wartości null w celu przedstawienia koncepcji rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="bee36-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="bee36-121">Pytania ankiety nigdy nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-121">The survey questions can never be null.</span></span> <span data-ttu-id="bee36-122">Respondenta może nie chce uzyskać odpowiedzi na pytanie.</span><span class="sxs-lookup"><span data-stu-id="bee36-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="bee36-123">W takim przypadku może mieć wartości null odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bee36-123">The responses might be null in this case.</span></span>

<span data-ttu-id="bee36-124">Kod, który Ty napiszesz omawiany w tym przykładzie wyrażenie wskaźnika tym przeznaczeniem, a kompilator wymusza tym przeznaczeniem.</span><span class="sxs-lookup"><span data-stu-id="bee36-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="bee36-125">Tworzenie aplikacji i włączanie typów referencyjnych dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="bee36-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="bee36-126">Utwórz nową aplikację konsoli w programie Visual Studio lub z wiersza polecenia przy użyciu `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="bee36-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="bee36-127">Nazwij aplikację `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="bee36-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="bee36-128">Po utworzeniu aplikacji, musisz włączyć C# 8 funkcje w wersji beta.</span><span class="sxs-lookup"><span data-stu-id="bee36-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="bee36-129">Otwórz `csproj` pliku i Dodaj `LangVersion` elementu `PropertyGroup` elementu:</span><span class="sxs-lookup"><span data-stu-id="bee36-129">Open the `csproj` file, and add a `LangVersion` element to the `PropertyGroup` element:</span></span>

```xml
<LangVersion>8.0</LangVersion>
```

<span data-ttu-id="bee36-130">Alternatywnie można użyć właściwości projektu programu Visual Studio umożliwiające C# 8.</span><span class="sxs-lookup"><span data-stu-id="bee36-130">Alternatively, you can use the Visual Studio project properties to enable C# 8.</span></span> <span data-ttu-id="bee36-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, wybierz opcję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bee36-131">In Solution Explorer, right click on the project node, select **Properties**.</span></span> <span data-ttu-id="bee36-132">Następnie wybierz **kompilacji** kartę, a następnie kliknij przycisk **zaawansowane...** . W menu rozwijanym dla wersji językowej, wybierz  **C# 8.0 (beta)**.</span><span class="sxs-lookup"><span data-stu-id="bee36-132">Then, select the **build** tab, and click **Advanced...**. In the dropdown for language version, select **C# 8.0 (beta)**.</span></span>

<span data-ttu-id="bee36-133">Użytkownik musi wyrazić zgodę **typy dopuszczające wartości null odwołań** funkcji, nawet w C# 8 projektów.</span><span class="sxs-lookup"><span data-stu-id="bee36-133">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="bee36-134">To dlatego po włączeniu funkcji istniejące deklaracje zmiennych odwołania stają się, że **typów referencyjnych dopuszcza**.</span><span class="sxs-lookup"><span data-stu-id="bee36-134">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="bee36-135">Podczas tej decyzji pomogą znaleźć problemy, gdy istniejący kod może nie mieć odpowiednich sprawdzanie wartości null, jego mogą nie odzwierciedla precyzyjnie zgodne z zamiarami użytkownika oryginalnego projektu.</span><span class="sxs-lookup"><span data-stu-id="bee36-135">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="bee36-136">Możesz włączyć tę funkcję za pomocą nowej dyrektywy pragma:</span><span class="sxs-lookup"><span data-stu-id="bee36-136">You turn on the feature with a new pragma:</span></span>

```csharp
#nullable enable
```

<span data-ttu-id="bee36-137">Poprzedni pragma można dodać dowolne miejsce w pliku źródłowym i od tego momentu jest włączona funkcja typu dopuszczającego wartość null odwołanie.</span><span class="sxs-lookup"><span data-stu-id="bee36-137">You can add the preceding pragma anywhere in a source file, and the nullable reference type feature is turned on from that point.</span></span> <span data-ttu-id="bee36-138">Obsługuje również pragmy `disable` argumentu, aby wyłączyć tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="bee36-138">The pragma also supports the `disable` argument to turn off the feature.</span></span>

<span data-ttu-id="bee36-139">Można też włączyć **typy dopuszczające wartości null odwołań** dla całego projektu, dodając następujący element do pliku csproj, na przykład, następujący bezpośrednio po `LangVersion` elementu, która umożliwiała C# 8.0:</span><span class="sxs-lookup"><span data-stu-id="bee36-139">You can also turn on **nullable reference types** for an entire project by adding the following element to your .csproj file, for example, immediately following the `LangVersion` element that enabled C# 8.0:</span></span>

```xml
<NullableReferenceTypes>true</NullableReferenceTypes>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="bee36-140">Projektowanie typów dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="bee36-140">Design the types for the application</span></span>

<span data-ttu-id="bee36-141">Ta aplikacja ankiety wymaga, tworząc liczby klas:</span><span class="sxs-lookup"><span data-stu-id="bee36-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="bee36-142">Klasa, która modele listę pytań.</span><span class="sxs-lookup"><span data-stu-id="bee36-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="bee36-143">Klasa, która modele listę osób skontaktować się z ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="bee36-144">Klasa, która modele odpowiedzi od osoby, która trwała ankiety.</span><span class="sxs-lookup"><span data-stu-id="bee36-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="bee36-145">Te typy spowoduje, że wykorzystanie zarówno dopuszczającego wartość null i typy nieprzyjmujące wartości odwołań do wyrażania elementów członkowskich, które są wymagane i elementów członkowskich, które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bee36-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="bee36-146">Typy dopuszczające wartości null odwołanie do komunikacji, wyraźnie projektowania przeznaczenie:</span><span class="sxs-lookup"><span data-stu-id="bee36-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="bee36-147">Pytania, na które są dostępne w ramach przeglądu nigdy nie może mieć wartość null: Nie ma sensu zadać pytanie puste.</span><span class="sxs-lookup"><span data-stu-id="bee36-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="bee36-148">Respondentów nigdy nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-148">The respondents can never be null.</span></span> <span data-ttu-id="bee36-149">Należy śledzić osób z Tobą, nawet respondentów, które odrzucone do udziału.</span><span class="sxs-lookup"><span data-stu-id="bee36-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="bee36-150">Każda odpowiedź na pytanie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-150">Any response to a question may be null.</span></span> <span data-ttu-id="bee36-151">Respondentów można odrzucić odpowiedzi na niektóre lub wszystkie pytania.</span><span class="sxs-lookup"><span data-stu-id="bee36-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="bee36-152">Jeśli został zaprogramowany w C#, można więc przyzwyczajeni do odwołania typów, które akceptuje wartości null, które mogły zostać pominięte innymi możliwościami do deklarowania dopuszcza wystąpień:</span><span class="sxs-lookup"><span data-stu-id="bee36-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="bee36-153">Kolekcji pytań, powinna być wartość null.</span><span class="sxs-lookup"><span data-stu-id="bee36-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="bee36-154">Kolekcja respondentów powinna być wartość null.</span><span class="sxs-lookup"><span data-stu-id="bee36-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="bee36-155">Podczas pisania kodu, zobaczysz, że typ odwołania nie dopuszcza wartości null jako domyślne dla odwołania pozwala uniknąć typowych pomyłek, które mogą prowadzić do wyjątków odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="bee36-156">Lekcja jeden z tego samouczka jest podjęliśmy decyzje, o których zmiennych może lub nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="bee36-157">Język nie dostarczył składni wyrażenia te decyzje.</span><span class="sxs-lookup"><span data-stu-id="bee36-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="bee36-158">Teraz robi.</span><span class="sxs-lookup"><span data-stu-id="bee36-158">Now it does.</span></span>

<span data-ttu-id="bee36-159">Aplikację, którą utworzysz będzie wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bee36-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="bee36-160">Tworzą ankietę i dodać pytania do niego.</span><span class="sxs-lookup"><span data-stu-id="bee36-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="bee36-161">Utwórz zestaw pseudolosową respondentów ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="bee36-162">Skontaktuj się z respondentów, dopóki numer celem osiągnie rozmiar przeprowadzone badania.</span><span class="sxs-lookup"><span data-stu-id="bee36-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="bee36-163">Zapisać ważnych statystyk w odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="bee36-164">Tworzenie przeglądu z typu dopuszczającego wartość null i nie dopuszcza wartości null</span><span class="sxs-lookup"><span data-stu-id="bee36-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="bee36-165">Pierwszy kod, który Ty napiszesz tworzy ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="bee36-166">Przedstawiono tworzenie klas modelu pytania ankiety i ankiety, uruchom.</span><span class="sxs-lookup"><span data-stu-id="bee36-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="bee36-167">Ankiety ma trzy rodzaje pytań związanych z rozróżnianych na podstawie formatu odpowiedzi: Tak/nie odbierze odpowiedzi numer i tekst odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bee36-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="bee36-168">Tworzenie `public` `SurveyQuestion` klasy.</span><span class="sxs-lookup"><span data-stu-id="bee36-168">Create a `public` `SurveyQuestion` class.</span></span> <span data-ttu-id="bee36-169">Obejmują `#nullable enable` pragma natychmiast po `using` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="bee36-169">Include the `#nullable enable` pragma immediately after the `using` statements:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="bee36-170">Dodawanie `#nullable enable` pragma oznacza, że kompilator interpretuje co deklaracji zmiennych typu odwołania jako **dopuszcza** odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="bee36-170">Adding the `#nullable enable` pragma means the compiler interprets every reference type variable declaration as a **non-nullable** reference type.</span></span> <span data-ttu-id="bee36-171">Można wyświetlić swoje pierwsze ostrzeżenie przez dodanie właściwości tekst pytania i rodzaju pytania, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bee36-171">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
#nullable enable
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

<span data-ttu-id="bee36-172">Ponieważ jeszcze nie zainicjowany `QuestionText`, kompilator generuje ostrzeżenie właściwości niedopuszczającej nie zostało zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="bee36-172">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="bee36-173">Projekt wymaga tekst pytania, aby mieć wartości null, więc dodać konstruktora, aby go zainicjować i `QuestionType` również wartość.</span><span class="sxs-lookup"><span data-stu-id="bee36-173">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="bee36-174">Definicja klasy Zakończono wygląda podobnie do poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="bee36-174">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="bee36-175">Dodanie konstruktora powoduje usunięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="bee36-175">Adding the constructor removes the warning.</span></span> <span data-ttu-id="bee36-176">Argument konstruktora jest również typem referencyjnym dopuszcza kompilator nie generuje żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="bee36-176">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="bee36-177">Następnie należy utworzyć `public` klasę o nazwie `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="bee36-177">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="bee36-178">Obejmują `#nullable enable` następujące pragmy `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bee36-178">Include the `#nullable enable` pragma following the `using` statements.</span></span> <span data-ttu-id="bee36-179">Ta klasa zawiera listę `SurveyQuestion` obiektów i metod, aby dodać pytania ankiety, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bee36-179">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

#nullable enable
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

<span data-ttu-id="bee36-180">Tak jak poprzednio należy zainicjować obiekt listy, do wartości innej niż null lub kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="bee36-180">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="bee36-181">Nie ma żadnych sprawdzanie wartości null w drugie przeciążenie `AddQuestion` , ponieważ nie są one potrzebne: Został zadeklarowany tej zmiennej jako wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-181">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="bee36-182">Jego wartość nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="bee36-182">Its value can't be `null`.</span></span>

<span data-ttu-id="bee36-183">Przełącz się do `Program.cs` w edytorze i Zastąp zawartość `Main` z następującymi wierszami kodu:</span><span class="sxs-lookup"><span data-stu-id="bee36-183">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="bee36-184">Bez `#nullable enable` dyrektywę w górnej części pliku, kompilator nie generuje ostrzeżenia podczas przekazywania `null` jako tekst `AddQuestion` argumentu.</span><span class="sxs-lookup"><span data-stu-id="bee36-184">Without the `#nullable enable` pragma at the top of the file, the compiler doesn't issue a warning when you pass `null` as the text for the `AddQuestion` argument.</span></span> <span data-ttu-id="bee36-185">Rozwiązać ten problem, dodając `#nullable enable` następujące `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bee36-185">Fix that by adding `#nullable enable` following the `using` statement.</span></span> <span data-ttu-id="bee36-186">Wypróbuj je, dodając następujący wiersz do `Main`:</span><span class="sxs-lookup"><span data-stu-id="bee36-186">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="bee36-187">Utwórz respondentów i Uzyskaj odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="bee36-187">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="bee36-188">Następnie napisz kod, który generuje odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-188">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="bee36-189">Obejmuje to kilka małych zadań:</span><span class="sxs-lookup"><span data-stu-id="bee36-189">This involves several small tasks:</span></span>

1. <span data-ttu-id="bee36-190">Tworzenie metody, która generuje obiekty respondentów.</span><span class="sxs-lookup"><span data-stu-id="bee36-190">Build a method that generates respondent objects.</span></span> <span data-ttu-id="bee36-191">Reprezentują one zadawane Wypełnij ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-191">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="bee36-192">Twórz logikę do symulacji udzielenia odpowiedzi na pytania respondentom i zbieranie odpowiedzi lub biorąc pod uwagę, że respondenta nie odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="bee36-192">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="bee36-193">Powtórz wystarczająco dużo respondentów Uzyskaj odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="bee36-193">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="bee36-194">Potrzebna będzie klasy do reprezentowania odpowiedź na ankietę, więc teraz dodać.</span><span class="sxs-lookup"><span data-stu-id="bee36-194">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="bee36-195">Włącz obsługę dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="bee36-195">Enable nullable support.</span></span> <span data-ttu-id="bee36-196">Dodaj `Id` właściwość i Konstruktor, który inicjuje go, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bee36-196">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="bee36-197">Następnie dodaj `static` metodę w celu utworzenia nowych uczestników, generując losowy identyfikator:</span><span class="sxs-lookup"><span data-stu-id="bee36-197">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="bee36-198">Podstawowa odpowiedzialność tej klasy jest do generowania odpowiedzi dla uczestników na pytania ankiety.</span><span class="sxs-lookup"><span data-stu-id="bee36-198">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="bee36-199">Ta odpowiedzialność składa się z kilku kroków:</span><span class="sxs-lookup"><span data-stu-id="bee36-199">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="bee36-200">Prosić o udział w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="bee36-200">Ask for participation in the survey.</span></span> <span data-ttu-id="bee36-201">Jeśli dana osoba nie zgodę, zwróć odpowiedź (wartość null lub nie).</span><span class="sxs-lookup"><span data-stu-id="bee36-201">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="bee36-202">Zadawaj pytania i Zapisz odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="bee36-202">Ask each question and record the answer.</span></span> <span data-ttu-id="bee36-203">Wszystkie odpowiedzi jest także (wartość null lub nie).</span><span class="sxs-lookup"><span data-stu-id="bee36-203">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="bee36-204">Dodaj następujący kod, aby Twoje `SurveyResponse` klasy:</span><span class="sxs-lookup"><span data-stu-id="bee36-204">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="bee36-205">Magazyn odpowiedzi udział w ankiecie jest `Dictionary<int, string>?`, wskazujący, że może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-205">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="bee36-206">Zadeklaruj zamiar projektu, kompilator i kto czyta swój kod w dalszej części za pomocą nowej funkcji języka.</span><span class="sxs-lookup"><span data-stu-id="bee36-206">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="bee36-207">Jeśli kiedykolwiek wyłuskania `surveyResponses` bez uprzedniego sprawdzania pod zawiera wartości null, zostanie wyświetlone ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="bee36-207">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="bee36-208">Nie pojawi się ostrzeżenie `AnswerSurvey` metody ponieważ kompilator może określić `surveyResponses` zmienna została ustawiona na wartość inną niż null powyżej.</span><span class="sxs-lookup"><span data-stu-id="bee36-208">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="bee36-209">Następnie należy napisać `PerformSurvey` method in Class metoda `SurveyRun` klasy.</span><span class="sxs-lookup"><span data-stu-id="bee36-209">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="bee36-210">Dodaj następujący kod w `SurveyRun` klasy:</span><span class="sxs-lookup"><span data-stu-id="bee36-210">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="bee36-211">Ponownie w tym miejscu, wybór dopuszczający wartości null `List<SurveyResponse>?` wskazuje odpowiedzi może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-211">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="bee36-212">Wskazuje, że udział w ankiecie nie zostały przypisane do żadnych respondentów jeszcze.</span><span class="sxs-lookup"><span data-stu-id="bee36-212">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="bee36-213">Należy zauważyć, że respondentów są dodawane do momentu wystarczająco wyrażono zgodę.</span><span class="sxs-lookup"><span data-stu-id="bee36-213">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="bee36-214">Ostatni krok, aby uruchomić udział w ankiecie jest dodanie wywołanie przeprowadzić ankietę na końcu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="bee36-214">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="bee36-215">Sprawdź odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="bee36-215">Examine survey responses</span></span>

<span data-ttu-id="bee36-216">Ostatnim krokiem jest do wyświetlania wyników ankiety.</span><span class="sxs-lookup"><span data-stu-id="bee36-216">The last step is to display survey results.</span></span> <span data-ttu-id="bee36-217">Następnie dodasz kod do wielu klas, które zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="bee36-217">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="bee36-218">Ten kod przedstawia wartość rozróżniania typów referencyjnych dopuszcza wartości null i nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-218">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="bee36-219">Rozpocznij, dodając następujące dwa elementy członkowskie z wyrażeniem do `SurveyResponse` klasy:</span><span class="sxs-lookup"><span data-stu-id="bee36-219">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="bee36-220">Ponieważ `surveyResponses` jest typem niedopuszczającym odwołania żadne testy nie są niezbędne przed do odwoływania się do niego.</span><span class="sxs-lookup"><span data-stu-id="bee36-220">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="bee36-221">`Answer` Metoda zwraca ciąg z innych niż null, więc wybierz przeciążenia `GetValueOrDefault` przyjmującej drugi argument dla wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="bee36-221">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="bee36-222">Następnie dodaj te trzy elementy członkowskie z wyrażeniem do `SurveyRun` klasy:</span><span class="sxs-lookup"><span data-stu-id="bee36-222">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="bee36-223">`AllParticipants` Element członkowski należy wziąć pod uwagę, `respondents` zmienna może mieć wartości null, ale wartość zwracana nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-223">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="bee36-224">Jeśli zmienisz to wyrażenie, usuwając `??` i pustej sekwencji, który następuje po kompilatora ostrzega, metoda może zwrócić `null` i jeho signatura zwracany zwraca typ niedopuszczający.</span><span class="sxs-lookup"><span data-stu-id="bee36-224">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="bee36-225">Na koniec Dodaj następującą pętlę w dolnej części `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="bee36-225">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="bee36-226">Nie potrzebujesz żadnej `null` sprawdza w tym kodzie, ponieważ został zaprojektowany podstawowych interfejsów, tak, aby wszystkie one zwracane typy nieprzyjmujące wartości odwołania.</span><span class="sxs-lookup"><span data-stu-id="bee36-226">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="bee36-227">Pobierz kod</span><span class="sxs-lookup"><span data-stu-id="bee36-227">Get the code</span></span>

<span data-ttu-id="bee36-228">Możesz też uzyskać kod Zakończono samouczek z naszych [przykłady](https://github.com/dotnet/samples) repozytorium w [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folderu.</span><span class="sxs-lookup"><span data-stu-id="bee36-228">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="bee36-229">Eksperymentować, zmieniając deklaracje typu między typami dopuszczającego wartość null i wartości null.</span><span class="sxs-lookup"><span data-stu-id="bee36-229">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="bee36-230">Zobacz, jak generujący różnych ostrzeżenia, aby upewnić się, przypadkowo nie wykonuj dereferencji `null`.</span><span class="sxs-lookup"><span data-stu-id="bee36-230">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bee36-231">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bee36-231">Next steps</span></span>

<span data-ttu-id="bee36-232">Dowiedz się więcej, zapoznając się z omówieniem typy dopuszczające wartości null odwołań...</span><span class="sxs-lookup"><span data-stu-id="bee36-232">Learn more by reading an overview of nullable reference types..</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="bee36-233">Przegląd odwołań dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="bee36-233">An overview of nullable references</span></span>](../nullable-references.md)
