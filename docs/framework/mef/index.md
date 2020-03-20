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
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181285"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="9a06f-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="9a06f-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="9a06f-103">Ten temat zawiera omówienie zarządzanej struktury rozszerzalności, która została wprowadzona w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9a06f-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="9a06f-104">Co to jest MEF?</span><span class="sxs-lookup"><span data-stu-id="9a06f-104">What is MEF?</span></span>

<span data-ttu-id="9a06f-105">Managed Extensibility Framework lub MEF to biblioteka do tworzenia aplikacji odciążonych i rozszerzalnych.</span><span class="sxs-lookup"><span data-stu-id="9a06f-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="9a06f-106">Umożliwia deweloperom aplikacji odnajdywanie i używanie rozszerzeń bez konieczności konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="9a06f-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="9a06f-107">Umożliwia również deweloperom rozszerzeń łatwe hermetyzowanie kodu i unikanie kruchych twardych zależności.</span><span class="sxs-lookup"><span data-stu-id="9a06f-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="9a06f-108">Mef umożliwia nie tylko ponowneużycie rozszerzeń w aplikacjach, ale także w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="9a06f-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="9a06f-109">Problem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="9a06f-109">The problem of extensibility</span></span>

<span data-ttu-id="9a06f-110">Wyobraź sobie, że jesteś architektem dużej aplikacji, która musi zapewnić obsługę rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="9a06f-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="9a06f-111">Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialna za ich tworzenie i uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="9a06f-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="9a06f-112">Najprostszym podejściem do problemu jest uwzględnienie składników jako kodu źródłowego w aplikacji i wywołanie ich bezpośrednio z kodu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="9a06f-113">Ma to wiele oczywistych wad.</span><span class="sxs-lookup"><span data-stu-id="9a06f-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="9a06f-114">Co najważniejsze, nie można dodawać nowych składników bez modyfikowania kodu źródłowego, ograniczenia, które mogą być dopuszczalne w, na przykład, aplikacji sieci Web, ale jest niewykonalne w aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="9a06f-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="9a06f-115">Równie problematyczne, może nie mieć dostępu do kodu źródłowego dla składników, ponieważ mogą one być opracowane przez osoby trzecie i z tego samego powodu nie można zezwolić im na dostęp do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="9a06f-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="9a06f-116">Nieco bardziej wyrafinowane podejście byłoby zapewnienie punktu rozszerzenia lub interfejsu, aby umożliwić oddzielenie między aplikacją i jej składników.</span><span class="sxs-lookup"><span data-stu-id="9a06f-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="9a06f-117">W ramach tego modelu może zapewnić interfejs, który składnik można zaimplementować i interfejsu API, aby umożliwić mu interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="9a06f-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="9a06f-118">Rozwiązuje to problem wymaga dostępu do kodu źródłowego, ale nadal ma swoje własne trudności.</span><span class="sxs-lookup"><span data-stu-id="9a06f-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="9a06f-119">Ponieważ aplikacja nie ma żadnej pojemności do odnajdywania składników na własną rękę, nadal musi być jawnie poinformowani, które składniki są dostępne i powinny być ładowane.</span><span class="sxs-lookup"><span data-stu-id="9a06f-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="9a06f-120">Zazwyczaj odbywa się to przez jawne rejestrowanie dostępnych składników w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="9a06f-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="9a06f-121">Oznacza to, że zapewnienie, że składniki są poprawne staje się problem konserwacji, szczególnie jeśli jest to użytkownik końcowy, a nie deweloper, który ma wykonać aktualizację.</span><span class="sxs-lookup"><span data-stu-id="9a06f-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="9a06f-122">Ponadto komponenty nie są w stanie komunikować się ze sobą, z wyjątkiem sztywno zdefiniowanych kanałów samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a06f-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="9a06f-123">Jeśli architekt aplikacji nie przewidział potrzeby określonej komunikacji, jest to zwykle niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="9a06f-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="9a06f-124">Na koniec deweloperzy składników musi zaakceptować zależność od zestawu, który zawiera interfejs, który implementują.</span><span class="sxs-lookup"><span data-stu-id="9a06f-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="9a06f-125">Utrudnia to składnik do użycia w więcej niż jednej aplikacji, a także może powodować problemy podczas tworzenia struktury testowej dla składników.</span><span class="sxs-lookup"><span data-stu-id="9a06f-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="9a06f-126">Co zapewnia MEF</span><span class="sxs-lookup"><span data-stu-id="9a06f-126">What MEF provides</span></span>

