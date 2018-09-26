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
ms.openlocfilehash: 8738e8d0f6a74e1b8ba963e487d4c153a0a6a872
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086492"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="c5c23-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="c5c23-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="c5c23-103">Ten temat zawiera omówienie Managed Extensibility Framework, która została wprowadzona w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c5c23-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a><span data-ttu-id="c5c23-104">Co to jest MEF?</span><span class="sxs-lookup"><span data-stu-id="c5c23-104">What is MEF?</span></span>

<span data-ttu-id="c5c23-105">Managed Extensibility Framework lub MEF to biblioteka do tworzenia aplikacji niewielka, rozszerzalna.</span><span class="sxs-lookup"><span data-stu-id="c5c23-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="c5c23-106">Umożliwia deweloperom wykrywanie i używanie rozszerzeń, bez konieczności konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="c5c23-107">Ponadto pozwala on deweloperzy rozszerzenia łatwo hermetyzacji kodu i uniknąć delikatna twardych zależności.</span><span class="sxs-lookup"><span data-stu-id="c5c23-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="c5c23-108">MEF umożliwia nie tylko rozszerzenia, które mają być ponownie używane w aplikacjach, ale także aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="c5c23-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="c5c23-109">Problem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="c5c23-109">The Problem of Extensibility</span></span>
 <span data-ttu-id="c5c23-110">Wyobraź sobie, czy architekta dużych aplikacji, które muszą obsługiwać rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="c5c23-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="c5c23-111">Aplikacja musi zawierać potencjalnie dużą liczbę mniejszych składników i jest odpowiedzialny za tworzenie i uruchamianie ich.</span><span class="sxs-lookup"><span data-stu-id="c5c23-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

 <span data-ttu-id="c5c23-112">Najprostsza metoda tego problemu jest zawiera składniki jako kod źródłowy w aplikacji, a następnie wywołaj je bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c5c23-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="c5c23-113">Ma to liczbę widocznych wady.</span><span class="sxs-lookup"><span data-stu-id="c5c23-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="c5c23-114">Co najważniejsze nie można dodać nowych składników, bez konieczności modyfikowania kodu źródłowego, ograniczenia, która może być niedopuszczalne w, na przykład aplikacji sieci Web, ale jest niedziałającym w aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="c5c23-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="c5c23-115">Równie problematyczne, możesz nie mieć dostępu do kodu źródłowego, składników, ponieważ może być opracowane przez strony trzecie, a nie zezwala na Twój dostęp do tego samego powodu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

 <span data-ttu-id="c5c23-116">Nieco bardziej wyszukane metody, byłoby punktu rozszerzenia lub interfejsu, aby zezwolić na oddzielenie między aplikacją i jej składniki.</span><span class="sxs-lookup"><span data-stu-id="c5c23-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="c5c23-117">W tym modelu można określić interfejs, który można wdrożyć składnika i interfejs API, aby umożliwić interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="c5c23-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="c5c23-118">To rozwiązuje problem konieczności stosowania dostęp do kodu źródłowego, ale nadal ma swój własny trudności.</span><span class="sxs-lookup"><span data-stu-id="c5c23-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

 <span data-ttu-id="c5c23-119">Ponieważ aplikacja nie jest w stanie wszelkich odnajdywania składników samodzielnie, jego musi nadal dowiedzieć się, jawnie składniki, które są dostępne i powinna być załadowany.</span><span class="sxs-lookup"><span data-stu-id="c5c23-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="c5c23-120">Zazwyczaj jest to osiągane przez jawnie rejestrowanie dostępne składniki w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="c5c23-121">Oznacza to, że zapewnienia, że składniki są poprawne staje się konserwacyjne, szczególnie w przypadku, gdy użytkownik końcowy i nie Deweloper, który oczekuje się, czy aktualizację.</span><span class="sxs-lookup"><span data-stu-id="c5c23-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

 <span data-ttu-id="c5c23-122">Ponadto składniki mają tradycyjnej możliwości komunikowania się ze sobą, z wyjątkiem za pośrednictwem sztywno określonych kanałów samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="c5c23-123">Jeśli Architekt aplikacji nie ma oczekiwać konieczności w celu komunikacji, jest zazwyczaj niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="c5c23-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

 <span data-ttu-id="c5c23-124">Ponadto deweloperzy składników musi zaakceptować twardych zależności, w jaki zestaw zawiera interfejs, które implementują.</span><span class="sxs-lookup"><span data-stu-id="c5c23-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="c5c23-125">Utrudnia składnik, który ma być używany w więcej niż jedną aplikację, a można również tworzyć problemy podczas tworzenia platformę testową dla składników.</span><span class="sxs-lookup"><span data-stu-id="c5c23-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a><span data-ttu-id="c5c23-126">Udostępnia MEF</span><span class="sxs-lookup"><span data-stu-id="c5c23-126">What MEF Provides</span></span>
 <span data-ttu-id="c5c23-127">Zamiast tego jawna rejestracja dostępne składniki MEF umożliwia ich wykrycie, niejawnie, przy użyciu *kompozycji*.</span><span class="sxs-lookup"><span data-stu-id="c5c23-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="c5c23-128">Składnik MEF, o nazwie *część*, w sposób deklaratywny określa zarówno z jego zależności (nazywane *importuje*) i jakie funkcje (nazywane *eksportuje*) dostępnych.</span><span class="sxs-lookup"><span data-stu-id="c5c23-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="c5c23-129">Gdy element zostanie utworzony, aparat składu MEF spełnia jego importów z tym, co dostępne z innych części.</span><span class="sxs-lookup"><span data-stu-id="c5c23-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

 <span data-ttu-id="c5c23-130">To podejście rozwiązuje problemy z opisanych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="c5c23-131">Ponieważ części MEF deklaratywne określenie ich możliwości, są one wykrywalne w czasie wykonywania, co oznacza, że aplikacja może wprowadzać Użyj części bez zakodowanych odwołań i plików konfiguracyjnych słabe.</span><span class="sxs-lookup"><span data-stu-id="c5c23-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="c5c23-132">MEF umożliwia aplikacjom odnaleźć i sprawdź elementy według ich metadanych bez tworzenia wystąpienia je lub nawet ładowania ich zestawów.</span><span class="sxs-lookup"><span data-stu-id="c5c23-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="c5c23-133">W rezultacie nie ma potrzeby dokładnie określić, kiedy i jak można załadować rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c5c23-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

 <span data-ttu-id="c5c23-134">Oprócz jego podana eksportuje element można określić jego importów, które zostaną wypełnione w innych częściach.</span><span class="sxs-lookup"><span data-stu-id="c5c23-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="c5c23-135">To sprawia, że komunikacja między części nie tylko to możliwe, ale dzieje się tak proste i umożliwia dobre wyprowadzenie kodu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="c5c23-136">Na przykład wspólne dla wielu składników usług można być brana pod uwagę w osobnym obszarze i łatwo zmodyfikowane lub zastąpione.</span><span class="sxs-lookup"><span data-stu-id="c5c23-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

 <span data-ttu-id="c5c23-137">Ponieważ MEF model wymaga niezależne twarde w zestawie konkretnej aplikacji, umożliwia rozszerzenia, które mają zostać ponownie użyte z aplikacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="c5c23-138">To ułatwia także do tworzenia kontroler testów, niezależnie od aplikacji, aby przetestować rozszerzenie składników.</span><span class="sxs-lookup"><span data-stu-id="c5c23-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

 <span data-ttu-id="c5c23-139">Rozszerzalne aplikacji napisanej za pomocą MEF deklaruje importu mogą zostać uzupełnione przez składniki rozszerzenia, która również może zadeklarować eksportuje w celu udostępnienia usługami aplikacji w celu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c5c23-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="c5c23-140">Każdy składnik rozszerzenia deklaruje eksportu i może również zadeklarować importów.</span><span class="sxs-lookup"><span data-stu-id="c5c23-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="c5c23-141">W ten sposób samych elementów rozszerzenia są automatycznie rozszerzonego.</span><span class="sxs-lookup"><span data-stu-id="c5c23-141">In this way, extension components themselves are automatically extensible.</span></span>

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a><span data-ttu-id="c5c23-142">Gdzie jest MEF?</span><span class="sxs-lookup"><span data-stu-id="c5c23-142">Where Is MEF Available?</span></span>
 <span data-ttu-id="c5c23-143">MEF jest integralną częścią [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]i jest dostępna wszędzie tam, gdzie .NET Framework jest używany.</span><span class="sxs-lookup"><span data-stu-id="c5c23-143">MEF is an integral part of the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="c5c23-144">W aplikacjach klienckich można użyć MEF, używają Windows Forms, WPF i innych technologii, czy w aplikacji serwera, które używają platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c5c23-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a><span data-ttu-id="c5c23-145">MEF i MAF</span><span class="sxs-lookup"><span data-stu-id="c5c23-145">MEF and MAF</span></span>
 <span data-ttu-id="c5c23-146">Poprzednie wersje programu .NET Framework wprowadzono zarządzane dodatku Framework (MAF), który umożliwia aplikacji, aby izolować i zarządzać rozszerzeniami.</span><span class="sxs-lookup"><span data-stu-id="c5c23-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="c5c23-147">MAF koncentruje się nieco wyższym poziomie niż MEF i skoncentrowanie się na rozszerzenie izolacji i ładowanie zestawów i wyładowywanie, podczas gdy firmy MEF koncentruje się na możliwości odnajdywania, rozszerzalność i przenośność.</span><span class="sxs-lookup"><span data-stu-id="c5c23-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="c5c23-148">Dwie struktury współdziałania sprawnie, a pojedynczą aplikacją korzystać z zalet obu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="c5c23-149">SimpleCalculator: Przykładowa aplikacja</span><span class="sxs-lookup"><span data-stu-id="c5c23-149">SimpleCalculator: An Example Application</span></span>

