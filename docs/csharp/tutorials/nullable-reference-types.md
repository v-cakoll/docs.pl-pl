---
title: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null
description: Ten zaawansowany samouczek zawiera wprowadzenie do typów referencyjnych dopuszczających wartość null. Dowiesz się, w jaki sposób projekt zostanie zastosowany, gdy wartości odniesienia mogą mieć wartość null, i że kompilator wymusi, gdy nie mogą mieć wartości null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: ea8059061dccc85060b4f6244ff0d7be9b7708b8
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214416"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="96a9c-104">Samouczek: Dokładniej zamierzanie projektu z typami odwołań dopuszczających wartości null i niedopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="96a9c-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="96a9c-105">C#8 wprowadza **typy odwołań do wartości null**, które uzupełniają typy odwołań w taki sam sposób, jak typy wartości null uzupełniają typy wartości.</span><span class="sxs-lookup"><span data-stu-id="96a9c-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="96a9c-106">Należy zadeklarować zmienną jako **typ referencyjny dopuszczający wartość null** poprzez dołączenie `?` do typu.</span><span class="sxs-lookup"><span data-stu-id="96a9c-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="96a9c-107">Na przykład `string?` reprezentuje wartość null `string`.</span><span class="sxs-lookup"><span data-stu-id="96a9c-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="96a9c-108">Możesz użyć tych nowych typów, aby dokładniej wyznaczać intencje projektowania: niektóre zmienne *muszą zawsze mieć wartość*, inne *mogą nie mieć wartości*.</span><span class="sxs-lookup"><span data-stu-id="96a9c-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="96a9c-109">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="96a9c-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="96a9c-110">Uwzględnianie typów referencyjnych dopuszczających wartości null i niedopuszczających wartości null do Twoich projektów</span><span class="sxs-lookup"><span data-stu-id="96a9c-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="96a9c-111">Włącz kontrolę typu odwołania do wartości null w całym kodzie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="96a9c-112">Napisz kod, w którym kompilator wymusza te decyzje projektowe.</span><span class="sxs-lookup"><span data-stu-id="96a9c-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="96a9c-113">Używanie funkcji referencyjnej nullable we własnych projektach</span><span class="sxs-lookup"><span data-stu-id="96a9c-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96a9c-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="96a9c-114">Prerequisites</span></span>

<span data-ttu-id="96a9c-115">Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0 beta.</span><span class="sxs-lookup"><span data-stu-id="96a9c-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="96a9c-116">Kompilator C# 8-Beta jest dostępny w programie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="96a9c-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="96a9c-117">W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a9c-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="96a9c-118">Dołączanie typów odwołań do wartości null do projektów</span><span class="sxs-lookup"><span data-stu-id="96a9c-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="96a9c-119">W tym samouczku utworzysz bibliotekę, w której będą wykonywane ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="96a9c-120">Kod używa zarówno typów referencyjnych dopuszczających wartości null, jak i niedopuszczających wartości null typy odwołań do reprezentowania rzeczywistych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="96a9c-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="96a9c-121">Pytania dotyczące ankiety nigdy nie mogą mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-121">The survey questions can never be null.</span></span> <span data-ttu-id="96a9c-122">Respondent może preferować nie odpowiedzieć na pytanie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="96a9c-123">W takim przypadku odpowiedzi mogą mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-123">The responses might be null in this case.</span></span>