<span data-ttu-id="9a06f-127">Zamiast tej jawnej rejestracji dostępnych składników, MEF zapewnia sposób, aby odkryć je w sposób dorozumiany, poprzez *skład*.</span><span class="sxs-lookup"><span data-stu-id="9a06f-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="9a06f-128">Składnik MEF, zwany *częścią,* deklaratywnie określa zarówno jego zależności (znane jako *import)* jak i jakie możliwości (znane jako *eksport)* udostępnia.</span><span class="sxs-lookup"><span data-stu-id="9a06f-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="9a06f-129">Podczas tworzenia części silnik kompozycji MEF spełnia swoje wymagania przywozowe z tym, co jest dostępne z innych części.</span><span class="sxs-lookup"><span data-stu-id="9a06f-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="9a06f-130">Takie podejście rozwiązuje problemy omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9a06f-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="9a06f-131">Ponieważ mef części deklaratywnie określić ich możliwości, są one wykrywalne w czasie wykonywania, co oznacza, że aplikacja może korzystać z części bez zakodowanych odwołań lub plików konfiguracji fragile.</span><span class="sxs-lookup"><span data-stu-id="9a06f-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="9a06f-132">MEF umożliwia aplikacjom odnajdowanie i badanie części przez ich metadane, bez tworzenia ich wystąpienia, a nawet ładowania ich zestawów.</span><span class="sxs-lookup"><span data-stu-id="9a06f-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="9a06f-133">W rezultacie nie ma potrzeby, aby dokładnie określić, kiedy i jak rozszerzenia powinny być ładowane.</span><span class="sxs-lookup"><span data-stu-id="9a06f-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="9a06f-134">Oprócz dostarczonego wywozu część może określić swój przywóz, który zostanie wypełniony innymi częściami.</span><span class="sxs-lookup"><span data-stu-id="9a06f-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="9a06f-135">To sprawia, że komunikacja między częściami nie tylko możliwe, ale łatwe i pozwala na dobre faktoringu kodu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="9a06f-136">Na przykład usługi wspólne dla wielu komponentów mogą być brane pod uwagę w oddzielnej części i łatwo modyfikować lub wymieniać.</span><span class="sxs-lookup"><span data-stu-id="9a06f-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="9a06f-137">Ponieważ model MEF nie wymaga żadnych twardych zależności od określonego zestawu aplikacji, umożliwia rozszerzenia do ponownegou stosowania z aplikacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a06f-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="9a06f-138">Ułatwia to również opracowanie uprzęży testowej, niezależnie od zastosowania, w celu przetestowania komponentów przedłużających.</span><span class="sxs-lookup"><span data-stu-id="9a06f-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="9a06f-139">Rozszerzalna aplikacja napisana przy użyciu MEF deklaruje import, który może być wypełniony przez składniki rozszerzenia, a także może deklarować eksport w celu udostępnienia usług aplikacji na rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9a06f-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="9a06f-140">Każdy składnik rozszerzenia deklaruje eksport i może również deklarować import.</span><span class="sxs-lookup"><span data-stu-id="9a06f-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="9a06f-141">W ten sposób same składniki rozszerzenia są automatycznie rozszerzalne.</span><span class="sxs-lookup"><span data-stu-id="9a06f-141">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="9a06f-142">Gdzie mef jest dostępny</span><span class="sxs-lookup"><span data-stu-id="9a06f-142">Where MEF is available</span></span>

