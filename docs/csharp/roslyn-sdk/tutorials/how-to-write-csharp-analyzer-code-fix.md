---
title: 'Samouczek: Napisz swój pierwszy analizator i naprawić kod'
description: Ten samouczek zawiera instrukcje krok po kroku do tworzenia analizatora i poprawki kodu przy użyciu zestawu SDK kompilatora .NET (Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240553"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="4e955-103">Samouczek: Napisz swój pierwszy analizator i naprawić kod</span><span class="sxs-lookup"><span data-stu-id="4e955-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="4e955-104">Zestaw SDK platformy kompilatora .NET udostępnia narzędzia potrzebne do tworzenia niestandardowych ostrzeżeń docelowych kodu C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4e955-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="4e955-105">**Analizator** zawiera kod, który rozpoznaje naruszenia reguły.</span><span class="sxs-lookup"><span data-stu-id="4e955-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="4e955-106">**Poprawka kodu** zawiera kod, który rozwiązuje naruszenie.</span><span class="sxs-lookup"><span data-stu-id="4e955-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="4e955-107">Implementowane reguły mogą być doczdą się od struktury kodu do stylu kodowania do konwencji nazewnictwa i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="4e955-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="4e955-108">Platforma kompilatora .NET zapewnia platformę do uruchamiania analizy, ponieważ deweloperzy piszą kod, a wszystkie funkcje interfejsu użytkownika programu Visual Studio do naprawiania kodu: wyświetlanie squiggles w edytorze, wypełnianie listy błędów programu Visual Studio, tworzenie "żarówki" sugestie i pokazujący bogaty podgląd sugerowanych poprawek.</span><span class="sxs-lookup"><span data-stu-id="4e955-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="4e955-109">W tym samouczku przejrzysz tworzenie **analizatora** i towarzyszącej mu **poprawki kodu** przy użyciu interfejsów API Roslyn.</span><span class="sxs-lookup"><span data-stu-id="4e955-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="4e955-110">Analizator jest sposobem na przeprowadzenie analizy kodu źródłowego i zgłoszenie problemu użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="4e955-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="4e955-111">Opcjonalnie analizator może również podać poprawkę kodu, która reprezentuje modyfikację kodu źródłowego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4e955-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="4e955-112">Ten samouczek tworzy analizator, który znajduje deklaracje zmiennych lokalnych, które mogą być zadeklarowane przy użyciu modyfikatora, `const` ale nie są.</span><span class="sxs-lookup"><span data-stu-id="4e955-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="4e955-113">Załączony kod fix modyfikuje te deklaracje, `const` aby dodać modyfikator.</span><span class="sxs-lookup"><span data-stu-id="4e955-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e955-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4e955-114">Prerequisites</span></span>

- [<span data-ttu-id="4e955-115">Studio wizualne 2017</span><span class="sxs-lookup"><span data-stu-id="4e955-115">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="4e955-116">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4e955-116">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="4e955-117">Musisz zainstalować zestaw **SDK platformy kompilatora .NET** za pośrednictwem Instalatora programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4e955-117">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="4e955-118">Istnieje kilka kroków do tworzenia i sprawdzania poprawności analizatora:</span><span class="sxs-lookup"><span data-stu-id="4e955-118">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="4e955-119">Utwórz rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="4e955-119">Create the solution.</span></span>
1. <span data-ttu-id="4e955-120">Zarejestruj nazwę i opis analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-120">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="4e955-121">Zgłoś ostrzeżenia i zalecenia analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-121">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="4e955-122">Zaimplementuj poprawkę kodu, aby zaakceptować zalecenia.</span><span class="sxs-lookup"><span data-stu-id="4e955-122">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="4e955-123">Usprawnij analizę za pomocą testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="4e955-123">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="4e955-124">Poznaj szablon analizatora</span><span class="sxs-lookup"><span data-stu-id="4e955-124">Explore the analyzer template</span></span>

<span data-ttu-id="4e955-125">Analizator raporty do użytkownika wszelkich deklaracji zmiennych lokalnych, które mogą być konwertowane na stałe lokalne.</span><span class="sxs-lookup"><span data-stu-id="4e955-125">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="4e955-126">Rozważmy na przykład następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4e955-126">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="4e955-127">W powyższym `x` kodzie jest przypisany wartość stała i nigdy nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="4e955-127">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="4e955-128">Można go zadeklarować `const` za pomocą modyfikatora:</span><span class="sxs-lookup"><span data-stu-id="4e955-128">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="4e955-129">Analiza w celu ustalenia, czy zmienna może być stała, wymaga analizy składniowej, stałej analizy wyrażenia inicjatora i analizy przepływu danych w celu zapewnienia, że zmienna nigdy nie jest zapisywana.</span><span class="sxs-lookup"><span data-stu-id="4e955-129">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="4e955-130">Platforma kompilatora .NET udostępnia interfejsy API, które ułatwiają wykonywanie tej analizy.</span><span class="sxs-lookup"><span data-stu-id="4e955-130">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="4e955-131">Pierwszym krokiem jest utworzenie nowego analizatora Języka C# **z projektem poprawki kodu.**</span><span class="sxs-lookup"><span data-stu-id="4e955-131">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="4e955-132">W programie Visual Studio wybierz pozycję **Plik > Nowy > Project...** aby wyświetlić okno dialogowe Nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="4e955-132">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="4e955-133">W **obszarze Visual C# > rozszerzalność**wybierz pozycję **Analizator z poprawką kodu (.NET Standard).**</span><span class="sxs-lookup"><span data-stu-id="4e955-133">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="4e955-134">Nazwij swój projekt "**MakeConst**" i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="4e955-134">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="4e955-135">Analizator z szablonem poprawki kodu tworzy trzy projekty: jeden zawiera analizator i poprawkę kodu, drugi jest projektem testu jednostkowego, a trzeci to projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="4e955-135">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="4e955-136">Domyślnym projektem startowym jest projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="4e955-136">The default startup project is the VSIX project.</span></span> <span data-ttu-id="4e955-137">Naciśnij **klawisz F5,** aby rozpocząć projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="4e955-137">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="4e955-138">Spowoduje to uruchomienie drugiego wystąpienia programu Visual Studio, który załadował nowy analizator.</span><span class="sxs-lookup"><span data-stu-id="4e955-138">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="4e955-139">Po uruchomieniu analizatora należy uruchomić drugą kopię programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-139">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="4e955-140">Ta druga kopia używa innej gałęzi rejestru do przechowywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="4e955-140">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="4e955-141">Umożliwia to odróżnienie ustawień wizualnych w dwóch kopiach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-141">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="4e955-142">Możesz wybrać inny motyw eksperymentalnego przebiegu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-142">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="4e955-143">Ponadto nie wędruj w ustawieniach ani nie loguj się do konta programu Visual Studio przy użyciu eksperymentalnego przebiegu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-143">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="4e955-144">To sprawia, że ustawienia są różne.</span><span class="sxs-lookup"><span data-stu-id="4e955-144">That keeps the settings different.</span></span>

<span data-ttu-id="4e955-145">W drugim wystąpieniu programu Visual Studio, które właśnie zostało uruchomione, utwórz nowy projekt aplikacji konsoli C# (projekt .NET Core lub .NET Framework będzie działać — analizatory działają na poziomie źródłowym). Umieść wskaźnik myszy na tokenie z falistym podkreśleniem, a zostanie wyświetlony tekst ostrzegawczy dostarczony przez analizator.</span><span class="sxs-lookup"><span data-stu-id="4e955-145">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="4e955-146">Szablon tworzy analizator, który zgłasza ostrzeżenie na każdej deklaracji typu, gdzie nazwa typu zawiera małe litery, jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="4e955-146">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Ostrzeżenie o raportowaniu analizatora](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="4e955-148">Szablon zawiera również poprawkę kodu, która zmienia dowolną nazwę typu zawierającą małe litery na wszystkie wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="4e955-148">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="4e955-149">Możesz kliknąć na żarówkę wyświetlaną z ostrzeżeniem, aby zobaczyć sugerowane zmiany.</span><span class="sxs-lookup"><span data-stu-id="4e955-149">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="4e955-150">Zaakceptowanie sugerowanych zmian aktualizuje nazwę typu i wszystkie odwołania do tego typu w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="4e955-150">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="4e955-151">Teraz, gdy widzisz wstępnego analizatora w akcji, zamknij drugie wystąpienie programu Visual Studio i powrót do projektu analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-151">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="4e955-152">Nie trzeba uruchomić drugą kopię programu Visual Studio i utworzyć nowy kod, aby przetestować każdą zmianę w analizatorze.</span><span class="sxs-lookup"><span data-stu-id="4e955-152">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="4e955-153">Szablon tworzy również projekt testu jednostkowego dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="4e955-153">The template also creates a unit test project for you.</span></span> <span data-ttu-id="4e955-154">Ten projekt zawiera dwa testy.</span><span class="sxs-lookup"><span data-stu-id="4e955-154">That project contains two tests.</span></span> <span data-ttu-id="4e955-155">`TestMethod1`pokazuje typowy format testu, który analizuje kod bez wyzwalania diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="4e955-155">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="4e955-156">`TestMethod2`pokazuje format testu, który wyzwala diagnostyki, a następnie stosuje sugerowaną poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-156">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="4e955-157">Podczas tworzenia analizatora i poprawki kodu, napiszesz testy dla różnych struktur kodu, aby zweryfikować swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="4e955-157">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="4e955-158">Testy jednostkowe analizatorów są znacznie szybsze niż testowanie ich interaktywnie za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-158">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="4e955-159">Testy jednostkowe analizatora są doskonałym narzędziem, gdy wiesz, jakie konstrukcje kodu powinny i nie powinny wyzwalać analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-159">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="4e955-160">Ładowanie analizatora w innej kopii programu Visual Studio jest doskonałym narzędziem do eksplorowania i znajdowania konstrukcji, o których jeszcze nie myślałeś.</span><span class="sxs-lookup"><span data-stu-id="4e955-160">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="4e955-161">Tworzenie rejestracji analizatora</span><span class="sxs-lookup"><span data-stu-id="4e955-161">Create analyzer registrations</span></span>

<span data-ttu-id="4e955-162">Szablon tworzy klasę `DiagnosticAnalyzer` początkową w **pliku MakeConstAnalyzer.cs.**</span><span class="sxs-lookup"><span data-stu-id="4e955-162">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="4e955-163">Ten wyjmator początkowy pokazuje dwie ważne właściwości każdego analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-163">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="4e955-164">Każdy analizator diagnostyczny musi zawierać atrybut opisujący `[DiagnosticAnalyzer]` język, na który działa.</span><span class="sxs-lookup"><span data-stu-id="4e955-164">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="4e955-165">Każdy analizator diagnostyczny <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> musi pochodzić z klasy.</span><span class="sxs-lookup"><span data-stu-id="4e955-165">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="4e955-166">Szablon pokazuje również podstawowe funkcje, które są częścią dowolnego analizatora:</span><span class="sxs-lookup"><span data-stu-id="4e955-166">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="4e955-167">Rejestrowanie akcji.</span><span class="sxs-lookup"><span data-stu-id="4e955-167">Register actions.</span></span> <span data-ttu-id="4e955-168">Akcje reprezentują zmiany kodu, które powinny wyzwolić analizator, aby zbadać kod pod kątem naruszeń.</span><span class="sxs-lookup"><span data-stu-id="4e955-168">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="4e955-169">Gdy program Visual Studio wykryje zmiany kodu, które pasują do zarejestrowanej akcji, wywołuje zarejestrowaną metodę analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-169">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="4e955-170">Tworzenie diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="4e955-170">Create diagnostics.</span></span> <span data-ttu-id="4e955-171">Gdy analizator wykryje naruszenie, tworzy obiekt diagnostyczny, który używa programu Visual Studio do powiadamiania użytkownika o naruszeniu.</span><span class="sxs-lookup"><span data-stu-id="4e955-171">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="4e955-172">Rejestrujesz akcje w <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> zastąpiosz metodę.</span><span class="sxs-lookup"><span data-stu-id="4e955-172">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4e955-173">W tym samouczku odwiedzisz **węzły składni** w poszukiwaniu deklaracji lokalnych i zobaczysz, które z nich mają stałe wartości.</span><span class="sxs-lookup"><span data-stu-id="4e955-173">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="4e955-174">Jeśli deklaracja może być stała, analizator utworzy i zgłosi diagnostykę.</span><span class="sxs-lookup"><span data-stu-id="4e955-174">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="4e955-175">Pierwszym krokiem jest zaktualizowanie stałych `Initialize` rejestracji i metody, dzięki czemu te stałe wskazują analizator "Make Const".</span><span class="sxs-lookup"><span data-stu-id="4e955-175">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="4e955-176">Większość stałych ciągu są zdefiniowane w pliku zasobu ciągu.</span><span class="sxs-lookup"><span data-stu-id="4e955-176">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="4e955-177">Należy postępować zgodnie z tą praktyką, aby ułatwić lokalizację.</span><span class="sxs-lookup"><span data-stu-id="4e955-177">You should follow that practice for easier localization.</span></span> <span data-ttu-id="4e955-178">Otwórz plik **Resources.resx** dla projektu analizatora **MakeConst.**</span><span class="sxs-lookup"><span data-stu-id="4e955-178">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="4e955-179">Spowoduje to wyświetlenie edytora zasobów.</span><span class="sxs-lookup"><span data-stu-id="4e955-179">This displays the resource editor.</span></span> <span data-ttu-id="4e955-180">Zaktualizuj zasoby ciągu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4e955-180">Update the string resources as follows:</span></span>

- <span data-ttu-id="4e955-181">Zmień `AnalyzerTitle` na "Zmienna może być stała".</span><span class="sxs-lookup"><span data-stu-id="4e955-181">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="4e955-182">Zmień `AnalyzerMessageFormat` na "Może być stała".</span><span class="sxs-lookup"><span data-stu-id="4e955-182">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="4e955-183">Zmień `AnalyzerDescription` na "Make Constant".</span><span class="sxs-lookup"><span data-stu-id="4e955-183">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="4e955-184">Ponadto zmień **modyfikator dostępu** `public`rozwijanego do .</span><span class="sxs-lookup"><span data-stu-id="4e955-184">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="4e955-185">Ułatwia to używanie tych stałych w testach jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="4e955-185">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="4e955-186">Po zakończeniu edytor zasobów powinien być wyświetlany na rysunku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4e955-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizowanie zasobów ciągu](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="4e955-188">Pozostałe zmiany znajdują się w pliku analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="4e955-189">Otwórz **MakeConstAnalyzer.cs** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-189">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="4e955-190">Zmień zarejestrowaną akcję z akcji, która działa na symbole, na jedną, która działa na składnię.</span><span class="sxs-lookup"><span data-stu-id="4e955-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="4e955-191">W `MakeConstAnalyzerAnalyzer.Initialize` metodzie znajdź wiersz, który rejestruje akcję na symbolach:</span><span class="sxs-lookup"><span data-stu-id="4e955-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="4e955-192">Zamień go na następujący wiersz:</span><span class="sxs-lookup"><span data-stu-id="4e955-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="4e955-193">Po tej zmianie można `AnalyzeSymbol` usunąć metodę.</span><span class="sxs-lookup"><span data-stu-id="4e955-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="4e955-194">Ten analizator <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>bada <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> , nie oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="4e955-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="4e955-195">Zauważ, `AnalyzeNode` że ma czerwone squiggles pod nim.</span><span class="sxs-lookup"><span data-stu-id="4e955-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="4e955-196">Kod, który właśnie `AnalyzeNode` dodał, odwołuje się do metody, która nie została zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="4e955-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="4e955-197">Deklaruj tę metodę przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4e955-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="4e955-198">Zmień `Category` na "Użycie" w **MakeConstAnalyzer.cs,** jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4e955-198">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="4e955-199">Znajdź deklaracje lokalne, które mogą być const</span><span class="sxs-lookup"><span data-stu-id="4e955-199">Find local declarations that could be const</span></span>

<span data-ttu-id="4e955-200">Nadszedł czas, aby napisać pierwszą wersję `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="4e955-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="4e955-201">Należy szukać jednej deklaracji lokalnej, `const` która może być, ale nie jest, jak następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4e955-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="4e955-202">Pierwszym krokiem jest znalezienie deklaracji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="4e955-202">The first step is to find local declarations.</span></span> <span data-ttu-id="4e955-203">Dodaj następujący kod `AnalyzeNode` do **MakeConstAnalyzer.cs:**</span><span class="sxs-lookup"><span data-stu-id="4e955-203">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="4e955-204">Ta rzutowanie zawsze powiedzie się, ponieważ analizator zarejestrowany chwalenie dla zmian deklaracji lokalnych i tylko deklaracje lokalne.</span><span class="sxs-lookup"><span data-stu-id="4e955-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="4e955-205">Żaden inny typ węzła wyzwala `AnalyzeNode` wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="4e955-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="4e955-206">Następnie sprawdź deklarację dla `const` wszystkich modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="4e955-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="4e955-207">Jeśli je znajdziesz, natychmiast wróć.</span><span class="sxs-lookup"><span data-stu-id="4e955-207">If you find them, return immediately.</span></span> <span data-ttu-id="4e955-208">Poniższy kod wyszbędzie żadnych `const` modyfikatorów deklaracji lokalnej:</span><span class="sxs-lookup"><span data-stu-id="4e955-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="4e955-209">Na koniec należy sprawdzić, czy `const`zmienna może być .</span><span class="sxs-lookup"><span data-stu-id="4e955-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="4e955-210">Oznacza to upewnienie się, że nigdy nie jest przypisany po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="4e955-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="4e955-211">Wykonasz analizę semantyczną <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="4e955-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="4e955-212">Argument służy `context` do określenia, czy można złożyć `const`deklarację zmiennej lokalnej .</span><span class="sxs-lookup"><span data-stu-id="4e955-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="4e955-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> reprezentuje wszystkie informacje semantyczne w jednym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="4e955-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="4e955-214">Możesz dowiedzieć się więcej w artykule, który obejmuje [modele semantyczne](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="4e955-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="4e955-215">Użyjesz <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> do wykonania analizy przepływu danych w instrukcji deklaracji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="4e955-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="4e955-216">Następnie należy użyć wyników tej analizy przepływu danych, aby upewnić się, że zmienna lokalna nie jest zapisywana z nową wartością nigdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="4e955-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="4e955-217">Wywołać <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodę rozszerzenia, <xref:Microsoft.CodeAnalysis.ILocalSymbol> aby pobrać dla zmiennej i sprawdzić, <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> czy nie jest zawarty z kolekcji analizy przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="4e955-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="4e955-218">Dodaj następujący kod na końcu `AnalyzeNode` metody:</span><span class="sxs-lookup"><span data-stu-id="4e955-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="4e955-219">Właśnie dodany kod zapewnia, że zmienna nie jest `const`modyfikowana i dlatego może być wykonana .</span><span class="sxs-lookup"><span data-stu-id="4e955-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="4e955-220">Nadszedł czas, aby podnieść diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="4e955-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="4e955-221">Dodaj następujący kod jako ostatni `AnalyzeNode`wiersz w:</span><span class="sxs-lookup"><span data-stu-id="4e955-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="4e955-222">Możesz sprawdzić swoje postępy, naciskając **klawisz F5,** aby uruchomić analizator.</span><span class="sxs-lookup"><span data-stu-id="4e955-222">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="4e955-223">Można załadować aplikację konsoli utworzoną wcześniej, a następnie dodać następujący kod testu:</span><span class="sxs-lookup"><span data-stu-id="4e955-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="4e955-224">Żarówka powinna pojawić się, a analizator powinien zgłosić diagnostykę.</span><span class="sxs-lookup"><span data-stu-id="4e955-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="4e955-225">Jednak żarówka nadal używa szablonu wygenerowanego kodu naprawić i informuje, że może być wykonane wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="4e955-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="4e955-226">W następnej sekcji wyjaśniono, jak napisać poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="4e955-227">Napisz poprawkę kodu</span><span class="sxs-lookup"><span data-stu-id="4e955-227">Write the code fix</span></span>

<span data-ttu-id="4e955-228">Analizator może dostarczyć jedną lub więcej poprawek kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="4e955-229">Poprawka kodu definiuje emisję, która rozwiązuje zgłoszony problem.</span><span class="sxs-lookup"><span data-stu-id="4e955-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="4e955-230">Dla analizatora, który został utworzony, można podać poprawkę kodu, która wstawia const słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="4e955-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="4e955-231">Użytkownik wybiera go z interfejsu użytkownika żarówki w edytorze i Visual Studio zmienia kod.</span><span class="sxs-lookup"><span data-stu-id="4e955-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="4e955-232">Otwórz plik **MakeConstCodeFixProvider.cs** dodany przez szablon.</span><span class="sxs-lookup"><span data-stu-id="4e955-232">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="4e955-233">Ta poprawka kodu jest już podłączona do identyfikatora diagnostycznego utworzonego przez analizator diagnostyczny, ale nie implementuje jeszcze przekształcenia odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-233">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="4e955-234">Najpierw należy usunąć niektóre z kodu szablonu.</span><span class="sxs-lookup"><span data-stu-id="4e955-234">First you should remove some of the template code.</span></span> <span data-ttu-id="4e955-235">Zmień ciąg tytułu na "Make constant":</span><span class="sxs-lookup"><span data-stu-id="4e955-235">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="4e955-236">Następnie usuń `MakeUppercaseAsync` metodę.</span><span class="sxs-lookup"><span data-stu-id="4e955-236">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="4e955-237">To już nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="4e955-237">It no longer applies.</span></span>

<span data-ttu-id="4e955-238">Wszyscy dostawcy poprawek kodu <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>pochodzą od .</span><span class="sxs-lookup"><span data-stu-id="4e955-238">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="4e955-239">Wszystkie one <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> zastąpić do raportu dostępne poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-239">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="4e955-240">W `RegisterCodeFixesAsync`przypadku zmiany typu węzła przodka, którego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> szukasz, na wartość diagnostyczną:</span><span class="sxs-lookup"><span data-stu-id="4e955-240">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="4e955-241">Następnie zmień ostatni wiersz, aby zarejestrować poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-241">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="4e955-242">Poprawka utworzy nowy dokument, który `const` wynika z dodawania modyfikatora do istniejącej deklaracji:</span><span class="sxs-lookup"><span data-stu-id="4e955-242">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="4e955-243">Zauważysz czerwone squiggles w kodzie, `MakeConstAsync`który właśnie dodał na symbolu .</span><span class="sxs-lookup"><span data-stu-id="4e955-243">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="4e955-244">Dodaj deklarację `MakeConstAsync` dla podobnych, podobnych kodów:</span><span class="sxs-lookup"><span data-stu-id="4e955-244">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="4e955-245">Nowa `MakeConstAsync` metoda przekształci <xref:Microsoft.CodeAnalysis.Document> reprezentujący plik źródłowy użytkownika <xref:Microsoft.CodeAnalysis.Document> w nowy, `const` który teraz zawiera deklarację.</span><span class="sxs-lookup"><span data-stu-id="4e955-245">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="4e955-246">Utwórz nowy `const` token słów kluczowych, aby wstawić z przodu instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="4e955-246">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="4e955-247">Należy uważać, aby najpierw usunąć wszelkie wiodące ciekawostki z `const` pierwszego tokenu deklaracji instrukcji i dołączyć go do tokenu.</span><span class="sxs-lookup"><span data-stu-id="4e955-247">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="4e955-248">Dodaj następujący kod do metody `MakeConstAsync`:</span><span class="sxs-lookup"><span data-stu-id="4e955-248">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="4e955-249">Następnie dodaj `const` token do deklaracji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4e955-249">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="4e955-250">Następnie sformatuj nową deklarację, aby dopasować reguły formatowania Języka C#.</span><span class="sxs-lookup"><span data-stu-id="4e955-250">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="4e955-251">Formatowanie zmian w celu dopasowania istniejącego kodu zapewnia lepsze środowisko.</span><span class="sxs-lookup"><span data-stu-id="4e955-251">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="4e955-252">Dodaj następującą instrukcję bezpośrednio po istniejącym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4e955-252">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="4e955-253">Dla tego kodu wymagany jest nowy obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="4e955-253">A new namespace is required for this code.</span></span> <span data-ttu-id="4e955-254">Dodaj następującą `using` instrukcję do górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="4e955-254">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="4e955-255">Ostatnim krokiem jest dokonanie edytowania.</span><span class="sxs-lookup"><span data-stu-id="4e955-255">The final step is to make your edit.</span></span> <span data-ttu-id="4e955-256">Istnieją trzy kroki tego procesu:</span><span class="sxs-lookup"><span data-stu-id="4e955-256">There are three steps to this process:</span></span>

1. <span data-ttu-id="4e955-257">Uzyskaj uchwyt do istniejącego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4e955-257">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="4e955-258">Utwórz nowy dokument, zastępując istniejącą deklarację nową deklaracją.</span><span class="sxs-lookup"><span data-stu-id="4e955-258">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="4e955-259">Zwróć nowy dokument.</span><span class="sxs-lookup"><span data-stu-id="4e955-259">Return the new document.</span></span>

<span data-ttu-id="4e955-260">Dodaj następujący kod na końcu `MakeConstAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="4e955-260">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="4e955-261">Poprawka kodu jest gotowa do wypróbowania.</span><span class="sxs-lookup"><span data-stu-id="4e955-261">Your code fix is ready to try.</span></span>  <span data-ttu-id="4e955-262">Naciśnij klawisz F5, aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-262">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="4e955-263">W drugim wystąpieniu programu Visual Studio utwórz nowy projekt aplikacji konsoli Języka C# i dodaj kilka deklaracji zmiennych lokalnych zainicjowanych z wartościami stałymi do Metody głównej.</span><span class="sxs-lookup"><span data-stu-id="4e955-263">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="4e955-264">Zobaczysz, że są one zgłaszane jako ostrzeżenia, jak poniżej.</span><span class="sxs-lookup"><span data-stu-id="4e955-264">You'll see that they are reported as warnings as below.</span></span>

![Może tworzyć ostrzeżenia const](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="4e955-266">Zrobiłeś duży postęp.</span><span class="sxs-lookup"><span data-stu-id="4e955-266">You've made a lot of progress.</span></span> <span data-ttu-id="4e955-267">Istnieją squiggles pod deklaracjami, które `const`mogą być wykonane .</span><span class="sxs-lookup"><span data-stu-id="4e955-267">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="4e955-268">Ale jest jeszcze wiele do zrobienia.</span><span class="sxs-lookup"><span data-stu-id="4e955-268">But there is still work to do.</span></span> <span data-ttu-id="4e955-269">To działa dobrze, `const` jeśli dodać do `i`deklaracji, począwszy od , następnie `j` i na koniec `k`.</span><span class="sxs-lookup"><span data-stu-id="4e955-269">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="4e955-270">Ale jeśli dodasz `const` modyfikator w innej `k`kolejności, począwszy `k` od , analizator tworzy błędy: `const`nie można zadeklarować , `i` chyba że i `j` są już `const`.</span><span class="sxs-lookup"><span data-stu-id="4e955-270">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="4e955-271">Musisz zrobić więcej analizy, aby upewnić się, że obsługuje różne sposoby zmienne mogą być deklarowane i inicjowane.</span><span class="sxs-lookup"><span data-stu-id="4e955-271">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="4e955-272">Tworzenie testów opartych na danych</span><span class="sxs-lookup"><span data-stu-id="4e955-272">Build data driven tests</span></span>

<span data-ttu-id="4e955-273">Analizator i kod naprawić pracy na prostym przypadku pojedynczej deklaracji, które mogą być wykonane const.</span><span class="sxs-lookup"><span data-stu-id="4e955-273">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="4e955-274">Istnieje wiele możliwych deklaracji oświadczenia, gdzie ta implementacja popełnia błędy.</span><span class="sxs-lookup"><span data-stu-id="4e955-274">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="4e955-275">Te przypadki zostaną zaadresować, współpracując z biblioteką testów jednostkowych napisaną przez szablon.</span><span class="sxs-lookup"><span data-stu-id="4e955-275">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="4e955-276">Jest znacznie szybszy niż wielokrotne otwieranie drugiej kopii programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4e955-276">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="4e955-277">Otwórz plik **MakeConstUnitTests.cs** w projekcie testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="4e955-277">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="4e955-278">Szablon utworzyli dwa testy, które są zgodne z dwoma typowymi wzorcami dla testu jednostkowego analizatora i kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-278">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="4e955-279">`TestMethod1`pokazuje wzorzec dla testu, który zapewnia analizator nie zgłasza diagnostyki, gdy nie powinien.</span><span class="sxs-lookup"><span data-stu-id="4e955-279">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="4e955-280">`TestMethod2`pokazuje wzorzec raportowania diagnostyki i uruchamiania poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-280">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="4e955-281">Kod dla prawie każdego testu analizatora następuje jeden z tych dwóch wzorców.</span><span class="sxs-lookup"><span data-stu-id="4e955-281">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="4e955-282">W pierwszym kroku można przetworzyć te testy jako testy oparte na danych.</span><span class="sxs-lookup"><span data-stu-id="4e955-282">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="4e955-283">Następnie będzie łatwo utworzyć nowe testy, dodając nowe stałe ciągu do reprezentowania różnych danych wejściowych testu.</span><span class="sxs-lookup"><span data-stu-id="4e955-283">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="4e955-284">Dla wydajności pierwszym krokiem jest refaktoryzacja dwóch testów do testów opartych na danych.</span><span class="sxs-lookup"><span data-stu-id="4e955-284">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="4e955-285">Następnie należy zdefiniować tylko kilka stałych ciągu dla każdego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="4e955-285">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="4e955-286">Podczas refaktoryzacji, zmień nazwę obu metod na lepsze nazwy.</span><span class="sxs-lookup"><span data-stu-id="4e955-286">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="4e955-287">Zamień `TestMethod1` na ten test, który zapewnia, że nie jest wywoływana żadna diagnostyka:</span><span class="sxs-lookup"><span data-stu-id="4e955-287">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="4e955-288">Można utworzyć nowy wiersz danych dla tego testu, definiując dowolny fragment kodu, który nie powinien powodować diagnostyki wyzwolić ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="4e955-288">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="4e955-289">To przeciążenie przebiegów, `VerifyCSharpDiagnostic` gdy nie ma diagnostyki wyzwalane dla fragmentu kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4e955-289">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="4e955-290">Następnie zastąp `TestMethod2` ten test, który zapewnia, że diagnostyka jest wywoływana i poprawka kodu zastosowana dla fragmentu kodu źródłowego:</span><span class="sxs-lookup"><span data-stu-id="4e955-290">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="4e955-291">Poprzedni kod również kilka zmian w kodzie, który tworzy oczekiwany wynik diagnostyczny.</span><span class="sxs-lookup"><span data-stu-id="4e955-291">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="4e955-292">Używa stałych publicznych zarejestrowanych `MakeConst` w analizatorze.</span><span class="sxs-lookup"><span data-stu-id="4e955-292">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="4e955-293">Ponadto używa dwóch stałych ciągu dla źródła wejściowego i stałego.</span><span class="sxs-lookup"><span data-stu-id="4e955-293">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="4e955-294">Dodaj następujące stałe ciągu `UnitTest` do klasy:</span><span class="sxs-lookup"><span data-stu-id="4e955-294">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="4e955-295">Uruchom te dwa testy, aby upewnić się, że przejdą.</span><span class="sxs-lookup"><span data-stu-id="4e955-295">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="4e955-296">W programie Visual Studio otwórz **Eksploratora testów,** wybierając pozycję > **Eksplorator testów\*\*\*\*systemu Windows** > . **Test**</span><span class="sxs-lookup"><span data-stu-id="4e955-296">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="4e955-297">Naciśnij łącze **Uruchom wszystko.**</span><span class="sxs-lookup"><span data-stu-id="4e955-297">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="4e955-298">Tworzenie testów dla prawidłowych deklaracji</span><span class="sxs-lookup"><span data-stu-id="4e955-298">Create tests for valid declarations</span></span>

<span data-ttu-id="4e955-299">Co do zasady analizatory powinny zakończyć pracę tak szybko, jak to możliwe, wykonując minimalną pracę.</span><span class="sxs-lookup"><span data-stu-id="4e955-299">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="4e955-300">Visual Studio wywołuje zarejestrowane analizatory jako kod zmiany użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4e955-300">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="4e955-301">Czas reakcji jest kluczowym wymogiem.</span><span class="sxs-lookup"><span data-stu-id="4e955-301">Responsiveness is a key requirement.</span></span> <span data-ttu-id="4e955-302">Istnieje kilka przypadków testowych dla kodu, który nie powinien podnieść diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="4e955-302">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="4e955-303">Analizator już obsługuje jeden z tych testów, w przypadku, gdy zmienna jest przypisana po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="4e955-303">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="4e955-304">Dodaj następującą stałą ciągu do testów, aby reprezentować tę sprawę:</span><span class="sxs-lookup"><span data-stu-id="4e955-304">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="4e955-305">Następnie dodaj wiersz danych dla tego testu, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="4e955-305">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="4e955-306">Ten test również zaakkuje.</span><span class="sxs-lookup"><span data-stu-id="4e955-306">This test passes as well.</span></span> <span data-ttu-id="4e955-307">Następnie dodaj stałe dla warunków, które jeszcze nie zostały obsłużonych:</span><span class="sxs-lookup"><span data-stu-id="4e955-307">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="4e955-308">Deklaracje, które `const`są już , ponieważ są one już const:</span><span class="sxs-lookup"><span data-stu-id="4e955-308">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="4e955-309">Deklaracje, które nie mają inicjatora, ponieważ nie ma żadnej wartości do użycia:</span><span class="sxs-lookup"><span data-stu-id="4e955-309">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="4e955-310">Deklaracje, w których inicjator nie jest stałą, ponieważ nie mogą być stałymi czaskompilacji:</span><span class="sxs-lookup"><span data-stu-id="4e955-310">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="4e955-311">Może to być jeszcze bardziej skomplikowane, ponieważ C# umożliwia wiele deklaracji jako jedną instrukcję.</span><span class="sxs-lookup"><span data-stu-id="4e955-311">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="4e955-312">Należy wziąć pod uwagę następujące stałej ciągu przypadku testowego:</span><span class="sxs-lookup"><span data-stu-id="4e955-312">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="4e955-313">Zmienna `i` może być stała, `j` ale zmienna nie może.</span><span class="sxs-lookup"><span data-stu-id="4e955-313">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="4e955-314">W związku z tym oświadczenie to nie może być deklaracją const.</span><span class="sxs-lookup"><span data-stu-id="4e955-314">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="4e955-315">Dodaj `DataRow` deklaracje dla wszystkich tych testów:</span><span class="sxs-lookup"><span data-stu-id="4e955-315">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="4e955-316">Uruchom testy ponownie, a zobaczysz te nowe przypadki testowe nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="4e955-316">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="4e955-317">Aktualizowanie analizatora w celu zignorowania poprawnych deklaracji</span><span class="sxs-lookup"><span data-stu-id="4e955-317">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="4e955-318">Potrzebujesz pewnych ulepszeń `AnalyzeNode` metody analizatora, aby odfiltrować kod, który pasuje do tych warunków.</span><span class="sxs-lookup"><span data-stu-id="4e955-318">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="4e955-319">Są to wszystkie warunki pokrewne, więc podobne zmiany naprawią wszystkie te warunki.</span><span class="sxs-lookup"><span data-stu-id="4e955-319">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="4e955-320">Wymiń `AnalyzeNode`następujące zmiany w :</span><span class="sxs-lookup"><span data-stu-id="4e955-320">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="4e955-321">Analiza semantyczna zbadała pojedynczą deklarację zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4e955-321">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="4e955-322">Ten kod musi znajdować `foreach` się w pętli, która sprawdza wszystkie zmienne zadeklarowane w tej samej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4e955-322">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="4e955-323">Każda zadeklarowana zmienna musi mieć inicjatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-323">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="4e955-324">Inicjator każdej zadeklarowanej zmiennej musi być stałą w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4e955-324">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="4e955-325">W `AnalyzeNode` metodzie zastąp oryginalną analizę semantyczną:</span><span class="sxs-lookup"><span data-stu-id="4e955-325">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="4e955-326">z następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="4e955-326">with the following code snippet:</span></span>

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

<span data-ttu-id="4e955-327">Pierwsza `foreach` pętla sprawdza każdą deklarację zmiennej przy użyciu analizy składni.</span><span class="sxs-lookup"><span data-stu-id="4e955-327">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="4e955-328">Pierwszy czek gwarantuje, że zmienna ma inicjatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-328">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="4e955-329">Drugi czek gwarantuje, że inicjator jest stałą.</span><span class="sxs-lookup"><span data-stu-id="4e955-329">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="4e955-330">Druga pętla ma oryginalną analizę semantyczną.</span><span class="sxs-lookup"><span data-stu-id="4e955-330">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="4e955-331">Kontrole semantyczne są w oddzielnej pętli, ponieważ ma większy wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="4e955-331">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="4e955-332">Uruchom testy ponownie, a powinny zobaczyć je wszystkie przejść.</span><span class="sxs-lookup"><span data-stu-id="4e955-332">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="4e955-333">Dodaj ostateczną polską</span><span class="sxs-lookup"><span data-stu-id="4e955-333">Add the final polish</span></span>

<span data-ttu-id="4e955-334">To już prawie koniec.</span><span class="sxs-lookup"><span data-stu-id="4e955-334">You're almost done.</span></span> <span data-ttu-id="4e955-335">Istnieje kilka innych warunków do obsługi analizatora.</span><span class="sxs-lookup"><span data-stu-id="4e955-335">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="4e955-336">Visual Studio wywołuje analizatory, gdy użytkownik pisze kod.</span><span class="sxs-lookup"><span data-stu-id="4e955-336">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="4e955-337">Często jest tak, że analizator zostanie wywołany dla kodu, który nie jest kompilowany.</span><span class="sxs-lookup"><span data-stu-id="4e955-337">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="4e955-338">Metoda analizatora `AnalyzeNode` diagnostycznego nie sprawdza, czy wartość stała jest konwertowalna na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4e955-338">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="4e955-339">Tak więc bieżąca implementacja będzie szczęśliwie konwertować niepoprawną deklarację, taką jak int i = "abc"' na stałą lokalną.</span><span class="sxs-lookup"><span data-stu-id="4e955-339">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="4e955-340">Dodaj stałą ciągu źródłowego dla tego warunku:</span><span class="sxs-lookup"><span data-stu-id="4e955-340">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="4e955-341">Ponadto typy odwołań nie są obsługiwane prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="4e955-341">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="4e955-342">Jedyną stałą wartością dozwoloną dla typu odwołania jest `null`, z wyjątkiem tego przypadku <xref:System.String?displayProperty=nameWithType>, co pozwala na literały ciągów.</span><span class="sxs-lookup"><span data-stu-id="4e955-342">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="4e955-343">Innymi słowy, `const string s = "abc"` jest legalne, ale `const object s = "abc"` nie jest.</span><span class="sxs-lookup"><span data-stu-id="4e955-343">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="4e955-344">Ten fragment kodu sprawdza ten warunek:</span><span class="sxs-lookup"><span data-stu-id="4e955-344">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="4e955-345">Aby być dokładne, należy dodać kolejny test, aby upewnić się, że można utworzyć stałą deklarację dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="4e955-345">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="4e955-346">Poniższy fragment kodu definiuje zarówno kod, który podnosi diagnostyczne, jak i kod po zastosowaniu poprawki:</span><span class="sxs-lookup"><span data-stu-id="4e955-346">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="4e955-347">Na koniec jeśli zmienna `var` jest zadeklarowana za pomocą słowa kluczowego, poprawka kodu wykonuje niewłaściwą `const var` rzecz i generuje deklarację, która nie jest obsługiwana przez język C#.</span><span class="sxs-lookup"><span data-stu-id="4e955-347">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="4e955-348">Aby naprawić ten błąd, poprawka `var` kodu musi zastąpić słowo kluczowe nazwą wywnioskowanego typu:</span><span class="sxs-lookup"><span data-stu-id="4e955-348">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="4e955-349">Te zmiany aktualizują deklaracje wierszy danych dla obu testów.</span><span class="sxs-lookup"><span data-stu-id="4e955-349">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="4e955-350">Poniższy kod przedstawia te testy ze wszystkimi atrybutami wiersza danych:</span><span class="sxs-lookup"><span data-stu-id="4e955-350">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="4e955-351">Na szczęście wszystkie powyższe błędy można rozwiązać przy użyciu tych samych technik, których właśnie się nauczyłeś.</span><span class="sxs-lookup"><span data-stu-id="4e955-351">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="4e955-352">Aby naprawić pierwszy błąd, najpierw otwórz **DiagnosticAnalyzer.cs** i zlokalizuj pętlę foreach, w której sprawdzane są każdego z inicjatorów deklaracji lokalnej, aby upewnić się, że są one przypisane ze stałymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="4e955-352">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="4e955-353">Bezpośrednio _przed_ pierwszą pętlą `context.SemanticModel.GetTypeInfo()` foreach wywołaj, aby pobrać szczegółowe informacje o zadeklarowanym typie deklaracji lokalnej:</span><span class="sxs-lookup"><span data-stu-id="4e955-353">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="4e955-354">Następnie w `foreach` pętli sprawdź każdy inicjator, aby upewnić się, że jest konwertowalny na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4e955-354">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="4e955-355">Dodaj następujące sprawdzanie po upewnieniu się, że inicjator jest stałą:</span><span class="sxs-lookup"><span data-stu-id="4e955-355">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="4e955-356">Następna zmiana opiera się na ostatniej.</span><span class="sxs-lookup"><span data-stu-id="4e955-356">The next change builds upon the last one.</span></span> <span data-ttu-id="4e955-357">Przed zamknięciem nawias klamrowy nawias u pierwszy foreach pętli, dodać następujący kod, aby sprawdzić typ deklaracji lokalnej, gdy stała jest ciąg lub null.</span><span class="sxs-lookup"><span data-stu-id="4e955-357">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="4e955-358">Musisz napisać nieco więcej kodu w dostawcy poprawki kodu, aby zastąpić var' słowo kluczowe z poprawną nazwą typu.</span><span class="sxs-lookup"><span data-stu-id="4e955-358">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="4e955-359">Wróć do **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="4e955-359">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="4e955-360">Kod, który dodasz, wykonuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4e955-360">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="4e955-361">Sprawdź, czy deklaracja jest deklaracją `var` i czy jest:</span><span class="sxs-lookup"><span data-stu-id="4e955-361">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="4e955-362">Utwórz nowy typ dla typu wywnioskowanego.</span><span class="sxs-lookup"><span data-stu-id="4e955-362">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="4e955-363">Upewnij się, że deklaracja typu nie jest aliasem.</span><span class="sxs-lookup"><span data-stu-id="4e955-363">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="4e955-364">Jeśli tak, to jest `const var`legalne, aby zadeklarować .</span><span class="sxs-lookup"><span data-stu-id="4e955-364">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="4e955-365">Upewnij się, że `var` nie jest to nazwa typu w tym programie.</span><span class="sxs-lookup"><span data-stu-id="4e955-365">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="4e955-366">(Jeśli tak, `const var` to jest legalne).</span><span class="sxs-lookup"><span data-stu-id="4e955-366">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="4e955-367">Uprość pełną nazwę typu</span><span class="sxs-lookup"><span data-stu-id="4e955-367">Simplify the full type name</span></span>

<span data-ttu-id="4e955-368">To brzmi jak dużo kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-368">That sounds like a lot of code.</span></span> <span data-ttu-id="4e955-369">Tak nie jest.</span><span class="sxs-lookup"><span data-stu-id="4e955-369">It's not.</span></span> <span data-ttu-id="4e955-370">Zamień wiersz, który deklaruje `newLocal` i inicjuje następującykod.</span><span class="sxs-lookup"><span data-stu-id="4e955-370">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="4e955-371">Idzie natychmiast po inicjalizacji: `newModifiers`</span><span class="sxs-lookup"><span data-stu-id="4e955-371">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="4e955-372">Aby użyć tego typu, należy dodać jedną `using` instrukcję: <xref:Microsoft.CodeAnalysis.Simplification.Simplifier></span><span class="sxs-lookup"><span data-stu-id="4e955-372">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="4e955-373">Uruchom testy, a wszystkie powinny przejść.</span><span class="sxs-lookup"><span data-stu-id="4e955-373">Run your tests, and they should all pass.</span></span> <span data-ttu-id="4e955-374">Pogratuluj sobie, uruchamiając gotowy analizator.</span><span class="sxs-lookup"><span data-stu-id="4e955-374">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="4e955-375">Naciśnij klawisze Ctrl+F5, aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio z załadowanym rozszerzeniem Roslyn Preview.</span><span class="sxs-lookup"><span data-stu-id="4e955-375">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="4e955-376">W drugim wystąpieniu programu Visual Studio utwórz nowy `int x = "abc";` projekt aplikacji konsoli Języka C# i dodaj do Metody głównej.</span><span class="sxs-lookup"><span data-stu-id="4e955-376">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="4e955-377">Dzięki pierwszej poprawce błędu nie należy zgłaszać żadnego ostrzeżenia dla tej deklaracji zmiennej lokalnej (chociaż zgodnie z oczekiwaniami występuje błąd kompilatora).</span><span class="sxs-lookup"><span data-stu-id="4e955-377">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="4e955-378">Następnie dodaj `object s = "abc";` do Main metody.</span><span class="sxs-lookup"><span data-stu-id="4e955-378">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="4e955-379">Ze względu na drugą poprawkę błędu nie należy zgłaszać żadnego ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="4e955-379">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="4e955-380">Na koniec dodaj inną zmienną lokalną, która używa słowa kluczowego. `var`</span><span class="sxs-lookup"><span data-stu-id="4e955-380">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="4e955-381">Zobaczysz, że ostrzeżenie jest zgłaszane, a pod po lewej stronie pojawi się sugestia.</span><span class="sxs-lookup"><span data-stu-id="4e955-381">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="4e955-382">Przesuń opiekuna edytora nad falistą podkreśleniem i naciśnij klawisze Ctrl+.</span><span class="sxs-lookup"><span data-stu-id="4e955-382">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="4e955-383">, aby wyświetlić sugerowaną poprawkę kodu.</span><span class="sxs-lookup"><span data-stu-id="4e955-383">to display the suggested code fix.</span></span> <span data-ttu-id="4e955-384">Po wybraniu poprawki kodu należy pamiętać, że słowo kluczowe var jest teraz obsługiwane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="4e955-384">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="4e955-385">Na koniec dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4e955-385">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="4e955-386">Po tych zmianach, masz czerwone squiggles tylko na pierwszych dwóch zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4e955-386">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="4e955-387">Dodaj `const` do `i` `j`obu i , i `k` pojawi się nowe `const`ostrzeżenie, ponieważ może być teraz .</span><span class="sxs-lookup"><span data-stu-id="4e955-387">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="4e955-388">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="4e955-388">Congratulations!</span></span> <span data-ttu-id="4e955-389">Utworzono pierwsze rozszerzenie platformy kompilatora .NET, które wykonuje analizę kodu w locie w celu wykrycia problemu i zapewnia szybką poprawkę, aby go poprawić.</span><span class="sxs-lookup"><span data-stu-id="4e955-389">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="4e955-390">Po drodze nauczysz się wielu interfejsów API kodu, które są częścią sdk platformy kompilatora .NET (Roslyn Interfejsów API).</span><span class="sxs-lookup"><span data-stu-id="4e955-390">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="4e955-391">Możesz sprawdzić swoją pracę na [ukończonym przykładzie](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) w naszym repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="4e955-391">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="4e955-392">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="4e955-392">Other resources</span></span>

- [<span data-ttu-id="4e955-393">Wprowadzenie do analizy składni</span><span class="sxs-lookup"><span data-stu-id="4e955-393">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="4e955-394">Wprowadzenie do analizy semantycznej</span><span class="sxs-lookup"><span data-stu-id="4e955-394">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
