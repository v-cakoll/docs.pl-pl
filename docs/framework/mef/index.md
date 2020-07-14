---
title: Managed Extensibility Framework (MEF)
description: Eksploruj Managed Extensibility Framework (MEF), dzięki któremu deweloperzy aplikacji mogą odnajdywać i używać rozszerzeń bez konfiguracji w programie .NET 4 lub nowszym.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 00ed48f2202d4c04039ac264b1fe71474a02432e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281254"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="8bfbe-103">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="8bfbe-103">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="8bfbe-104">Ten temat zawiera omówienie Managed Extensibility Framework, które zostały wprowadzone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-104">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="8bfbe-105">Co to jest MEF?</span><span class="sxs-lookup"><span data-stu-id="8bfbe-105">What is MEF?</span></span>

<span data-ttu-id="8bfbe-106">Managed Extensibility Framework lub MEF to biblioteka służąca do tworzenia lekkich i rozszerzalnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-106">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="8bfbe-107">Dzięki temu deweloperzy aplikacji mogą odnajdywać i używać rozszerzeń bez konieczności konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-107">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="8bfbe-108">Pozwala to również deweloperom rozszerzeń na łatwe hermetyzację kodu i uniknięcie delikatnych zależności.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-108">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="8bfbe-109">MEF umożliwia nie tylko używanie rozszerzeń w aplikacjach, ale również w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-109">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="8bfbe-110">Problem z rozszerzalnością</span><span class="sxs-lookup"><span data-stu-id="8bfbe-110">The problem of extensibility</span></span>

<span data-ttu-id="8bfbe-111">Załóżmy, że jesteś architektem dużej aplikacji, która musi zapewnić obsługę rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-111">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="8bfbe-112">Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialna za tworzenie i uruchamianie ich.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-112">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="8bfbe-113">Najprostszym podejściem do problemu jest dołączenie składników jako kodu źródłowego w aplikacji i wywołanie ich bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-113">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="8bfbe-114">Ma to wiele oczywistych niedogodności.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-114">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="8bfbe-115">Co najważniejsze, nie można dodawać nowych składników bez modyfikowania kodu źródłowego, ograniczenia, które mogą być akceptowane na przykład aplikacji sieci Web, ale nie są w aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-115">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="8bfbe-116">Jednakowe problemy mogą nie mieć dostępu do kodu źródłowego składników, ponieważ mogą one być opracowywane przez inne osoby. z tego powodu nie można zezwolić na dostęp do niego.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-116">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="8bfbe-117">Nieco bardziej zaawansowaną metodą jest udostępnienie punktu rozszerzenia lub interfejsu, aby umożliwić rozdzielenie między aplikacją i jej składnikami.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-117">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="8bfbe-118">W ramach tego modelu można podać interfejs, który może być zaimplementowany przez składnik, oraz interfejs API umożliwiający współistnienie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-118">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="8bfbe-119">Rozwiązuje to problem z wymaganiem dostępu do kodu źródłowego, ale nadal ma własne problemy.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-119">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="8bfbe-120">Ze względu na to, że aplikacja nie ma żadnej pojemności do odnajdowania składników samodzielnie, nadal musi być jawnie powiadamiana, które składniki są dostępne i powinny być ładowane.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-120">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="8bfbe-121">Jest to zazwyczaj realizowane przez jawne zarejestrowanie składników dostępnych w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-121">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="8bfbe-122">Oznacza to, że zapewnienie, że składniki są poprawne, jest problemem konserwacji, szczególnie jeśli jest to użytkownik końcowy, a nie Deweloper, który powinien wykonać aktualizację.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-122">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="8bfbe-123">Ponadto składniki nie mogą komunikować się ze sobą, z wyjątkiem sztywno zdefiniowanych kanałów samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-123">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="8bfbe-124">Jeśli architekt aplikacji nie przewiduje potrzeby określonej komunikacji, zwykle jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-124">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="8bfbe-125">Na koniec Deweloperzy składników muszą akceptować twardą zależność od zestawu zawierającego interfejs, który implementuje.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-125">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="8bfbe-126">Utrudnia to używanie składnika w więcej niż jednej aplikacji, a także umożliwia tworzenie problemów podczas tworzenia środowiska testowego dla składników.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-126">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="8bfbe-127">Co zapewnia MEF</span><span class="sxs-lookup"><span data-stu-id="8bfbe-127">What MEF provides</span></span>

