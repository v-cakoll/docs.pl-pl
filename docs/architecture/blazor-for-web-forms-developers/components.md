---
title: Kompiluj składniki interfejsu użytkownika wielokrotnego użytku z Blazor
description: Dowiedz się, jak tworzyć składniki interfejsu użytkownika wielokrotnego użytku przy użyciu programu Blazor i porównać je z kontrolkami formularzy sieci Web ASP.NET.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: b461cf1b572de389c746b894d79d157bf2791e48
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183953"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="14a11-103">Kompiluj składniki interfejsu użytkownika wielokrotnego użytku z Blazor</span><span class="sxs-lookup"><span data-stu-id="14a11-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="14a11-104">Jednym z atrakcyjnych elementów formularzy sieci Web ASP.NET jest to, jak umożliwia hermetyzację fragmentów kodu interfejsu użytkownika do wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="14a11-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="14a11-105">Niestandardowe kontrolki użytkownika można definiować w znacznikach przy użyciu plików *. ascx* .</span><span class="sxs-lookup"><span data-stu-id="14a11-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="14a11-106">Można również tworzyć rozbudowane kontrolki serwera w kodzie za pomocą pełnego wsparcia projektanta.</span><span class="sxs-lookup"><span data-stu-id="14a11-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="14a11-107">Blazor obsługuje także hermetyzację interfejsu użytkownika za poorednictwem *składników*.</span><span class="sxs-lookup"><span data-stu-id="14a11-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="14a11-108">Składnik:</span><span class="sxs-lookup"><span data-stu-id="14a11-108">A component:</span></span>

* <span data-ttu-id="14a11-109">Jest samodzielnym fragmentem interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14a11-109">Is a self-contained chunk of UI.</span></span>
* <span data-ttu-id="14a11-110">Utrzymuje własny stan i logikę renderowania.</span><span class="sxs-lookup"><span data-stu-id="14a11-110">Maintains its own state and rendering logic.</span></span>
* <span data-ttu-id="14a11-111">Można zdefiniować procedury obsługi zdarzeń interfejsu użytkownika, powiązać dane wejściowe i zarządzać własnym cyklem życia.</span><span class="sxs-lookup"><span data-stu-id="14a11-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
* <span data-ttu-id="14a11-112">Jest zazwyczaj definiowana w pliku *Razor* przy użyciu składnia Razor.</span><span class="sxs-lookup"><span data-stu-id="14a11-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="14a11-113">Wprowadzenie do Razor</span><span class="sxs-lookup"><span data-stu-id="14a11-113">An introduction to Razor</span></span>

<span data-ttu-id="14a11-114">Razor to lekki język tworzenia szablonów znaczników oparty na kodzie HTML i C#.</span><span class="sxs-lookup"><span data-stu-id="14a11-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="14a11-115">Przy użyciu Razor można bezproblemowo przechodzić między znacznikami i C# kodem w celu zdefiniowania logiki renderowania składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="14a11-116">Po skompilowaniu pliku *Razor* logika renderowania jest przechwytywana w sposób uporządkowany w klasie .NET.</span><span class="sxs-lookup"><span data-stu-id="14a11-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="14a11-117">Nazwa skompilowanej klasy jest pobierana z nazwy pliku *Razor* .</span><span class="sxs-lookup"><span data-stu-id="14a11-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="14a11-118">Przestrzeń nazw jest pobierana z domyślnej przestrzeni nazw dla projektu i ścieżki folderu, lub można jawnie określić przestrzeń nazw za pomocą `@namespace` dyrektywy (więcej informacji na temat poniższych dyrektyw Razor).</span><span class="sxs-lookup"><span data-stu-id="14a11-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="14a11-119">Logika renderowania składnika jest utworzona przy użyciu standardowego znacznika HTML z dynamiczną logiką dodaną przy użyciu C#.</span><span class="sxs-lookup"><span data-stu-id="14a11-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="14a11-120">Znak jest używany do przejścia do C# `@`</span><span class="sxs-lookup"><span data-stu-id="14a11-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="14a11-121">Razor jest zazwyczaj inteligentnym sposobem na ustalenie, kiedy przełączono z powrotem do formatu HTML.</span><span class="sxs-lookup"><span data-stu-id="14a11-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="14a11-122">Na przykład poniższy składnik renderuje `<p>` tag z bieżącym czasem:</span><span class="sxs-lookup"><span data-stu-id="14a11-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="14a11-123">Aby jawnie określić początek i koniec C# wyrażenia, użyj nawiasów:</span><span class="sxs-lookup"><span data-stu-id="14a11-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="14a11-124">Razor również ułatwia użycie C# przepływu sterowania w logice renderowania.</span><span class="sxs-lookup"><span data-stu-id="14a11-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="14a11-125">Na przykład można warunkowo renderować niektóre HTML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="14a11-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="14a11-126">Można też wygenerować listę elementów przy użyciu zwykłej C# `foreach` pętli podobnej do:</span><span class="sxs-lookup"><span data-stu-id="14a11-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