<span data-ttu-id="9a06f-143">MEF jest integralną częścią .NET Framework 4 i jest dostępny wszędzie tam, gdzie jest używany program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a06f-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="9a06f-144">MeF można używać w aplikacjach klienckich, czy używają windows forms, WPF lub innej technologii lub w aplikacjach serwera, które używają ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9a06f-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="9a06f-145">MEF i MAF</span><span class="sxs-lookup"><span data-stu-id="9a06f-145">MEF and MAF</span></span>

<span data-ttu-id="9a06f-146">Poprzednie wersje programu .NET Framework wprowadzono managed add-in framework (MAF), zaprojektowany, aby umożliwić aplikacjom izolowanie i zarządzanie rozszerzeniami.</span><span class="sxs-lookup"><span data-stu-id="9a06f-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="9a06f-147">Maf koncentruje się na nieco wyższym poziomie niż MEF, koncentrując się na izolacji rozszerzenia i montażu załadunku i rozładunku, podczas gdy MEF koncentruje się na wykrywalności, rozszerzalności i przenośności.</span><span class="sxs-lookup"><span data-stu-id="9a06f-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="9a06f-148">Dwie struktury współdziałają płynnie, a pojedyncza aplikacja może korzystać z obu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="9a06f-149">SimpleCalculator: przykładowa aplikacja</span><span class="sxs-lookup"><span data-stu-id="9a06f-149">SimpleCalculator: An example application</span></span>