<span data-ttu-id="8bfbe-128">Zamiast tej jawnej rejestracji dostępnych składników MEF zapewnia sposób ich niejawnego wykrycia za pośrednictwem *kompozycji*.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-128">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="8bfbe-129">Składnik MEF, zwany *częścią*, deklaratywnie określa zarówno jego zależności (znane jako *Importy*), jak i jakie możliwości (znane jako *eksporty*) stają się dostępne.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-129">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="8bfbe-130">Po utworzeniu części aparat kompozycji MEF jest zgodny z tym, co jest dostępne w innych częściach.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-130">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="8bfbe-131">Takie podejście rozwiązuje problemy omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-131">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="8bfbe-132">Ze względu na to, że MEF części jednoznacznie określają ich możliwości, są wykrywalne w czasie wykonywania, co oznacza, że aplikacja może korzystać z części bez zakodowanych odwołań lub plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-132">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="8bfbe-133">MEF umożliwia aplikacjom odnajdywanie i sprawdzanie części według ich metadanych, bez tworzenia ich wystąpień, a nawet ładowania ich zestawów.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-133">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="8bfbe-134">W związku z tym nie ma potrzeby dokładnego określania, kiedy i jak powinny być ładowane rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-134">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="8bfbe-135">Poza dostarczonymi eksportami, część może określać jego Importy, które będą wypełniane innymi częściami.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-135">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="8bfbe-136">Dzięki temu komunikacja między częściami nie jest możliwa, ale prosta i pozwala na dobre factoring kodu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-136">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="8bfbe-137">Na przykład usługi wspólne dla wielu składników mogą być uwzględniane w osobnych częściach i łatwo modyfikowane lub zastępowane.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-137">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="8bfbe-138">Ponieważ model MEF nie wymaga twardej zależności od określonego zestawu aplikacji, umożliwia on używanie rozszerzeń z aplikacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-138">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="8bfbe-139">Ułatwia to również tworzenie zespołu testowego, niezależnego od aplikacji, do testowania składników rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-139">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="8bfbe-140">Rozszerzalna aplikacja zapisywana przy użyciu MEF deklaruje import, który może być wypełniony przez składniki rozszerzenia i może również deklarować Eksporty w celu udostępnienia usług aplikacji rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-140">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="8bfbe-141">Każdy składnik rozszerzenia deklaruje eksport i może również deklarować Importy.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-141">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="8bfbe-142">W ten sposób składniki rozszerzenia są automatycznie rozszerzalne.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-142">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="8bfbe-143">Gdzie MEF jest dostępny</span><span class="sxs-lookup"><span data-stu-id="8bfbe-143">Where MEF is available</span></span>

<span data-ttu-id="8bfbe-144">MEF jest integralną częścią .NET Framework 4 i jest dostępna wszędzie tam, gdzie .NET Framework jest używany.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-144">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="8bfbe-145">Możesz używać MEF w aplikacjach klienckich, niezależnie od tego, czy korzystają z Windows Forms, WPF czy innej technologii, czy też w aplikacjach serwerowych, które korzystają z ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-145">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="8bfbe-146">MEF i</span><span class="sxs-lookup"><span data-stu-id="8bfbe-146">MEF and MAF</span></span>

<span data-ttu-id="8bfbe-147">W poprzednich wersjach .NET Framework wprowadzono zarządzaną strukturę dodatków (nr.), która umożliwia aplikacjom izolowanie rozszerzeń i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-147">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="8bfbe-148">Skoncentrowano się na nieznacznie wyższym poziomie niż MEF, skoncentrowaniu się na izolacji rozszerzeń i ładowaniu zestawu i wyładowaniu, podczas gdy MEF jest wykrywalny, rozszerzalność i przenośność.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-148">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="8bfbe-149">Dwie struktury współdziałają bezproblemowo, a pojedyncza aplikacja może korzystać z obu tych elementów.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-149">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="8bfbe-150">SimpleCalculator: przykładowa aplikacja</span><span class="sxs-lookup"><span data-stu-id="8bfbe-150">SimpleCalculator: An example application</span></span>