<span data-ttu-id="96a9c-124">Kod, który napiszesz dla tego przykładu, oznacza, że zamiar, a kompilator wymusza ten cel.</span><span class="sxs-lookup"><span data-stu-id="96a9c-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="96a9c-125">Tworzenie aplikacji i włączanie typów referencyjnych dopuszczających wartość null</span><span class="sxs-lookup"><span data-stu-id="96a9c-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="96a9c-126">Utwórz nową aplikację konsolową w programie Visual Studio lub za pomocą `dotnet new console`polecenia.</span><span class="sxs-lookup"><span data-stu-id="96a9c-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="96a9c-127">Nadaj nazwę aplikacji `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="96a9c-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="96a9c-128">Po utworzeniu aplikacji należy włączyć C# 8 funkcji w wersji beta.</span><span class="sxs-lookup"><span data-stu-id="96a9c-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="96a9c-129">Otwórz plik i `LangVersion` Dodaj element do `PropertyGroup` elementu. `csproj`</span><span class="sxs-lookup"><span data-stu-id="96a9c-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="96a9c-130">Należy wybrać funkcję **typów referencyjnych dopuszczających wartość null** , nawet C# w 8 projektach.</span><span class="sxs-lookup"><span data-stu-id="96a9c-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="96a9c-131">Dzieje się tak, ponieważ po włączeniu tej funkcji istniejące deklaracje zmiennej odwołania stają się **typami odwołań niedopuszczających wartości null**.</span><span class="sxs-lookup"><span data-stu-id="96a9c-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="96a9c-132">Chociaż ta decyzja pomoże w znalezieniu problemów, w których istniejący kod może nie mieć odpowiednich testów o wartości null, może nie dokładnie odzwierciedlać pierwotny cel projektowania.</span><span class="sxs-lookup"><span data-stu-id="96a9c-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="96a9c-133">Aby włączyć tę funkcję, należy ustawić `Nullable` element na: `enable`</span><span class="sxs-lookup"><span data-stu-id="96a9c-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> <span data-ttu-id="96a9c-134">Element miał wcześniej nazwę `NullableContextOptions`. `Nullable`</span><span class="sxs-lookup"><span data-stu-id="96a9c-134">The `Nullable` element was previously named `NullableContextOptions`.</span></span> <span data-ttu-id="96a9c-135">Zmiana nazwy jest dostarczana z programem Visual Studio 2019, 16,2-P1.</span><span class="sxs-lookup"><span data-stu-id="96a9c-135">The rename ships with Visual Studio 2019, 16.2-p1.</span></span> <span data-ttu-id="96a9c-136">Ta zmiana nie ma zestaw .NET Core SDK 3.0.100-preview5-011568.</span><span class="sxs-lookup"><span data-stu-id="96a9c-136">The .NET Core SDK 3.0.100-preview5-011568 does not have this change.</span></span> <span data-ttu-id="96a9c-137">Jeśli używasz interfejs wiersza polecenia platformy .NET Core, musisz użyć `NullableContextOptions` do momentu udostępnienia kolejnej wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="96a9c-137">If you are using the .NET Core CLI, you'll need to use `NullableContextOptions` until the next preview is available.</span></span>

> [!NOTE]
> <span data-ttu-id="96a9c-138">Po C# wydaniu 8 (w trybie podglądu) `Nullable` element zostanie dodany przez nowe szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="96a9c-138">When C# 8 is released (not in preview mode), the `Nullable` element will be added by new project templates.</span></span> <span data-ttu-id="96a9c-139">Do tego momentu należy dodać ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-139">Until then, you'll need to add it manually.</span></span>

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="96a9c-140">Projektowanie typów aplikacji</span><span class="sxs-lookup"><span data-stu-id="96a9c-140">Design the types for the application</span></span>