<span data-ttu-id="9a06f-150">Najprostszym sposobem, aby zobaczyć, co MEF może zrobić, to zbudować prostą aplikację MEF.</span><span class="sxs-lookup"><span data-stu-id="9a06f-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="9a06f-151">W tym przykładzie można utworzyć bardzo prosty kalkulator o nazwie SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="9a06f-152">Celem SimpleCalculator jest utworzenie aplikacji konsoli, która akceptuje podstawowe polecenia arytmetyczne, w postaci "5 + 3" lub "6-2", i zwraca poprawne odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a06f-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="9a06f-153">Za pomocą MEF, będziesz mógł dodać nowe operatory bez zmiany kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a06f-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="9a06f-154">Aby pobrać pełny kod w tym przykładzie, zobacz [przykład SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="9a06f-154">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="9a06f-155">Celem SimpleCalculator jest zademonstrowanie pojęć i składni MEF, a nie koniecznie zapewnić realistyczny scenariusz jego użycia.</span><span class="sxs-lookup"><span data-stu-id="9a06f-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="9a06f-156">Wiele aplikacji, które najbardziej skorzystają z mocy MEF są bardziej złożone niż SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="9a06f-157">Aby uzyskać bardziej obszerne przykłady, zobacz [managed extensibility framework](https://github.com/MicrosoftArchive/mef) w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="9a06f-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="9a06f-158">Aby rozpocząć, w programie Visual Studio utwórz `SimpleCalculator`nowy projekt aplikacji konsoli i nadaj jego nazwę .</span><span class="sxs-lookup"><span data-stu-id="9a06f-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="9a06f-159">Dodaj odwołanie do `System.ComponentModel.Composition` zestawu, gdzie znajduje się MEF.</span><span class="sxs-lookup"><span data-stu-id="9a06f-159">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="9a06f-160">Otwórz *module1.vb* lub *Program.cs* i `Imports` `using` dodaj `System.ComponentModel.Composition` lub `System.ComponentModel.Composition.Hosting`wyciągi dla i .</span><span class="sxs-lookup"><span data-stu-id="9a06f-160">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="9a06f-161">Te dwa obszary nazw zawierają typy MEF, które należy opracować rozszerzalną aplikację.</span><span class="sxs-lookup"><span data-stu-id="9a06f-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="9a06f-162">Jeśli używasz języka Visual Basic, dodaj `Public` słowo kluczowe `Module1` do wiersza, który deklaruje moduł.</span><span class="sxs-lookup"><span data-stu-id="9a06f-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="9a06f-163">Kontener kompozycji i katalogi</span><span class="sxs-lookup"><span data-stu-id="9a06f-163">Composition container and catalogs</span></span>

<span data-ttu-id="9a06f-164">Rdzeniem modelu kompozycji MEF jest *pojemnik na kompozycję,* który zawiera wszystkie dostępne części i wykonuje kompozycję.</span><span class="sxs-lookup"><span data-stu-id="9a06f-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="9a06f-165">Skład jest dopasowanie do importu do eksportu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="9a06f-166">Najczęstszym typem kontenera <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>kompozycji jest , i użyjesz go dla SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="9a06f-167">Jeśli używasz języka Visual Basic, dodaj `Program` klasę publiczną o nazwie w *module 1.vb*.</span><span class="sxs-lookup"><span data-stu-id="9a06f-167">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="9a06f-168">Dodaj następujący wiersz `Program` do klasy w *module1.vb* lub *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="9a06f-168">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="9a06f-169">Aby odkryć dostępne części, pojemniki kompozycji korzystają z *katalogu.*</span><span class="sxs-lookup"><span data-stu-id="9a06f-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="9a06f-170">Katalog jest obiektem, który udostępnia części odnalezione z jakiegoś źródła.</span><span class="sxs-lookup"><span data-stu-id="9a06f-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="9a06f-171">MEF udostępnia katalogi do odnajdywać części z podanego typu, zestawu lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="9a06f-172">Deweloperzy aplikacji można łatwo tworzyć nowe katalogi do odnajdowania części z innych źródeł, takich jak usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9a06f-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="9a06f-173">Dodaj do `Program` klasy następujący konstruktor:</span><span class="sxs-lookup"><span data-stu-id="9a06f-173">Add the following constructor to the `Program` class:</span></span>

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

<span data-ttu-id="9a06f-174">Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontenera kompozycji, aby skomponować określony zestaw części, w tym przypadku bieżące `Program`wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="9a06f-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="9a06f-175">W tym momencie jednak nic `Program` się nie stanie, ponieważ nie ma importu do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="9a06f-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="9a06f-176">Import i eksport z atrybutami</span><span class="sxs-lookup"><span data-stu-id="9a06f-176">Imports and Exports with attributes</span></span>

<span data-ttu-id="9a06f-177">Najpierw `Program` zaimportujesz kalkulator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="9a06f-178">Pozwala to na oddzielenie problemów interfejsu użytkownika, takich jak `Program`wejście konsoli i wyjście, które zostaną wprowadzone , od logiki kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="9a06f-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="9a06f-179">Dodaj następujący kod `Program` do klasy:</span><span class="sxs-lookup"><span data-stu-id="9a06f-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="9a06f-180">Należy zauważyć, że `calculator` deklaracja obiektu nie jest niczym niezwykłym, ale jest ozdobiony atrybutem. <xref:System.ComponentModel.Composition.ImportAttribute></span><span class="sxs-lookup"><span data-stu-id="9a06f-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="9a06f-181">Ten atrybut deklaruje coś do importu; oznacza to, że zostanie on wypełniony przez aparat kompozycji, gdy obiekt jest złożony.</span><span class="sxs-lookup"><span data-stu-id="9a06f-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="9a06f-182">Każdy import ma *umowę,* która określa, z jakim eksportem będzie on dopasowany.</span><span class="sxs-lookup"><span data-stu-id="9a06f-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="9a06f-183">Kontrakt może być jawnie określony ciąg lub może być generowany automatycznie przez MEF z `ICalculator`danego typu, w tym przypadku interfejsu .</span><span class="sxs-lookup"><span data-stu-id="9a06f-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="9a06f-184">Każdy eksport zadeklarowany z pasującym kontraktem będzie spełniał ten import.</span><span class="sxs-lookup"><span data-stu-id="9a06f-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="9a06f-185">Należy zauważyć, że `calculator` podczas gdy `ICalculator`typ obiektu jest w rzeczywistości, nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="9a06f-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="9a06f-186">Kontrakt jest niezależny od typu obiektu importującego.</span><span class="sxs-lookup"><span data-stu-id="9a06f-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="9a06f-187">(W takim przypadku można pominąć `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="9a06f-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="9a06f-188">MEF automatycznie przyjmie, że umowa będzie oparta na typie importu, chyba że określisz ją jawnie.)</span><span class="sxs-lookup"><span data-stu-id="9a06f-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="9a06f-189">Dodaj ten bardzo prosty interfejs `SimpleCalculator` do modułu lub przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="9a06f-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

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