<span data-ttu-id="8bfbe-151">Najprostszym sposobem, aby sprawdzić, jakie MEF może być kompilacja prostej aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-151">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="8bfbe-152">W tym przykładzie utworzysz prosty kalkulator o nazwie SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-152">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="8bfbe-153">Celem SimpleCalculator jest utworzenie aplikacji konsolowej, która akceptuje podstawowe polecenia arytmetyczne w postaci "5 + 3" lub "6-2", i zwraca poprawne odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-153">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="8bfbe-154">Korzystając z MEF, będziesz mieć możliwość dodawania nowych operatorów bez zmiany kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-154">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="8bfbe-155">Aby pobrać pełny kod dla tego przykładu, zobacz [przykład SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-155">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="8bfbe-156">Celem SimpleCalculator jest przedstawienie koncepcji i składni MEF, a nie koniecznie zapewnienia realistycznego scenariusza do użycia.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-156">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="8bfbe-157">Wiele aplikacji, które byłyby korzystne dla większości możliwości MEF, jest bardziej skomplikowane niż SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-157">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="8bfbe-158">Aby uzyskać bardziej szczegółowe przykłady, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-158">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="8bfbe-159">Aby rozpocząć, w programie Visual Studio Utwórz nowy projekt aplikacji konsolowej i nadaj mu nazwę `SimpleCalculator` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-159">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="8bfbe-160">Dodaj odwołanie do `System.ComponentModel.Composition` zestawu, w którym znajduje się MEF.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-160">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="8bfbe-161">Otwórz *Module1. vb* lub *program.cs* i Dodaj `Imports` `using` instrukcje or dla `System.ComponentModel.Composition` i `System.ComponentModel.Composition.Hosting` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-161">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="8bfbe-162">Te dwie przestrzenie nazw zawierają typy MEF, które będą potrzebne do opracowania rozszerzalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-162">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="8bfbe-163">Jeśli używasz Visual Basic, Dodaj `Public` słowo kluczowe do wiersza, który deklaruje `Module1` moduł.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-163">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="8bfbe-164">Kontener i wykazy kompozycji</span><span class="sxs-lookup"><span data-stu-id="8bfbe-164">Composition container and catalogs</span></span>

<span data-ttu-id="8bfbe-165">Rdzeń modelu kompozycji MEF jest *kontenerem kompozycji*, który zawiera wszystkie dostępne części i wykonuje kompozycję.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-165">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="8bfbe-166">Kompozycja jest zgodna z importami do eksportu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-166">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="8bfbe-167">Najbardziej typowym typem kontenera kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> , który będzie używany do SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-167">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="8bfbe-168">Jeśli używasz Visual Basic, Dodaj klasę publiczną o nazwie `Program` w *Module1. vb*.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-168">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="8bfbe-169">Dodaj następujący wiersz do `Program` klasy w *Module1. vb* lub *program.cs*:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-169">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="8bfbe-170">Aby można było odnaleźć dostępne dla niego części, kontenery kompozycji używają *wykazu*.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-170">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="8bfbe-171">Wykaz jest obiektem, który udostępnia dostępne części wykryte z niektórych źródeł.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-171">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="8bfbe-172">MEF udostępnia wykazy do odnajdywania części z podanego typu, zestawu lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-172">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="8bfbe-173">Deweloperzy aplikacji mogą łatwo tworzyć nowe katalogi w celu odnajdywania części z innych źródeł, takich jak usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-173">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="8bfbe-174">Dodaj następującego konstruktora do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-174">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="8bfbe-175">Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> instruuje kontener kompozycji, aby złożyć określony zestaw części, w tym przypadku bieżące wystąpienie `Program` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-175">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="8bfbe-176">W tym momencie nic się nie dzieje, ponieważ nie `Program` ma żadnych operacji importowania do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-176">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="8bfbe-177">Importy i eksporty z atrybutami</span><span class="sxs-lookup"><span data-stu-id="8bfbe-177">Imports and Exports with attributes</span></span>

<span data-ttu-id="8bfbe-178">Najpierw `Program` zaimportowano Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-178">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="8bfbe-179">Dzięki temu można rozdzielić problemy związane z interfejsem użytkownika, takie jak dane wejściowe i wyjściowe konsoli, które będą używane `Program` , z logiki kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-179">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="8bfbe-180">Dodaj następujący kod do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-180">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="8bfbe-181">Należy zauważyć, że deklaracja `calculator` obiektu nie jest nietypowa, ale ma <xref:System.ComponentModel.Composition.ImportAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-181">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="8bfbe-182">Ten atrybut deklaruje coś do zaimportowania; oznacza to, że zostanie wypełniony przez aparat kompozycji, gdy obiekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-182">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="8bfbe-183">Każdy import ma *umowę*, która określa, do czego eksportów będzie pasować.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-183">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="8bfbe-184">Kontrakt może być jawnie określonym ciągiem lub może być automatycznie generowany przez MEF z danego typu, w tym przypadku interfejsu `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-184">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="8bfbe-185">Wszystkie eksporty zadeklarowane za pomocą pasujących kontraktów zostaną spełnione.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-185">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="8bfbe-186">Należy pamiętać, że podczas gdy typ `calculator` obiektu jest w rzeczywistości `ICalculator` , nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-186">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="8bfbe-187">Kontrakt jest niezależny od typu obiektu importującego.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-187">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="8bfbe-188">(W tym przypadku można opuścić `typeof(ICalculator)` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-188">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="8bfbe-189">MEF automatycznie przyjmie, że kontrakt będzie oparty na typie importu, chyba że zostanie on jawnie określony.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-189">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="8bfbe-190">Dodaj ten bardzo prosty interfejs do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-190">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="8bfbe-191">Teraz, gdy już masz zdefiniowane `ICalculator` , potrzebujesz klasy implementującej ją.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-191">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="8bfbe-192">Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-192">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

<span data-ttu-id="8bfbe-193">Poniżej przedstawiono eksport, który będzie zgodny z importem w programie `Program` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-193">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="8bfbe-194">Aby eksport był zgodny z importem, eksport musi mieć ten sam kontrakt.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-194">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="8bfbe-195">Eksportowanie pod umową w oparciu o `typeof(MySimpleCalculator)` spowodowałaby wygenerowanie niezgodności i importowanie nie zostanie wypełnione; kontrakt musi być dokładnie dopasowany.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-195">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="8bfbe-196">Ponieważ kontener kompozycji zostanie wypełniony wszystkimi częściami dostępnymi w tym zestawie, `MySimpleCalculator` część będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-196">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="8bfbe-197">Gdy Konstruktor do `Program` wykonywania kompozycji na `Program` obiekcie, jego import zostanie wypełniony `MySimpleCalculator` obiektem, który zostanie utworzony w tym celu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-197">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="8bfbe-198">Warstwa interfejsu użytkownika ( `Program` ) nie musi wiedzieć coś innego.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-198">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="8bfbe-199">W związku z tym można wypełnić resztę logiki interfejsu użytkownika w `Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-199">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="8bfbe-200">Dodaj następujący kod do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-200">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="8bfbe-201">Ten kod po prostu odczytuje wiersz danych wejściowych i wywołuje `Calculate` funkcję `ICalculator` w wyniku, która zapisuje z powrotem w konsoli.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-201">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="8bfbe-202">Jest to cały kod, którego potrzebujesz `Program` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-202">That is all the code you need in `Program`.</span></span> <span data-ttu-id="8bfbe-203">Cała pozostała część pracy będzie występować w częściach.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-203">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="8bfbe-204">Dalsze Importy i ImportMany</span><span class="sxs-lookup"><span data-stu-id="8bfbe-204">Further Imports and ImportMany</span></span>

<span data-ttu-id="8bfbe-205">Aby SimpleCalculator można było rozszerzyć, należy zaimportować listę operacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-205">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="8bfbe-206">Zwykły <xref:System.ComponentModel.Composition.ImportAttribute> atrybut jest wypełniany przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute> .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-206">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="8bfbe-207">Jeśli jest dostępny więcej niż jeden, aparat kompozycji generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-207">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="8bfbe-208">Aby utworzyć import, który może zostać wypełniony przez dowolną liczbę eksportów, można użyć <xref:System.ComponentModel.Composition.ImportManyAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-208">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="8bfbe-209">Dodaj następującą właściwość operacji do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-209">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="8bfbe-210"><xref:System.Lazy%602>jest typem dostarczanym przez MEF do przechowywania pośrednich odwołań do eksportów.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-210"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="8bfbe-211">W tym miejscu oprócz wyeksportowanego obiektu można również uzyskać *metadane eksportu*lub informacje opisujące wyeksportowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-211">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="8bfbe-212">Każda <xref:System.Lazy%602> z nich zawiera `IOperation` obiekt, reprezentujący rzeczywistą operację i `IOperationData` obiekt reprezentujący swoje metadane.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-212">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="8bfbe-213">Dodaj następujące proste interfejsy do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-213">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="8bfbe-214">W takim przypadku metadane dla każdej operacji są symbolem, który reprezentuje tę operację, taką jak +,-, \* i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-214">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="8bfbe-215">Aby zapewnić dostępność operacji dodawania, Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-215">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

<span data-ttu-id="8bfbe-216"><xref:System.ComponentModel.Composition.ExportAttribute>Atrybut działa jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-216">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="8bfbe-217">Ten <xref:System.ComponentModel.Composition.ExportMetadataAttribute> atrybut dołącza metadane w postaci pary nazwa-wartość do tego eksportu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-217">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="8bfbe-218">Podczas `Add` implementowania klasy Klasa `IOperation` , która implementuje `IOperationData` nie jest jawnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-218">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="8bfbe-219">Zamiast tego Klasa jest niejawnie tworzona przez MEF z właściwościami opartymi na nazwach dostarczonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-219">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="8bfbe-220">(Jest to jeden z kilku sposobów uzyskiwania dostępu do metadanych w MEF).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-220">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="8bfbe-221">Kompozycja w MEF jest *cykliczna*.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-221">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="8bfbe-222">Obiekt, który został `Program` zaimportowany, nie został jawnie utworzony `ICalculator` `MySimpleCalculator` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-222">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="8bfbe-223">`MySimpleCalculator`z kolei importuje kolekcję `IOperation` obiektów i import zostanie wypełniony `MySimpleCalculator` , gdy zostanie utworzony, w tym samym czasie, w którym importuje `Program` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-223">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="8bfbe-224">Jeśli `Add` Klasa deklaruje dalsze importowanie, które nie powinny być wypełnione i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-224">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="8bfbe-225">Każdy import pozostał niewypełniony wynikami błędu kompozycji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-225">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="8bfbe-226">(Istnieje jednak możliwość deklarowania importu jako opcjonalnego lub do przypisywania do nich wartości domyślnych).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-226">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="8bfbe-227">Logika kalkulatora</span><span class="sxs-lookup"><span data-stu-id="8bfbe-227">Calculator Logic</span></span>

<span data-ttu-id="8bfbe-228">W przypadku tych części, wszystkie pozostające to logika kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-228">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="8bfbe-229">Dodaj następujący kod do klasy w `MySimpleCalculator` celu zaimplementowania `Calculate` metody:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-229">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

<span data-ttu-id="8bfbe-230">Początkowe kroki analizują ciąg wejściowy do lewego i prawego operandu oraz znaku operatora.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-230">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="8bfbe-231">W `foreach` pętli każdy element członkowski `operations` kolekcji jest badany.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-231">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="8bfbe-232">Te obiekty są typu <xref:System.Lazy%602> , a ich wartości metadanych i wyeksportowany obiekt są dostępne z <xref:System.Lazy%602.Metadata%2A> właściwością i <xref:System.Lazy%601.Value%2A> właściwością.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-232">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="8bfbe-233">W takim przypadku, jeśli `Symbol` Właściwość `IOperationData` obiektu zostanie odnaleziona jako odpowiednik, kalkulator wywołuje `Operate` metodę `IOperation` obiektu i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-233">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="8bfbe-234">Aby ukończyć kalkulator, należy również uzyskać metodę pomocnika zwracającą pozycję pierwszego znaku niebędącego cyfrą w ciągu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-234">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="8bfbe-235">Dodaj następującą metodę pomocnika do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-235">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="8bfbe-236">Teraz powinno być możliwe skompilowanie i uruchomienie projektu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-236">You should now be able to compile and run the project.</span></span> <span data-ttu-id="8bfbe-237">W Visual Basic upewnij się, że `Public` słowo kluczowe zostało dodane do `Module1` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-237">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="8bfbe-238">W oknie konsoli wpisz operację dodawania, taką jak "5 + 3", a Kalkulator zwraca wyniki.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-238">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="8bfbe-239">Wszystkie inne operatory mają wynik "nie znaleziono operacji!"</span><span class="sxs-lookup"><span data-stu-id="8bfbe-239">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="8bfbe-240">.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-240">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="8bfbe-241">Rozszerzanie SimpleCalculator przy użyciu nowej klasy</span><span class="sxs-lookup"><span data-stu-id="8bfbe-241">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="8bfbe-242">Teraz, gdy Kalkulator działa, Dodawanie nowej operacji jest proste.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-242">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="8bfbe-243">Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-243">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

<span data-ttu-id="8bfbe-244">Skompiluj i Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-244">Compile and run the project.</span></span> <span data-ttu-id="8bfbe-245">Wpisz operację odejmowania, na przykład "5-3".</span><span class="sxs-lookup"><span data-stu-id="8bfbe-245">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="8bfbe-246">Kalkulator obsługuje teraz również odejmowanie i Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-246">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="8bfbe-247">Rozszerzanie SimpleCalculator przy użyciu nowego zestawu</span><span class="sxs-lookup"><span data-stu-id="8bfbe-247">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="8bfbe-248">Dodawanie klas do kodu źródłowego jest wystarczająco proste, ale MEF zapewnia możliwość wyszukiwania poza źródłem części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-248">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="8bfbe-249">Aby to zademonstrować, należy zmodyfikować SimpleCalculator, aby przeszukać katalog, a także jego własny zestaw, dla części, przez dodanie <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-249">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="8bfbe-250">Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-250">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="8bfbe-251">Upewnij się, że dodano ją na poziomie projektu, a nie na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-251">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="8bfbe-252">Następnie Dodaj nowy projekt biblioteki klas do rozwiązania o nazwie `ExtendedOperations` .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-252">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="8bfbe-253">Nowy projekt zostanie skompilowany w osobnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-253">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="8bfbe-254">Otwórz projektanta właściwości projektu dla projektu ExtendedOperations, a następnie kliknij kartę **kompilacja** lub **kompilacja** . Zmień **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową** , aby wskazywała katalog rozszerzeń w katalogu projektu SimpleCalculator (\*.. \SimpleCalculator\Extensions \\ \*).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-254">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="8bfbe-255">W *Module1. vb* lub *program.cs*Dodaj następujący wiersz do `Program` konstruktora:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-255">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="8bfbe-256">Zastąp przykładową ścieżkę ścieżką do katalogu rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-256">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="8bfbe-257">(Ta ścieżka bezwzględna służy tylko do celów debugowania.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-257">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="8bfbe-258">W aplikacji produkcyjnej należy użyć ścieżki względnej. <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>Teraz zostaną dodane wszystkie części znajdujące się w każdym z zestawów w katalogu rozszerzeń do kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-258">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="8bfbe-259">W projekcie ExtendedOperations Dodaj odwołania do SimpleCalculator i system. ComponentModel. kompozycji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-259">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="8bfbe-260">W pliku klasy ExtendedOperations Dodaj `Imports` `using` instrukcję or dla elementu System. ComponentModel. kompozycji.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-260">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="8bfbe-261">W Visual Basic Dodaj również `Imports` instrukcję dla SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-261">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="8bfbe-262">Następnie Dodaj następującą klasę do pliku klasy ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-262">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

<span data-ttu-id="8bfbe-263">Należy pamiętać, że w celu dopasowania kontraktu <xref:System.ComponentModel.Composition.ExportAttribute> atrybut musi mieć taki sam typ jak <xref:System.ComponentModel.Composition.ImportAttribute> .</span><span class="sxs-lookup"><span data-stu-id="8bfbe-263">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="8bfbe-264">Skompiluj i Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-264">Compile and run the project.</span></span> <span data-ttu-id="8bfbe-265">Przetestuj nowy mod (%) zakład.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-265">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="8bfbe-266">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8bfbe-266">Conclusion</span></span>

<span data-ttu-id="8bfbe-267">W tym temacie omówiono podstawowe pojęcia dotyczące MEF.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-267">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="8bfbe-268">Części, wykazy i kontener kompozycji</span><span class="sxs-lookup"><span data-stu-id="8bfbe-268">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="8bfbe-269">Części i kontener kompozycji są podstawowymi blokami konstrukcyjnymi aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-269">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="8bfbe-270">Część to każdy obiekt, który importuje lub eksportuje wartość, do i włącznie.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-270">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="8bfbe-271">Wykaz zawiera zbiór części z konkretnego źródła.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-271">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="8bfbe-272">Kontener kompozycji używa części dostarczonych przez wykaz do wykonywania kompozycji, powiązania importu do eksportu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-272">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="8bfbe-273">Importy i eksporty</span><span class="sxs-lookup"><span data-stu-id="8bfbe-273">Imports and exports</span></span>

     <span data-ttu-id="8bfbe-274">Importy i eksporty są sposobem, w jaki składniki komunikują się.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-274">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="8bfbe-275">W przypadku importu składnik określa potrzebę konkretnej wartości lub obiektu, a eksport określa dostępność wartości.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-275">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="8bfbe-276">Każdy import jest dopasowywany do listy eksportów według jej kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-276">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8bfbe-277">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8bfbe-277">Next steps</span></span>

<span data-ttu-id="8bfbe-278">Aby pobrać pełny kod dla tego przykładu, zobacz [przykład SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-278">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="8bfbe-279">Aby uzyskać więcej informacji i przykładów kodu, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-279">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="8bfbe-280">Aby uzyskać listę typów MEF, zobacz <xref:System.ComponentModel.Composition?displayProperty=nameWithType> przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="8bfbe-280">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