<span data-ttu-id="96a9c-141">Ta aplikacja do ankiety wymaga utworzenia szeregu klas:</span><span class="sxs-lookup"><span data-stu-id="96a9c-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="96a9c-142">Klasa, która modeluje listę pytań.</span><span class="sxs-lookup"><span data-stu-id="96a9c-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="96a9c-143">Klasa, która modeluje listę osób, którym kontaktowali się na potrzeby ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="96a9c-144">Klasa, która modeluje odpowiedzi od osoby, która przeprowadziła ankietę.</span><span class="sxs-lookup"><span data-stu-id="96a9c-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="96a9c-145">Te typy będą używały typów referencyjnych dopuszczających wartości null i niedopuszczających wartości null do wyznaczania, które elementy członkowskie są wymagane i które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="96a9c-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="96a9c-146">Typy referencyjne dopuszczające wartość null komunikują się, że projekt zamierzenia</span><span class="sxs-lookup"><span data-stu-id="96a9c-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="96a9c-147">Pytania, które są częścią ankiety, nie mogą być puste: Nie ma sensu, aby zadać puste pytanie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="96a9c-148">Respondenci nie mogą być puste.</span><span class="sxs-lookup"><span data-stu-id="96a9c-148">The respondents can never be null.</span></span> <span data-ttu-id="96a9c-149">Użytkownik chce śledzić osoby, którym nastąpi kontakt, nawet respondentów, którzy odrzucili uczestnictwo.</span><span class="sxs-lookup"><span data-stu-id="96a9c-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="96a9c-150">Każda odpowiedź na pytanie może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-150">Any response to a question may be null.</span></span> <span data-ttu-id="96a9c-151">Respondenci mogą odrzucić niektóre lub wszystkie pytania.</span><span class="sxs-lookup"><span data-stu-id="96a9c-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="96a9c-152">Jeśli zaznaczono program w programie C#, można go przywołać do typów referencyjnych, które zezwalają na wartości null, które mogły pominąć inne możliwości deklarowania wystąpień niedopuszczających wartości null:</span><span class="sxs-lookup"><span data-stu-id="96a9c-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="96a9c-153">Kolekcje pytań nie mogą dopuszczać wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="96a9c-154">Kolekcja respondentów nie powinna być dopuszczana do wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="96a9c-155">Podczas pisania kodu zobaczysz, że typ referencyjny niedopuszczający wartości null jako domyślny dla odwołań pozwala uniknąć częstych błędów, które mogą prowadzić do wyjątków odwołania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="96a9c-156">Jedną z lekcji w tym samouczku jest to, że podjęto decyzję o tym, które zmienne mogły lub nie mogą mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="96a9c-157">Język nie dostarczył składni do wyrażania tych decyzji.</span><span class="sxs-lookup"><span data-stu-id="96a9c-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="96a9c-158">Teraz.</span><span class="sxs-lookup"><span data-stu-id="96a9c-158">Now it does.</span></span>