<span data-ttu-id="9a06f-190">Teraz, gdy `ICalculator`zostały zdefiniowane , trzeba klasy, która implementuje go.</span><span class="sxs-lookup"><span data-stu-id="9a06f-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="9a06f-191">Dodaj następującą klasę do `SimpleCalculator` modułu lub obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="9a06f-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

<span data-ttu-id="9a06f-192">Oto eksport, który będzie pasował `Program`do importu w .</span><span class="sxs-lookup"><span data-stu-id="9a06f-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="9a06f-193">Aby eksport był zgodny z importem, eksport musi mieć ten sam kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9a06f-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="9a06f-194">Wywóz na podstawie umowy opartej na `typeof(MySimpleCalculator)` spowoduje niezgodność, a przywóz nie zostanie wypełniony; kontrakt musi dokładnie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="9a06f-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="9a06f-195">Ponieważ kontener kompozycji zostanie wypełniony wszystkimi częściami `MySimpleCalculator` dostępnymi w tym złożeniu, część będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="9a06f-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="9a06f-196">Gdy konstruktor `Program` wykonuje kompozycję `Program` na obiekcie, jego `MySimpleCalculator` import zostanie wypełniony obiektem, który zostanie utworzony w tym celu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="9a06f-197">Warstwa interfejsu`Program`użytkownika ( ) nie musi wiedzieć nic więcej.</span><span class="sxs-lookup"><span data-stu-id="9a06f-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="9a06f-198">W związku z tym można wypełnić w `Main` pozostałej części logiki interfejsu użytkownika w metodzie.</span><span class="sxs-lookup"><span data-stu-id="9a06f-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="9a06f-199">Dodaj następujący kod do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="9a06f-199">Add the following code to the `Main` method:</span></span>

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

 <span data-ttu-id="9a06f-200">Ten kod po prostu odczytuje `Calculate` wiersz `ICalculator` danych wejściowych i wywołuje funkcję na wynik, który zapisuje z powrotem do konsoli.</span><span class="sxs-lookup"><span data-stu-id="9a06f-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="9a06f-201">To jest cały kod, `Program`którego potrzebujesz w .</span><span class="sxs-lookup"><span data-stu-id="9a06f-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="9a06f-202">Cała reszta pracy będzie się działo w częściach.</span><span class="sxs-lookup"><span data-stu-id="9a06f-202">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="9a06f-203">Dalsze importy i importwież</span><span class="sxs-lookup"><span data-stu-id="9a06f-203">Further Imports and ImportMany</span></span>