<span data-ttu-id="14a11-127">Dyrektywy Razor, podobnie jak dyrektywy w ASP.NET Web Forms, kontrolują wiele aspektów sposobu kompilowania składnika Razor.</span><span class="sxs-lookup"><span data-stu-id="14a11-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="14a11-128">Przykłady obejmują:</span><span class="sxs-lookup"><span data-stu-id="14a11-128">Examples include the component's:</span></span>

* <span data-ttu-id="14a11-129">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="14a11-129">Namespace</span></span>
* <span data-ttu-id="14a11-130">Klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="14a11-130">Base class</span></span>
* <span data-ttu-id="14a11-131">Zaimplementowane interfejsy</span><span class="sxs-lookup"><span data-stu-id="14a11-131">Implemented interfaces</span></span>
* <span data-ttu-id="14a11-132">Parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="14a11-132">Generic parameters</span></span>
* <span data-ttu-id="14a11-133">Zaimportowane przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="14a11-133">Imported namespaces</span></span>
* <span data-ttu-id="14a11-134">Rozsyłan</span><span class="sxs-lookup"><span data-stu-id="14a11-134">Routes</span></span>

<span data-ttu-id="14a11-135">Dyrektywy Razor zaczynają się `@` od znaku i są zwykle używane na początku nowego wiersza na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="14a11-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="14a11-136">Na przykład `@namespace` dyrektywa definiuje przestrzeń nazw składnika:</span><span class="sxs-lookup"><span data-stu-id="14a11-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="14a11-137">Poniższa tabela zawiera podsumowanie różnych dyrektyw Razor używanych w Blazor i ich odpowiedników formularzy sieci Web ASP.NET, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="14a11-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="14a11-138">— Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="14a11-138">Directive</span></span>    |<span data-ttu-id="14a11-139">Opis</span><span class="sxs-lookup"><span data-stu-id="14a11-139">Description</span></span>|<span data-ttu-id="14a11-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="14a11-140">Example</span></span>|<span data-ttu-id="14a11-141">Odpowiednik formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="14a11-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="14a11-142">Dodaje atrybut Level klasy do składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="14a11-143">Brak</span><span class="sxs-lookup"><span data-stu-id="14a11-143">None</span></span>|
|`@code`      |<span data-ttu-id="14a11-144">Dodaje składowe klasy do składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="14a11-145">Implementuje określony interfejs</span><span class="sxs-lookup"><span data-stu-id="14a11-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="14a11-146">Użyj kodu</span><span class="sxs-lookup"><span data-stu-id="14a11-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="14a11-147">Dziedziczy z określonej klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="14a11-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="14a11-148">Wprowadza usługę do składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="14a11-149">Brak</span><span class="sxs-lookup"><span data-stu-id="14a11-149">None</span></span>|
|`@layout`    |<span data-ttu-id="14a11-150">Określa składnik układu dla składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="14a11-151">Ustawia przestrzeń nazw dla składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="14a11-152">Brak</span><span class="sxs-lookup"><span data-stu-id="14a11-152">None</span></span>|
|`@page`      |<span data-ttu-id="14a11-153">Określa trasę dla składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="14a11-154">Określa parametr typu ogólnego dla składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="14a11-155">Użyj kodu</span><span class="sxs-lookup"><span data-stu-id="14a11-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="14a11-156">Określa przestrzeń nazw do dołączenia do zakresu</span><span class="sxs-lookup"><span data-stu-id="14a11-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="14a11-157">Dodaj przestrzeń nazw w *pliku Web. config*</span><span class="sxs-lookup"><span data-stu-id="14a11-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="14a11-158">Składniki Razor również dzielą użycie *atrybutów dyrektywy* dla elementów w celu kontrolowania różnych aspektów kompilowania składników (obsługa zdarzeń, powiązanie danych, składnik & odwołań elementów itp.).</span><span class="sxs-lookup"><span data-stu-id="14a11-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="14a11-159">Atrybuty dyrektywy All są zgodne ze wspólną składnią ogólną, w której wartości w nawiasach są opcjonalne:</span><span class="sxs-lookup"><span data-stu-id="14a11-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="14a11-160">Poniższa tabela zawiera podsumowanie różnych atrybutów dyrektyw Razor używanych w Blazor.</span><span class="sxs-lookup"><span data-stu-id="14a11-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="14a11-161">Atrybut</span><span class="sxs-lookup"><span data-stu-id="14a11-161">Attribute</span></span>    |<span data-ttu-id="14a11-162">Opis</span><span class="sxs-lookup"><span data-stu-id="14a11-162">Description</span></span>|<span data-ttu-id="14a11-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="14a11-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="14a11-164">Renderuje słownik atrybutów</span><span class="sxs-lookup"><span data-stu-id="14a11-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="14a11-165">Tworzy dwukierunkowe powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="14a11-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="14a11-166">Dodaje program obsługi zdarzeń dla określonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="14a11-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="14a11-167">Określa klucz, który ma być używany przez algorytm porównujący do zachowywania elementów w kolekcji</span><span class="sxs-lookup"><span data-stu-id="14a11-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="14a11-168">Przechwytuje odwołanie do składnika lub elementu HTML</span><span class="sxs-lookup"><span data-stu-id="14a11-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="14a11-169">Różne atrybuty dyrektywy używane przez Blazor (`@onclick`, `@bind`, `@ref`, i tak dalej) zostały omówione w poniższych sekcjach i w dalszej części rozdziału.</span><span class="sxs-lookup"><span data-stu-id="14a11-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="14a11-170">Wiele składni używanych w plikach *. aspx* i *. ascx* ma składnie równoległe w Razor.</span><span class="sxs-lookup"><span data-stu-id="14a11-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="14a11-171">Poniżej znajduje się proste porównanie składni dla ASP.NET Web Forms i Razor.</span><span class="sxs-lookup"><span data-stu-id="14a11-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="14a11-172">Funkcja</span><span class="sxs-lookup"><span data-stu-id="14a11-172">Feature</span></span>                      |<span data-ttu-id="14a11-173">Formularze sieci Web</span><span class="sxs-lookup"><span data-stu-id="14a11-173">Web Forms</span></span>           |<span data-ttu-id="14a11-174">Składnia</span><span class="sxs-lookup"><span data-stu-id="14a11-174">Syntax</span></span>               |<span data-ttu-id="14a11-175">Razor</span><span class="sxs-lookup"><span data-stu-id="14a11-175">Razor</span></span>         |<span data-ttu-id="14a11-176">Składnia</span><span class="sxs-lookup"><span data-stu-id="14a11-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="14a11-177">Dyrektyw</span><span class="sxs-lookup"><span data-stu-id="14a11-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="14a11-178">Bloki kodu</span><span class="sxs-lookup"><span data-stu-id="14a11-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="14a11-179">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="14a11-179">Expressions</span></span><br><span data-ttu-id="14a11-180">(Kodowane HTML)</span><span class="sxs-lookup"><span data-stu-id="14a11-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="14a11-181">Konwersja`@`</span><span class="sxs-lookup"><span data-stu-id="14a11-181">Implicit: `@`</span></span><br><span data-ttu-id="14a11-182">Wprost`@()`</span><span class="sxs-lookup"><span data-stu-id="14a11-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="14a11-183">Komentarze</span><span class="sxs-lookup"><span data-stu-id="14a11-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="14a11-184">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="14a11-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="14a11-185">Aby dodać elementy członkowskie do klasy składnika Razor, użyj `@code` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="14a11-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="14a11-186">Ta technika jest podobna do użycia `<script runat="server">...</script>` bloku w kontrolce użytkownika lub stronie formularzy sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="14a11-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="14a11-187">Ze względu na to C#, że Razor jest oparta na, musi C# być skompilowana z poziomu projektu ( *. csproj*).</span><span class="sxs-lookup"><span data-stu-id="14a11-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="14a11-188">Nie można kompilować plików *Razor* z projektu VB ( *. vbproj*).</span><span class="sxs-lookup"><span data-stu-id="14a11-188">You can't compile *.razor* files from a VB project (*.vbproj*).</span></span> <span data-ttu-id="14a11-189">Nadal można odwoływać się do projektów VB z projektu Blazor.</span><span class="sxs-lookup"><span data-stu-id="14a11-189">You can still reference VB projects from your Blazor project.</span></span> <span data-ttu-id="14a11-190">Przeciwieństwo jest również prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="14a11-190">The opposite is true too.</span></span>