<span data-ttu-id="96a9c-159">Aplikacja, którą utworzysz, wykona następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="96a9c-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="96a9c-160">Utwórz ankietę i Dodaj do niej pytania.</span><span class="sxs-lookup"><span data-stu-id="96a9c-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="96a9c-161">Utwórz pseudo-losowy zbiór respondentów dla ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="96a9c-162">Skontaktuj się z respondentami do momentu, aż ukończony rozmiar ankiety osiągnie numer celu.</span><span class="sxs-lookup"><span data-stu-id="96a9c-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="96a9c-163">Zapisuj ważne dane statystyczne odpowiedzi na ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="96a9c-164">Kompilowanie ankiety przy użyciu typów dopuszczających wartości null i nie dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="96a9c-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="96a9c-165">Pierwszy kod, który napiszesz, tworzy ankietę.</span><span class="sxs-lookup"><span data-stu-id="96a9c-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="96a9c-166">Należy napisać klasy do modelowania pytania ankietowego i uruchomienia ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="96a9c-167">Ankieta zawiera trzy typy pytań, które różnią się formatem odpowiedzi: Tak/nie odpowiedzi, liczba odpowiedzi i odpowiedzi tekstowe.</span><span class="sxs-lookup"><span data-stu-id="96a9c-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="96a9c-168">`public` Utwórz`SurveyQuestion` klasę:</span><span class="sxs-lookup"><span data-stu-id="96a9c-168">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="96a9c-169">Kompilator interpretuje każdą deklarację zmiennej typu odwołania jako typ referencyjny **niedopuszczający wartości null** dla kodu w kontekście, w którym włączono wartość null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-169">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="96a9c-170">Pierwsze ostrzeżenie można zobaczyć, dodając właściwości dla tekstu pytania i typ pytania, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="96a9c-170">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="96a9c-171">Ponieważ nie zainicjowano `QuestionText`, kompilator generuje ostrzeżenie, że nie zainicjowano właściwości, która nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-171">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="96a9c-172">Projekt wymaga, aby tekst pytania miał wartość różną od null, więc można dodać konstruktora, aby go zainicjować i `QuestionType` wartość.</span><span class="sxs-lookup"><span data-stu-id="96a9c-172">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="96a9c-173">Gotowa definicja klasy wygląda podobnie do następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="96a9c-173">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="96a9c-174">Dodanie konstruktora spowoduje usunięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="96a9c-174">Adding the constructor removes the warning.</span></span> <span data-ttu-id="96a9c-175">Argument konstruktora jest również typem referencyjnym, który nie dopuszcza wartości null, więc kompilator nie wystawia żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="96a9c-175">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="96a9c-176">Następnie Utwórz `public` klasę o nazwie `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="96a9c-176">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="96a9c-177">Ta klasa zawiera listę `SurveyQuestion` obiektów i metod, które umożliwiają dodawanie pytań do ankiety, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="96a9c-177">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="96a9c-178">Tak jak wcześniej, należy zainicjować obiekt listy w wartości innej niż null lub kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-178">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="96a9c-179">W drugim przeciążeniu `AddQuestion` nie ma sprawdzania wartości null, ponieważ nie są one potrzebne: Zadeklarowano, że zmienna nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-179">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="96a9c-180">Wartość nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="96a9c-180">Its value can't be `null`.</span></span>

<span data-ttu-id="96a9c-181">Przejdź do `Program.cs` programu w edytorze i Zastąp `Main` zawartość następującym wierszem kodu:</span><span class="sxs-lookup"><span data-stu-id="96a9c-181">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="96a9c-182">Ponieważ cały projekt znajduje się w kontekście, w którym włączono wartość null, otrzymasz ostrzeżenia, `null` gdy przejdziesz do dowolnej metody, która oczekuje typu referencyjnego, który nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-182">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="96a9c-183">Wypróbuj go, dodając następujący wiersz do `Main`:</span><span class="sxs-lookup"><span data-stu-id="96a9c-183">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="96a9c-184">Twórz respondenci i uzyskuj odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="96a9c-184">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="96a9c-185">Następnie napisz kod, który generuje odpowiedzi na ankietę.</span><span class="sxs-lookup"><span data-stu-id="96a9c-185">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="96a9c-186">Ten proces obejmuje kilka małych zadań:</span><span class="sxs-lookup"><span data-stu-id="96a9c-186">This process involves several small tasks:</span></span>

1. <span data-ttu-id="96a9c-187">Kompiluj metodę generującą obiekty respondentów.</span><span class="sxs-lookup"><span data-stu-id="96a9c-187">Build a method that generates respondent objects.</span></span> <span data-ttu-id="96a9c-188">Reprezentują one osoby, które poprosiły o wypełnienie ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-188">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="96a9c-189">Utwórz logikę, aby symulować pytania do respondenta i zbierać odpowiedzi lub zauważyć, że respondent nie odpowiedział.</span><span class="sxs-lookup"><span data-stu-id="96a9c-189">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="96a9c-190">Powtarzaj do momentu, aż wystarczające respondenci przepowieli ankietę.</span><span class="sxs-lookup"><span data-stu-id="96a9c-190">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="96a9c-191">Potrzebujesz klasy do reprezentowania odpowiedzi ankiety, więc Dodaj ją teraz.</span><span class="sxs-lookup"><span data-stu-id="96a9c-191">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="96a9c-192">Włącz obsługę dopuszczania wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-192">Enable nullable support.</span></span> <span data-ttu-id="96a9c-193">`Id` Dodaj właściwość i konstruktora, która go inicjuje, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="96a9c-193">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="96a9c-194">Następnie Dodaj `static` metodę, aby utworzyć nowych uczestników przez wygenerowanie losowego identyfikatora:</span><span class="sxs-lookup"><span data-stu-id="96a9c-194">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="96a9c-195">Główną odpowiedzialnością tej klasy jest generowanie odpowiedzi dla uczestnika na pytania w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-195">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="96a9c-196">Ta odpowiedzialność obejmuje kilka kroków:</span><span class="sxs-lookup"><span data-stu-id="96a9c-196">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="96a9c-197">Poproś o uczestnictwo w ankiecie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-197">Ask for participation in the survey.</span></span> <span data-ttu-id="96a9c-198">Jeśli osoba nie wyraża zgody, zwróć odpowiedź o brakującą wartość (lub null).</span><span class="sxs-lookup"><span data-stu-id="96a9c-198">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="96a9c-199">Zadawaj każde pytanie i zanotuj odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="96a9c-199">Ask each question and record the answer.</span></span> <span data-ttu-id="96a9c-200">Każda odpowiedź może być również brakująca (lub mieć wartość null).</span><span class="sxs-lookup"><span data-stu-id="96a9c-200">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="96a9c-201">Dodaj następujący kod do `SurveyResponse` klasy:</span><span class="sxs-lookup"><span data-stu-id="96a9c-201">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="96a9c-202">Magazyn dla odpowiedzi na ankiety jest `Dictionary<int, string>?`, co oznacza, że może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-202">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="96a9c-203">Używasz nowej funkcji języka do deklarowania zamiaru projektu, zarówno do kompilatora, jak i do każdego, kto czyta kod później.</span><span class="sxs-lookup"><span data-stu-id="96a9c-203">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="96a9c-204">Jeśli kiedykolwiek chcesz usunąć odwołanie `surveyResponses` bez sprawdzania, czy wartość null jest najpierw, otrzymasz ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="96a9c-204">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="96a9c-205">Nie otrzymujesz ostrzeżenia w `AnswerSurvey` metodzie, ponieważ kompilator może określić, że `surveyResponses` dla zmiennej została ustawiona wartość inna niż null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-205">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="96a9c-206">Użycie `null` w przypadku brakujących odpowiedzi podświetla kluczowy punkt do pracy z typami odwołań dopuszczających wartość null: `null` nie można usunąć wszystkich wartości z programu.</span><span class="sxs-lookup"><span data-stu-id="96a9c-206">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="96a9c-207">Zamiast tego celem jest upewnienie się, że napisany kod wyraża zamiar Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="96a9c-207">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="96a9c-208">Brakujące wartości są koniecznym pojęciem do wyrażania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-208">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="96a9c-209">`null` Wartość jest jasne, aby wyrazić te brakujące wartości.</span><span class="sxs-lookup"><span data-stu-id="96a9c-209">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="96a9c-210">Próba usunięcia wszystkich `null` wartości powoduje tylko określenie, że nie `null`są to wartości brakujące.</span><span class="sxs-lookup"><span data-stu-id="96a9c-210">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="96a9c-211">Następnie należy napisać `PerformSurvey` metodę `SurveyRun` w klasie.</span><span class="sxs-lookup"><span data-stu-id="96a9c-211">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="96a9c-212">Dodaj następujący kod do `SurveyRun` klasy:</span><span class="sxs-lookup"><span data-stu-id="96a9c-212">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="96a9c-213">W tym przypadku wybór wartości null `List<SurveyResponse>?` wskazuje, że odpowiedź może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-213">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="96a9c-214">Oznacza to, że ankieta nie została jeszcze udzielona żadnym respondentom.</span><span class="sxs-lookup"><span data-stu-id="96a9c-214">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="96a9c-215">Zwróć uwagę, że respondenci są dodawani, dopóki nie zostanie osiągnięta wystarczająca liczba.</span><span class="sxs-lookup"><span data-stu-id="96a9c-215">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="96a9c-216">Ostatnim krokiem do uruchomienia ankiety jest dodanie wywołania do wykonania ankiety na końcu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="96a9c-216">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="96a9c-217">Zbadaj odpowiedzi na ankietę</span><span class="sxs-lookup"><span data-stu-id="96a9c-217">Examine survey responses</span></span>

<span data-ttu-id="96a9c-218">Ostatnim krokiem jest wyświetlenie wyników ankiety.</span><span class="sxs-lookup"><span data-stu-id="96a9c-218">The last step is to display survey results.</span></span> <span data-ttu-id="96a9c-219">Dodasz kod do wielu utworzonych klas.</span><span class="sxs-lookup"><span data-stu-id="96a9c-219">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="96a9c-220">Ten kod demonstruje wartość odróżniania typów referencyjnych dopuszczających wartości null i niedopuszczających wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-220">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="96a9c-221">Zacznij od dodania następujących dwóch składowych wyrażeń do `SurveyResponse` klasy:</span><span class="sxs-lookup"><span data-stu-id="96a9c-221">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="96a9c-222">Ponieważ `surveyResponses` to nie jest typ referencyjny niedopuszczający wartości null, przed cofnięciem odwołania nie są wymagane żadne kontrole.</span><span class="sxs-lookup"><span data-stu-id="96a9c-222">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="96a9c-223">Metoda zwraca ciąg niedopuszczający wartości null, dlatego wybierz `GetValueOrDefault` Przeciążenie, które przyjmuje drugi argument dla wartości domyślnej. `Answer`</span><span class="sxs-lookup"><span data-stu-id="96a9c-223">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="96a9c-224">Następnie Dodaj te trzy składowe z wyrażeniami do `SurveyRun` klasy:</span><span class="sxs-lookup"><span data-stu-id="96a9c-224">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="96a9c-225">Element członkowski musi wziąć pod uwagę `respondents` , że zmienna może mieć wartość null, ale zwracana wartość nie może być równa null. `AllParticipants`</span><span class="sxs-lookup"><span data-stu-id="96a9c-225">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="96a9c-226">Jeśli zmienisz to wyrażenie poprzez usunięcie `??` i pustej sekwencji, która następuje, kompilator ostrzega o tym, że metoda może zostać zwrócona `null` , a jej sygnatura zwrotna zwraca typ niedopuszczający wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-226">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="96a9c-227">Na koniec Dodaj następującą pętlę w dolnej części `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="96a9c-227">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="96a9c-228">Nie musisz `null` już sprawdzać w tym kodzie, ponieważ zostały zaprojektowane bazowe interfejsy, aby wszystkie zwracane były typy odwołań niedopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-228">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="96a9c-229">Pobierz kod</span><span class="sxs-lookup"><span data-stu-id="96a9c-229">Get the code</span></span>

<span data-ttu-id="96a9c-230">Możesz uzyskać kod gotowego samouczka z naszego repozytorium [przykładów](https://github.com/dotnet/samples) w folderze [CSharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) .</span><span class="sxs-lookup"><span data-stu-id="96a9c-230">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="96a9c-231">Eksperymentowanie, zmieniając deklaracje typu między typami odwołań dopuszczających wartości null i niedopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="96a9c-231">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="96a9c-232">Zobacz, jak generuje różne ostrzeżenia, aby zapobiec przypadkowemu `null`wykorzystaniu.</span><span class="sxs-lookup"><span data-stu-id="96a9c-232">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="96a9c-233">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="96a9c-233">Next steps</span></span>

<span data-ttu-id="96a9c-234">Dowiedz się więcej przez Migrowanie istniejącej aplikacji w celu używania typów referencyjnych dopuszczających wartości null:</span><span class="sxs-lookup"><span data-stu-id="96a9c-234">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="96a9c-235">Uaktualnianie aplikacji w celu używania typów referencyjnych dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="96a9c-235">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
