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
ms.openlocfilehash: 1f950779514975a3ee76af76506c7579e046537f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393188"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="1057c-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="1057c-102">Managed Extensibility Framework (MEF)</span></span>
<span data-ttu-id="1057c-103">Ten temat zawiera omówienie Managed Extensibility Framework wprowadzone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1057c-103">This topic provides an overview of the Managed Extensibility Framework introduced in the .NET Framework 4.</span></span>  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a><span data-ttu-id="1057c-104">Co to jest MEF?</span><span class="sxs-lookup"><span data-stu-id="1057c-104">What is MEF?</span></span>  
 <span data-ttu-id="1057c-105">Managed Extensibility Framework lub MEF to biblioteka dla tworzenia niewielka, rozszerzalne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1057c-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="1057c-106">Umożliwia deweloperom aplikacji na wykrywanie i używanie rozszerzeń z wymagana żadna konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="1057c-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="1057c-107">Ponadto pozwala on usłudze deweloperów rozszerzenia łatwo Hermetyzowanie kodu i uniknąć wrażliwych twardych zależności.</span><span class="sxs-lookup"><span data-stu-id="1057c-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="1057c-108">MEF umożliwia nie tylko rozszerzenia zostanie ponownie w ramach aplikacji, ale w aplikacjach oraz.</span><span class="sxs-lookup"><span data-stu-id="1057c-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="1057c-109">Problem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="1057c-109">The Problem of Extensibility</span></span>  
 <span data-ttu-id="1057c-110">Załóżmy, czy Architekt dużej aplikacji, który muszą obsługiwać rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="1057c-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="1057c-111">Aplikacja musi zawierać potencjalnie dużej liczby składników mniejsze i jest odpowiedzialny za tworzenie i uruchamianie ich.</span><span class="sxs-lookup"><span data-stu-id="1057c-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>  
  
 <span data-ttu-id="1057c-112">Najprostsza metoda problem jest zawiera składniki jako kod źródłowy w aplikacji i połączeń telefonicznych z nimi bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1057c-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span>  <span data-ttu-id="1057c-113">To jest liczba widocznych wady.</span><span class="sxs-lookup"><span data-stu-id="1057c-113">This has a number of obvious drawbacks.</span></span>  <span data-ttu-id="1057c-114">Najważniejsze nie można dodać nowych składników, bez konieczności modyfikacji kodu źródłowego, ograniczenia, może być do przyjęcia w, na przykład aplikacji sieci Web, ale niedziałającym w aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="1057c-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span>  <span data-ttu-id="1057c-115">Równie powodować problemów, nie masz dostępu do kodu źródłowego dla składników, ponieważ może być opracowana przez osoby trzecie, a także z tego samego powodu się, że nie można zezwolić im dostęp do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="1057c-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>  
  
 <span data-ttu-id="1057c-116">Nieco bardziej złożone rozwiązanie byłoby Podaj punkt rozszerzenia lub interfejsu, aby zezwolić na oddzielenie od aplikacji i jej składniki.</span><span class="sxs-lookup"><span data-stu-id="1057c-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span>  <span data-ttu-id="1057c-117">W tym modelu można określić interfejs, który można wdrożyć składnika i interfejs API do interakcji z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="1057c-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span>  <span data-ttu-id="1057c-118">To rozwiązuje problem polegający na wymaganiu dostęp do kodu źródłowego, ale nadal ma własną trudności.</span><span class="sxs-lookup"><span data-stu-id="1057c-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>  
  
 <span data-ttu-id="1057c-119">Ponieważ aplikacja nie ma żadnych pojemności do odnajdywania składników samodzielnie, go musi nadal można jawnie informację składniki, które są dostępne i powinna być załadowana.</span><span class="sxs-lookup"><span data-stu-id="1057c-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span>  <span data-ttu-id="1057c-120">Zazwyczaj jest to osiągane przez jawnie rejestrowanie dostępne składniki w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1057c-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="1057c-121">Oznacza to, że zapewnienia, że składniki są prawidłowe staje się konserwacyjne, zwłaszcza gdy jest użytkownika końcowego i nie projektanta, który powinien wykonać uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="1057c-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>  
  
 <span data-ttu-id="1057c-122">Ponadto składniki są niezdolne do komunikacji ze sobą, z wyjątkiem kanałami zdefiniowanych sztywno z samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1057c-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span>  <span data-ttu-id="1057c-123">Jeśli Architekt aplikacji nie ma oczekiwać potrzeby w celu komunikacji, jest zazwyczaj niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="1057c-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>  
  
 <span data-ttu-id="1057c-124">Na koniec deweloperzy składnika zaakceptować twardych zależność, jaki zestaw zawiera interfejs, który implementuje one.</span><span class="sxs-lookup"><span data-stu-id="1057c-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span>  <span data-ttu-id="1057c-125">Utrudnia składnika używanego w więcej niż jedną aplikację, a można również tworzyć problemy podczas tworzenia struktury testowej, składników.</span><span class="sxs-lookup"><span data-stu-id="1057c-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a><span data-ttu-id="1057c-126">Udostępnia MEF</span><span class="sxs-lookup"><span data-stu-id="1057c-126">What MEF Provides</span></span>  
 <span data-ttu-id="1057c-127">Zamiast jawnego rejestracji dostępnych składników MEF pozwala wykrywać je niejawnie, przy użyciu *kompozycji*.</span><span class="sxs-lookup"><span data-stu-id="1057c-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span>  <span data-ttu-id="1057c-128">Składnik MEF, o nazwie *części*, deklaratywnego określa zarówno jego zależności (znane jako *importuje*) i jakie funkcje (nazywane *eksportuje*) dostępnych.</span><span class="sxs-lookup"><span data-stu-id="1057c-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="1057c-129">Po utworzeniu części MEF aparat kompozycji spełnia jego procesów importu, co jest dostępne z innymi częściami.</span><span class="sxs-lookup"><span data-stu-id="1057c-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>  
  
 <span data-ttu-id="1057c-130">Takie podejście rozwiązuje problemy opisanych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1057c-130">This approach solves the problems discussed in the previous section.</span></span>  <span data-ttu-id="1057c-131">Ponieważ części MEF deklaratywnie określić ich możliwości, są one wykrywalny w czasie wykonywania, co oznacza, że aplikacja może sprawić, użyj elementów bez odwołań ustalony lub pliki wrażliwe konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1057c-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span>  <span data-ttu-id="1057c-132">MEF umożliwia aplikacjom na potrzeby odnajdywania i zbadać części ich metadanych bez tworzenia wystąpienia je lub nawet ładowania ich zestawów.</span><span class="sxs-lookup"><span data-stu-id="1057c-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="1057c-133">W związku z tym jest niepotrzebna dokładnie określić, kiedy i jak można załadować rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="1057c-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>  
  
 <span data-ttu-id="1057c-134">Oprócz jego podana eksportuje części można określić jego procesów importu, które zostaną wypełnione innych części.</span><span class="sxs-lookup"><span data-stu-id="1057c-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span>  <span data-ttu-id="1057c-135">To sprawia, że komunikacji między części nie tylko to możliwe, ale łatwa i pozwala na dobrej factoring kodu.</span><span class="sxs-lookup"><span data-stu-id="1057c-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="1057c-136">Na przykład usług wspólnych dla wielu składników można być brana pod uwagę w osobnym obszarze i łatwo zmodyfikowane lub zastąpione.</span><span class="sxs-lookup"><span data-stu-id="1057c-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>  
  
 <span data-ttu-id="1057c-137">MEF model wymaga nie twardych zależności zestawu aplikacji, dlatego umożliwia rozszerzenia ponowne użycie z aplikacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1057c-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span>  <span data-ttu-id="1057c-138">To ułatwia także do opracowywania kontroler testu, niezależnie od aplikacji, aby sprawdzić składniki rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1057c-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>  
  
 <span data-ttu-id="1057c-139">Aplikacji rozszerzalnej napisane przy użyciu MEF deklaruje obiektu import, który może zostać wypełniony przez składniki rozszerzenia i może deklarować także eksportuje w celu udostępnienia usług aplikacji do rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1057c-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span>  <span data-ttu-id="1057c-140">Każdy składnik rozszerzenia deklaruje eksportu i może deklarować także importów.</span><span class="sxs-lookup"><span data-stu-id="1057c-140">Each extension component declares an export, and may also declare imports.</span></span>  <span data-ttu-id="1057c-141">W ten sposób samych elementów rozszerzenia są automatycznie rozszerzonego.</span><span class="sxs-lookup"><span data-stu-id="1057c-141">In this way, extension components themselves are automatically extensible.</span></span>  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a><span data-ttu-id="1057c-142">Gdzie jest MEF?</span><span class="sxs-lookup"><span data-stu-id="1057c-142">Where Is MEF Available?</span></span>  
 <span data-ttu-id="1057c-143">MEF jest integralną częścią [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]i jest dostępna we wszystkich programu .NET Framework jest używana.</span><span class="sxs-lookup"><span data-stu-id="1057c-143">MEF is an integral part of the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], and is available wherever the .NET Framework is used.</span></span>  <span data-ttu-id="1057c-144">Można użyć MEF w aplikacjach klienckich, korzystają z formularzy systemu Windows, WPF lub innych technologii, czy w aplikacji serwerowych, które używają programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1057c-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a><span data-ttu-id="1057c-145">MEF i MAF</span><span class="sxs-lookup"><span data-stu-id="1057c-145">MEF and MAF</span></span>  
 <span data-ttu-id="1057c-146">Poprzednie wersje programu .NET Framework wprowadzono zarządzane dodatku Framework (MAF), umożliwia aplikacji w celu odizolowania i Zarządzaj rozszerzeniami.</span><span class="sxs-lookup"><span data-stu-id="1057c-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span>  <span data-ttu-id="1057c-147">MAF koncentruje się nieco wyższego niż MEF skupienie się na izolację rozszerzenia i zestawu ładowanie i zwalnianie podczas jego MEF skoncentrować się na rozszerzalności, przenośność i możliwości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="1057c-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span>  <span data-ttu-id="1057c-148">Dwie struktury bezproblemowe współdziałanie, a pojedynczą aplikacją można korzystać z obu.</span><span class="sxs-lookup"><span data-stu-id="1057c-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="1057c-149">SimpleCalculator: Przykładowa aplikacja</span><span class="sxs-lookup"><span data-stu-id="1057c-149">SimpleCalculator: An Example Application</span></span>  
 <span data-ttu-id="1057c-150">Najprostszym sposobem, aby zobaczyć, co można zrobić MEF jest utworzyć prostą aplikację MEF.</span><span class="sxs-lookup"><span data-stu-id="1057c-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="1057c-151">W tym przykładzie kompilacji jest bardzo prosty kalkulator o nazwie SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1057c-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="1057c-152">Celem SimpleCalculator jest tworzenie aplikacji konsoli, która akceptuje podstawowe polecenia arytmetyczne, w formie "5 + 3" lub "6-2" i zwraca poprawnych odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1057c-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="1057c-153">Przy użyciu MEF, można dodać nowych operatorów bez konieczności zmieniania kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1057c-153">Using MEF, you will be able to add new operators without changing the application code.</span></span>  
  
 <span data-ttu-id="1057c-154">Aby pobrać kompletny kod dla tego przykładu, zobacz [próbki SimpleCalculator](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="1057c-154">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1057c-155">Celem SimpleCalculator jest aby zademonstrować pojęcia i składni MEF, zamiast niekoniecznie zapewnienie scenariusza realistyczne jej wykorzystanie.</span><span class="sxs-lookup"><span data-stu-id="1057c-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="1057c-156">Wiele aplikacji, które mogłyby, korzystają najbardziej z możliwości MEF jest bardziej złożone niż SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1057c-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="1057c-157">Bardziej rozległych przykłady można znaleźć [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="1057c-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>
  
 <span data-ttu-id="1057c-158">Aby uruchomić w [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], Utwórz nowy projekt aplikacji konsoli o nazwie `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="1057c-158">To start, in [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], create a new Console Application project named `SimpleCalculator`.</span></span> <span data-ttu-id="1057c-159">Dodaj odwołanie do zestawu System.ComponentModel.Composition, w którym znajduje się MEF.</span><span class="sxs-lookup"><span data-stu-id="1057c-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span> <span data-ttu-id="1057c-160">Otwórz Module1.vb lub Program.cs i Dodaj `Imports` lub `using` instrukcje System.ComponentModel.Composition i System.ComponentModel.Composition.Hosting.</span><span class="sxs-lookup"><span data-stu-id="1057c-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="1057c-161">Te dwie przestrzenie nazw zawierają typy MEF musisz utworzyć aplikację rozszerzonego.</span><span class="sxs-lookup"><span data-stu-id="1057c-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span> <span data-ttu-id="1057c-162">W języku Visual Basic, Dodaj `Public` — słowo kluczowe do wiersza, który deklaruje `Module1` modułu.</span><span class="sxs-lookup"><span data-stu-id="1057c-162">In Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a><span data-ttu-id="1057c-163">Kontener kompozycji i katalogi</span><span class="sxs-lookup"><span data-stu-id="1057c-163">Composition Container and Catalogs</span></span>  
 <span data-ttu-id="1057c-164">Podstawowy model kompozycji MEF jest *kontenera kompozycji*, który zawiera wszystkie części i wykonuje kompozycji.</span><span class="sxs-lookup"><span data-stu-id="1057c-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span>  <span data-ttu-id="1057c-165">(To znaczy dopasowanie importów do eksportuje.)  Najczęściej spotykanym typem kontenera kompozycji jest <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, i zostanie ona użyta dla SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1057c-165">(That is, the matching up of imports to exports.)  The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you will use this for SimpleCalculator.</span></span>  
  
 <span data-ttu-id="1057c-166">W języku Visual Basic Module1.vb, Dodaj Klasa publiczna o nazwie `Program`.</span><span class="sxs-lookup"><span data-stu-id="1057c-166">In Visual Basic, in Module1.vb, add a public class named `Program`.</span></span> <span data-ttu-id="1057c-167">Następnie dodaj następujący wiersz do `Program` klasy Module1.vb lub pliku Program.cs:</span><span class="sxs-lookup"><span data-stu-id="1057c-167">Then add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 <span data-ttu-id="1057c-168">Aby odnaleźć elementy dostępne do niego kontenery kompozycji sprawia, że użycie *katalogu*.</span><span class="sxs-lookup"><span data-stu-id="1057c-168">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="1057c-169">Katalog jest obiekt, który sprawia, że dostępne elementy wykryte z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="1057c-169">A catalog is an object that makes available parts discovered from some source.</span></span>  <span data-ttu-id="1057c-170">MEF udostępnia katalogi do odnajdywania części z udostępnionego typu, zestawów lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="1057c-170">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="1057c-171">Deweloperzy aplikacji można łatwo utworzyć nowe katalogi do odnajdywania części z innych źródeł, takich jak usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1057c-171">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>  
  
 <span data-ttu-id="1057c-172">Dodaj następujący Konstruktor do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="1057c-172">Add the following constructor to the `Program` class:</span></span>  
  
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
  
 <span data-ttu-id="1057c-173">Wywołanie <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> informuje kontenera kompozycji utworzenie określonych części, w tym przypadku bieżące wystąpienie klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="1057c-173">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="1057c-174">W tym momencie, nic się nie stanie, ponieważ `Program` ma żadnych importów do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="1057c-174">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="1057c-175">Importu i eksportu z atrybutami</span><span class="sxs-lookup"><span data-stu-id="1057c-175">Imports and Exports with Attributes</span></span>  
 <span data-ttu-id="1057c-176">Po pierwsze, masz `Program` zaimportować Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="1057c-176">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="1057c-177">Dzięki temu rozdzielenie użytkownika interfejsu problemy, takie jak konsola przychodzących i wychodzących, które zostaną umieszczone w `Program`, z logiką Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="1057c-177">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>  
  
 <span data-ttu-id="1057c-178">Dodaj następujący kod do `Program` klasy:</span><span class="sxs-lookup"><span data-stu-id="1057c-178">Add the following code to the `Program` class:</span></span>  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 <span data-ttu-id="1057c-179">Zwróć uwagę, że deklaracja `calculator` obiekt nie jest rzadko, ale ma ona <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1057c-179">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span>  <span data-ttu-id="1057c-180">Ten atrybut deklaruje coś się importu; oznacza to, że zostaną wprowadzone przez aparat kompozycji podczas składa się obiekt.</span><span class="sxs-lookup"><span data-stu-id="1057c-180">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>  
  
 <span data-ttu-id="1057c-181">Każdego importu ma *kontraktu*, która określa, jakie eksportu zostanie dopasowana z.</span><span class="sxs-lookup"><span data-stu-id="1057c-181">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="1057c-182">Kontrakt może być jawnie określony ciąg lub jego mogą być automatycznie generowane przez MEF z danego typu, w tym przypadku interfejs `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="1057c-182">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span>  <span data-ttu-id="1057c-183">Wszelkie eksportu zadeklarowana ze zgodnego kontraktu spełniają tego importu.</span><span class="sxs-lookup"><span data-stu-id="1057c-183">Any export declared with a matching contract will fulfill this import.</span></span>  <span data-ttu-id="1057c-184">Należy pamiętać, że podczas typ `calculator` obiekt jest w rzeczywistości `ICalculator`, nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="1057c-184">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="1057c-185">Kontrakt nie zależy od typu obiektu importowania.</span><span class="sxs-lookup"><span data-stu-id="1057c-185">The contract is independent from the type of the importing object.</span></span>  <span data-ttu-id="1057c-186">(W takim przypadku można pozostawić `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="1057c-186">(In this case, you could leave out the `typeof(ICalculator)`.</span></span>  <span data-ttu-id="1057c-187">MEF automatycznie przyjmie kontraktu opartego na typ importu, chyba że jawnie określony.)</span><span class="sxs-lookup"><span data-stu-id="1057c-187">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>  
  
 <span data-ttu-id="1057c-188">Dodaj ten bardzo prosty interfejs do modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1057c-188">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="1057c-189">Teraz, gdy zdefiniowano `ICalculator`, należy klasa, która implementuje go.</span><span class="sxs-lookup"><span data-stu-id="1057c-189">Now that you have defined `ICalculator`, you need a class that implements it.</span></span>  <span data-ttu-id="1057c-190">Dodaj następujące klasy modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1057c-190">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="1057c-191">Oto eksportu odpowiadających importu w `Program`.</span><span class="sxs-lookup"><span data-stu-id="1057c-191">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="1057c-192">Aby eksportu do dopasowania importu eksportu muszą mieć ten sam kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1057c-192">In order for the export to match the import, the export must have the same contract.</span></span>  <span data-ttu-id="1057c-193">Eksportowanie na podstawie umowy, na podstawie `typeof(MySimpleCalculator)` dałby w efekcie niezgodność i importu nie może być wypełnione; kontrakt musi dokładnie pasować.</span><span class="sxs-lookup"><span data-stu-id="1057c-193">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>  
  
 <span data-ttu-id="1057c-194">Ponieważ kontener kompozycji zostanie wypełniona części dostępne w tym zestawie `MySimpleCalculator` części będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="1057c-194">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span>  <span data-ttu-id="1057c-195">Gdy konstruktora dla `Program` przeprowadzają kompozycji `Program` obiekt i jego import zostanie wypełniona `MySimpleCalculator` obiektu, który zostanie utworzony w tym celu.</span><span class="sxs-lookup"><span data-stu-id="1057c-195">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>  
  
 <span data-ttu-id="1057c-196">Warstwę interfejsu użytkownika (`Program`) nie musi wiedzieć, inaczej.</span><span class="sxs-lookup"><span data-stu-id="1057c-196">The user interface layer (`Program`) does not need to know anything else.</span></span>  <span data-ttu-id="1057c-197">W związku z tym można wprowadzić w pozostałej części logika interfejsu użytkownika w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="1057c-197">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>  
  
 <span data-ttu-id="1057c-198">Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="1057c-198">Add the following code to the `Main` method:</span></span>  
  
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
  
 <span data-ttu-id="1057c-199">Ten kod po prostu odczytuje wiersz danych wejściowych i wywołania `Calculate` funkcji `ICalculator` w wyniku powrotem zapisuje się do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1057c-199">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="1057c-200">Oznacza to cały kod w `Program`.</span><span class="sxs-lookup"><span data-stu-id="1057c-200">That is all the code you need in `Program`.</span></span>  <span data-ttu-id="1057c-201">Wszystkie pozostałe pracy nastąpi w częściach.</span><span class="sxs-lookup"><span data-stu-id="1057c-201">All the rest of the work will happen in the parts.</span></span>  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a><span data-ttu-id="1057c-202">Importy i ImportMany</span><span class="sxs-lookup"><span data-stu-id="1057c-202">Further Imports and ImportMany</span></span>  
 <span data-ttu-id="1057c-203">Aby SimpleCalculator być rozszerzalny musi zaimportować listę operacji.</span><span class="sxs-lookup"><span data-stu-id="1057c-203">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="1057c-204">Zwykły <xref:System.ComponentModel.Composition.ImportAttribute> atrybutu jest wypełniana przez jeden i tylko jeden <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1057c-204">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span>  <span data-ttu-id="1057c-205">Jeśli jest więcej niż jeden dostępny, aparat kompozycji powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="1057c-205">If more than one is available, the composition engine produces an error.</span></span>  <span data-ttu-id="1057c-206">Aby utworzyć obiektu import, który może zostać wypełniony przez dowolną liczbę eksportu, można użyć <xref:System.ComponentModel.Composition.ImportManyAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1057c-206">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>  
  
 <span data-ttu-id="1057c-207">Dodaj następujące właściwości działania do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="1057c-207">Add the following operations property to the `MySimpleCalculator` class:</span></span>  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <span data-ttu-id="1057c-208"><xref:System.Lazy%602> Typ jest zapewniana przez MEF do przechowywania pośredniego odwołania do eksportu.</span><span class="sxs-lookup"><span data-stu-id="1057c-208"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span>  <span data-ttu-id="1057c-209">W tym miejscu, oprócz samego obiektu wyeksportowanego umożliwia również wyświetlenie *Eksportowanie metadanych*, lub informacje opisujące eksportowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1057c-209">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="1057c-210">Każdy <xref:System.Lazy%602> zawiera `IOperation` obiekt reprezentujący bieżącej operacji i `IOperationData` obiekt reprezentujący jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="1057c-210">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>  
  
 <span data-ttu-id="1057c-211">Dodaj następujące proste interfejsy modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1057c-211">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="1057c-212">W takim przypadku metadanych dla każdej operacji jest symbol, który reprezentuje danej operacji, takich jak +, -, \*, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1057c-212">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="1057c-213">Aby udostępnić operacja dodawania, należy dodać następujące klasy modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1057c-213">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="1057c-214"><xref:System.ComponentModel.Composition.ExportAttribute> Atrybutu funkcje, tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="1057c-214">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span>  <span data-ttu-id="1057c-215"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> Atrybut dołącza metadanych w postaci pary nazwa wartość do tego eksportu.</span><span class="sxs-lookup"><span data-stu-id="1057c-215">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span>  <span data-ttu-id="1057c-216">Gdy `Add` klasa implementuje `IOperation`, klasy, która implementuje `IOperationData` nie jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="1057c-216">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="1057c-217">Zamiast tego klasy niejawnie jest tworzony przez MEF o właściwościach opartych na nazwach podane metadanych.</span><span class="sxs-lookup"><span data-stu-id="1057c-217">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span>  <span data-ttu-id="1057c-218">(Jest to jeden z kilku sposobów uzyskuje dostęp do metadanych w MEF.)</span><span class="sxs-lookup"><span data-stu-id="1057c-218">(This is one of several ways to access metadata in MEF.)</span></span>  
  
 <span data-ttu-id="1057c-219">Kompozycja w MEF *cykliczne*.</span><span class="sxs-lookup"><span data-stu-id="1057c-219">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="1057c-220">Należy jawnie składane `Program` obiektu, który zaimportowane `ICalculator` , który był typu `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="1057c-220">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span>  <span data-ttu-id="1057c-221">`MySimpleCalculator`, z kolei importuje Kolekcja `IOperation` obiektów i że import zostanie wprowadzona podczas `MySimpleCalculator` jest tworzony w tym samym czasie jako importów elementu `Program`.</span><span class="sxs-lookup"><span data-stu-id="1057c-221">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="1057c-222">Jeśli `Add` klasy zadeklarowany dalsze importu, który zbyt musi być wypełnione i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1057c-222">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="1057c-223">Wszelkie zaimportować po lewej stronie powoduje błąd kompozycji.</span><span class="sxs-lookup"><span data-stu-id="1057c-223">Any import left unfilled results in a composition error.</span></span>  <span data-ttu-id="1057c-224">(Jest to możliwe, jednak aby zadeklarować importów jako opcjonalną lub przypisać te wartości domyślne.)</span><span class="sxs-lookup"><span data-stu-id="1057c-224">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a><span data-ttu-id="1057c-225">Kalkulator logiki</span><span class="sxs-lookup"><span data-stu-id="1057c-225">Calculator Logic</span></span>  
 <span data-ttu-id="1057c-226">Z tych elementów w miejscu liście nie zostanie samej logiki Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="1057c-226">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="1057c-227">Dodaj następujący kod w `MySimpleCalculator` klasy do zaimplementowania `Calculate` metody:</span><span class="sxs-lookup"><span data-stu-id="1057c-227">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>  
  
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
  
 <span data-ttu-id="1057c-228">Początkowe kroki przeanalizować ciągu wejściowego w lewy i prawy operandy i znaku operatora.</span><span class="sxs-lookup"><span data-stu-id="1057c-228">The initial steps parse the input string into left and right operands and an operator character.</span></span>  <span data-ttu-id="1057c-229">W `foreach` pętli, każdy element członkowski `operations` się zbadana kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1057c-229">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="1057c-230">Te obiekty są typu <xref:System.Lazy%602>, i ich wartości metadanych i eksportowanego obiektu są dostępne z <xref:System.Lazy%602.Metadata%2A> właściwości i <xref:System.Lazy%601.Value%2A> właściwości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1057c-230">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="1057c-231">W tym przypadku jeśli `Symbol` właściwość `IOperationData` obiektu po odnalezieniu jako dopasowania, wywołania Kalkulator `Operate` metody `IOperation` obiektu i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="1057c-231">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>  
  
 <span data-ttu-id="1057c-232">Do wykonania Kalkulator, potrzebne są również metody pomocnika, która zwraca położenie pierwszego znaku,-cyfrowy w ciągu.</span><span class="sxs-lookup"><span data-stu-id="1057c-232">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span>  <span data-ttu-id="1057c-233">Dodaj następującą metodę pomocnika do `MySimpleCalculator` klasy:</span><span class="sxs-lookup"><span data-stu-id="1057c-233">Add the following helper method to the `MySimpleCalculator` class:</span></span>  
  
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
  
 <span data-ttu-id="1057c-234">Teraz można skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="1057c-234">You should now be able to compile and run the project.</span></span> <span data-ttu-id="1057c-235">W języku Visual Basic, upewnij się, że dodane `Public` słowa kluczowego `Module1`.</span><span class="sxs-lookup"><span data-stu-id="1057c-235">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="1057c-236">W oknie konsoli wpisz operacja dodawania, np. "5 + 3", a Kalkulator zwróci wyniki.</span><span class="sxs-lookup"><span data-stu-id="1057c-236">In the console window, type an addition operation, such as "5+3", and the calculator will return the results.</span></span>  <span data-ttu-id="1057c-237">Inne operator spowoduje "Operacja nie została odnaleziona!"</span><span class="sxs-lookup"><span data-stu-id="1057c-237">Any other operator will result in the "Operation Not Found!"</span></span> <span data-ttu-id="1057c-238">Komunikat.</span><span class="sxs-lookup"><span data-stu-id="1057c-238">message.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="1057c-239">Rozszerzanie SimpleCalculator przy użyciu nowej klasy</span><span class="sxs-lookup"><span data-stu-id="1057c-239">Extending SimpleCalculator Using A New Class</span></span>  
 <span data-ttu-id="1057c-240">Teraz, gdy działa Kalkulator, Dodawanie nowej operacji jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="1057c-240">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="1057c-241">Dodaj następujące klasy modułu lub `SimpleCalculator` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1057c-241">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
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
  
 <span data-ttu-id="1057c-242">Kompilowanie i uruchamianie projektu.</span><span class="sxs-lookup"><span data-stu-id="1057c-242">Compile and run the project.</span></span> <span data-ttu-id="1057c-243">Wpisz operację odejmowania, takie jak "5-3".</span><span class="sxs-lookup"><span data-stu-id="1057c-243">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="1057c-244">Kalkulator obsługuje teraz odejmowania, a także dodanie.</span><span class="sxs-lookup"><span data-stu-id="1057c-244">The calculator now supports subtraction as well as addition.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="1057c-245">Rozszerzanie SimpleCalculator przy użyciu nowego zestawu</span><span class="sxs-lookup"><span data-stu-id="1057c-245">Extending SimpleCalculator Using A New Assembly</span></span>  
 <span data-ttu-id="1057c-246">Dodawanie klas do źródła kodu jest prosta, ale MEF pozwala, aby wyszukać części poza źródła własnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1057c-246">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="1057c-247">Aby zademonstrować, to, należy zmodyfikować SimpleCalculator do przeszukania katalogu, a także własny zestaw składników, dodając <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="1057c-247">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>  
  
 <span data-ttu-id="1057c-248">Dodaj nowy katalog o nazwie `Extensions` do projektu SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1057c-248">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span>  <span data-ttu-id="1057c-249">Upewnij się dodać go na poziomie projektu, a nie na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="1057c-249">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="1057c-250">Następnie dodaj nowego projektu biblioteki klas w rozwiązaniu o nazwie `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="1057c-250">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="1057c-251">Nowy projekt zostanie skompilowany w ramach oddzielnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1057c-251">The new project will compile into a separate assembly.</span></span>  
  
 <span data-ttu-id="1057c-252">Otwórz w Projektancie właściwości projektu dla projektu ExtendedOperations i kliknij przycisk **skompilować** lub **kompilacji** kartę. Zmień **ścieżki wyjściowej kompilacji** lub **ścieżka wyjściowa** wskaż katalogu rozszerzeń w katalogu projektu SimpleCalculator (.. \SimpleCalculator\Extensions\\).</span><span class="sxs-lookup"><span data-stu-id="1057c-252">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>  
  
 <span data-ttu-id="1057c-253">W Module1.vb lub pliku Program.cs Dodaj następujący wiersz do `Program` konstruktora:</span><span class="sxs-lookup"><span data-stu-id="1057c-253">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 <span data-ttu-id="1057c-254">Zamień ścieżki przykład ścieżki do katalogu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1057c-254">Replace the example path with the path to your Extensions directory.</span></span>  <span data-ttu-id="1057c-255">(Jest to ścieżka bezwzględna do debugowania tylko do celów.</span><span class="sxs-lookup"><span data-stu-id="1057c-255">(This absolute path is for debugging purposes only.</span></span>  <span data-ttu-id="1057c-256">W aplikacji produkcyjnej należy użyć ścieżki względnej.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Teraz doda żadnych części w wszystkie zestawy w katalogu rozszerzeń do kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="1057c-256">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>  
  
 <span data-ttu-id="1057c-257">W projekcie ExtendedOperations Dodaj odwołania do SimpleCalculator i System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="1057c-257">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="1057c-258">Plik klasy ExtendedOperations, Dodaj `Imports` lub `using` instrukcji dla System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="1057c-258">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="1057c-259">W języku Visual Basic, należy również dodać `Imports` instrukcji dla SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="1057c-259">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="1057c-260">Następnie dodaj następujące klasy w pliku klasy ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="1057c-260">Then add the following class to the ExtendedOperations class file:</span></span>  
  
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
  
 <span data-ttu-id="1057c-261">Należy pamiętać, aby tej umowy do dopasowania, <xref:System.ComponentModel.Composition.ExportAttribute> atrybut musi mieć taki sam typ jak <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1057c-261">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>  
  
 <span data-ttu-id="1057c-262">Kompilowanie i uruchamianie projektu.</span><span class="sxs-lookup"><span data-stu-id="1057c-262">Compile and run the project.</span></span> <span data-ttu-id="1057c-263">Przetestuj nowy operator Mod (%).</span><span class="sxs-lookup"><span data-stu-id="1057c-263">Test the new Mod (%) operator.</span></span>  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="1057c-264">Wniosek</span><span class="sxs-lookup"><span data-stu-id="1057c-264">Conclusion</span></span>  
 <span data-ttu-id="1057c-265">W tym temacie opisano podstawowe pojęcia MEF.</span><span class="sxs-lookup"><span data-stu-id="1057c-265">This topic covered the basic concepts of MEF.</span></span>  
  
-   <span data-ttu-id="1057c-266">Części, katalogów i kontener kompozycji</span><span class="sxs-lookup"><span data-stu-id="1057c-266">Parts, catalogs, and the composition container</span></span>  
  
     <span data-ttu-id="1057c-267">Części i kontener kompozycji są podstawowe bloki konstrukcyjne aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="1057c-267">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="1057c-268">Element jest dowolny obiekt, który importuje lub eksportuje wartość, w tym sam.</span><span class="sxs-lookup"><span data-stu-id="1057c-268">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="1057c-269">Katalog udostępnia kolekcję części z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="1057c-269">A catalog provides a collection of parts from a particular source.</span></span>  <span data-ttu-id="1057c-270">Kontener kompozycji używa części udostępniane przez wykaz do utworzenia powiązania importów do eksportu.</span><span class="sxs-lookup"><span data-stu-id="1057c-270">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>  
  
-   <span data-ttu-id="1057c-271">Importu i eksportu</span><span class="sxs-lookup"><span data-stu-id="1057c-271">Imports and exports</span></span>  
  
     <span data-ttu-id="1057c-272">Importu i eksportu są sposób za pomocą którego komunikują się składników.</span><span class="sxs-lookup"><span data-stu-id="1057c-272">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="1057c-273">Importowania składnika określa potrzeba obiektu lub określonej wartości, i z eksportu określa dostępność wartość.</span><span class="sxs-lookup"><span data-stu-id="1057c-273">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="1057c-274">Każdej operacji importowania jest zgodny z listą eksporty i jej kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1057c-274">Each import is matched with a list of exports by way of its contract.</span></span>  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a><span data-ttu-id="1057c-275">Gdzie mogę teraz?</span><span class="sxs-lookup"><span data-stu-id="1057c-275">Where Do I Go Now?</span></span>  
 <span data-ttu-id="1057c-276">Aby pobrać kompletny kod dla tego przykładu, zobacz [próbki SimpleCalculator](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span><span class="sxs-lookup"><span data-stu-id="1057c-276">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
 <span data-ttu-id="1057c-277">Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span><span class="sxs-lookup"><span data-stu-id="1057c-277">For more information and code examples, see [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span></span> <span data-ttu-id="1057c-278">Aby uzyskać listę typów MEF, zobacz <xref:System.ComponentModel.Composition?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1057c-278">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