<span data-ttu-id="c5c23-150">Najprostszym sposobem, aby zobaczyć, co można zrobić MEF jest tworzenie prostej aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="c5c23-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="c5c23-151">W tym przykładzie utworzysz bardzo prosty kalkulator, o nazwie SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="c5c23-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="c5c23-152">Celem SimpleCalculator jest, aby utworzyć aplikację konsolową, która akceptuje podstawowe polecenia arytmetyczne, w postaci "5 + 3" lub "6-2" i zwraca poprawnych odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c5c23-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="c5c23-153">Za pomocą MEF, będziesz mieć możliwość dodawania nowych operatorów bez konieczności zmieniania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="c5c23-154">Aby pobrać kompletny kod dla tego przykładu, zobacz [przykładowe SimpleCalculator](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="c5c23-154">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

> [!NOTE]
> <span data-ttu-id="c5c23-155">Celem SimpleCalculator jest, aby zademonstrować pojęć i składnia MEF, a nie zapewnienie niekoniecznie realistyczny scenariusz, w ramach jego użycia.</span><span class="sxs-lookup"><span data-stu-id="c5c23-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="c5c23-156">Wiele aplikacji, które będą korzystać z najbardziej z możliwości MEF jest bardziej skomplikowane niż SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="c5c23-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="c5c23-157">Aby bardziej rozległe przykładów, zobacz [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="c5c23-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="c5c23-158">Aby rozpocząć, w programie Visual Studio Utwórz nowy projekt aplikacji konsoli i nadaj mu nazwę `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="c5c23-159">Dodaj odwołanie do zestawu System.ComponentModel.Composition, w którym znajduje się MEF.</span><span class="sxs-lookup"><span data-stu-id="c5c23-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span>

- <span data-ttu-id="c5c23-160">Otwórz Module1.vb lub plik Program.cs i Dodaj `Imports` lub `using` instrukcji dla elementy System.ComponentModel.Composition i System.ComponentModel.Composition.Hosting.</span><span class="sxs-lookup"><span data-stu-id="c5c23-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="c5c23-161">Te dwie przestrzenie nazw zawierają typy MEF, konieczne będzie tworzenie aplikacji rozszerzalnej.</span><span class="sxs-lookup"><span data-stu-id="c5c23-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="c5c23-162">Jeśli używasz języka Visual Basic, Dodaj `Public` — słowo kluczowe do wiersza, który deklaruje `Module1` modułu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="c5c23-163">Kontener kompozycji i katalogi</span><span class="sxs-lookup"><span data-stu-id="c5c23-163">Composition Container and Catalogs</span></span>

<span data-ttu-id="c5c23-164">Podstawowy model kompozycji MEF jest *pojemnik składu*, który zawiera wszystkie elementy i wykonuje kompozycji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="c5c23-165">Kompozycja działa dopasowywania importów do eksportu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="c5c23-166">Najczęściej spotykanym typem kontener kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, i użyjesz to SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="c5c23-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="c5c23-167">Jeśli używasz języka Visual Basic w Module1.vb, Dodaj klasę publiczną, o nazwie `Program`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-167">If you're using Visual Basic, in Module1.vb, add a public class named `Program`.</span></span>

<span data-ttu-id="c5c23-168">Dodaj następujący wiersz do `Program` klasy Module1.vb lub plik Program.cs:</span><span class="sxs-lookup"><span data-stu-id="c5c23-168">Add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="c5c23-169">Aby odnaleźć elementy dostępne do niego kontenery kompozycji sprawia, że użycie *katalogu*.</span><span class="sxs-lookup"><span data-stu-id="c5c23-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="c5c23-170">Wykaz jest obiektem, który sprawia, że dostępne elementy wykryte z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="c5c23-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="c5c23-171">MEF zawiera katalogi, aby odnaleźć składniki Report Part z podany typ, zespół lub katalog.</span><span class="sxs-lookup"><span data-stu-id="c5c23-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="c5c23-172">Deweloperzy aplikacji można łatwo tworzyć nowe katalogi do odnajdywania składniki Report Part z innych źródeł, takich jak usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c5c23-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="c5c23-173">Dodaj następującego konstruktora do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="c5c23-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
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

<span data-ttu-id="c5c23-174">Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje tworzą zbiór części, w tym przypadku kontener kompozycji bieżące wystąpienie `Program`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="c5c23-175">W tym momencie jednak nic się nie stanie, ponieważ `Program` ma żadnych importów do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="c5c23-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="c5c23-176">Przywozu i wywozu za pomocą atrybutów</span><span class="sxs-lookup"><span data-stu-id="c5c23-176">Imports and Exports with Attributes</span></span>
 <span data-ttu-id="c5c23-177">Po pierwsze, masz `Program` zaimportować Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="c5c23-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="c5c23-178">Dzięki temu rozdzielenie użytkownika dotyczy interfejsu, takich jak konsola przychodzących i wychodzących, które zostaną umieszczone w `Program`, od logiki kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="c5c23-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

 <span data-ttu-id="c5c23-179">Dodaj następujący kod do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="c5c23-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 <span data-ttu-id="c5c23-180">Należy zauważyć, że deklaracja `calculator` obiektu nie jest niczym niezwykłym, ale ma ona <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="c5c23-181">Ten atrybut deklaruje ważne importu; oznacza to, że zostaną wprowadzone przez aparat kompozycji podczas składa się obiekt.</span><span class="sxs-lookup"><span data-stu-id="c5c23-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

 <span data-ttu-id="c5c23-182">Każdego importu ma *kontraktu*, która określa, jakie eksporty będzie porównywany z.</span><span class="sxs-lookup"><span data-stu-id="c5c23-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="c5c23-183">Kontrakt może być jawnie określony ciąg lub mogą być automatycznie generowane przez MEF danego typu, w tym przypadku interfejs `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="c5c23-184">Wszelkie eksportu zadeklarowane za pomocą dopasowywania kontraktu zostanie spełnienia tego importu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="c5c23-185">Należy pamiętać, że podczas typ `calculator` obiekt jest w rzeczywistości `ICalculator`, nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="c5c23-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="c5c23-186">Kontrakt jest niezależna od typu obiektu importowania.</span><span class="sxs-lookup"><span data-stu-id="c5c23-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="c5c23-187">(W tym przypadku można pozostawisz `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="c5c23-188">MEF automatycznie przyjmie kontraktu była oparta na typ importu, chyba że wyraźnie określono.)</span><span class="sxs-lookup"><span data-stu-id="c5c23-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

 <span data-ttu-id="c5c23-189">Dodaj to bardzo prosty interfejs do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c5c23-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="c5c23-190">Skoro zdefiniowano `ICalculator`, potrzebujesz klasę, która implementuje go.</span><span class="sxs-lookup"><span data-stu-id="c5c23-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="c5c23-191">Dodaj poniższą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c5c23-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="c5c23-192">Oto eksportu, które będą zgodne importu w `Program`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="c5c23-193">Eksport do dopasowania importu, eksportu musi mieć ten sam kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c5c23-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="c5c23-194">Eksportowanie w ramach umowy na podstawie `typeof(MySimpleCalculator)` dałby w efekcie niezgodności i importowania nie będą wypełnione; kontrakt musi dokładnie pasować.</span><span class="sxs-lookup"><span data-stu-id="c5c23-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

 <span data-ttu-id="c5c23-195">Ponieważ kontener kompozycji zostanie wypełniony ze wszystkimi częściami dostępne w tym zestawie `MySimpleCalculator` część będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="c5c23-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="c5c23-196">Podczas konstruktora dla `Program` wykonuje kompozycji `Program` obiekt i jego importu będzie wypełniona `MySimpleCalculator` obiektu, który zostanie utworzony w tym celu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

 <span data-ttu-id="c5c23-197">Warstwa interfejsu użytkownika (`Program`) nie musi wiedzieć niczego else.</span><span class="sxs-lookup"><span data-stu-id="c5c23-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="c5c23-198">Pozostała część logika interfejsu użytkownika w związku z tym można wypełnić `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="c5c23-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

 <span data-ttu-id="c5c23-199">Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="c5c23-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
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
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="c5c23-200">Ten kod po prostu odczytuje wiersz danych wejściowych i wywołania `Calculate` funkcji `ICalculator` w wyniku ponownie zapisuje się do konsoli.</span><span class="sxs-lookup"><span data-stu-id="c5c23-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="c5c23-201">Oznacza to cały kod w `Program`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="c5c23-202">Wszystkie pozostałe pracy będzie miało miejsce, w części.</span><span class="sxs-lookup"><span data-stu-id="c5c23-202">All the rest of the work will happen in the parts.</span></span>

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a><span data-ttu-id="c5c23-203">Dalsze przywozu i ImportMany</span><span class="sxs-lookup"><span data-stu-id="c5c23-203">Further Imports and ImportMany</span></span>
 <span data-ttu-id="c5c23-204">Aby SimpleCalculator to rozszerzalny musi zaimportować listę operacji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="c5c23-205">Zwykłej <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu jest wypełniana przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c5c23-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="c5c23-206">Jeśli jest więcej niż jeden dostępny, aparat składu powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="c5c23-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="c5c23-207">Aby utworzyć importu, które mogą zostać uzupełnione przez dowolną liczbę eksportu, można użyć <xref:System.ComponentModel.Composition.ImportManyAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

 <span data-ttu-id="c5c23-208">Dodaj następującą właściwość operacji do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="c5c23-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <span data-ttu-id="c5c23-209"><xref:System.Lazy%602> Typ świadczą MEF do przechowywania pośredniego odwołania do eksportu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="c5c23-210">W tym miejscu wyeksportowanego samego obiektu, możesz także uzyskać *Eksportowanie metadanych*, i informacje opisujące eksportowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="c5c23-211">Każdy <xref:System.Lazy%602> zawiera `IOperation` obiekt reprezentujący bieżącej operacji i `IOperationData` obiekt reprezentujący jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="c5c23-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

 <span data-ttu-id="c5c23-212">Dodaj następujące proste interfejsy modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c5c23-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="c5c23-213">W tym przypadku metadanych dla każdej operacji to symbol, który reprezentuje tej operacji, takich jak +, -, \*, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c5c23-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="c5c23-214">Aby udostępnić operacja dodawania, Dodaj poniższą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c5c23-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="c5c23-215"><xref:System.ComponentModel.Composition.ExportAttribute> Atrybutu funkcji, tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="c5c23-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="c5c23-216"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atrybut dołącza metadane w postaci pary nazwa wartość, że Eksport.</span><span class="sxs-lookup"><span data-stu-id="c5c23-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="c5c23-217">Gdy `Add` klasy implementuje `IOperation`, klasa, która implementuje `IOperationData` nie jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="c5c23-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="c5c23-218">Zamiast tego klasy jest tworzone niejawnie za MEF z właściwościami na podstawie nazw metadanych pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="c5c23-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="c5c23-219">(Jest to jeden z kilku sposobów dostępu do metadanych w MEF.)</span><span class="sxs-lookup"><span data-stu-id="c5c23-219">(This is one of several ways to access metadata in MEF.)</span></span>

 <span data-ttu-id="c5c23-220">Kompozycja w MEF *cyklicznego*.</span><span class="sxs-lookup"><span data-stu-id="c5c23-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="c5c23-221">Możesz jawnie składa się `Program` obiektu, który zaimportowany `ICalculator` , są typu `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="c5c23-222">`MySimpleCalculator`, z kolei importuje kolekcję `IOperation` obiektów i że importu zostaną wypełnione podczas `MySimpleCalculator` jest tworzony w tym samym czasie jako operacji importu `Program`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="c5c23-223">Jeśli `Add` klasy zadeklarowane dalsze importu, który zbyt musi zostać wypełniony i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c5c23-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="c5c23-224">Dowolny zaimportować po lewej stronie powoduje błędu kompozycji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="c5c23-225">(Jest to możliwe, jednak do deklarowania Importy opcjonalne lub przypisać je wartościami domyślnymi.)</span><span class="sxs-lookup"><span data-stu-id="c5c23-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a><span data-ttu-id="c5c23-226">Logika Kalkulator</span><span class="sxs-lookup"><span data-stu-id="c5c23-226">Calculator Logic</span></span>
 <span data-ttu-id="c5c23-227">Z tymi częściami w miejscu pozostaje logiki Kalkulator, sam.</span><span class="sxs-lookup"><span data-stu-id="c5c23-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="c5c23-228">Dodaj następujący kod w `MySimpleCalculator` klasy do zaimplementowania `Calculate` metody:</span><span class="sxs-lookup"><span data-stu-id="c5c23-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
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
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
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

 <span data-ttu-id="c5c23-229">Początkowe kroki przeanalizować ciągu wejściowego do lewego i prawego argumentów i znak operatora.</span><span class="sxs-lookup"><span data-stu-id="c5c23-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="c5c23-230">W `foreach` pętli, każdy członek `operations` kolekcji jest sprawdzany pod.</span><span class="sxs-lookup"><span data-stu-id="c5c23-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="c5c23-231">Te obiekty są typu <xref:System.Lazy%602>, i ich wartości metadanych i eksportowanego obiektu można uzyskać dostęp za pomocą <xref:System.Lazy%602.Metadata%2A> właściwości i <xref:System.Lazy%601.Value%2A> właściwość odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c5c23-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="c5c23-232">W takim przypadku `Symbol` właściwość `IOperationData` obiekt został odnaleziony do dopasowania, wywołania kalkulatora `Operate` metody `IOperation` obiektu i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="c5c23-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

 <span data-ttu-id="c5c23-233">Aby wykonać kalkulatorze, potrzebne są także metody pomocnika, która zwraca pozycję pierwszego wystąpienia znaku niebędący cyfrą w ciągu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="c5c23-234">Dodaj następującą metodę pomocnika do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="c5c23-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 <span data-ttu-id="c5c23-235">Teraz można skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="c5c23-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="c5c23-236">W języku Visual Basic, upewnij się, że dodano `Public` słowa kluczowego `Module1`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="c5c23-237">W oknie konsoli typu operacji dodawania, np. "5 + 3", a Kalkulator zwraca wyniki.</span><span class="sxs-lookup"><span data-stu-id="c5c23-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="c5c23-238">Wszystkie inne podmioty wynikiem "nie znaleziono operacji!"</span><span class="sxs-lookup"><span data-stu-id="c5c23-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="c5c23-239">Komunikat.</span><span class="sxs-lookup"><span data-stu-id="c5c23-239">message.</span></span>

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="c5c23-240">Rozszerzanie SimpleCalculator przy użyciu nowej klasy</span><span class="sxs-lookup"><span data-stu-id="c5c23-240">Extending SimpleCalculator Using A New Class</span></span>
 <span data-ttu-id="c5c23-241">Teraz, gdy działa Kalkulator, Dodawanie nowej operacji jest proste.</span><span class="sxs-lookup"><span data-stu-id="c5c23-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="c5c23-242">Dodaj poniższą klasę do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c5c23-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

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

 <span data-ttu-id="c5c23-243">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="c5c23-243">Compile and run the project.</span></span> <span data-ttu-id="c5c23-244">Typ operacji odejmowania, takie jak "5-3".</span><span class="sxs-lookup"><span data-stu-id="c5c23-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="c5c23-245">Kalkulator obsługuje teraz odejmowania, a także dodawanie.</span><span class="sxs-lookup"><span data-stu-id="c5c23-245">The calculator now supports subtraction as well as addition.</span></span>

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="c5c23-246">Rozszerzanie SimpleCalculator za pomocą nowego zestawu</span><span class="sxs-lookup"><span data-stu-id="c5c23-246">Extending SimpleCalculator Using A New Assembly</span></span>
 <span data-ttu-id="c5c23-247">Dodawanie klas do źródła kodu jest proste, ale MEF, udostępnia możliwość wyświetlenia poza źródłem własnych aplikacji dla części.</span><span class="sxs-lookup"><span data-stu-id="c5c23-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="c5c23-248">Aby to wykazać, konieczne będzie modyfikować SimpleCalculator do wyszukiwania w katalogu, a także swój własny zestaw, dla części, przez dodanie <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="c5c23-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

 <span data-ttu-id="c5c23-249">Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="c5c23-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="c5c23-250">Upewnij się dodać go na poziomie projektu, a nie na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c5c23-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="c5c23-251">Następnie dodaj nowy projekt biblioteki klas w rozwiązaniu o nazwie `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="c5c23-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="c5c23-252">Nowy projekt zostanie skompilowany w osobnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="c5c23-252">The new project will compile into a separate assembly.</span></span>

 <span data-ttu-id="c5c23-253">Otwórz projektanta właściwości projektu dla projektu ExtendedOperations, a następnie kliknij przycisk **skompilować** lub **kompilacji** kartę. Zmiana **ścieżkę wyjściową kompilacji** lub **ścieżkę wyjściową** wskaż katalogu rozszerzeń w katalogu projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="c5c23-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>

 <span data-ttu-id="c5c23-254">W pliku Program.cs lub Module1.vb Dodaj następujący wiersz do `Program` Konstruktor:</span><span class="sxs-lookup"><span data-stu-id="c5c23-254">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 <span data-ttu-id="c5c23-255">Przykładowa ścieżka Zamień na ścieżkę do katalogu rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="c5c23-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="c5c23-256">(Jest to ścieżka bezwzględna do debugowania tylko do celów.</span><span class="sxs-lookup"><span data-stu-id="c5c23-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="c5c23-257">W przypadku aplikacji produkcyjnych należy użyć ścieżki względnej.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teraz należy dodać częściami w żadnych zestawów w katalogu rozszerzeń do kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="c5c23-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

 <span data-ttu-id="c5c23-258">W projekcie ExtendedOperations dodać odwołania do SimpleCalculator i System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="c5c23-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="c5c23-259">W pliku klasy ExtendedOperations Dodaj `Imports` lub `using` poufności informacji dotyczące System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="c5c23-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="c5c23-260">W języku Visual Basic należy również dodać `Imports` poufności informacji dotyczące SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="c5c23-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="c5c23-261">Następnie dodaj poniższą klasę do pliku klasy ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="c5c23-261">Then add the following class to the ExtendedOperations class file:</span></span>

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

 <span data-ttu-id="c5c23-262">Należy pamiętać, tej w kolejności dla kontraktu dopasować, <xref:System.ComponentModel.Composition.ExportAttribute> atrybut musi mieć taki sam typ co <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c5c23-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

 <span data-ttu-id="c5c23-263">Skompiluj i uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="c5c23-263">Compile and run the project.</span></span> <span data-ttu-id="c5c23-264">Przetestuj nowy operator Mod (%).</span><span class="sxs-lookup"><span data-stu-id="c5c23-264">Test the new Mod (%) operator.</span></span>

<a name="conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="c5c23-265">Wniosek</span><span class="sxs-lookup"><span data-stu-id="c5c23-265">Conclusion</span></span>
 <span data-ttu-id="c5c23-266">W tym temacie opisano podstawowe pojęcia dotyczące środowiska MEF.</span><span class="sxs-lookup"><span data-stu-id="c5c23-266">This topic covered the basic concepts of MEF.</span></span>

-   <span data-ttu-id="c5c23-267">Części, katalogi i kontener kompozycji</span><span class="sxs-lookup"><span data-stu-id="c5c23-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="c5c23-268">Części i kontener kompozycji są podstawowe bloki konstrukcyjne aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="c5c23-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="c5c23-269">Część jest dowolnego obiektu, który importuje i eksportuje wartość, w tym sam.</span><span class="sxs-lookup"><span data-stu-id="c5c23-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="c5c23-270">Wykaz zawiera zbiór składniki Report Part z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="c5c23-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="c5c23-271">Pojemnik składu używa części, dostarczone przez katalog do utworzenia, wiązanie importu do eksportu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

-   <span data-ttu-id="c5c23-272">Przywozu i wywozu</span><span class="sxs-lookup"><span data-stu-id="c5c23-272">Imports and exports</span></span>

     <span data-ttu-id="c5c23-273">Przywozu i wywozu są sposób za pomocą którego komunikacji między składnikami.</span><span class="sxs-lookup"><span data-stu-id="c5c23-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="c5c23-274">Importowania składnika określa na potrzeby określonej wartości lub obiekt, a z eksportową określa dostępność wartość.</span><span class="sxs-lookup"><span data-stu-id="c5c23-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="c5c23-275">Każdej operacji importowania jest dopasowany do listy eksporty za pomocą jego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c5c23-275">Each import is matched with a list of exports by way of its contract.</span></span>

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a><span data-ttu-id="c5c23-276">Gdzie mogę teraz?</span><span class="sxs-lookup"><span data-stu-id="c5c23-276">Where Do I Go Now?</span></span>
 <span data-ttu-id="c5c23-277">Aby pobrać kompletny kod dla tego przykładu, zobacz [przykładowe SimpleCalculator](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="c5c23-277">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>

 <span data-ttu-id="c5c23-278">Aby uzyskać więcej informacji i przykłady kodu, zobacz [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span><span class="sxs-lookup"><span data-stu-id="c5c23-278">For more information and code examples, see [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span></span> <span data-ttu-id="c5c23-279">Aby uzyskać listę typów MEF, zobacz <xref:System.ComponentModel.Composition?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c5c23-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
