---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fc66837dc31dc1697bcb4ad6dddfb57bfb99bd4
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68434095"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="4e17b-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="4e17b-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="4e17b-103">Ten temat zawiera omówienie Managed Extensibility Framework, które zostały wprowadzone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4e17b-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="4e17b-104">Co to jest MEF?</span><span class="sxs-lookup"><span data-stu-id="4e17b-104">What is MEF?</span></span>

<span data-ttu-id="4e17b-105">Managed Extensibility Framework lub MEF to biblioteka służąca do tworzenia uproszczonych, rozszerzalnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="4e17b-106">Dzięki temu deweloperzy aplikacji mogą odnajdywać i używać rozszerzeń bez konieczności konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="4e17b-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="4e17b-107">Pozwala to również deweloperom rozszerzeń na łatwe hermetyzację kodu i uniknięcie delikatnych zależności.</span><span class="sxs-lookup"><span data-stu-id="4e17b-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="4e17b-108">MEF umożliwia nie tylko używanie rozszerzeń w aplikacjach, ale również w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="4e17b-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="4e17b-109">Problem z rozszerzalnością</span><span class="sxs-lookup"><span data-stu-id="4e17b-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="4e17b-110">Załóżmy, że jesteś architektem dużej aplikacji, która musi zapewnić obsługę rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="4e17b-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="4e17b-111">Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialna za tworzenie i uruchamianie ich.</span><span class="sxs-lookup"><span data-stu-id="4e17b-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="4e17b-112">Najprostszym podejściem do problemu jest dołączenie składników jako kodu źródłowego w aplikacji i wywołanie ich bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="4e17b-113">Ma to wiele oczywistych niedogodności.</span><span class="sxs-lookup"><span data-stu-id="4e17b-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="4e17b-114">Co najważniejsze, nie można dodawać nowych składników bez modyfikowania kodu źródłowego, ograniczenia, które mogą być akceptowane na przykład aplikacji sieci Web, ale nie są w aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="4e17b-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="4e17b-115">Jednakowe problemy mogą nie mieć dostępu do kodu źródłowego składników, ponieważ mogą one być opracowywane przez inne osoby. z tego powodu nie można zezwolić na dostęp do niego.</span><span class="sxs-lookup"><span data-stu-id="4e17b-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="4e17b-116">Nieco bardziej zaawansowaną metodą jest udostępnienie punktu rozszerzenia lub interfejsu, aby umożliwić rozdzielenie między aplikacją i jej składnikami.</span><span class="sxs-lookup"><span data-stu-id="4e17b-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="4e17b-117">W ramach tego modelu można podać interfejs, który może być zaimplementowany przez składnik, oraz interfejs API umożliwiający współistnienie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="4e17b-118">Rozwiązuje to problem z wymaganiem dostępu do kodu źródłowego, ale nadal ma własne problemy.</span><span class="sxs-lookup"><span data-stu-id="4e17b-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="4e17b-119">Ze względu na to, że aplikacja nie ma żadnej pojemności do odnajdowania składników samodzielnie, nadal musi być jawnie powiadamiana, które składniki są dostępne i powinny być ładowane.</span><span class="sxs-lookup"><span data-stu-id="4e17b-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="4e17b-120">Jest to zazwyczaj realizowane przez jawne zarejestrowanie składników dostępnych w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="4e17b-121">Oznacza to, że zapewnienie, że składniki są poprawne, jest problemem konserwacji, szczególnie jeśli jest to użytkownik końcowy, a nie Deweloper, który powinien wykonać aktualizację.</span><span class="sxs-lookup"><span data-stu-id="4e17b-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="4e17b-122">Ponadto składniki nie mogą komunikować się ze sobą, z wyjątkiem sztywno zdefiniowanych kanałów samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="4e17b-123">Jeśli architekt aplikacji nie przewiduje potrzeby określonej komunikacji, zwykle jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="4e17b-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="4e17b-124">Na koniec Deweloperzy składników muszą akceptować twardą zależność od zestawu zawierającego interfejs, który implementuje.</span><span class="sxs-lookup"><span data-stu-id="4e17b-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="4e17b-125">Utrudnia to używanie składnika w więcej niż jednej aplikacji, a także umożliwia tworzenie problemów podczas tworzenia środowiska testowego dla składników.</span><span class="sxs-lookup"><span data-stu-id="4e17b-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="4e17b-126">Co zapewnia MEF</span><span class="sxs-lookup"><span data-stu-id="4e17b-126">What MEF Provides</span></span>
 <span data-ttu-id="4e17b-127">Zamiast tej jawnej rejestracji dostępnych składników MEF zapewnia sposób ich niejawnego wykrycia za pośrednictwem *kompozycji*.</span><span class="sxs-lookup"><span data-stu-id="4e17b-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="4e17b-128">Składnik MEF, zwany częścią , deklaratywnie określa zarówno jego zależności (znane jako *Importy*), jak i jakie możliwości (znane jako *eksporty*) stają się dostępne.</span><span class="sxs-lookup"><span data-stu-id="4e17b-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="4e17b-129">Po utworzeniu części aparat kompozycji MEF jest zgodny z tym, co jest dostępne w innych częściach.</span><span class="sxs-lookup"><span data-stu-id="4e17b-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="4e17b-130">Takie podejście rozwiązuje problemy omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="4e17b-131">Ze względu na to, że MEF części jednoznacznie określają ich możliwości, są wykrywalne w czasie wykonywania, co oznacza, że aplikacja może korzystać z części bez zakodowanych odwołań lub plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="4e17b-132">MEF umożliwia aplikacjom odnajdywanie i sprawdzanie części według ich metadanych, bez tworzenia ich wystąpień, a nawet ładowania ich zestawów.</span><span class="sxs-lookup"><span data-stu-id="4e17b-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="4e17b-133">W związku z tym nie ma potrzeby dokładnego określania, kiedy i jak powinny być ładowane rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4e17b-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="4e17b-134">Poza dostarczonymi eksportami, część może określać jego Importy, które będą wypełniane innymi częściami.</span><span class="sxs-lookup"><span data-stu-id="4e17b-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="4e17b-135">Dzięki temu komunikacja między częściami nie jest możliwa, ale prosta i pozwala na dobre factoring kodu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="4e17b-136">Na przykład usługi wspólne dla wielu składników mogą być uwzględniane w osobnych częściach i łatwo modyfikowane lub zastępowane.</span><span class="sxs-lookup"><span data-stu-id="4e17b-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="4e17b-137">Ponieważ model MEF nie wymaga twardej zależności od określonego zestawu aplikacji, umożliwia on używanie rozszerzeń z aplikacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="4e17b-138">Ułatwia to również tworzenie zespołu testowego, niezależnego od aplikacji, do testowania składników rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4e17b-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="4e17b-139">Rozszerzalna aplikacja zapisywana przy użyciu MEF deklaruje import, który może być wypełniony przez składniki rozszerzenia i może również deklarować Eksporty w celu udostępnienia usług aplikacji rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4e17b-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="4e17b-140">Każdy składnik rozszerzenia deklaruje eksport i może również deklarować Importy.</span><span class="sxs-lookup"><span data-stu-id="4e17b-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="4e17b-141">W ten sposób składniki rozszerzenia są automatycznie rozszerzalne.</span><span class="sxs-lookup"><span data-stu-id="4e17b-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="4e17b-142">Gdzie jest dostępny MEF?</span><span class="sxs-lookup"><span data-stu-id="4e17b-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="4e17b-143">MEF jest integralną częścią .NET Framework 4 i jest dostępna wszędzie tam, gdzie .NET Framework jest używany.</span><span class="sxs-lookup"><span data-stu-id="4e17b-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="4e17b-144">Możesz używać MEF w aplikacjach klienckich, niezależnie od tego, czy korzystają z Windows Forms, WPF czy innej technologii, czy też w aplikacjach serwerowych, które korzystają z ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4e17b-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="4e17b-145">MEF i</span><span class="sxs-lookup"><span data-stu-id="4e17b-145">MEF and MAF</span></span>
 <span data-ttu-id="4e17b-146">W poprzednich wersjach .NET Framework wprowadzono zarządzaną strukturę dodatków (nr.), która umożliwia aplikacjom izolowanie rozszerzeń i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="4e17b-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="4e17b-147">Skoncentrowano się na nieznacznie wyższym poziomie niż MEF, skoncentrowaniu się na izolacji rozszerzeń i ładowaniu zestawu i wyładowaniu, podczas gdy MEF jest wykrywalny, rozszerzalność i przenośność.</span><span class="sxs-lookup"><span data-stu-id="4e17b-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="4e17b-148">Dwie struktury współdziałają bezproblemowo, a pojedyncza aplikacja może korzystać z obu tych elementów.</span><span class="sxs-lookup"><span data-stu-id="4e17b-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="4e17b-149">SimpleCalculator: Przykładowa aplikacja</span><span class="sxs-lookup"><span data-stu-id="4e17b-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="4e17b-150">Najprostszym sposobem, aby sprawdzić, jakie MEF może być kompilacja prostej aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="4e17b-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="4e17b-151">W tym przykładzie utworzysz prosty kalkulator o nazwie SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="4e17b-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="4e17b-152">Celem SimpleCalculator jest utworzenie aplikacji konsolowej, która akceptuje podstawowe polecenia arytmetyczne w postaci "5 + 3" lub "6-2", i zwraca poprawne odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4e17b-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="4e17b-153">Korzystając z MEF, będziesz mieć możliwość dodawania nowych operatorów bez zmiany kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="4e17b-154">Aby pobrać kompletny kod dla tego przykładu, zobacz [przykład SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="4e17b-154">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="4e17b-155">Celem SimpleCalculator jest przedstawienie koncepcji i składni MEF, a nie koniecznie zapewnienia realistycznego scenariusza do użycia.</span><span class="sxs-lookup"><span data-stu-id="4e17b-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="4e17b-156">Wiele aplikacji, które byłyby korzystne dla większości możliwości MEF, jest bardziej skomplikowane niż SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="4e17b-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="4e17b-157">Aby uzyskać bardziej szczegółowe przykłady, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="4e17b-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="4e17b-158">Aby rozpocząć, w programie Visual Studio Utwórz nowy projekt aplikacji konsolowej i nadaj mu `SimpleCalculator`nazwę.</span><span class="sxs-lookup"><span data-stu-id="4e17b-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="4e17b-159">Dodaj odwołanie do zestawu System. ComponentModel. kompozycji, gdzie znajduje się MEF.</span><span class="sxs-lookup"><span data-stu-id="4e17b-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="4e17b-160">Otwórz Module1. vb lub program.cs i instrukcje `Imports` Add `using` lub for System. ComponentModel. kompozycji i system. ComponentModel. kompozycji. hosting.</span><span class="sxs-lookup"><span data-stu-id="4e17b-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="4e17b-161">Te dwie przestrzenie nazw zawierają typy MEF, które będą potrzebne do opracowania rozszerzalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="4e17b-162">Jeśli używasz Visual Basic, Dodaj `Public` słowo kluczowe do wiersza, który `Module1` deklaruje moduł.</span><span class="sxs-lookup"><span data-stu-id="4e17b-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="4e17b-163">Kontener i wykazy kompozycji</span><span class="sxs-lookup"><span data-stu-id="4e17b-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="4e17b-164">Rdzeń modelu kompozycji MEF jest *kontenerem kompozycji*, który zawiera wszystkie dostępne części i wykonuje kompozycję.</span><span class="sxs-lookup"><span data-stu-id="4e17b-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="4e17b-165">Kompozycja jest zgodna z importami do eksportu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="4e17b-166">Najbardziej typowym typem kontenera kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, który będzie używany do SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="4e17b-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="4e17b-167">Jeśli używasz Visual Basic, w Module1. vb, Dodaj klasę publiczną o nazwie `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e17b-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="4e17b-168">Dodaj następujący wiersz do `Program` klasy w Module1. vb lub program.cs:</span><span class="sxs-lookup"><span data-stu-id="4e17b-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="4e17b-169">Aby można było odnaleźć dostępne dla niego części, kontenery kompozycji używają *wykazu*.</span><span class="sxs-lookup"><span data-stu-id="4e17b-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="4e17b-170">Wykaz jest obiektem, który udostępnia dostępne części wykryte z niektórych źródeł.</span><span class="sxs-lookup"><span data-stu-id="4e17b-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="4e17b-171">MEF udostępnia wykazy do odnajdywania części z podanego typu, zestawu lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="4e17b-172">Deweloperzy aplikacji mogą łatwo tworzyć nowe katalogi w celu odnajdywania części z innych źródeł, takich jak usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4e17b-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="4e17b-173">Dodaj następującego konstruktora do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="4e17b-173">Add the following constructor to the `Program` class:</span></span>

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

<span data-ttu-id="4e17b-174">Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> instruuje kontener kompozycji, aby złożyć określony zestaw części, w tym przypadku bieżące `Program`wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="4e17b-175">W tym momencie nic się nie dzieje, ponieważ `Program` nie ma żadnych operacji importowania do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="4e17b-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="4e17b-176">Importy i eksporty z atrybutami</span><span class="sxs-lookup"><span data-stu-id="4e17b-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="4e17b-177">`Program` Najpierw zaimportowano Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="4e17b-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="4e17b-178">Dzięki temu można rozdzielić problemy związane z interfejsem użytkownika, takie jak dane wejściowe i wyjściowe konsoli `Program`, które będą używane, z logiki kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="4e17b-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="4e17b-179">Dodaj następujący kod do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="4e17b-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="4e17b-180">Należy zauważyć, że deklaracja `calculator` obiektu nie jest nietypowa, ale ma <xref:System.ComponentModel.Composition.ImportAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="4e17b-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="4e17b-181">Ten atrybut deklaruje coś do zaimportowania; oznacza to, że zostanie wypełniony przez aparat kompozycji, gdy obiekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="4e17b-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="4e17b-182">Każdy import ma *umowę*, która określa, do czego eksportów będzie pasować.</span><span class="sxs-lookup"><span data-stu-id="4e17b-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="4e17b-183">Kontrakt może być jawnie określonym ciągiem lub może być automatycznie generowany przez MEF z danego typu, w tym przypadku interfejsu `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="4e17b-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="4e17b-184">Wszystkie eksporty zadeklarowane za pomocą pasujących kontraktów zostaną spełnione.</span><span class="sxs-lookup"><span data-stu-id="4e17b-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="4e17b-185">Należy pamiętać, że podczas gdy typ `calculator` obiektu jest w rzeczywistości `ICalculator`, nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="4e17b-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="4e17b-186">Kontrakt jest niezależny od typu obiektu importującego.</span><span class="sxs-lookup"><span data-stu-id="4e17b-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="4e17b-187">(W tym przypadku można opuścić `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="4e17b-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="4e17b-188">MEF automatycznie przyjmie, że kontrakt będzie oparty na typie importu, chyba że zostanie on jawnie określony.</span><span class="sxs-lookup"><span data-stu-id="4e17b-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="4e17b-189">Dodaj ten bardzo prosty interfejs do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4e17b-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 <span data-ttu-id="4e17b-190">Teraz, gdy już masz `ICalculator`zdefiniowane, potrzebujesz klasy implementującej ją.</span><span class="sxs-lookup"><span data-stu-id="4e17b-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="4e17b-191">Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4e17b-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="4e17b-192">Poniżej przedstawiono eksport, który będzie zgodny z importem `Program`w programie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="4e17b-193">Aby eksport był zgodny z importem, eksport musi mieć ten sam kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4e17b-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="4e17b-194">Eksportowanie pod umową w oparciu `typeof(MySimpleCalculator)` o spowodowałaby wygenerowanie niezgodności i importowanie nie zostanie wypełnione; kontrakt musi być dokładnie dopasowany.</span><span class="sxs-lookup"><span data-stu-id="4e17b-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="4e17b-195">Ponieważ kontener kompozycji zostanie wypełniony wszystkimi częściami dostępnymi w tym zestawie, `MySimpleCalculator` część będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="4e17b-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="4e17b-196">Gdy Konstruktor do `Program` wykonywania kompozycji `Program` na obiekcie, jego import `MySimpleCalculator` zostanie wypełniony obiektem, który zostanie utworzony w tym celu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="4e17b-197">Warstwa interfejsu użytkownika (`Program`) nie musi wiedzieć coś innego.</span><span class="sxs-lookup"><span data-stu-id="4e17b-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="4e17b-198">W związku z tym można wypełnić resztę logiki interfejsu użytkownika w `Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="4e17b-199">Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="4e17b-199">Add the following code to the `Main` method:</span></span>

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
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="4e17b-200">Ten kod po prostu odczytuje wiersz danych wejściowych i wywołuje `Calculate` `ICalculator` funkcję w wyniku, która zapisuje z powrotem w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4e17b-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="4e17b-201">Jest to cały kod, którego potrzebujesz `Program`.</span><span class="sxs-lookup"><span data-stu-id="4e17b-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="4e17b-202">Cała pozostała część pracy będzie występować w częściach.</span><span class="sxs-lookup"><span data-stu-id="4e17b-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="4e17b-203">Dalsze Importy i ImportMany</span><span class="sxs-lookup"><span data-stu-id="4e17b-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="4e17b-204">Aby SimpleCalculator można było rozszerzyć, należy zaimportować listę operacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="4e17b-205">Zwykły <xref:System.ComponentModel.Composition.ImportAttribute> atrybut jest wypełniany przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4e17b-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="4e17b-206">Jeśli jest dostępny więcej niż jeden, aparat kompozycji generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="4e17b-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="4e17b-207">Aby utworzyć import, który może zostać wypełniony przez dowolną liczbę eksportów, można użyć <xref:System.ComponentModel.Composition.ImportManyAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="4e17b-208">Dodaj następującą właściwość operacji do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="4e17b-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="4e17b-209"><xref:System.Lazy%602>jest typem dostarczanym przez MEF do przechowywania pośrednich odwołań do eksportów.</span><span class="sxs-lookup"><span data-stu-id="4e17b-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="4e17b-210">W tym miejscu oprócz wyeksportowanego obiektu można również uzyskać *metadane eksportu*lub informacje opisujące wyeksportowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="4e17b-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="4e17b-211">Każda <xref:System.Lazy%602> z `IOperation` nich zawiera obiekt, reprezentujący `IOperationData` rzeczywistą operację i obiekt reprezentujący swoje metadane.</span><span class="sxs-lookup"><span data-stu-id="4e17b-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="4e17b-212">Dodaj następujące proste interfejsy do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4e17b-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
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

 <span data-ttu-id="4e17b-213">W takim przypadku metadane dla każdej operacji są symbolem, który reprezentuje tę operację, taką jak +,-, \* i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="4e17b-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="4e17b-214">Aby zapewnić dostępność operacji dodawania, Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4e17b-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
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

 <span data-ttu-id="4e17b-215"><xref:System.ComponentModel.Composition.ExportAttribute> Atrybut działa jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4e17b-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="4e17b-216">Ten <xref:System.ComponentModel.Composition.ExportMetadataAttribute> atrybut dołącza metadane w postaci pary nazwa-wartość do tego eksportu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="4e17b-217">Podczas implementowania `IOperation`klasy Klasa, która implementuje `IOperationData` nie jest jawnie zdefiniowana. `Add`</span><span class="sxs-lookup"><span data-stu-id="4e17b-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="4e17b-218">Zamiast tego Klasa jest niejawnie tworzona przez MEF z właściwościami opartymi na nazwach dostarczonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="4e17b-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="4e17b-219">(Jest to jeden z kilku sposobów uzyskiwania dostępu do metadanych w MEF).</span><span class="sxs-lookup"><span data-stu-id="4e17b-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="4e17b-220">Kompozycja w MEF jest cykliczna.</span><span class="sxs-lookup"><span data-stu-id="4e17b-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="4e17b-221">`Program` Obiekt, który został `ICalculator` zaimportowany `MySimpleCalculator`, nie został jawnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="4e17b-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="4e17b-222">`MySimpleCalculator`z kolei importuje kolekcję `IOperation` obiektów i import zostanie wypełniony, gdy `MySimpleCalculator` zostanie utworzony, w tym samym `Program`czasie, w którym importuje.</span><span class="sxs-lookup"><span data-stu-id="4e17b-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="4e17b-223">`Add` Jeśli Klasa deklaruje dalsze importowanie, które nie powinny być wypełnione i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="4e17b-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="4e17b-224">Każdy import pozostał niewypełniony wynikami błędu kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="4e17b-225">(Istnieje jednak możliwość deklarowania importu jako opcjonalnego lub do przypisywania do nich wartości domyślnych).</span><span class="sxs-lookup"><span data-stu-id="4e17b-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="4e17b-226">Logika kalkulatora</span><span class="sxs-lookup"><span data-stu-id="4e17b-226">Calculator Logic</span></span>
 <span data-ttu-id="4e17b-227">W przypadku tych części, wszystkie pozostające to logika kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="4e17b-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="4e17b-228">Dodaj następujący kod do `MySimpleCalculator` klasy w celu `Calculate` zaimplementowania metody:</span><span class="sxs-lookup"><span data-stu-id="4e17b-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
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
public String Calculate(String input)
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

 <span data-ttu-id="4e17b-229">Początkowe kroki analizują ciąg wejściowy do lewego i prawego operandu oraz znaku operatora.</span><span class="sxs-lookup"><span data-stu-id="4e17b-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="4e17b-230">W pętli każdy element członkowski `operations` kolekcji jest badany. `foreach`</span><span class="sxs-lookup"><span data-stu-id="4e17b-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="4e17b-231">Te obiekty są typu <xref:System.Lazy%602>, a ich wartości metadanych i wyeksportowany obiekt są dostępne <xref:System.Lazy%602.Metadata%2A> z właściwością i <xref:System.Lazy%601.Value%2A> właściwością.</span><span class="sxs-lookup"><span data-stu-id="4e17b-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="4e17b-232">W takim przypadku, `Symbol` Jeśli właściwość `IOperationData` obiektu zostanie odnaleziona jako odpowiednik `Operate` , kalkulator `IOperation` wywołuje metodę obiektu i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="4e17b-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="4e17b-233">Aby ukończyć kalkulator, należy również uzyskać metodę pomocnika zwracającą pozycję pierwszego znaku niebędącego cyfrą w ciągu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="4e17b-234">Dodaj następującą metodę pomocnika do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="4e17b-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length - 1
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="4e17b-235">Teraz powinno być możliwe skompilowanie i uruchomienie projektu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="4e17b-236">W Visual Basic upewnij się, że `Public` słowo kluczowe zostało dodane do. `Module1`</span><span class="sxs-lookup"><span data-stu-id="4e17b-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="4e17b-237">W oknie konsoli wpisz operację dodawania, taką jak "5 + 3", a Kalkulator zwraca wyniki.</span><span class="sxs-lookup"><span data-stu-id="4e17b-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="4e17b-238">Wszystkie inne operatory mają wynik "nie znaleziono operacji!"</span><span class="sxs-lookup"><span data-stu-id="4e17b-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="4e17b-239">Komunikat.</span><span class="sxs-lookup"><span data-stu-id="4e17b-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="4e17b-240">Rozszerzanie SimpleCalculator przy użyciu nowej klasy</span><span class="sxs-lookup"><span data-stu-id="4e17b-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="4e17b-241">Teraz, gdy Kalkulator działa, Dodawanie nowej operacji jest proste.</span><span class="sxs-lookup"><span data-stu-id="4e17b-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="4e17b-242">Dodaj następującą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4e17b-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
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

 <span data-ttu-id="4e17b-243">Skompiluj i Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="4e17b-243">Compile and run the project.</span></span> <span data-ttu-id="4e17b-244">Wpisz operację odejmowania, na przykład "5-3".</span><span class="sxs-lookup"><span data-stu-id="4e17b-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="4e17b-245">Kalkulator obsługuje teraz również odejmowanie i Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="4e17b-246">Rozszerzanie SimpleCalculator przy użyciu nowego zestawu</span><span class="sxs-lookup"><span data-stu-id="4e17b-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="4e17b-247">Dodawanie klas do kodu źródłowego jest wystarczająco proste, ale MEF zapewnia możliwość wyszukiwania poza źródłem części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="4e17b-248">Aby to zademonstrować, należy zmodyfikować SimpleCalculator, aby przeszukać katalog, a także jego własny zestaw, dla części, przez dodanie <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="4e17b-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="4e17b-249">Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="4e17b-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="4e17b-250">Upewnij się, że dodano ją na poziomie projektu, a nie na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4e17b-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="4e17b-251">Następnie Dodaj nowy projekt biblioteki klas do rozwiązania o nazwie `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="4e17b-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="4e17b-252">Nowy projekt zostanie skompilowany w osobnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="4e17b-253">Otwórz projektanta właściwości projektu dla projektu ExtendedOperations, a następnie kliknij kartę **kompilacja** lub **kompilacja** . Zmień **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową** , aby wskazywała katalog rozszerzeń w katalogu projektu SimpleCalculator (... \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="4e17b-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="4e17b-254">W Module1. vb lub program.cs Dodaj następujący wiersz do `Program` konstruktora:</span><span class="sxs-lookup"><span data-stu-id="4e17b-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="4e17b-255">Zastąp przykładową ścieżkę ścieżką do katalogu rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="4e17b-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="4e17b-256">(Ta ścieżka bezwzględna służy tylko do celów debugowania.</span><span class="sxs-lookup"><span data-stu-id="4e17b-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="4e17b-257">W aplikacji produkcyjnej należy użyć ścieżki względnej. Teraz <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> zostaną dodane wszystkie części znajdujące się w każdym z zestawów w katalogu rozszerzeń do kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="4e17b-258">W projekcie ExtendedOperations Dodaj odwołania do SimpleCalculator i system. ComponentModel. kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="4e17b-259">W pliku klasy ExtendedOperations Dodaj `Imports` `using` instrukcję or dla elementu System. ComponentModel. kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4e17b-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="4e17b-260">W Visual Basic Dodaj `Imports` również instrukcję dla SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="4e17b-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="4e17b-261">Następnie Dodaj następującą klasę do pliku klasy ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="4e17b-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
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

 <span data-ttu-id="4e17b-262">Należy pamiętać, że w celu dopasowania <xref:System.ComponentModel.Composition.ExportAttribute> kontraktu atrybut musi mieć taki sam typ <xref:System.ComponentModel.Composition.ImportAttribute>jak.</span><span class="sxs-lookup"><span data-stu-id="4e17b-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="4e17b-263">Skompiluj i Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="4e17b-263">Compile and run the project.</span></span> <span data-ttu-id="4e17b-264">Przetestuj nowy mod (%) zakład.</span><span class="sxs-lookup"><span data-stu-id="4e17b-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="4e17b-265">Wniosek</span><span class="sxs-lookup"><span data-stu-id="4e17b-265">Conclusion</span></span>
 <span data-ttu-id="4e17b-266">W tym temacie omówiono podstawowe pojęcia dotyczące MEF.</span><span class="sxs-lookup"><span data-stu-id="4e17b-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="4e17b-267">Części, wykazy i kontener kompozycji</span><span class="sxs-lookup"><span data-stu-id="4e17b-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="4e17b-268">Części i kontener kompozycji są podstawowymi blokami konstrukcyjnymi aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="4e17b-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="4e17b-269">Część to każdy obiekt, który importuje lub eksportuje wartość, do i włącznie.</span><span class="sxs-lookup"><span data-stu-id="4e17b-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="4e17b-270">Wykaz zawiera zbiór części z konkretnego źródła.</span><span class="sxs-lookup"><span data-stu-id="4e17b-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="4e17b-271">Kontener kompozycji używa części dostarczonych przez wykaz do wykonywania kompozycji, powiązania importu do eksportu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="4e17b-272">Importy i eksporty</span><span class="sxs-lookup"><span data-stu-id="4e17b-272">Imports and exports</span></span>

     <span data-ttu-id="4e17b-273">Importy i eksporty są sposobem, w jaki składniki komunikują się.</span><span class="sxs-lookup"><span data-stu-id="4e17b-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="4e17b-274">W przypadku importu składnik określa potrzebę konkretnej wartości lub obiektu, a eksport określa dostępność wartości.</span><span class="sxs-lookup"><span data-stu-id="4e17b-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="4e17b-275">Każdy import jest dopasowywany do listy eksportów według jej kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4e17b-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="4e17b-276">Gdzie teraz mogę przejść?</span><span class="sxs-lookup"><span data-stu-id="4e17b-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="4e17b-277">Aby pobrać kompletny kod dla tego przykładu, zobacz [przykład SimpleCalculator](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="4e17b-277">To download the complete code for this example, see the [SimpleCalculator sample](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="4e17b-278">Aby uzyskać więcej informacji i przykładów kodu, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="4e17b-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="4e17b-279">Aby uzyskać listę typów MEF, zobacz <xref:System.ComponentModel.Composition?displayProperty=nameWithType> przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="4e17b-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