<span data-ttu-id="9a06f-204">Aby SimpleCalculator był rozszerzalny, musi zaimportować listę operacji.</span><span class="sxs-lookup"><span data-stu-id="9a06f-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="9a06f-205">Zwykły <xref:System.ComponentModel.Composition.ImportAttribute> atrybut jest wypełniany przez <xref:System.ComponentModel.Composition.ExportAttribute>jeden i tylko jeden .</span><span class="sxs-lookup"><span data-stu-id="9a06f-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="9a06f-206">Jeśli dostępnych jest więcej niż jeden, aparat kompozycji generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="9a06f-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="9a06f-207">Aby utworzyć import, który może być wypełniony przez dowolną <xref:System.ComponentModel.Composition.ImportManyAttribute> liczbę eksportu, można użyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="9a06f-208">Dodaj do klasy następującą `MySimpleCalculator` właściwość operations:</span><span class="sxs-lookup"><span data-stu-id="9a06f-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="9a06f-209"><xref:System.Lazy%602>jest typem dostarczonym przez MEF w celu posiadania pośrednich odniesień do wywozu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="9a06f-210">W tym miejscu, oprócz samego wyeksportowanego obiektu, otrzymasz również *metadane eksportu*lub informacje opisujące eksportowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="9a06f-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="9a06f-211">Każdy <xref:System.Lazy%602> zawiera `IOperation` obiekt reprezentujący rzeczywistą operację `IOperationData` i obiekt reprezentujący jego metadane.</span><span class="sxs-lookup"><span data-stu-id="9a06f-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="9a06f-212">Dodaj następujące proste interfejsy do `SimpleCalculator` modułu lub obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="9a06f-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="9a06f-213">W takim przypadku metadane dla każdej operacji jest symbolem, który reprezentuje \*tę operację, takich jak +, -, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9a06f-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="9a06f-214">Aby udostępnić operację dodawania, dodaj następującą `SimpleCalculator` klasę do modułu lub obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="9a06f-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