<span data-ttu-id="14a11-191">Aby uzyskać pełne informacje dotyczące składnia Razor, zobacz [składnia Razor Reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="14a11-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="14a11-192">Używanie składników</span><span class="sxs-lookup"><span data-stu-id="14a11-192">Use components</span></span>

<span data-ttu-id="14a11-193">Oprócz normalnego HTML składniki mogą również używać innych składników jako części logiki renderowania.</span><span class="sxs-lookup"><span data-stu-id="14a11-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="14a11-194">Składnia służąca do używania składnika w Razor jest podobna do użycia kontrolki użytkownika w aplikacji ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="14a11-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="14a11-195">Składniki są określane przy użyciu tagu elementu, który jest zgodny z nazwą typu składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="14a11-196">Na przykład można dodać `Counter` składnik podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="14a11-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="14a11-197">W przeciwieństwie do ASP.NET formularzy sieci Web, składników w Blazor:</span><span class="sxs-lookup"><span data-stu-id="14a11-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

* <span data-ttu-id="14a11-198">Nie używaj prefiksu elementu (na przykład `asp:`).</span><span class="sxs-lookup"><span data-stu-id="14a11-198">Don't use an element prefix (for example, `asp:`).</span></span>
* <span data-ttu-id="14a11-199">Nie wymagaj rejestracji na stronie lub w *pliku Web. config*.</span><span class="sxs-lookup"><span data-stu-id="14a11-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="14a11-200">Należy wziąć pod uwagę składniki Razor, takie jak typy .NET, ponieważ dokładnie te elementy są.</span><span class="sxs-lookup"><span data-stu-id="14a11-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="14a11-201">Jeśli zestaw zawierający składnik jest przywoływany, składnik jest dostępny do użycia.</span><span class="sxs-lookup"><span data-stu-id="14a11-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="14a11-202">Aby przenieść przestrzeń nazw składnika do zakresu, Zastosuj `@using` dyrektywę:</span><span class="sxs-lookup"><span data-stu-id="14a11-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="14a11-203">Tak jak w przypadku domyślnych projektów Blazor, często należy umieścić `@using` dyrektywy w pliku *_Imports. Razor* , aby zostały zaimportowane do wszystkich plików *. Razor* w tym samym katalogu i w katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="14a11-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="14a11-204">Jeśli przestrzeń nazw składnika nie znajduje się w zakresie, możesz określić składnik przy użyciu jego pełnej nazwy typu, jak można w C#:</span><span class="sxs-lookup"><span data-stu-id="14a11-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="14a11-205">Parametry składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-205">Component parameters</span></span>

<span data-ttu-id="14a11-206">W formularzach sieci Web ASP.NET można przepływać parametry i dane do kontrolek przy użyciu właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="14a11-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="14a11-207">Te właściwości można ustawić w znacznikach przy użyciu atrybutów lub ustawionych bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="14a11-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="14a11-208">Składniki Blazor działają w podobny sposób, chociaż właściwości składnika również muszą być oznaczone `[Parameter]` atrybutem, który ma być traktowany jako parametry składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="14a11-209">Poniższy `Counter` składnik definiuje parametr składnika o nazwie `IncrementAmount` , który może służyć do określenia kwoty, którą należy zwiększyć `Counter` przy każdym kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="14a11-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="14a11-210">Aby określić parametr składnika w Blazor, Użyj atrybutu tak jak w ASP.NET Web Forms:</span><span class="sxs-lookup"><span data-stu-id="14a11-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="14a11-211">Programy obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="14a11-211">Event handlers</span></span>

<span data-ttu-id="14a11-212">Zarówno ASP.NET Web Forms, jak i Blazor zapewniają oparty na zdarzeniach model programowania do obsługi zdarzeń interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14a11-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="14a11-213">Przykłady takich zdarzeń obejmują kliknięcia przycisku i wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="14a11-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="14a11-214">W formularzach sieci Web ASP.NET używasz kontrolek serwera HTML do obsługi zdarzeń interfejsu użytkownika uwidocznionych przez DOM lub można obsługiwać zdarzenia udostępniane przez formanty serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="14a11-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="14a11-215">Zdarzenia są nakierowane na serwer za pomocą żądań post-Back.</span><span class="sxs-lookup"><span data-stu-id="14a11-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="14a11-216">Rozważmy poniższy przycisk formularzy sieci Web, a następnie kliknij przycisk przykład:</span><span class="sxs-lookup"><span data-stu-id="14a11-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="14a11-217">*Counter. ascx*</span><span class="sxs-lookup"><span data-stu-id="14a11-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="14a11-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="14a11-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="14a11-219">W programie Blazor można rejestrować procedury obsługi zdarzeń interfejsu użytkownika DOM bezpośrednio przy użyciu atrybutów dyrektywy formularza `@on{event}`.</span><span class="sxs-lookup"><span data-stu-id="14a11-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="14a11-220">`{event}` Symbol zastępczy reprezentuje nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="14a11-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="14a11-221">Na przykład można nasłuchiwać przycisku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="14a11-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="14a11-222">Procedury obsługi zdarzeń mogą akceptować opcjonalny, specyficzny dla zdarzenia argument, aby uzyskać więcej informacji o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="14a11-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="14a11-223">Na przykład zdarzenia myszy mogą przyjmować `MouseEventArgs` argument, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="14a11-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e) 
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="14a11-224">Zamiast odwoływać się do grupy metod programu obsługi zdarzeń, można użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="14a11-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="14a11-225">Wyrażenie lambda umożliwia zamknięcie innych wartości w zakresie.</span><span class="sxs-lookup"><span data-stu-id="14a11-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="14a11-226">Procedury obsługi zdarzeń mogą być wykonywane synchronicznie lub asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="14a11-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="14a11-227">Na przykład następująca `OnClick` procedura obsługi zdarzeń wykonuje asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="14a11-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick() 
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="14a11-228">Po obsłudze zdarzenia składnik jest renderowany w celu uwzględnienia zmian stanu składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="14a11-229">W przypadku obsługi zdarzeń asynchronicznych składnik jest renderowany natychmiast po zakończeniu wykonywania procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="14a11-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="14a11-230">Składnik jest renderowany *ponownie* po asynchronicznym `Task` zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="14a11-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="14a11-231">Ten asynchroniczny tryb wykonywania umożliwia renderowanie niektórych odpowiednich interfejsów użytkownika, podczas gdy `Task` asynchroniczne jest nadal w toku.</span><span class="sxs-lookup"><span data-stu-id="14a11-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="Get message">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code 
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="14a11-232">Składniki mogą także definiować własne zdarzenia przez zdefiniowanie parametru składnika typu `EventCallback<TValue>`.</span><span class="sxs-lookup"><span data-stu-id="14a11-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="14a11-233">Wywołania zwrotne zdarzeń obsługują wszystkie odmiany programów obsługi zdarzeń interfejsu użytkownika DOM: argumenty opcjonalne, synchroniczne lub asynchroniczne, grupy metod lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="14a11-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="14a11-234">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="14a11-234">Data binding</span></span>

