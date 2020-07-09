---
title: 'Samouczek: Napisz pierwszy Analizator i poprawkę kodu'
description: Ten samouczek zawiera instrukcje krok po kroku dotyczące kompilowania analizatora i poprawki kodu przy użyciu zestawu SDK kompilatora .NET (interfejsy API Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: c70fcacc6cb30969e5c69ffd0954ac52e637a915
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100941"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="387df-103">Samouczek: Napisz pierwszy Analizator i poprawkę kodu</span><span class="sxs-lookup"><span data-stu-id="387df-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="387df-104">Zestaw SDK .NET Compiler Platform zawiera narzędzia potrzebne do tworzenia niestandardowych ostrzeżeń, które są przeznaczone dla kodu w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="387df-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="387df-105">**Analizator** zawiera kod, który rozpoznaje naruszenia reguły.</span><span class="sxs-lookup"><span data-stu-id="387df-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="387df-106">**Poprawka kodu** zawiera kod, który naprawia naruszenie.</span><span class="sxs-lookup"><span data-stu-id="387df-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="387df-107">Implementowane reguły mogą być dowolne od struktury kodu do stylu kodowania do konwencji nazewnictwa i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="387df-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="387df-108">.NET Compiler Platform zapewnia strukturę do uruchamiania analizy, ponieważ deweloperzy piszą kod i wszystkie funkcje interfejsu użytkownika programu Visual Studio umożliwiające naprawianie kodu: wyświetlanie zygzaków w edytorze, zapełnianie Lista błędów programu Visual Studio, tworzenie sugestii "żarówki" i wyświetlanie bogatej wersji zapoznawczej sugerowanych poprawek.</span><span class="sxs-lookup"><span data-stu-id="387df-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="387df-109">W tym samouczku przedstawiono tworzenie **analizatora** i dołączoną **poprawkę kodu** przy użyciu interfejsów API Roslyn.</span><span class="sxs-lookup"><span data-stu-id="387df-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="387df-110">Analizator jest sposobem przeprowadzenia analizy kodu źródłowego i zgłoszenia problemu do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="387df-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="387df-111">Opcjonalnie Analizator może również dostarczyć poprawkę kodu, która reprezentuje modyfikację kodu źródłowego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="387df-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="387df-112">Ten samouczek tworzy Analizator, który wyszukuje deklaracje zmiennych lokalnych, które mogą być deklarowane przy użyciu `const` modyfikatora, ale nie są.</span><span class="sxs-lookup"><span data-stu-id="387df-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="387df-113">Poprawka kodu towarzyszącego modyfikuje te deklaracje w celu dodania `const` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="387df-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="387df-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="387df-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="387df-115">Bieżąca wersja programu Visual Studio **Analyzer z szablonem poprawki kodu (.NET standard)** zawiera znaną usterkę w nim i powinna zostać naprawiona w programie Visual Studio 2019 w wersji 16,7.</span><span class="sxs-lookup"><span data-stu-id="387df-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="387df-116">Projekty w szablonie nie zostaną skompilowane, chyba że zostaną wykonane następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="387df-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="387df-117">Wybieranie **narzędzi**  >  **Opcje**narzędzia  >  **Menedżer pakietów NuGet**  >  **źródła pakietów**</span><span class="sxs-lookup"><span data-stu-id="387df-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="387df-118">Wybierz przycisk Plus, aby dodać nowe źródło:</span><span class="sxs-lookup"><span data-stu-id="387df-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="387df-119">Ustaw **Źródło** na `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` i wybierz pozycję **Aktualizuj**</span><span class="sxs-lookup"><span data-stu-id="387df-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="387df-120">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **MakeConst. vsix** i wybierz polecenie **Edytuj plik projektu**</span><span class="sxs-lookup"><span data-stu-id="387df-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="387df-121">Zaktualizuj `<AssemblyName>` węzeł, aby dodać `.Visx` sufiks:</span><span class="sxs-lookup"><span data-stu-id="387df-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="387df-122">`<ProjectReference>`Aby zmienić wartość, zaktualizuj węzeł w wierszu 41 `TargetFramework` :</span><span class="sxs-lookup"><span data-stu-id="387df-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="387df-123">Zaktualizuj plik *MakeConstUnitTests.cs* w projekcie *MakeConst. test* :</span><span class="sxs-lookup"><span data-stu-id="387df-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="387df-124">Zmień wiersz 9 na następujący, Zauważ zmianę przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="387df-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="387df-125">Zmień wiersz 24 na następującą metodę:</span><span class="sxs-lookup"><span data-stu-id="387df-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="387df-126">Zmień wiersz 62 na następującą metodę:</span><span class="sxs-lookup"><span data-stu-id="387df-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="387df-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="387df-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="387df-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="387df-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="387df-129">Musisz zainstalować **zestaw SDK .NET compiler platform** za pomocą Instalator programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="387df-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="387df-130">Istnieje kilka kroków, które należy wykonać, aby utworzyć i zweryfikować analizator:</span><span class="sxs-lookup"><span data-stu-id="387df-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="387df-131">Utwórz rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="387df-131">Create the solution.</span></span>
1. <span data-ttu-id="387df-132">Zarejestruj nazwę i opis analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="387df-133">Ostrzeżenia i zalecenia analizatora raportów.</span><span class="sxs-lookup"><span data-stu-id="387df-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="387df-134">Zaimplementuj poprawkę kodu, aby akceptować zalecenia.</span><span class="sxs-lookup"><span data-stu-id="387df-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="387df-135">Popraw analizę poprzez testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="387df-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="387df-136">Eksplorowanie szablonu analizatora</span><span class="sxs-lookup"><span data-stu-id="387df-136">Explore the analyzer template</span></span>

<span data-ttu-id="387df-137">Analizator raportuje do użytkownika wszystkie deklaracje zmiennych lokalnych, które mogą być konwertowane na stałe lokalne.</span><span class="sxs-lookup"><span data-stu-id="387df-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="387df-138">Rozważmy na przykład następujący kod:</span><span class="sxs-lookup"><span data-stu-id="387df-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="387df-139">W powyższym kodzie `x` jest przypisana stała wartość i nigdy nie jest modyfikowana.</span><span class="sxs-lookup"><span data-stu-id="387df-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="387df-140">Można go zadeklarować przy użyciu `const` modyfikatora:</span><span class="sxs-lookup"><span data-stu-id="387df-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="387df-141">Analiza umożliwiająca ustalenie, czy zmienna może być stałą, jest uwzględniana, wymagająca analizy składniowej, stałej analizie wyrażenia inicjatora i analizy przepływu danych, aby upewnić się, że zmienna nigdy nie jest zapisywana.</span><span class="sxs-lookup"><span data-stu-id="387df-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="387df-142">.NET Compiler Platform udostępnia interfejsy API, które ułatwiają wykonywanie tej analizy.</span><span class="sxs-lookup"><span data-stu-id="387df-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="387df-143">Pierwszym krokiem jest utworzenie nowego **analizatora C# z rozwiązaniem kodu** Project.</span><span class="sxs-lookup"><span data-stu-id="387df-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="387df-144">W programie Visual Studio wybierz kolejno pozycje **plik > nowy > projekt...** , aby wyświetlić okno dialogowe Nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="387df-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="387df-145">W obszarze **rozszerzalność > Visual C#** wybierz opcję **Analizator z poprawkami kodu (.NET standard)**.</span><span class="sxs-lookup"><span data-stu-id="387df-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="387df-146">Nadaj projektowi nazwę "**MakeConst**" i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="387df-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="387df-147">Analizator z szablonem poprawki kodu tworzy trzy projekty: jeden zawiera Analizator i poprawkę kodu, drugi jest projektem testu jednostkowego, a trzeci jest projektem VSIX.</span><span class="sxs-lookup"><span data-stu-id="387df-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="387df-148">Domyślny projekt startowy jest projektem VSIX.</span><span class="sxs-lookup"><span data-stu-id="387df-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="387df-149">Naciśnij klawisz <kbd>F5</kbd> , aby uruchomić projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="387df-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="387df-150">Spowoduje to uruchomienie drugiego wystąpienia programu Visual Studio, które załadowało nowy Analizator.</span><span class="sxs-lookup"><span data-stu-id="387df-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="387df-151">Po uruchomieniu analizatora zostanie rozpoczęta druga kopia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="387df-152">Druga kopia używa innej gałęzi rejestru do przechowywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="387df-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="387df-153">Pozwala to na odróżnienie ustawień wizualizacji w dwóch kopiach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="387df-154">Możesz wybrać inny motyw dla eksperymentalnego przebiegu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="387df-155">Ponadto nie należy przeroamingować ustawień ani zalogować się do konta programu Visual Studio przy użyciu eksperymentalnego przebiegu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="387df-156">Te ustawienia są inne.</span><span class="sxs-lookup"><span data-stu-id="387df-156">That keeps the settings different.</span></span>

<span data-ttu-id="387df-157">W drugim wystąpieniu programu Visual Studio, które właśnie zostało uruchomione, Utwórz nowy projekt aplikacji konsolowej w języku C# (projekt platformy .NET Core lub .NET Framework będzie działać — analizatory pracują na poziomie źródła). Umieść kursor nad tokenem podkreślonym linią falistą i pojawi się tekst ostrzegawczy podany przez analizator.</span><span class="sxs-lookup"><span data-stu-id="387df-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="387df-158">Szablon tworzy Analizator, który raportuje Ostrzeżenie dla każdej deklaracji typu, gdzie nazwa typu zawiera małe litery, jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="387df-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Ostrzeżenie dotyczące raportowania analizatora](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="387df-160">Szablon zawiera również poprawkę kodu, która zmienia nazwę dowolnego typu zawierającego małe litery na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="387df-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="387df-161">Możesz kliknąć ikonę żarówki wyświetlaną z ostrzeżeniem, aby zobaczyć sugerowane zmiany.</span><span class="sxs-lookup"><span data-stu-id="387df-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="387df-162">Zaakceptowanie sugerowanych zmian aktualizuje nazwę typu i wszystkie odwołania do tego typu w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="387df-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="387df-163">Teraz, gdy już widzisz początkową analizator w działaniu, Zamknij drugie wystąpienie programu Visual Studio i wróć do projektu analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="387df-164">Nie trzeba rozpoczynać drugiej kopii programu Visual Studio i utworzyć nowego kodu do testowania każdej zmiany w analizatorze.</span><span class="sxs-lookup"><span data-stu-id="387df-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="387df-165">Szablon tworzy również projekt testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="387df-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="387df-166">Ten projekt zawiera dwa testy.</span><span class="sxs-lookup"><span data-stu-id="387df-166">That project contains two tests.</span></span> <span data-ttu-id="387df-167">`TestMethod1`pokazuje typowy format testu, który analizuje kod bez wyzwalania diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="387df-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="387df-168">`TestMethod2`pokazuje format testu, który wyzwala diagnostykę, a następnie stosuje sugerowaną poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="387df-169">Podczas kompilowania analizatora i poprawki kodu należy napisać testy dla różnych struktur kodu w celu zweryfikowania pracy.</span><span class="sxs-lookup"><span data-stu-id="387df-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="387df-170">Testy jednostkowe dla analizatorów są znacznie szybsze niż testowanie ich interaktywnie przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="387df-171">Testy jednostkowe analizatora są doskonałym narzędziem, gdy wiesz, jakie konstrukcje kodu powinny być i nie powinny wyzwalać analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="387df-172">Ładowanie analizatora w innej kopii programu Visual Studio to doskonałe narzędzie do eksplorowania i znajdowania konstrukcji, które nie zostały jeszcze przemyślane.</span><span class="sxs-lookup"><span data-stu-id="387df-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="387df-173">Tworzenie rejestracji analizatora</span><span class="sxs-lookup"><span data-stu-id="387df-173">Create analyzer registrations</span></span>

<span data-ttu-id="387df-174">Szablon tworzy klasę początkową `DiagnosticAnalyzer` w pliku **MakeConstAnalyzer.cs** .</span><span class="sxs-lookup"><span data-stu-id="387df-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="387df-175">Ta początkowa Analizator przedstawia dwie ważne właściwości każdej analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="387df-176">Każdy Analizator diagnostyki musi dostarczyć `[DiagnosticAnalyzer]` atrybut opisujący język, w którym działa.</span><span class="sxs-lookup"><span data-stu-id="387df-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="387df-177">Każdy Analizator diagnostyki musi być pochodną <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> klasy.</span><span class="sxs-lookup"><span data-stu-id="387df-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="387df-178">Szablon zawiera również podstawowe funkcje, które są częścią dowolnego analizatora:</span><span class="sxs-lookup"><span data-stu-id="387df-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="387df-179">Rejestrowanie akcji.</span><span class="sxs-lookup"><span data-stu-id="387df-179">Register actions.</span></span> <span data-ttu-id="387df-180">Akcje reprezentują zmiany kodu, które powinny spowodować, że analizator sprawdzi kod pod kątem naruszeń.</span><span class="sxs-lookup"><span data-stu-id="387df-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="387df-181">Gdy program Visual Studio wykrywa edycje kodu pasujące do zarejestrowanej akcji, wywołuje zarejestrowaną metodę analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="387df-182">Tworzenie diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="387df-182">Create diagnostics.</span></span> <span data-ttu-id="387df-183">Po wykryciu naruszenia przez analizatora powstaje obiekt diagnostyczny używany przez program Visual Studio do powiadamiania użytkownika o naruszeniu.</span><span class="sxs-lookup"><span data-stu-id="387df-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="387df-184">Akcje można rejestrować w zastąpieniu <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="387df-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="387df-185">W tym samouczku zostaną odwiedzane **węzły składni** szukające lokalnych deklaracji i zobacz, które z nich mają stałe wartości.</span><span class="sxs-lookup"><span data-stu-id="387df-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="387df-186">Jeśli deklaracja może być stała, Analizator utworzy i zgłosi diagnostykę.</span><span class="sxs-lookup"><span data-stu-id="387df-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="387df-187">Pierwszym krokiem jest zaktualizowanie stałych rejestracji i `Initialize` metody, aby te stałe wskazywały Analizator "Make const".</span><span class="sxs-lookup"><span data-stu-id="387df-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="387df-188">Większość stałych ciągów jest zdefiniowana w pliku zasobów ciągu.</span><span class="sxs-lookup"><span data-stu-id="387df-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="387df-189">Należy postępować zgodnie z tym rozwiązaniem, aby ułatwić lokalizację.</span><span class="sxs-lookup"><span data-stu-id="387df-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="387df-190">Otwórz plik **resources. resx** dla projektu analizatora **MakeConst** .</span><span class="sxs-lookup"><span data-stu-id="387df-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="387df-191">Spowoduje to wyświetlenie edytora zasobów.</span><span class="sxs-lookup"><span data-stu-id="387df-191">This displays the resource editor.</span></span> <span data-ttu-id="387df-192">Zaktualizuj zasoby ciągu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="387df-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="387df-193">Zmiana `AnalyzerTitle` na "zmienna może być stała".</span><span class="sxs-lookup"><span data-stu-id="387df-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="387df-194">Zmień `AnalyzerMessageFormat` na "może to być stała".</span><span class="sxs-lookup"><span data-stu-id="387df-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="387df-195">Zmień `AnalyzerDescription` na "Ustaw stałą".</span><span class="sxs-lookup"><span data-stu-id="387df-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="387df-196">Ponadto Zmień listę rozwijaną **modyfikator dostępu** na `public` .</span><span class="sxs-lookup"><span data-stu-id="387df-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="387df-197">Ułatwia to korzystanie z tych stałych w testach jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="387df-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="387df-198">Po zakończeniu Edytor zasobów powinien wyglądać tak, jak pokazano na ilustracji:</span><span class="sxs-lookup"><span data-stu-id="387df-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizowanie zasobów ciągów](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="387df-200">Pozostałe zmiany znajdują się w pliku analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="387df-201">Otwórz **MakeConstAnalyzer.cs** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="387df-202">Zmień zarejestrowanej akcji z jednej, która działa w symbolach na jeden, który działa w składni.</span><span class="sxs-lookup"><span data-stu-id="387df-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="387df-203">W `MakeConstAnalyzerAnalyzer.Initialize` metodzie Znajdź wiersz, który rejestruje akcję na symbole:</span><span class="sxs-lookup"><span data-stu-id="387df-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="387df-204">Zastąp go następującym wierszem:</span><span class="sxs-lookup"><span data-stu-id="387df-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="387df-205">Po tej zmianie można usunąć `AnalyzeSymbol` metodę.</span><span class="sxs-lookup"><span data-stu-id="387df-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="387df-206">Ten Analizator analizuje <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> , nie <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> instrukcje.</span><span class="sxs-lookup"><span data-stu-id="387df-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="387df-207">Zwróć uwagę, że `AnalyzeNode` w tym kolorze czerwona jest zygzakowata.</span><span class="sxs-lookup"><span data-stu-id="387df-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="387df-208">Właśnie dodany kod odwołuje się do `AnalyzeNode` metody, która nie została zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="387df-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="387df-209">Zadeklaruj tę metodę przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="387df-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="387df-210">Zmień `Category` na "użycie" w **MakeConstAnalyzer.cs** , jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="387df-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="387df-211">Znajdowanie lokalnych deklaracji, które mogą być stałe</span><span class="sxs-lookup"><span data-stu-id="387df-211">Find local declarations that could be const</span></span>

<span data-ttu-id="387df-212">Czas zapisywania pierwszej wersji `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="387df-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="387df-213">Należy szukać pojedynczej deklaracji lokalnej, która może być `const` , ale nie jest, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="387df-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="387df-214">Pierwszym krokiem jest znalezienie lokalnych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="387df-214">The first step is to find local declarations.</span></span> <span data-ttu-id="387df-215">Dodaj następujący kod do `AnalyzeNode` programu w programie **MakeConstAnalyzer.cs**:</span><span class="sxs-lookup"><span data-stu-id="387df-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="387df-216">To rzutowanie zawsze powiedzie się, ponieważ Analizator zarejestrował się pod kątem zmian lokalnych deklaracji i tylko deklaracji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="387df-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="387df-217">Żaden inny typ węzła nie wyzwala wywołania `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="387df-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="387df-218">Następnie sprawdź, czy deklaracja ma dowolne `const` modyfikatory.</span><span class="sxs-lookup"><span data-stu-id="387df-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="387df-219">Jeśli je znajdziesz, zwróć natychmiast.</span><span class="sxs-lookup"><span data-stu-id="387df-219">If you find them, return immediately.</span></span> <span data-ttu-id="387df-220">Poniższy kod szuka `const` modyfikatorów w deklaracji lokalnej:</span><span class="sxs-lookup"><span data-stu-id="387df-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="387df-221">Na koniec należy sprawdzić, czy zmienna może być `const` .</span><span class="sxs-lookup"><span data-stu-id="387df-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="387df-222">Oznacza to, że nigdy nie jest przypisywany po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="387df-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="387df-223">Przeprowadzasz analizę semantyki przy użyciu <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> .</span><span class="sxs-lookup"><span data-stu-id="387df-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="387df-224">Użyj argumentu, `context` Aby określić, czy można wykonać deklarację zmiennej lokalnej `const` .</span><span class="sxs-lookup"><span data-stu-id="387df-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="387df-225"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>Reprezentuje wszystkie informacje semantyczne w jednym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="387df-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="387df-226">Więcej informacji można znaleźć w artykule obejmującym [modele semantyczne](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="387df-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="387df-227">Będziesz używać <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> do przeprowadzania analizy przepływu danych w lokalnej instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="387df-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="387df-228">Następnie użyj wyników tej analizy przepływu danych, aby upewnić się, że zmienna lokalna nie jest zapisywana z nową wartością w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="387df-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="387df-229">Wywołaj <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodę rozszerzenia, aby pobrać <xref:Microsoft.CodeAnalysis.ILocalSymbol> dla zmiennej i sprawdź, czy nie jest ona zawarta w <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> kolekcji analizy przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="387df-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="387df-230">Dodaj następujący kod na końcu `AnalyzeNode` metody:</span><span class="sxs-lookup"><span data-stu-id="387df-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="387df-231">Właśnie dodany kod gwarantuje, że zmienna nie jest modyfikowana i w związku z tym może zostać wykonana `const` .</span><span class="sxs-lookup"><span data-stu-id="387df-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="387df-232">Czas na podniesienie poziomu diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="387df-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="387df-233">Dodaj następujący kod jako ostatni wiersz w `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="387df-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="387df-234">Możesz sprawdzić postęp, naciskając klawisz <kbd>F5</kbd> , aby uruchomić Analizator.</span><span class="sxs-lookup"><span data-stu-id="387df-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="387df-235">Możesz załadować utworzoną wcześniej aplikację konsolową, a następnie dodać następujący kod testu:</span><span class="sxs-lookup"><span data-stu-id="387df-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="387df-236">Powinna zostać wyświetlona Żarówka, a Analizator powinien zgłosić diagnostykę.</span><span class="sxs-lookup"><span data-stu-id="387df-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="387df-237">Jednak żarówka nadal korzysta z wygenerowanej przez szablon poprawki kodu i informuje o tym, że można ją wielką literą.</span><span class="sxs-lookup"><span data-stu-id="387df-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="387df-238">W następnej sekcji wyjaśniono, jak napisać poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="387df-239">Napisz poprawkę kodu</span><span class="sxs-lookup"><span data-stu-id="387df-239">Write the code fix</span></span>

<span data-ttu-id="387df-240">Analizator może dostarczyć co najmniej jedną poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="387df-241">Poprawka kodu definiuje edycję, która dotyczy zgłoszonego problemu.</span><span class="sxs-lookup"><span data-stu-id="387df-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="387df-242">Dla utworzonej analizatora można podać poprawkę kodu, która wstawia słowo kluczowe const:</span><span class="sxs-lookup"><span data-stu-id="387df-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="387df-243">Użytkownik wybiera go z poziomu interfejsu użytkownika żarówki w edytorze, a program Visual Studio zmieni kod.</span><span class="sxs-lookup"><span data-stu-id="387df-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="387df-244">Otwórz plik **MakeConstCodeFixProvider.cs** dodany przez szablon.</span><span class="sxs-lookup"><span data-stu-id="387df-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="387df-245">Ta poprawka kodu jest już przewodowa do identyfikatora diagnostyki utworzonego przez analizatora diagnostycznego, ale nie implementuje jeszcze odpowiedniego przekształcenia kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="387df-246">Najpierw należy usunąć część kodu szablonu.</span><span class="sxs-lookup"><span data-stu-id="387df-246">First you should remove some of the template code.</span></span> <span data-ttu-id="387df-247">Zmień ciąg tytułu na "Ustaw stałą":</span><span class="sxs-lookup"><span data-stu-id="387df-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="387df-248">Następnie usuń `MakeUppercaseAsync` metodę.</span><span class="sxs-lookup"><span data-stu-id="387df-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="387df-249">Nie ma już zastosowania.</span><span class="sxs-lookup"><span data-stu-id="387df-249">It no longer applies.</span></span>

<span data-ttu-id="387df-250">Wszyscy dostawcy poprawek kodu pochodzą z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> .</span><span class="sxs-lookup"><span data-stu-id="387df-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="387df-251">Wszystkie przesłonięcia <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> w celu zgłaszania poprawek kodu są dostępne.</span><span class="sxs-lookup"><span data-stu-id="387df-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="387df-252">W programie `RegisterCodeFixesAsync` Zmień typ węzła nadrzędnego, który jest wyszukiwany, aby dopasować go do <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> diagnostyki:</span><span class="sxs-lookup"><span data-stu-id="387df-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="387df-253">Następnie zmień ostatni wiersz, aby zarejestrować poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="387df-254">Poprawka spowoduje utworzenie nowego dokumentu, który skutkuje dodaniem `const` modyfikatora do istniejącej deklaracji:</span><span class="sxs-lookup"><span data-stu-id="387df-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="387df-255">Zobaczysz czerwony zygzak w kodzie, który właśnie został dodany do symbolu `MakeConstAsync` .</span><span class="sxs-lookup"><span data-stu-id="387df-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="387df-256">Dodaj deklarację dla `MakeConstAsync` następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="387df-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="387df-257">Nowa `MakeConstAsync` Metoda przekształca <xref:Microsoft.CodeAnalysis.Document> plik źródłowy użytkownika w nową <xref:Microsoft.CodeAnalysis.Document> , która teraz zawiera `const` deklarację.</span><span class="sxs-lookup"><span data-stu-id="387df-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="387df-258">Należy utworzyć nowy `const` token słowa kluczowego do wstawienia na początku instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="387df-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="387df-259">Należy zachować ostrożność, aby najpierw usunąć wszystkie wiodące kwizy z pierwszego tokenu instrukcji deklaracji i dołączyć je do `const` tokenu.</span><span class="sxs-lookup"><span data-stu-id="387df-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="387df-260">Dodaj następujący kod do metody `MakeConstAsync`:</span><span class="sxs-lookup"><span data-stu-id="387df-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="387df-261">Następnie Dodaj `const` token do deklaracji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="387df-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="387df-262">Następnie sformatuj nową deklarację pod kątem zgodności z regułami formatowania języka C#.</span><span class="sxs-lookup"><span data-stu-id="387df-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="387df-263">Formatowanie zmian pod kątem zgodności z istniejącym kodem powoduje utworzenie lepszego środowiska.</span><span class="sxs-lookup"><span data-stu-id="387df-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="387df-264">Dodaj następującą instrukcję bezpośrednio po istniejącym kodzie:</span><span class="sxs-lookup"><span data-stu-id="387df-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="387df-265">Dla tego kodu jest wymagana Nowa przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="387df-265">A new namespace is required for this code.</span></span> <span data-ttu-id="387df-266">Dodaj następującą `using` dyrektywę na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="387df-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="387df-267">Ostatnim krokiem jest dokonanie edycji.</span><span class="sxs-lookup"><span data-stu-id="387df-267">The final step is to make your edit.</span></span> <span data-ttu-id="387df-268">Ten proces obejmuje trzy kroki:</span><span class="sxs-lookup"><span data-stu-id="387df-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="387df-269">Pobierz uchwyt do istniejącego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="387df-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="387df-270">Utwórz nowy dokument przez zastąpienie istniejącej deklaracji nową deklaracją.</span><span class="sxs-lookup"><span data-stu-id="387df-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="387df-271">Zwróć nowy dokument.</span><span class="sxs-lookup"><span data-stu-id="387df-271">Return the new document.</span></span>

<span data-ttu-id="387df-272">Dodaj następujący kod na końcu `MakeConstAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="387df-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="387df-273">Poprawka kodu jest gotowa do wypróbowania.</span><span class="sxs-lookup"><span data-stu-id="387df-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="387df-274">Naciśnij klawisz <kbd>F5</kbd> , aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="387df-275">W drugim wystąpieniu programu Visual Studio Utwórz nowy projekt aplikacji konsolowej C# i Dodaj kilka lokalnych deklaracji zmiennych, które zostały zainicjowane z użyciem wartości stałych do metody Main.</span><span class="sxs-lookup"><span data-stu-id="387df-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="387df-276">Zobaczysz, że są one raportowane jako ostrzeżenia poniżej.</span><span class="sxs-lookup"><span data-stu-id="387df-276">You'll see that they are reported as warnings as below.</span></span>

![Może wprowadzać ostrzeżenia const](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="387df-278">Wykonano wiele postępów.</span><span class="sxs-lookup"><span data-stu-id="387df-278">You've made a lot of progress.</span></span> <span data-ttu-id="387df-279">W deklaracji, które mogą zostać wykonane, znajdują się tutaj `const` .</span><span class="sxs-lookup"><span data-stu-id="387df-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="387df-280">Jednak nadal działa.</span><span class="sxs-lookup"><span data-stu-id="387df-280">But there is still work to do.</span></span> <span data-ttu-id="387df-281">Jest to dobre rozwiązanie, jeśli dodasz `const` do deklaracji zaczynających się od `i` , then `j` i finally `k` .</span><span class="sxs-lookup"><span data-stu-id="387df-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="387df-282">Ale w przypadku dodania `const` modyfikatora w innej kolejności, rozpoczynając od `k` , Analizator tworzy błędy: `k` nie można zadeklarować `const` , chyba że `i` i `j` są one jednocześnie `const` .</span><span class="sxs-lookup"><span data-stu-id="387df-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="387df-283">W celu zapewnienia obsługi różnych zmiennych można zadeklarować i zainicjować więcej możliwości analizy.</span><span class="sxs-lookup"><span data-stu-id="387df-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="387df-284">Tworzenie testów opartych na danych</span><span class="sxs-lookup"><span data-stu-id="387df-284">Build data driven tests</span></span>

<span data-ttu-id="387df-285">Analizator i poprawka kodu działają w prostym przypadku pojedynczej deklaracji, która może być poddana stałej.</span><span class="sxs-lookup"><span data-stu-id="387df-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="387df-286">Istnieje wiele możliwych instrukcji deklaracji, w których ta implementacja wprowadza błędy.</span><span class="sxs-lookup"><span data-stu-id="387df-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="387df-287">Te przypadki są rozwiązywane przez pracę z biblioteką testów jednostkowych zapisaną przez szablon.</span><span class="sxs-lookup"><span data-stu-id="387df-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="387df-288">Jest to znacznie szybsze niż Wielokrotne otwieranie drugiej kopii programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="387df-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="387df-289">Otwórz plik **MakeConstUnitTests.cs** w projekcie testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="387df-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="387df-290">Szablon utworzył dwa testy, które są zgodne z dwoma typowymi wzorcami w celu sprawdzenia, czy kod naprawi test jednostkowy.</span><span class="sxs-lookup"><span data-stu-id="387df-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="387df-291">`TestMethod1`pokazuje wzorzec dla testu, który gwarantuje, że analizator nie raportuje diagnostyki, gdy nie powinien.</span><span class="sxs-lookup"><span data-stu-id="387df-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="387df-292">`TestMethod2`pokazuje wzorzec zgłaszania diagnostyki i uruchamiania poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="387df-293">Kod prawie każdego testu dla analizatora jest zgodny z jednym z tych dwóch wzorców.</span><span class="sxs-lookup"><span data-stu-id="387df-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="387df-294">W pierwszym kroku można wykonać te testy jako testy oparte na danych.</span><span class="sxs-lookup"><span data-stu-id="387df-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="387df-295">Następnie można łatwo utworzyć nowe testy przez dodanie nowych stałych ciągów, aby reprezentować różne dane wejściowe testu.</span><span class="sxs-lookup"><span data-stu-id="387df-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="387df-296">W celu uzyskania skuteczności pierwszy krok polega na refaktoryzacji dwóch testów w testach opartych na danych.</span><span class="sxs-lookup"><span data-stu-id="387df-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="387df-297">Następnie wystarczy zdefiniować tylko kilka ciągów stałych dla każdego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="387df-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="387df-298">Podczas refaktoryzacji Zmień nazwy obu tych metod na lepsze.</span><span class="sxs-lookup"><span data-stu-id="387df-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="387df-299">Zamień `TestMethod1` na ten test, który gwarantuje, że nie zostanie zgłoszona żadna Diagnostyka:</span><span class="sxs-lookup"><span data-stu-id="387df-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="387df-300">Można utworzyć nowy wiersz danych dla tego testu przez zdefiniowanie dowolnego fragmentu kodu, który nie powinien powodować wyzwalania ostrzeżenia przez diagnostykę.</span><span class="sxs-lookup"><span data-stu-id="387df-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="387df-301">To Przeciążenie `VerifyCSharpDiagnostic` przebiega w przypadku braku wyzwalanej diagnostyki dla fragmentu kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="387df-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="387df-302">Następnie zastąp ciąg `TestMethod2` tym testem, który zapewnia podniesienie poziomu diagnostyki i zastosowanie poprawki kodu do fragmentu kodu źródłowego:</span><span class="sxs-lookup"><span data-stu-id="387df-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="387df-303">Poprzedni kod również wprowadził kilka zmian w kodzie, który kompiluje oczekiwany wynik diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="387df-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="387df-304">Używa on publicznych stałych zarejestrowanych w `MakeConst` analizatorze.</span><span class="sxs-lookup"><span data-stu-id="387df-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="387df-305">Ponadto używa dwóch stałych ciągów dla źródła danych wejściowych i stałych.</span><span class="sxs-lookup"><span data-stu-id="387df-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="387df-306">Dodaj następujące stałe ciągów do `UnitTest` klasy:</span><span class="sxs-lookup"><span data-stu-id="387df-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="387df-307">Uruchom te dwa testy, aby upewnić się, że są one przekazywane.</span><span class="sxs-lookup"><span data-stu-id="387df-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="387df-308">W programie Visual Studio Otwórz **Eksploratora testów** , wybierając kolejno pozycje **Testuj**  >  Eksplorator testów**systemu Windows**  >  **Test Explorer**.</span><span class="sxs-lookup"><span data-stu-id="387df-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="387df-309">Następnie wybierz łącze **Uruchom wszystko** .</span><span class="sxs-lookup"><span data-stu-id="387df-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="387df-310">Utwórz testy dla prawidłowych deklaracji</span><span class="sxs-lookup"><span data-stu-id="387df-310">Create tests for valid declarations</span></span>

<span data-ttu-id="387df-311">Zgodnie z ogólną zasadą analizatory powinny zakończyć się tak szybko, jak to możliwe, wykonując minimalną pracę.</span><span class="sxs-lookup"><span data-stu-id="387df-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="387df-312">Program Visual Studio wywołuje zarejestrowane analizatory, gdy użytkownik edytuje kod.</span><span class="sxs-lookup"><span data-stu-id="387df-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="387df-313">Czas odpowiedzi jest wymaganym kluczem.</span><span class="sxs-lookup"><span data-stu-id="387df-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="387df-314">Istnieje kilka przypadków testowych dla kodu, który nie powinien podnieść danych diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="387df-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="387df-315">Analizator już obsługuje jeden z tych testów, przypadek, w którym zmienna jest przypisywana po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="387df-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="387df-316">Dodaj następującą stałą ciągu do testów, aby reprezentować ten przypadek:</span><span class="sxs-lookup"><span data-stu-id="387df-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="387df-317">Następnie Dodaj wiersz danych dla tego testu, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="387df-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="387df-318">Ten test również kończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="387df-318">This test passes as well.</span></span> <span data-ttu-id="387df-319">Następnie Dodaj stałe dla warunków, które nie zostały jeszcze obsłużone:</span><span class="sxs-lookup"><span data-stu-id="387df-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="387df-320">Deklaracje, które są już `const` stałe:</span><span class="sxs-lookup"><span data-stu-id="387df-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="387df-321">Deklaracje, które nie mają inicjatora, ponieważ nie ma wartości do użycia:</span><span class="sxs-lookup"><span data-stu-id="387df-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="387df-322">Deklaracje, w których inicjator nie jest stałą, ponieważ nie mogą być stałymi czasu kompilacji:</span><span class="sxs-lookup"><span data-stu-id="387df-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="387df-323">Może być jeszcze bardziej skomplikowany, ponieważ C# umożliwia stosowanie wielu deklaracji jako jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="387df-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="387df-324">Rozważmy następującą stałą ciągu przypadku testowego:</span><span class="sxs-lookup"><span data-stu-id="387df-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="387df-325">Zmienna `i` może być stałą, ale zmienna `j` nie może.</span><span class="sxs-lookup"><span data-stu-id="387df-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="387df-326">W związku z tym nie można wykonać tej instrukcji jako deklaracji const.</span><span class="sxs-lookup"><span data-stu-id="387df-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="387df-327">Dodaj `DataRow` deklaracje dla wszystkich tych testów:</span><span class="sxs-lookup"><span data-stu-id="387df-327">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="387df-328">Uruchom testy ponownie i zobaczysz, że te nowe przypadki testowe zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="387df-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="387df-329">Aktualizowanie analizatora w celu ignorowania prawidłowych deklaracji</span><span class="sxs-lookup"><span data-stu-id="387df-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="387df-330">Aby `AnalyzeNode` odfiltrować kod, który spełnia te warunki, potrzebne są pewne ulepszenia metody analizatora.</span><span class="sxs-lookup"><span data-stu-id="387df-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="387df-331">Są to wszystkie powiązane warunki, więc podobne zmiany spowodują naprawienie wszystkich tych warunków.</span><span class="sxs-lookup"><span data-stu-id="387df-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="387df-332">Wprowadź następujące zmiany `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="387df-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="387df-333">Analiza semantyczna zbadała deklarację pojedynczej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="387df-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="387df-334">Ten kod musi znajdować się w `foreach` pętli, która bada wszystkie zmienne zadeklarowane w tej samej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="387df-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="387df-335">Każda zadeklarowana zmienna musi mieć inicjator.</span><span class="sxs-lookup"><span data-stu-id="387df-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="387df-336">Każdy zadeklarowany inicjator zmiennej musi być stałą czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="387df-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="387df-337">W `AnalyzeNode` metodzie Zastąp pierwotną analizę semantyczną:</span><span class="sxs-lookup"><span data-stu-id="387df-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="387df-338">z poniższym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="387df-338">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="387df-339">Pierwsza `foreach` Pętla analizuje każdą deklarację zmiennej przy użyciu analizy składni.</span><span class="sxs-lookup"><span data-stu-id="387df-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="387df-340">Pierwsze sprawdzenie gwarantuje, że zmienna ma inicjator.</span><span class="sxs-lookup"><span data-stu-id="387df-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="387df-341">Druga kontrola gwarantuje, że inicjator jest stałą.</span><span class="sxs-lookup"><span data-stu-id="387df-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="387df-342">Druga pętla ma pierwotną analizę semantyczną.</span><span class="sxs-lookup"><span data-stu-id="387df-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="387df-343">Testy semantyczne znajdują się w osobnej pętli, ponieważ ma ona większy wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="387df-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="387df-344">Uruchom testy ponownie, a wszystkie powinny być widoczne.</span><span class="sxs-lookup"><span data-stu-id="387df-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="387df-345">Dodaj końcowy Polski</span><span class="sxs-lookup"><span data-stu-id="387df-345">Add the final polish</span></span>

<span data-ttu-id="387df-346">To już prawie koniec.</span><span class="sxs-lookup"><span data-stu-id="387df-346">You're almost done.</span></span> <span data-ttu-id="387df-347">Aby Analizator mógł obsłużyć kilka dodatkowych warunków.</span><span class="sxs-lookup"><span data-stu-id="387df-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="387df-348">Program Visual Studio wywołuje analizatory podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="387df-349">Często zdarza się, że analizator zostanie wywołany dla kodu, który nie kompiluje.</span><span class="sxs-lookup"><span data-stu-id="387df-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="387df-350">Metoda analizatora diagnostyki nie `AnalyzeNode` sprawdza, czy wartość stała jest możliwa do przekonwertowania na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="387df-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="387df-351">Dlatego bieżąca implementacja Happily konwersję niepoprawnej deklaracji, takiej jak int i = "ABC", na stałą lokalną.</span><span class="sxs-lookup"><span data-stu-id="387df-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="387df-352">Dodaj stałą wartość ciągu źródłowego dla tego warunku:</span><span class="sxs-lookup"><span data-stu-id="387df-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="387df-353">Ponadto typy odwołań nie są prawidłowo obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="387df-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="387df-354">Jedyną wartością stałą dozwoloną dla typu referencyjnego jest `null` , z wyjątkiem tego <xref:System.String?displayProperty=nameWithType> , który umożliwia literały ciągu.</span><span class="sxs-lookup"><span data-stu-id="387df-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="387df-355">Innymi słowy, `const string s = "abc"` jest to dozwolone, ale `const object s = "abc"` nie jest.</span><span class="sxs-lookup"><span data-stu-id="387df-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="387df-356">Ten fragment kodu weryfikuje ten warunek:</span><span class="sxs-lookup"><span data-stu-id="387df-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="387df-357">Aby upewnić się, że musisz dodać kolejny test, aby mieć pewność, że można utworzyć deklarację stałą dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="387df-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="387df-358">Poniższy fragment kodu definiuje kod, który wywołuje diagnostykę, i kod po zastosowaniu poprawki:</span><span class="sxs-lookup"><span data-stu-id="387df-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="387df-359">Na koniec Jeśli zmienna jest zadeklarowana za pomocą `var` słowa kluczowego, Poprawka kodu robi niewłaściwe i generuje `const var` deklarację, która nie jest obsługiwana przez język C#.</span><span class="sxs-lookup"><span data-stu-id="387df-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="387df-360">Aby naprawić ten błąd, Poprawka kodu musi zastąpić `var` słowo kluczowe nazwą wywnioskowanego typu:</span><span class="sxs-lookup"><span data-stu-id="387df-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="387df-361">Te zmiany aktualizują deklaracje wiersza danych dla obu testów.</span><span class="sxs-lookup"><span data-stu-id="387df-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="387df-362">Poniższy kod przedstawia te testy ze wszystkimi atrybutami wiersza danych:</span><span class="sxs-lookup"><span data-stu-id="387df-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="387df-363">Na szczęście wszystkie powyższe usterki mogą być rozwiązywane przy użyciu tych samych metod, które zostały już zapamiętane.</span><span class="sxs-lookup"><span data-stu-id="387df-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="387df-364">Aby naprawić pierwszy błąd, najpierw Otwórz **DiagnosticAnalyzer.cs** i Znajdź pętlę Foreach, w której jest sprawdzana każda z inicjatorów deklaracji lokalnej, aby upewnić się, że są one przypisane do wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="387df-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="387df-365">Bezpośrednio _przed_ pierwszą pętlą foreach należy wywołać, `context.SemanticModel.GetTypeInfo()` Aby uzyskać szczegółowe informacje na temat zadeklarowanego typu deklaracji lokalnej:</span><span class="sxs-lookup"><span data-stu-id="387df-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="387df-366">Następnie w `foreach` pętli Sprawdź każdy inicjator, aby upewnić się, że jest on konwertowany na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="387df-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="387df-367">Po upewnieniu się, że inicjator jest stałą, należy dodać następujące sprawdzenie:</span><span class="sxs-lookup"><span data-stu-id="387df-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="387df-368">Następna zmiana jest oparta na ostatnim.</span><span class="sxs-lookup"><span data-stu-id="387df-368">The next change builds upon the last one.</span></span> <span data-ttu-id="387df-369">Przed zamykającym nawiasem klamrowym pierwszej pętli Foreach Dodaj następujący kod, aby sprawdzić typ deklaracji lokalnej, gdy stała jest ciągiem lub wartością null.</span><span class="sxs-lookup"><span data-stu-id="387df-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="387df-370">Aby zamienić słowo kluczowe var na poprawną nazwę typu, należy napisać nieco więcej kodu w ramach dostawcy poprawek kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-370">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="387df-371">Wróć do **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="387df-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="387df-372">Kod, który dodasz, wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="387df-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="387df-373">Sprawdź, czy deklaracja jest `var` deklaracją, a jeśli jest:</span><span class="sxs-lookup"><span data-stu-id="387df-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="387df-374">Utwórz nowy typ dla wnioskowanego typu.</span><span class="sxs-lookup"><span data-stu-id="387df-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="387df-375">Upewnij się, że deklaracja typu nie jest aliasem.</span><span class="sxs-lookup"><span data-stu-id="387df-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="387df-376">Jeśli tak, można zadeklarować `const var` .</span><span class="sxs-lookup"><span data-stu-id="387df-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="387df-377">Upewnij się, że `var` nie jest to nazwa typu w tym programie.</span><span class="sxs-lookup"><span data-stu-id="387df-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="387df-378">(Jeśli tak, `const var` jest to dozwolone).</span><span class="sxs-lookup"><span data-stu-id="387df-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="387df-379">Uprość pełną nazwę typu</span><span class="sxs-lookup"><span data-stu-id="387df-379">Simplify the full type name</span></span>

<span data-ttu-id="387df-380">Dźwięki takie jak wiele kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-380">That sounds like a lot of code.</span></span> <span data-ttu-id="387df-381">Nie jest.</span><span class="sxs-lookup"><span data-stu-id="387df-381">It's not.</span></span> <span data-ttu-id="387df-382">Zastąp wiersz, który deklaruje i inicjuje `newLocal` z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="387df-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="387df-383">Przechodzi natychmiast po zainicjowaniu `newModifiers` :</span><span class="sxs-lookup"><span data-stu-id="387df-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="387df-384">Musisz dodać jedną `using` dyrektywę, aby użyć <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> typu:</span><span class="sxs-lookup"><span data-stu-id="387df-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="387df-385">Uruchom testy i wszystkie powinny być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="387df-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="387df-386">Congratulate siebie, uruchamiając gotowy Analizator.</span><span class="sxs-lookup"><span data-stu-id="387df-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="387df-387">Naciśnij <kbd>kombinację klawiszy CTRL + F5</kbd> , aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio z załadowanym rozszerzeniem Roslyn Preview.</span><span class="sxs-lookup"><span data-stu-id="387df-387">Press <kbd>Ctrl+F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="387df-388">W drugim wystąpieniu programu Visual Studio Utwórz nowy projekt aplikacji konsolowej C# i Dodaj `int x = "abc";` go do metody Main.</span><span class="sxs-lookup"><span data-stu-id="387df-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="387df-389">Z powodu pierwszej poprawki błędów nie należy podawać ostrzeżenia dla tej deklaracji zmiennej lokalnej (chociaż występuje błąd kompilatora w oczekiwany sposób).</span><span class="sxs-lookup"><span data-stu-id="387df-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="387df-390">Następnie Dodaj `object s = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="387df-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="387df-391">Ze względu na drugą poprawkę błędu nie należy podawać ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="387df-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="387df-392">Na koniec Dodaj kolejną zmienną lokalną, która używa `var` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="387df-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="387df-393">Zobaczysz, że zostało zgłoszone ostrzeżenie i pojawi się sugestia poniżej lewej strony.</span><span class="sxs-lookup"><span data-stu-id="387df-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="387df-394">Przenieś karetkę edytora na falistej podkreślenie i naciśnij <kbd>klawisze CTRL +</kbd>.</span><span class="sxs-lookup"><span data-stu-id="387df-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl+</kbd>.</span></span> <span data-ttu-id="387df-395">Aby wyświetlić sugerowaną poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="387df-395">to display the suggested code fix.</span></span> <span data-ttu-id="387df-396">Po wybraniu poprawki kodu należy zauważyć, że słowo kluczowe var jest teraz prawidłowo obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="387df-396">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="387df-397">Na koniec Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="387df-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="387df-398">Po wprowadzeniu tych zmian otrzymujesz czerwoną literę tylko dla pierwszych dwóch zmiennych.</span><span class="sxs-lookup"><span data-stu-id="387df-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="387df-399">Dodaj `const` do obu `i` i i `j` Otrzymuj nowe ostrzeżenie, `k` ponieważ teraz może być `const` .</span><span class="sxs-lookup"><span data-stu-id="387df-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="387df-400">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="387df-400">Congratulations!</span></span> <span data-ttu-id="387df-401">Zostało utworzone pierwsze rozszerzenie .NET Compiler Platform, które wykonuje analizę kodu na bieżąco w celu wykrywania problemu i zawiera szybką poprawkę, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="387df-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="387df-402">W ten sposób poznasz wiele interfejsów API kodu, które są częścią zestawu SDK .NET Compiler Platform (Roslyn interfejsy API).</span><span class="sxs-lookup"><span data-stu-id="387df-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="387df-403">Możesz sprawdzić, czy pracujesz z [ukończonym przykładem](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) w naszym repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="387df-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="387df-404">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="387df-404">Other resources</span></span>

- [<span data-ttu-id="387df-405">Wprowadzenie do analizy składni</span><span class="sxs-lookup"><span data-stu-id="387df-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="387df-406">Wprowadzenie do analizy semantycznej</span><span class="sxs-lookup"><span data-stu-id="387df-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