<span data-ttu-id="9a06f-215">Atrybut <xref:System.ComponentModel.Composition.ExportAttribute> działa tak, jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="9a06f-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="9a06f-216">Atrybut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> dołącza metadane, w postaci pary nazwa wartość, do tego eksportu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="9a06f-217">Podczas `Add` gdy klasa `IOperation`implementuje , `IOperationData` klasa, która implementuje nie jest jawnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="9a06f-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="9a06f-218">Zamiast tego klasa jest niejawnie tworzony przez MEF z właściwości na podstawie nazw metadanych pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="9a06f-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="9a06f-219">(Jest to jeden z kilku sposobów dostępu do metadanych w MEF.)</span><span class="sxs-lookup"><span data-stu-id="9a06f-219">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="9a06f-220">Skład w MEF jest *cykliczny*.</span><span class="sxs-lookup"><span data-stu-id="9a06f-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="9a06f-221">Obiekt został jawnie skomponowany, `Program` który zaimportował `ICalculator` obiekt, który okazał się typem `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="9a06f-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="9a06f-222">`MySimpleCalculator`, z kolei importuje `IOperation` kolekcję obiektów, a import `MySimpleCalculator` zostanie wypełniony podczas tworzenia, w `Program`tym samym czasie co przywóz pliku .</span><span class="sxs-lookup"><span data-stu-id="9a06f-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="9a06f-223">Gdyby `Add` klasa zadeklarowała dalszy przywóz, to też musiałoby zostać wypełnione i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9a06f-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="9a06f-224">Każdy import pozostawiony niewypełniony powoduje błąd składu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="9a06f-225">(Możliwe jest jednak zadeklarowanie importu jako opcjonalnego lub przypisanie im wartości domyślnych).</span><span class="sxs-lookup"><span data-stu-id="9a06f-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="9a06f-226">Logika kalkulatora</span><span class="sxs-lookup"><span data-stu-id="9a06f-226">Calculator Logic</span></span>

<span data-ttu-id="9a06f-227">Z tych części w miejscu, wszystko, co pozostaje jest sama logika kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="9a06f-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="9a06f-228">Dodaj następujący kod `MySimpleCalculator` w klasie, `Calculate` aby zaimplementować metodę:</span><span class="sxs-lookup"><span data-stu-id="9a06f-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

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

<span data-ttu-id="9a06f-229">Początkowe kroki analizują ciąg wejściowy w lewej i prawej opery i znak operatora.</span><span class="sxs-lookup"><span data-stu-id="9a06f-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="9a06f-230">W `foreach` pętli każdy element `operations` członkowski kolekcji jest badane.</span><span class="sxs-lookup"><span data-stu-id="9a06f-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="9a06f-231">Obiekty te są <xref:System.Lazy%602>typu , a ich wartości metadanych i <xref:System.Lazy%602.Metadata%2A> eksportowany <xref:System.Lazy%601.Value%2A> obiekt można uzyskać za pomocą właściwości i właściwości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9a06f-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="9a06f-232">W takim przypadku `Symbol` jeśli właściwość `IOperationData` obiektu zostanie wykryta jako zgodne, `Operate` kalkulator wywołuje `IOperation` metodę obiektu i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="9a06f-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="9a06f-233">Aby ukończyć kalkulator, potrzebujesz również metody pomocniczej, która zwraca pozycję pierwszego znaku niecyfrowego w ciągu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="9a06f-234">Dodaj następującą metodę pomocnika `MySimpleCalculator` do klasy:</span><span class="sxs-lookup"><span data-stu-id="9a06f-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

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

<span data-ttu-id="9a06f-235">Teraz powinieneś być w stanie skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="9a06f-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="9a06f-236">W języku Visual Basic upewnij `Public` się, `Module1`że słowo kluczowe zostało dodane do pliku .</span><span class="sxs-lookup"><span data-stu-id="9a06f-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="9a06f-237">W oknie konsoli wpisz operację dodawania, taką jak "5+3", a kalkulator zwraca wyniki.</span><span class="sxs-lookup"><span data-stu-id="9a06f-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="9a06f-238">Każdy inny operator skutkuje "Operacją Nie znaleziono!"</span><span class="sxs-lookup"><span data-stu-id="9a06f-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="9a06f-239">.</span><span class="sxs-lookup"><span data-stu-id="9a06f-239">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="9a06f-240">Rozszerzanie simplecalculator przy użyciu nowej klasy</span><span class="sxs-lookup"><span data-stu-id="9a06f-240">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="9a06f-241">Teraz, gdy kalkulator działa, dodanie nowej operacji jest łatwe.</span><span class="sxs-lookup"><span data-stu-id="9a06f-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="9a06f-242">Dodaj następującą klasę do `SimpleCalculator` modułu lub obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="9a06f-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

<span data-ttu-id="9a06f-243">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="9a06f-243">Compile and run the project.</span></span> <span data-ttu-id="9a06f-244">Wpisz operację odejmowania, taką jak "5-3".</span><span class="sxs-lookup"><span data-stu-id="9a06f-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="9a06f-245">Kalkulator obsługuje teraz odejmowanie, a także dodawanie.</span><span class="sxs-lookup"><span data-stu-id="9a06f-245">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="9a06f-246">Rozszerzanie simplecalculator przy użyciu nowego zestawu</span><span class="sxs-lookup"><span data-stu-id="9a06f-246">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="9a06f-247">Dodawanie klas do kodu źródłowego jest dość proste, ale MEF zapewnia możliwość wyszukiwania poza własne źródło aplikacji dla części.</span><span class="sxs-lookup"><span data-stu-id="9a06f-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="9a06f-248">Aby to zademonstrować, należy zmodyfikować SimpleCalculator, aby przeszukać katalog, a także jego <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>własny zestaw, dla części, dodając program .</span><span class="sxs-lookup"><span data-stu-id="9a06f-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="9a06f-249">Dodaj nowy katalog `Extensions` o nazwie do projektu SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="9a06f-250">Upewnij się, aby dodać go na poziomie projektu, a nie na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9a06f-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="9a06f-251">Następnie dodaj nowy projekt biblioteki klas `ExtendedOperations`do rozwiązania o nazwie .</span><span class="sxs-lookup"><span data-stu-id="9a06f-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="9a06f-252">Nowy projekt zostanie skompilowany w oddzielnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="9a06f-252">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="9a06f-253">Otwórz Projektanta właściwości projektu dla projektu Rozszerzoneoperacje i kliknij kartę **Kompilacja** lub **Kompilacja.** Zmień **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową,** aby wskazać katalog Rozszerzeń w katalogu projektu SimpleCalculator (*.. \SimpleCalculator\Rozszerzenia\\*).</span><span class="sxs-lookup"><span data-stu-id="9a06f-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="9a06f-254">W *module1.vb* lub *Program.cs*dodaj następujący wiersz `Program` do konstruktora:</span><span class="sxs-lookup"><span data-stu-id="9a06f-254">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="9a06f-255">Zastąp przykładową ścieżkę ścieżką do katalogu Rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="9a06f-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="9a06f-256">(Ta ścieżka bezwzględna służy tylko do debugowania.</span><span class="sxs-lookup"><span data-stu-id="9a06f-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="9a06f-257">W aplikacji produkcyjnej należy użyć ścieżki względnej.) Teraz <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> doda wszystkie części znalezione we wszystkich złożeniach w katalogu Rozszerzenia do kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="9a06f-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="9a06f-258">W projekcie ExtendedOperations dodaj odwołania do SimpleCalculator i System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="9a06f-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="9a06f-259">W pliku klasy ExtendedOperations `Imports` dodaj `using` lub instrukcję dla System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="9a06f-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="9a06f-260">W języku Visual Basic `Imports` należy również dodać instrukcję dla SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="9a06f-261">Następnie dodaj następującą klasę do pliku klasy ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="9a06f-261">Then add the following class to the ExtendedOperations class file:</span></span>

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

<span data-ttu-id="9a06f-262">Należy zauważyć, że aby kontrakt <xref:System.ComponentModel.Composition.ExportAttribute> był zgodny, atrybut musi <xref:System.ComponentModel.Composition.ImportAttribute>mieć ten sam typ co .</span><span class="sxs-lookup"><span data-stu-id="9a06f-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="9a06f-263">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="9a06f-263">Compile and run the project.</span></span> <span data-ttu-id="9a06f-264">Przetestuj nowy Mod (%) Operator.</span><span class="sxs-lookup"><span data-stu-id="9a06f-264">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="9a06f-265">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9a06f-265">Conclusion</span></span>

<span data-ttu-id="9a06f-266">W tym temacie poruszono podstawowe pojęcia MEF.</span><span class="sxs-lookup"><span data-stu-id="9a06f-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="9a06f-267">Części, katalogi i kontener kompozycji</span><span class="sxs-lookup"><span data-stu-id="9a06f-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="9a06f-268">Części i kontener kompozycji są podstawowymi elementami składowymi aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="9a06f-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="9a06f-269">Częścią jest dowolny obiekt, który importuje lub eksportuje wartość, do siebie włącznie.</span><span class="sxs-lookup"><span data-stu-id="9a06f-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="9a06f-270">Katalog zawiera kolekcję części z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="9a06f-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="9a06f-271">Kontener kompozycji używa części dostarczonych przez katalog do wykonywania kompozycji, wiązania importu do eksportu.</span><span class="sxs-lookup"><span data-stu-id="9a06f-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="9a06f-272">Import i eksport</span><span class="sxs-lookup"><span data-stu-id="9a06f-272">Imports and exports</span></span>

     <span data-ttu-id="9a06f-273">Import i eksport są sposobem, w jaki składniki komunikują się.</span><span class="sxs-lookup"><span data-stu-id="9a06f-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="9a06f-274">W przypadku importu składnik określa potrzebę określonej wartości lub obiektu, a przy eksporcie określa dostępność wartości.</span><span class="sxs-lookup"><span data-stu-id="9a06f-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="9a06f-275">Każdy import jest dopasowywał do listy wywozu w ramach jego umowy.</span><span class="sxs-lookup"><span data-stu-id="9a06f-275">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9a06f-276">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9a06f-276">Next steps</span></span>

<span data-ttu-id="9a06f-277">Aby pobrać pełny kod w tym przykładzie, zobacz [przykład SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="9a06f-277">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="9a06f-278">Aby uzyskać więcej informacji i przykłady kodu, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="9a06f-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="9a06f-279">Aby uzyskać listę typów MEF, <xref:System.ComponentModel.Composition?displayProperty=nameWithType> zobacz obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="9a06f-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