<span data-ttu-id="14a11-235">Blazor zapewnia prosty mechanizm wiązania danych ze składnika interfejsu użytkownika ze stanem składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="14a11-236">Takie podejście różni się od funkcji w formularzach sieci Web ASP.NET w celu powiązania danych ze źródeł danych z kontrolkami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14a11-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="14a11-237">Będziemy odkrywać dane obsługi z różnych źródeł danych w sekcji [dotyczącej danych](data.md) .</span><span class="sxs-lookup"><span data-stu-id="14a11-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="14a11-238">Aby utworzyć dwukierunkowe powiązanie danych ze składnika interfejsu użytkownika ze stanem składnika, użyj `@bind` atrybutu dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="14a11-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="14a11-239">W poniższym przykładzie wartość pola wyboru jest powiązana `isChecked` z polem.</span><span class="sxs-lookup"><span data-stu-id="14a11-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="14a11-240">Gdy składnik jest renderowany, wartość pola wyboru jest ustawiana na wartość w `isChecked` polu.</span><span class="sxs-lookup"><span data-stu-id="14a11-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="14a11-241">Gdy użytkownik przełącza pole wyboru, `onchange` zdarzenie jest wywoływane, `isChecked` a pole jest ustawione na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="14a11-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="14a11-242">`@bind` Składnia w tym przypadku jest równoważna następującym znacznikiem:</span><span class="sxs-lookup"><span data-stu-id="14a11-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="14a11-243">Aby zmienić zdarzenie używane dla powiązania, użyj `@bind:event` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14a11-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="14a11-244">Składniki mogą również obsługiwać powiązanie danych z parametrami.</span><span class="sxs-lookup"><span data-stu-id="14a11-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="14a11-245">Aby powiązać dane, zdefiniuj parametr wywołania zwrotnego zdarzenia o takiej samej nazwie jak parametr możliwy do powiązania.</span><span class="sxs-lookup"><span data-stu-id="14a11-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="14a11-246">Sufiks "zmieniony" został dodany do nazwy.</span><span class="sxs-lookup"><span data-stu-id="14a11-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="14a11-247">*PasswordBox. Razor*</span><span class="sxs-lookup"><span data-stu-id="14a11-247">*PasswordBox.razor*</span></span>

```razor
Password: <input 
    value="@Password" 
    @oninput="OnPasswordChanged" 
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="14a11-248">Aby połączyć dane z podstawowym elementem interfejsu użytkownika, należy ustawić wartość i obsłużyć zdarzenie bezpośrednio dla elementu interfejsu użytkownika zamiast używać `@bind` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14a11-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="14a11-249">Aby powiązać z parametrem składnika, użyj `@bind-{Parameter}` atrybutu, aby określić parametr, do którego chcesz utworzyć powiązanie.</span><span class="sxs-lookup"><span data-stu-id="14a11-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="14a11-250">Zmiany stanu</span><span class="sxs-lookup"><span data-stu-id="14a11-250">State changes</span></span>

<span data-ttu-id="14a11-251">Jeśli stan składnika uległ zmianie poza normalnym zdarzeniem interfejsu użytkownika lub wywołaniem zwrotnym zdarzenia, składnik musi ręcznie sygnalizować, że musi być renderowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="14a11-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="14a11-252">Aby sygnalizować zmianę stanu składnika, wywołaj `StateHasChanged` metodę w składniku.</span><span class="sxs-lookup"><span data-stu-id="14a11-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="14a11-253">W poniższym przykładzie składnik wyświetla komunikat z `AppState` usługi, którą można zaktualizować za pomocą innych części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14a11-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="14a11-254">Składnik rejestruje `StateHasChanged` metodę `AppState.OnChange` ze zdarzeniem, aby składnik był renderowany za każdym razem, gdy komunikat zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="14a11-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="14a11-255">Cykl życia składnika</span><span class="sxs-lookup"><span data-stu-id="14a11-255">Component lifecycle</span></span>

<span data-ttu-id="14a11-256">Struktura formularzy sieci Web ASP.NET ma dobrze zdefiniowane metody cyklu życia dla modułów, stron i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="14a11-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="14a11-257">Na przykład poniższy formant implementuje programy obsługi zdarzeń dla `Init`zdarzeń, `Load`i `UnLoad` cyklu życia:</span><span class="sxs-lookup"><span data-stu-id="14a11-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="14a11-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="14a11-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="14a11-259">Składniki Blazor mają również dobrze zdefiniowany cykl życia.</span><span class="sxs-lookup"><span data-stu-id="14a11-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="14a11-260">Cykl życia składnika może służyć do inicjowania stanu składnika i implementowania zaawansowanych zachowań składników.</span><span class="sxs-lookup"><span data-stu-id="14a11-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span> 

<span data-ttu-id="14a11-261">Wszystkie metody cyklu życia składnika Blazor mają wersje synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="14a11-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="14a11-262">Renderowanie składnika jest synchroniczne.</span><span class="sxs-lookup"><span data-stu-id="14a11-262">Component rendering is synchronous.</span></span> <span data-ttu-id="14a11-263">Nie można uruchomić logiki asynchronicznej jako części renderowania składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="14a11-264">Wszystkie logiki asynchroniczne muszą zostać wykonane w ramach `async` metody cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="14a11-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="14a11-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="14a11-265">OnInitialized</span></span>

<span data-ttu-id="14a11-266">Metody `OnInitialized` i`OnInitializedAsync` są używane do inicjowania składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="14a11-267">Składnik jest zazwyczaj inicjowany po pierwszym renderowaniu.</span><span class="sxs-lookup"><span data-stu-id="14a11-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="14a11-268">Po zainicjowaniu składnika można go renderować wiele razy, zanim zostanie ostatecznie usunięty.</span><span class="sxs-lookup"><span data-stu-id="14a11-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="14a11-269">Metoda jest podobna `Page_Load` do zdarzenia na stronach i formantach formularzy sieci Web ASP.NET. `OnInitialized`</span><span class="sxs-lookup"><span data-stu-id="14a11-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="14a11-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="14a11-270">OnParametersSet</span></span>

<span data-ttu-id="14a11-271">Metody `OnParametersSet` i`OnParametersSetAsync` są wywoływane, gdy składnik otrzymał parametry z jego elementu nadrzędnego, a wartość jest przypisana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="14a11-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="14a11-272">Te metody są wykonywane po zainicjowaniu składnika i za *każdym razem, gdy składnik jest renderowany*.</span><span class="sxs-lookup"><span data-stu-id="14a11-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="14a11-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="14a11-273">OnAfterRender</span></span>

<span data-ttu-id="14a11-274">Metody `OnAfterRender` i`OnAfterRenderAsync` są wywoływane po zakończeniu renderowania składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="14a11-275">Odwołania do elementów i składników są wypełniane w tym punkcie (więcej informacji znajduje się poniżej).</span><span class="sxs-lookup"><span data-stu-id="14a11-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="14a11-276">W tym momencie jest włączona funkcja interaktywność z przeglądarką.</span><span class="sxs-lookup"><span data-stu-id="14a11-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="14a11-277">Interakcje z obsługą DOM i wykonanie kodu JavaScript mogą być bezpiecznie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="14a11-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span> 

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="14a11-278">`OnAfterRender`i `OnAfterRenderAsync` *nie są wywoływane podczas renderowania na serwerze*.</span><span class="sxs-lookup"><span data-stu-id="14a11-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="14a11-279">Parametr jest `true` przy pierwszym renderowaniu składnika; w przeciwnym razie jego wartość to `false`. `firstRender`</span><span class="sxs-lookup"><span data-stu-id="14a11-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="14a11-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="14a11-280">IDisposable</span></span>

<span data-ttu-id="14a11-281">Składniki Blazor można zaimplementować `IDisposable` do usuwania zasobów, gdy składnik zostanie usunięty z interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14a11-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="14a11-282">Składnik Razor można zaimplementować `IDispose` przy `@implements` użyciu dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="14a11-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="14a11-283">Przechwyć odwołania do składników</span><span class="sxs-lookup"><span data-stu-id="14a11-283">Capture component references</span></span>

<span data-ttu-id="14a11-284">W programie ASP.NET Web Forms często można manipulować wystąpieniem formantu bezpośrednio w kodzie, odwołując się do jego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="14a11-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="14a11-285">W Blazor jest również możliwe przechwycenie i manipulowanie odwołaniem do składnika, chociaż jest to znacznie mniej typowe.</span><span class="sxs-lookup"><span data-stu-id="14a11-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="14a11-286">Aby przechwycić odwołanie do składnika w Blazor, należy `@ref` użyć atrybutu dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="14a11-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="14a11-287">Wartość atrybutu powinna być zgodna z nazwą pola settable o tym samym typie co składnik, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="14a11-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="14a11-288">Gdy składnik nadrzędny jest renderowany, pole zostanie wypełnione wystąpieniem składnika podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="14a11-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="14a11-289">Następnie można wywołać metody lub w inny sposób manipulować wystąpieniem składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="14a11-290">Manipulowanie stanem składnika bezpośrednio przy użyciu odwołań do składników nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="14a11-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="14a11-291">Uniemożliwia to automatyczne renderowanie składnika w prawidłowym czasie.</span><span class="sxs-lookup"><span data-stu-id="14a11-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="14a11-292">Przechwyć odwołania do elementów</span><span class="sxs-lookup"><span data-stu-id="14a11-292">Capture element references</span></span>

<span data-ttu-id="14a11-293">Składniki Blazor mogą przechwytywać odwołania do elementu.</span><span class="sxs-lookup"><span data-stu-id="14a11-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="14a11-294">W przeciwieństwie do kontrolek serwera HTML w formularzach sieci Web ASP.NET nie można manipulować modelem DOM bezpośrednio przy użyciu odwołania do elementu w Blazor.</span><span class="sxs-lookup"><span data-stu-id="14a11-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="14a11-295">Blazor obsługuje większość interakcji z modelem DOM przy użyciu algorytmu różnicowania modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="14a11-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="14a11-296">Przechwycone odwołania do elementów w Blazor są nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="14a11-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="14a11-297">Są one jednak używane do przekazywania określonego odwołania do elementu w wywołaniu JavaScript Interop.</span><span class="sxs-lookup"><span data-stu-id="14a11-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="14a11-298">Aby uzyskać więcej informacji na temat międzyoperacyjności języka JavaScript, zobacz [ASP.NET Core Blazoring JavaScript Interop](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="14a11-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="14a11-299">Składniki z szablonami</span><span class="sxs-lookup"><span data-stu-id="14a11-299">Templated components</span></span>

<span data-ttu-id="14a11-300">W formularzach sieci Web ASP.NET można tworzyć *kontrolki z szablonami*.</span><span class="sxs-lookup"><span data-stu-id="14a11-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="14a11-301">Kontrolki z szablonami umożliwiają deweloperowi określenie fragmentu kodu HTML służącego do renderowania kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="14a11-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="14a11-302">Mechanics kompilowania formantów serwera są złożone, ale zapewniają zaawansowane scenariusze renderowania danych w sposób dostosowywalny przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14a11-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="14a11-303">Przykłady formantów z szablonami obejmują `Repeater` i `DataList`.</span><span class="sxs-lookup"><span data-stu-id="14a11-303">Examples of templated controls include `Repeater` and `DataList`.</span></span> 

<span data-ttu-id="14a11-304">Składniki Blazor można także definiować za pomocą definiowania parametrów składnika typu `RenderFragment` lub. `RenderFragment<T>`</span><span class="sxs-lookup"><span data-stu-id="14a11-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="14a11-305">`RenderFragment` Reprezentuje fragment znacznika Razor, który będzie następnie renderowany przez składnik.</span><span class="sxs-lookup"><span data-stu-id="14a11-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="14a11-306">A `RenderFragment<T>` to fragment znacznika Razor, który przyjmuje parametr, który można określić podczas renderowania fragmentu renderowania.</span><span class="sxs-lookup"><span data-stu-id="14a11-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="14a11-307">Zawartość podrzędna</span><span class="sxs-lookup"><span data-stu-id="14a11-307">Child content</span></span>

<span data-ttu-id="14a11-308">Składniki Blazor mogą przechwytywać zawartość podrzędną jako `RenderFragment` i renderować tę zawartość w ramach renderowania składników.</span><span class="sxs-lookup"><span data-stu-id="14a11-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="14a11-309">Aby przechwycić zawartość podrzędną, zdefiniuj parametr składnika typu `RenderFragment` i nadaj mu `ChildContent`nazwę.</span><span class="sxs-lookup"><span data-stu-id="14a11-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="14a11-310">*ChildContentComponent. Razor*</span><span class="sxs-lookup"><span data-stu-id="14a11-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="14a11-311">Składnik nadrzędny może następnie dostarczyć zawartość podrzędną przy użyciu normalnego składnia Razor.</span><span class="sxs-lookup"><span data-stu-id="14a11-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="14a11-312">Parametry szablonu</span><span class="sxs-lookup"><span data-stu-id="14a11-312">Template parameters</span></span>

<span data-ttu-id="14a11-313">Składnik Blazor z szablonem może również definiować wiele parametrów składnika typu `RenderFragment` lub. `RenderFragment<T>`</span><span class="sxs-lookup"><span data-stu-id="14a11-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="14a11-314">Parametr dla elementu `RenderFragment<T>` można określić, gdy jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="14a11-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="14a11-315">Aby określić parametr typu ogólnego dla składnika, użyj `@typeparam` dyrektywy Razor.</span><span class="sxs-lookup"><span data-stu-id="14a11-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="14a11-316">*SimpleListView. Razor*</span><span class="sxs-lookup"><span data-stu-id="14a11-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="14a11-317">W przypadku korzystania z składnika z szablonem parametry szablonu można określić za pomocą elementów podrzędnych, które pasują do nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="14a11-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="14a11-318">Argumenty składnika typu `RenderFragment<T>` przekazane jako elementy mają niejawny parametr o `context`nazwie.</span><span class="sxs-lookup"><span data-stu-id="14a11-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="14a11-319">Nazwę tego parametru implementacji można zmienić przy użyciu `Context` atrybutu elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="14a11-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="14a11-320">Wszystkie parametry typu ogólnego można określić przy użyciu atrybutu, który jest zgodny z nazwą parametru typu.</span><span class="sxs-lookup"><span data-stu-id="14a11-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="14a11-321">Parametr typu zostanie wywnioskowany, jeśli jest to możliwe:</span><span class="sxs-lookup"><span data-stu-id="14a11-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="14a11-322">Dane wyjściowe tego składnika wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="14a11-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="14a11-323">Związane z kodem</span><span class="sxs-lookup"><span data-stu-id="14a11-323">Code-behind</span></span>

<span data-ttu-id="14a11-324">Składnik Blazor jest zwykle tworzony w pojedynczym pliku *Razor* .</span><span class="sxs-lookup"><span data-stu-id="14a11-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="14a11-325">Można jednak również oddzielić kod i znaczniki przy użyciu pliku związanego z kodem.</span><span class="sxs-lookup"><span data-stu-id="14a11-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="14a11-326">Aby użyć pliku składnika, Dodaj C# plik, który jest zgodny z nazwą pliku składnika, ale z dodanym rozszerzeniem *CS* (*Counter.Razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="14a11-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="14a11-327">Użyj pliku C# , aby zdefiniować klasę bazową dla składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="14a11-328">Można nazwać klasę bazową w dowolnym celu, ale jest ona wspólna dla nazwy klasy, która jest taka sama jak Klasa składnika, ale z `Base` dodanym rozszerzeniem (`CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="14a11-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="14a11-329">Klasa oparta na składnikach musi również pochodzić od `ComponentBase`.</span><span class="sxs-lookup"><span data-stu-id="14a11-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="14a11-330">Następnie w pliku składnika Razor Dodaj `@inherits` dyrektywę, aby określić klasę bazową składnika (`@inherits CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="14a11-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="14a11-331">*Counter. Razor*</span><span class="sxs-lookup"><span data-stu-id="14a11-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="14a11-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="14a11-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase 
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="14a11-333">Widoczność elementów członkowskich składnika w klasie bazowej musi być `protected` lub `public` widoczna dla klasy składnika.</span><span class="sxs-lookup"><span data-stu-id="14a11-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="14a11-334">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="14a11-334">Additional resources</span></span>

<span data-ttu-id="14a11-335">Powyższe nie jest wyczerpujące dla wszystkich aspektów składników Blazor.</span><span class="sxs-lookup"><span data-stu-id="14a11-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="14a11-336">Aby uzyskać więcej informacji na temat [tworzenia i używania ASP.NET Core składników Razor](/aspnet/core/blazor/components), zapoznaj się z dokumentacją Blazor.</span><span class="sxs-lookup"><span data-stu-id="14a11-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="14a11-337">[Poprzedni](app-startup.md)
>[Następny](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="14a11-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
