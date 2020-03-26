---
title: Tworzenie komponentów interfejsu użytkownika wielokrotnego wykorzystania za pomocą blazora
description: Dowiedz się, jak tworzyć składniki interfejsu użytkownika wielokrotnegoużytniczego za pomocą blazora i jak je porównywać z formantami ASP.NET formularzy sieci Web.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228625"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="72ec0-103">Tworzenie komponentów interfejsu użytkownika wielokrotnego wykorzystania za pomocą blazora</span><span class="sxs-lookup"><span data-stu-id="72ec0-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="72ec0-104">Jedną z pięknych rzeczy na temat ASP.NET formularzy sieci Web jest to, jak umożliwia hermetyzację fragmentów interfejsu użytkownika wielokrotnego dostępu (UI) do formantów interfejsu użytkownika wielokrotnegoużytnia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="72ec0-105">Niestandardowe formanty użytkownika można zdefiniować w znacznikach przy użyciu plików *ascx.*</span><span class="sxs-lookup"><span data-stu-id="72ec0-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="72ec0-106">Można również tworzyć rozbudowane formanty serwera w kodzie z pełną obsługą projektanta.</span><span class="sxs-lookup"><span data-stu-id="72ec0-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="72ec0-107">Blazor obsługuje również hermetyzację interfejsu użytkownika za pomocą *komponentów.*</span><span class="sxs-lookup"><span data-stu-id="72ec0-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="72ec0-108">Składnik:</span><span class="sxs-lookup"><span data-stu-id="72ec0-108">A component:</span></span>

- <span data-ttu-id="72ec0-109">Jest samodzielnym fragmentem interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="72ec0-110">Zachowuje swój własny stan i logiki renderowania.</span><span class="sxs-lookup"><span data-stu-id="72ec0-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="72ec0-111">Można zdefiniować programy obsługi zdarzeń interfejsu użytkownika, powiązać z danymi wejściowymi i zarządzać własnym cyklem życia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="72ec0-112">Jest zazwyczaj zdefiniowany w pliku *.brzytwa* przy użyciu składni Razor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="72ec0-113">Wprowadzenie do Razor</span><span class="sxs-lookup"><span data-stu-id="72ec0-113">An introduction to Razor</span></span>

<span data-ttu-id="72ec0-114">Razor to lekki język tworzenia znaczników oparty na HTML i C#.</span><span class="sxs-lookup"><span data-stu-id="72ec0-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="72ec0-115">Za pomocą razor można bezproblemowo przejść między znacznikami i kodem Języka C#, aby zdefiniować logikę renderowania składników.</span><span class="sxs-lookup"><span data-stu-id="72ec0-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="72ec0-116">Po skompilowaniu pliku *.brzytwa* logika renderowania jest przechwytywany w sposób strukturalny w klasie .NET.</span><span class="sxs-lookup"><span data-stu-id="72ec0-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="72ec0-117">Nazwa skompilowana klasa jest pobierana od nazwy pliku *.brzytwa.*</span><span class="sxs-lookup"><span data-stu-id="72ec0-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="72ec0-118">Obszar nazw jest pobierana z domyślnego obszaru nazw dla projektu i ścieżki folderu `@namespace` lub można jawnie określić obszar nazw przy użyciu dyrektywy (więcej na temat dyrektyw Razor poniżej).</span><span class="sxs-lookup"><span data-stu-id="72ec0-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="72ec0-119">Logika renderowania składnika jest tworzone przy użyciu normalnego znaczników HTML z logiką dynamiczną dodaną przy użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="72ec0-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="72ec0-120">Znak `@` jest używany do przejścia do języka C#.</span><span class="sxs-lookup"><span data-stu-id="72ec0-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="72ec0-121">Razor jest zazwyczaj inteligentny w wymyślaniu po przełączeniu z powrotem do HTML.</span><span class="sxs-lookup"><span data-stu-id="72ec0-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="72ec0-122">Na przykład następujący składnik renderuje `<p>` znacznik z bieżącym czasem:</span><span class="sxs-lookup"><span data-stu-id="72ec0-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="72ec0-123">Aby jawnie określić początek i koniec wyrażenia C#, należy użyć nawiasów:</span><span class="sxs-lookup"><span data-stu-id="72ec0-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="72ec0-124">Razor ułatwia również korzystanie z przepływu sterowania języka C# w logice renderowania.</span><span class="sxs-lookup"><span data-stu-id="72ec0-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="72ec0-125">Na przykład można warunkowo renderować niektóre html w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="72ec0-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="72ec0-126">Lub można wygenerować listę elementów `foreach` przy użyciu normalnej pętli C#:</span><span class="sxs-lookup"><span data-stu-id="72ec0-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="72ec0-127">Dyrektywy razor, takie jak dyrektywy w ASP.NET formularzy sieci Web, kontrolują wiele aspektów sposobu kompilowania komponentu Razor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="72ec0-128">Przykłady obejmują składnik:</span><span class="sxs-lookup"><span data-stu-id="72ec0-128">Examples include the component's:</span></span>

- <span data-ttu-id="72ec0-129">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="72ec0-129">Namespace</span></span>
- <span data-ttu-id="72ec0-130">Klasa podstawowa</span><span class="sxs-lookup"><span data-stu-id="72ec0-130">Base class</span></span>
- <span data-ttu-id="72ec0-131">Zaimplementowane interfejsy</span><span class="sxs-lookup"><span data-stu-id="72ec0-131">Implemented interfaces</span></span>
- <span data-ttu-id="72ec0-132">Parametry ogólne</span><span class="sxs-lookup"><span data-stu-id="72ec0-132">Generic parameters</span></span>
- <span data-ttu-id="72ec0-133">Importowane przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="72ec0-133">Imported namespaces</span></span>
- <span data-ttu-id="72ec0-134">Trasy</span><span class="sxs-lookup"><span data-stu-id="72ec0-134">Routes</span></span>

<span data-ttu-id="72ec0-135">Dyrektywy razor zaczynają `@` się od znaku i są zwykle używane na początku nowego wiersza na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="72ec0-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="72ec0-136">Na przykład `@namespace` dyrektywa definiuje obszar nazw składnika:</span><span class="sxs-lookup"><span data-stu-id="72ec0-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="72ec0-137">W poniższej tabeli podsumowano różne dyrektywy Razor używane w blazor i ich odpowiedniki ASP.NET Web Forms, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="72ec0-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="72ec0-138">Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="72ec0-138">Directive</span></span>    |<span data-ttu-id="72ec0-139">Opis</span><span class="sxs-lookup"><span data-stu-id="72ec0-139">Description</span></span>|<span data-ttu-id="72ec0-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="72ec0-140">Example</span></span>|<span data-ttu-id="72ec0-141">Odpowiednik formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="72ec0-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="72ec0-142">Dodaje atrybut na poziomie klasy do składnika</span><span class="sxs-lookup"><span data-stu-id="72ec0-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="72ec0-143">Brak</span><span class="sxs-lookup"><span data-stu-id="72ec0-143">None</span></span>|
|`@code`      |<span data-ttu-id="72ec0-144">Dodaje elementy członkowskie klasy do składnika</span><span class="sxs-lookup"><span data-stu-id="72ec0-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="72ec0-145">Implementuje określony interfejs</span><span class="sxs-lookup"><span data-stu-id="72ec0-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="72ec0-146">Korzystanie z kodu</span><span class="sxs-lookup"><span data-stu-id="72ec0-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="72ec0-147">Dziedziczy z określonej klasy podstawowej</span><span class="sxs-lookup"><span data-stu-id="72ec0-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="72ec0-148">Wstrzykuje usługę do składnika</span><span class="sxs-lookup"><span data-stu-id="72ec0-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="72ec0-149">Brak</span><span class="sxs-lookup"><span data-stu-id="72ec0-149">None</span></span>|
|`@layout`    |<span data-ttu-id="72ec0-150">Określa składnik układu dla komponentu</span><span class="sxs-lookup"><span data-stu-id="72ec0-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="72ec0-151">Ustawia obszar nazw dla składnika</span><span class="sxs-lookup"><span data-stu-id="72ec0-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="72ec0-152">Brak</span><span class="sxs-lookup"><span data-stu-id="72ec0-152">None</span></span>|
|`@page`      |<span data-ttu-id="72ec0-153">Określa trasę dla komponentu</span><span class="sxs-lookup"><span data-stu-id="72ec0-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="72ec0-154">Określa parametr typu ogólnego dla składnika</span><span class="sxs-lookup"><span data-stu-id="72ec0-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="72ec0-155">Korzystanie z kodu</span><span class="sxs-lookup"><span data-stu-id="72ec0-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="72ec0-156">Określa obszar nazw, który ma być wprowadzany do zakresu</span><span class="sxs-lookup"><span data-stu-id="72ec0-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="72ec0-157">Dodawanie obszaru nazw w *witrynie web.config*</span><span class="sxs-lookup"><span data-stu-id="72ec0-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="72ec0-158">Składniki razor również szeroko używać *atrybutów dyrektywy* na elementy do kontrolowania różnych aspektów, jak składniki są kompilowane (obsługa zdarzeń, powiązanie danych, składnik & odwołania do elementów i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="72ec0-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="72ec0-159">Wszystkie atrybuty dyrektywy są zgodne ze wspólną składnią rodzajową, w której wartości w nawiasie są opcjonalne:</span><span class="sxs-lookup"><span data-stu-id="72ec0-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="72ec0-160">W poniższej tabeli podsumowano różne atrybuty dyrektyw Razor używanych w Blazor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="72ec0-161">Atrybut</span><span class="sxs-lookup"><span data-stu-id="72ec0-161">Attribute</span></span>    |<span data-ttu-id="72ec0-162">Opis</span><span class="sxs-lookup"><span data-stu-id="72ec0-162">Description</span></span>|<span data-ttu-id="72ec0-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="72ec0-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="72ec0-164">Renderuje słownik atrybutów</span><span class="sxs-lookup"><span data-stu-id="72ec0-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="72ec0-165">Tworzy dwukierunkowe powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="72ec0-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="72ec0-166">Dodaje program obsługi zdarzeń dla określonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="72ec0-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="72ec0-167">Określa klucz, który ma być używany przez algorytm różnicowania do zachowywania elementów w kolekcji</span><span class="sxs-lookup"><span data-stu-id="72ec0-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="72ec0-168">Przechwytuje odwołanie do składnika lub elementu HTML</span><span class="sxs-lookup"><span data-stu-id="72ec0-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="72ec0-169">Różne atrybuty dyrektywy używane`@onclick`przez `@bind` `@ref`Blazora ( , , i tak dalej) są opisane w poniższych sekcjach i w późniejszych rozdziałach.</span><span class="sxs-lookup"><span data-stu-id="72ec0-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="72ec0-170">Wiele składni używanych w plikach *.aspx* i *.ascx* ma równoległe składni w Razor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="72ec0-171">Poniżej znajduje się proste porównanie składni dla ASP.NET formularzy sieci Web i Razor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="72ec0-172">Funkcja</span><span class="sxs-lookup"><span data-stu-id="72ec0-172">Feature</span></span>                      |<span data-ttu-id="72ec0-173">Formularze sieci Web</span><span class="sxs-lookup"><span data-stu-id="72ec0-173">Web Forms</span></span>           |<span data-ttu-id="72ec0-174">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ec0-174">Syntax</span></span>               |<span data-ttu-id="72ec0-175">Razor</span><span class="sxs-lookup"><span data-stu-id="72ec0-175">Razor</span></span>         |<span data-ttu-id="72ec0-176">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ec0-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="72ec0-177">Dyrektyw</span><span class="sxs-lookup"><span data-stu-id="72ec0-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="72ec0-178">Bloki kodu</span><span class="sxs-lookup"><span data-stu-id="72ec0-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="72ec0-179">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="72ec0-179">Expressions</span></span><br><span data-ttu-id="72ec0-180">(zakodowane w formacie HTML)</span><span class="sxs-lookup"><span data-stu-id="72ec0-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="72ec0-181">Niejawne:`@`</span><span class="sxs-lookup"><span data-stu-id="72ec0-181">Implicit: `@`</span></span><br><span data-ttu-id="72ec0-182">Jawne:`@()`</span><span class="sxs-lookup"><span data-stu-id="72ec0-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="72ec0-183">Komentarze</span><span class="sxs-lookup"><span data-stu-id="72ec0-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="72ec0-184">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="72ec0-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="72ec0-185">Aby dodać elementy członkowskie do klasy `@code` komponentu Razor, należy użyć dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="72ec0-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="72ec0-186">Ta technika jest `<script runat="server">...</script>` podobna do używania bloku w ASP.NET formantu użytkownika lub strony formularzy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="72ec0-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="72ec0-187">Ponieważ razor jest oparty na języku C#, musi być skompilowany z poziomu projektu C# (*.csproj*).</span><span class="sxs-lookup"><span data-stu-id="72ec0-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="72ec0-188">Nie można skompilować plików *.brzytwa* z projektu języka Visual Basic (*.vbproj*).</span><span class="sxs-lookup"><span data-stu-id="72ec0-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="72ec0-189">Nadal można odwoływać się do projektów języka Visual Basic z projektu Blazor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="72ec0-190">Jest też odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-190">The opposite is true too.</span></span>

<span data-ttu-id="72ec0-191">Aby uzyskać pełne odwołanie do składni Razor, zobacz [Odwołanie do składni Razor dla ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="72ec0-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="72ec0-192">Użyj komponentów</span><span class="sxs-lookup"><span data-stu-id="72ec0-192">Use components</span></span>

<span data-ttu-id="72ec0-193">Oprócz normalnego kodu HTML, składniki mogą również używać innych składników jako części ich logiki renderowania.</span><span class="sxs-lookup"><span data-stu-id="72ec0-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="72ec0-194">Składnia przy użyciu składnika w Razor jest podobny do korzystania z formantu użytkownika w aplikacji ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="72ec0-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="72ec0-195">Komponenty są określane przy użyciu znacznika elementu, który pasuje do nazwy typu składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="72ec0-196">Na przykład można dodać `Counter` składnik w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="72ec0-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="72ec0-197">W przeciwieństwie do ASP.NET formularzy sieci Web, składniki w Blazor:</span><span class="sxs-lookup"><span data-stu-id="72ec0-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="72ec0-198">Nie używaj prefiksu elementu `asp:`(na przykład).</span><span class="sxs-lookup"><span data-stu-id="72ec0-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="72ec0-199">Nie wymaga rejestracji na stronie lub w *web.config*.</span><span class="sxs-lookup"><span data-stu-id="72ec0-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="72ec0-200">Pomyśl o komponentach Razor, takich jak typy .NET, ponieważ to jest dokładnie to, czym są.</span><span class="sxs-lookup"><span data-stu-id="72ec0-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="72ec0-201">Jeśli odwołuje się do złożenia zawierającego komponent, komponent jest dostępny do użycia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="72ec0-202">Aby wprowadzić obszar nazw składnika do `@using` zakresu, zastosuj dyrektywę:</span><span class="sxs-lookup"><span data-stu-id="72ec0-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="72ec0-203">Jak widać w domyślnych projektach Blazor, `@using` często umieszcza się dyrektywy w pliku *_Imports.brzytwa,* aby były importowane do wszystkich plików *.brzytwa* w tym samym katalogu i w katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="72ec0-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="72ec0-204">Jeśli obszar nazw składnika nie znajduje się w zakresie, można określić składnik przy użyciu jego pełnej nazwy typu, tak jak w języku C#:</span><span class="sxs-lookup"><span data-stu-id="72ec0-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="72ec0-205">Parametry komponentu</span><span class="sxs-lookup"><span data-stu-id="72ec0-205">Component parameters</span></span>

<span data-ttu-id="72ec0-206">W ASP.NET formularzy sieci Web można przesyłać parametry i dane do formantów przy użyciu właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="72ec0-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="72ec0-207">Właściwości te można ustawić w znacznikach przy użyciu atrybutów lub ustawić bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="72ec0-208">Składniki Blazor działają w podobny sposób, chociaż właściwości komponentu `[Parameter]` muszą być również oznaczone atrybutem, który ma być uważany za parametry komponentu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="72ec0-209">Następujący `Counter` składnik definiuje parametr składnika o nazwie, `IncrementAmount` który może `Counter` służyć do określenia kwoty, która powinna być zwiększana za każdym razem, gdy przycisk jest klikany.</span><span class="sxs-lookup"><span data-stu-id="72ec0-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="72ec0-210">Aby określić parametr składnika w blazorze, użyj atrybutu tak, jak w ASP.NET formularzy sieci Web:</span><span class="sxs-lookup"><span data-stu-id="72ec0-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="72ec0-211">Procedury obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="72ec0-211">Event handlers</span></span>

<span data-ttu-id="72ec0-212">Zarówno ASP.NET formularze sieci Web, jak i blazor zapewniają model programowania oparty na zdarzeniach do obsługi zdarzeń interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="72ec0-213">Przykładami takich zdarzeń są kliknięcia przycisków i wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="72ec0-214">W ASP.NET formularzy sieci Web służy kontrolki serwera HTML do obsługi zdarzeń interfejsu użytkownika udostępniane przez dom lub można obsługiwać zdarzenia udostępniane przez formanty serwera sieci web.</span><span class="sxs-lookup"><span data-stu-id="72ec0-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="72ec0-215">Zdarzenia są ujmowany na serwerze za pośrednictwem żądania post-back formularza.</span><span class="sxs-lookup"><span data-stu-id="72ec0-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="72ec0-216">Rozważmy następujący przykład kliknięcia przycisku Formularze sieci Web:</span><span class="sxs-lookup"><span data-stu-id="72ec0-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="72ec0-217">*Licznik.ascx*</span><span class="sxs-lookup"><span data-stu-id="72ec0-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="72ec0-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="72ec0-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="72ec0-219">W blazorze można zarejestrować programy obsługi zdarzeń interfejsu użytkownika DOM `@on{event}`bezpośrednio przy użyciu atrybutów dyrektywy formularza .</span><span class="sxs-lookup"><span data-stu-id="72ec0-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="72ec0-220">Symbol `{event}` zastępczy reprezentuje nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="72ec0-221">Na przykład można nasłuchiić kliknięć przycisków w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="72ec0-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="72ec0-222">Programy obsługi zdarzeń mogą akceptować opcjonalny argument specyficzny dla zdarzenia, aby uzyskać więcej informacji na temat zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="72ec0-223">Na przykład zdarzenia myszy `MouseEventArgs` można wziąć argument, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="72ec0-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="72ec0-224">Zamiast odwoływać się do grupy metod dla programu obsługi zdarzeń, można użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="72ec0-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="72ec0-225">Wyrażenie lambda umożliwia zamknięcie innych wartości w zakresie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="72ec0-226">Programy obsługi zdarzeń można wykonywać synchronicznie lub asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="72ec0-227">Na przykład następujący `OnClick` program obsługi zdarzeń wykonuje asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="72ec0-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="72ec0-228">Po obsłudze zdarzenia składnik jest renderowany w celu uwzględnienia zmian stanu składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="72ec0-229">W przypadku programów obsługi zdarzeń asynchronicznych składnik jest renderowany natychmiast po zakończeniu wykonywania programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="72ec0-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="72ec0-230">Składnik jest renderowany *ponownie* po zakończeniu `Task` asynchronii.</span><span class="sxs-lookup"><span data-stu-id="72ec0-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="72ec0-231">Ten tryb wykonywania asynchronii zapewnia możliwość renderowania niektórych odpowiednich `Task` interfejsu użytkownika, podczas gdy asynchroniczne jest nadal w toku.</span><span class="sxs-lookup"><span data-stu-id="72ec0-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

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

<span data-ttu-id="72ec0-232">Komponenty mogą również definiować własne zdarzenia, `EventCallback<TValue>`definiując parametr komponentu typu .</span><span class="sxs-lookup"><span data-stu-id="72ec0-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="72ec0-233">Wywołania zwrotne zdarzeń obsługują wszystkie odmiany programów obsługi zdarzeń interfejsu użytkownika DOM: opcjonalne argumenty, synchroniczne lub asynchroniczne, grupy metod lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="72ec0-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="72ec0-234">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="72ec0-234">Data binding</span></span>

<span data-ttu-id="72ec0-235">Blazor zapewnia prosty mechanizm powiązania danych ze składnika interfejsu użytkownika ze stanem składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="72ec0-236">Takie podejście różni się od funkcji w ASP.NET formularzy sieci Web dla powiązania danych ze źródeł danych do formantów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="72ec0-237">Omówimy obsługę danych z różnych źródeł danych w sekcji [Radzenie sobie z danymi.](data.md)</span><span class="sxs-lookup"><span data-stu-id="72ec0-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="72ec0-238">Aby utworzyć dwukierunkowe powiązanie danych ze składnika interfejsu użytkownika `@bind` ze stanem składnika, należy użyć atrybutu dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="72ec0-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="72ec0-239">W poniższym przykładzie wartość pola wyboru jest `isChecked` powiązana z polem.</span><span class="sxs-lookup"><span data-stu-id="72ec0-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="72ec0-240">Podczas renderowania składnika wartość pola wyboru jest ustawiona na `isChecked` wartość pola.</span><span class="sxs-lookup"><span data-stu-id="72ec0-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="72ec0-241">Gdy użytkownik przełączy to pole wyboru, `onchange` zdarzenie jest `isChecked` uruchamiane, a pole jest ustawione na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="72ec0-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="72ec0-242">Składnia `@bind` w tym przypadku jest równoważna następującej znaczników:</span><span class="sxs-lookup"><span data-stu-id="72ec0-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="72ec0-243">Aby zmienić zdarzenie używane dla `@bind:event` powiązania, użyj atrybutu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="72ec0-244">Składniki mogą również obsługiwać powiązanie danych z ich parametrami.</span><span class="sxs-lookup"><span data-stu-id="72ec0-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="72ec0-245">Aby związać dane, zdefiniuj parametr wywołania zwrotnego zdarzenia o takiej samej nazwie jak parametr, który można powiązać.</span><span class="sxs-lookup"><span data-stu-id="72ec0-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="72ec0-246">Sufiks "Zmieniono" jest dodawany do nazwy.</span><span class="sxs-lookup"><span data-stu-id="72ec0-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="72ec0-247">*Pole do golenia w pliku PasswordBox*</span><span class="sxs-lookup"><span data-stu-id="72ec0-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="72ec0-248">Aby łańcuch powiązania danych do podstawowego elementu interfejsu użytkownika, ustawić wartość i obsługiwać zdarzenie `@bind` bezpośrednio na element interfejsu użytkownika zamiast przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="72ec0-249">Aby powiązać z parametrem `@bind-{Parameter}` składnika, należy użyć atrybutu, aby określić parametr, z którym chcesz powiązać.</span><span class="sxs-lookup"><span data-stu-id="72ec0-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="72ec0-250">Zmiany stanu</span><span class="sxs-lookup"><span data-stu-id="72ec0-250">State changes</span></span>

<span data-ttu-id="72ec0-251">Jeśli stan składnika uległ zmianie poza normalnym zdarzeniem interfejsu użytkownika lub wywołaniem zwrotnym zdarzenia, składnik musi ręcznie sygnalizować, że musi być renderowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="72ec0-252">Aby zasygnalizować, że stan `StateHasChanged` składnika uległ zmianie, należy wywołać metodę na składniku.</span><span class="sxs-lookup"><span data-stu-id="72ec0-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="72ec0-253">W poniższym przykładzie składnik wyświetla `AppState` komunikat z usługi, które mogą być aktualizowane przez inne części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72ec0-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="72ec0-254">Składnik rejestruje jego `StateHasChanged` metody `AppState.OnChange` ze zdarzeniem, tak aby składnik jest renderowany za każdym razem, gdy wiadomość zostanie zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="72ec0-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

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

## <a name="component-lifecycle"></a><span data-ttu-id="72ec0-255">Cykl życia komponentu</span><span class="sxs-lookup"><span data-stu-id="72ec0-255">Component lifecycle</span></span>

<span data-ttu-id="72ec0-256">Struktura ASP.NET formularzy sieci Web ma dobrze zdefiniowane metody cyklu życia modułów, stron i formantów.</span><span class="sxs-lookup"><span data-stu-id="72ec0-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="72ec0-257">Na przykład następujący formant implementuje programy `Init` `Load`obsługi `UnLoad` zdarzeń dla zdarzeń , i cyklu życia:</span><span class="sxs-lookup"><span data-stu-id="72ec0-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="72ec0-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="72ec0-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="72ec0-259">Komponenty Blazor mają również dobrze zdefiniowany cykl życia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="72ec0-260">Cykl życia składnika może służyć do inicjowania stanu składnika i implementowania zaawansowanych zachowań składników.</span><span class="sxs-lookup"><span data-stu-id="72ec0-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="72ec0-261">Wszystkie metody cyklu życia komponentów Blazora mają zarówno wersje synchroniczne, jak i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="72ec0-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="72ec0-262">Renderowanie składników jest synchroniczne.</span><span class="sxs-lookup"><span data-stu-id="72ec0-262">Component rendering is synchronous.</span></span> <span data-ttu-id="72ec0-263">Nie można uruchomić logiki asynchroniczowej jako część renderowania składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="72ec0-264">Wszystkie logiki asynchroniczne musi `async` wykonać jako część metody cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="72ec0-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="72ec0-265">OnInitialized</span><span class="sxs-lookup"><span data-stu-id="72ec0-265">OnInitialized</span></span>

<span data-ttu-id="72ec0-266">Metody `OnInitialized` `OnInitializedAsync` i metody są używane do inicjowania składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="72ec0-267">Składnik jest zazwyczaj inicjowany po jego pierwszym renderowaniu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="72ec0-268">Po zainicjowaniu składnika może być renderowany wiele razy, zanim zostanie ostatecznie usunięty.</span><span class="sxs-lookup"><span data-stu-id="72ec0-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="72ec0-269">Metoda `OnInitialized` jest podobna `Page_Load` do zdarzenia w ASP.NET stron i formantów formularzy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="72ec0-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="72ec0-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="72ec0-270">OnParametersSet</span></span>

<span data-ttu-id="72ec0-271">Metody `OnParametersSet` `OnParametersSetAsync` i są wywoływane, gdy składnik odebrał parametry od jego elementu nadrzędnego, a wartość jest przypisywana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="72ec0-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="72ec0-272">Metody te są wykonywane po inicjalizacji komponentu i *za każdym razem, gdy komponent jest renderowany*.</span><span class="sxs-lookup"><span data-stu-id="72ec0-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="72ec0-273">OnAfterRender (OnAfterRender)</span><span class="sxs-lookup"><span data-stu-id="72ec0-273">OnAfterRender</span></span>

<span data-ttu-id="72ec0-274">Metody `OnAfterRender` `OnAfterRenderAsync` i są wywoływane po zakończeniu renderowania składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="72ec0-275">Odwołania do elementów i składników są wypełniane w tym momencie (więcej na temat tych pojęć poniżej).</span><span class="sxs-lookup"><span data-stu-id="72ec0-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="72ec0-276">Interaktywność z przeglądarką jest włączona w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="72ec0-277">Interakcje z wykonaniem DOM i JavaScript mogą odbywać się bezpiecznie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="72ec0-278">`OnAfterRender`i `OnAfterRenderAsync` *nie są wywoływane podczas prerendering na serwerze*.</span><span class="sxs-lookup"><span data-stu-id="72ec0-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="72ec0-279">Parametr `firstRender` jest `true` pierwszym renderowaniem składnika; w przeciwnym razie `false`jego wartość wynosi .</span><span class="sxs-lookup"><span data-stu-id="72ec0-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="72ec0-280">Idisposable</span><span class="sxs-lookup"><span data-stu-id="72ec0-280">IDisposable</span></span>

<span data-ttu-id="72ec0-281">Składniki Blazor `IDisposable` można zaimplementować do usuwania zasobów, gdy składnik jest usuwany z interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="72ec0-282">Składnik Razor można `IDispose` zaimplementować przy użyciu `@implements` dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="72ec0-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="72ec0-283">Przechwytywanie odwołań do składników</span><span class="sxs-lookup"><span data-stu-id="72ec0-283">Capture component references</span></span>

<span data-ttu-id="72ec0-284">W ASP.NET formularzy sieci Web jest wspólne do manipulowania wystąpienie formantu bezpośrednio w kodzie, odwołując się do jego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="72ec0-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="72ec0-285">W Blazor, jest również możliwe do przechwytywania i manipulowania odniesienie do składnika, choć jest to znacznie mniej powszechne.</span><span class="sxs-lookup"><span data-stu-id="72ec0-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="72ec0-286">Aby przechwycić odwołanie do `@ref` składnika w Blazor, należy użyć atrybutu dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="72ec0-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="72ec0-287">Wartość atrybutu powinna być zgodna z nazwą pola settable o tym samym typie co składnik, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="72ec0-288">Podczas renderowania składnika nadrzędnego pole jest wypełniane wystąpieniem komponentu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="72ec0-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="72ec0-289">Następnie można wywołać metody na lub w inny sposób manipulować wystąpienie składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="72ec0-290">Manipulowanie stanem komponentu bezpośrednio przy użyciu odwołań do składników nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="72ec0-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="72ec0-291">Zapobiega to renderowaniu komponentu automatycznie w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="72ec0-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="72ec0-292">Przechwytywanie odwołań do elementów</span><span class="sxs-lookup"><span data-stu-id="72ec0-292">Capture element references</span></span>

<span data-ttu-id="72ec0-293">Komponenty Blazora mogą przechwytywać odwołania do elementu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="72ec0-294">W przeciwieństwie do kontrolek serwera HTML w ASP.NET formularzy sieci Web, nie można manipulować dom bezpośrednio przy użyciu odwołania do elementu w Blazor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="72ec0-295">Blazor obsługuje większość interakcji DOM za pomocą algorytmu różnicowania DOM.</span><span class="sxs-lookup"><span data-stu-id="72ec0-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="72ec0-296">Przechwycone odniesienia do elementów w Blazor są nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="72ec0-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="72ec0-297">Jednak są one używane do przekazywania odwołania do określonego elementu w wywołaniu interop JavaScript.</span><span class="sxs-lookup"><span data-stu-id="72ec0-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="72ec0-298">Aby uzyskać więcej informacji na temat interop JavaScript, zobacz [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="72ec0-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="72ec0-299">Składniki z szablonami</span><span class="sxs-lookup"><span data-stu-id="72ec0-299">Templated components</span></span>

<span data-ttu-id="72ec0-300">W ASP.NET formularzy sieci Web można tworzyć *formanty szablonowe*.</span><span class="sxs-lookup"><span data-stu-id="72ec0-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="72ec0-301">Formanty szablonu umożliwiają deweloperowi określenie części kodu HTML używanej do renderowania formantu kontenera.</span><span class="sxs-lookup"><span data-stu-id="72ec0-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="72ec0-302">Mechanika tworzenia formantów serwera szablonów są złożone, ale umożliwiają zaawansowane scenariusze renderowania danych w sposób dostosowywany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="72ec0-303">Przykłady formantów `Repeater` szablonów obejmują i `DataList`.</span><span class="sxs-lookup"><span data-stu-id="72ec0-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="72ec0-304">Komponenty Blazora można również szablonować, `RenderFragment` definiując parametry komponentów typu lub `RenderFragment<T>`.</span><span class="sxs-lookup"><span data-stu-id="72ec0-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="72ec0-305">A `RenderFragment` reprezentuje fragment znaczników Razor, które następnie mogą być renderowane przez składnik.</span><span class="sxs-lookup"><span data-stu-id="72ec0-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="72ec0-306">A `RenderFragment<T>` jest fragment znaczników Razor, który przyjmuje parametr, który może być określony podczas renderowania fragmentu renderowania.</span><span class="sxs-lookup"><span data-stu-id="72ec0-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="72ec0-307">Zawartość podrzędna</span><span class="sxs-lookup"><span data-stu-id="72ec0-307">Child content</span></span>

<span data-ttu-id="72ec0-308">Składniki Blazora mogą przechwytywać zawartość podrzędną jako zawartość podrzędną `RenderFragment` i renderować tę zawartość jako część renderowania składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="72ec0-309">Aby przechwycić zawartość podrzędną, należy zdefiniować parametr komponentu typu `RenderFragment` i nazwać go `ChildContent`.</span><span class="sxs-lookup"><span data-stu-id="72ec0-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="72ec0-310">*DzieckoContentComponent.brzytwa*</span><span class="sxs-lookup"><span data-stu-id="72ec0-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="72ec0-311">Składnik nadrzędny może następnie dostarczyć zawartość podrzędną przy użyciu normalnej składni Razor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="72ec0-312">Parametry szablonu</span><span class="sxs-lookup"><span data-stu-id="72ec0-312">Template parameters</span></span>

<span data-ttu-id="72ec0-313">Szablonowy komponent Blazora może również definiować wiele parametrów komponentu typu `RenderFragment` lub `RenderFragment<T>`.</span><span class="sxs-lookup"><span data-stu-id="72ec0-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="72ec0-314">Parametr dla `RenderFragment<T>` a można określić, gdy jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="72ec0-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="72ec0-315">Aby określić parametr typu ogólnego dla `@typeparam` składnika, należy użyć dyrektywy Razor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="72ec0-316">*SimpleListView.brzytwa*</span><span class="sxs-lookup"><span data-stu-id="72ec0-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
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

<span data-ttu-id="72ec0-317">Podczas korzystania z składnika szablonu parametry szablonu można określić przy użyciu elementów podrzędnych, które pasują do nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="72ec0-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="72ec0-318">Argumenty komponentu `RenderFragment<T>` typu przekazywane jako elementy `context`mają parametr niejawny o nazwie .</span><span class="sxs-lookup"><span data-stu-id="72ec0-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="72ec0-319">Można zmienić nazwę tego parametru `Context` implementacji przy użyciu atrybutu na elemencie podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="72ec0-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="72ec0-320">Wszystkie parametry typu ogólnego można określić przy użyciu atrybutu, który pasuje do nazwy parametru typu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="72ec0-321">Parametr typu zostanie wywnioskowany, jeśli to możliwe:</span><span class="sxs-lookup"><span data-stu-id="72ec0-321">The type parameter will be inferred if possible:</span></span>

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

<span data-ttu-id="72ec0-322">Dane wyjściowe tego składnika wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="72ec0-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="72ec0-323">Zakodowane</span><span class="sxs-lookup"><span data-stu-id="72ec0-323">Code-behind</span></span>

<span data-ttu-id="72ec0-324">Składnik Blazor jest zazwyczaj autorstwa w jednym pliku *.brzytwa.*</span><span class="sxs-lookup"><span data-stu-id="72ec0-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="72ec0-325">Jednak jest również możliwe do oddzielenia kodu i znaczników przy użyciu pliku związane z kodem.</span><span class="sxs-lookup"><span data-stu-id="72ec0-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="72ec0-326">Aby użyć pliku składnika, dodaj plik C#, który pasuje do nazwy pliku składnika, ale z dodanym rozszerzeniem *cs* *(Counter.razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="72ec0-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="72ec0-327">Użyj pliku C#, aby zdefiniować klasę podstawową dla składnika.</span><span class="sxs-lookup"><span data-stu-id="72ec0-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="72ec0-328">Klasę podstawową można nazwać wszystkim, co chcesz, ale często nazywasz klasę taką samą `Base` jak`CounterBase`klasa składnika, ale z dodanym rozszerzeniem ( ).</span><span class="sxs-lookup"><span data-stu-id="72ec0-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="72ec0-329">Klasa oparta na składniku `ComponentBase`musi również pochodzić z .</span><span class="sxs-lookup"><span data-stu-id="72ec0-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="72ec0-330">Następnie w pliku komponentu Razor `@inherits` dodaj dyrektywę, aby określić klasę podstawową dla komponentu (`@inherits CounterBase`).</span><span class="sxs-lookup"><span data-stu-id="72ec0-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="72ec0-331">*Counter.brzytwa*</span><span class="sxs-lookup"><span data-stu-id="72ec0-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="72ec0-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="72ec0-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="72ec0-333">Widoczność elementów członkowskich komponentu w klasie `protected` `public` podstawowej musi być lub być widoczna dla klasy komponentu.</span><span class="sxs-lookup"><span data-stu-id="72ec0-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="72ec0-334">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="72ec0-334">Additional resources</span></span>

<span data-ttu-id="72ec0-335">Poprzednie nie jest wyczerpujące traktowanie wszystkich aspektów elementów Blazor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="72ec0-336">Aby uzyskać więcej informacji na temat [tworzenia i używania ASP.NET podstawowych komponentów razor,](/aspnet/core/blazor/components)zobacz dokumentację Blazor.</span><span class="sxs-lookup"><span data-stu-id="72ec0-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72ec0-337">[Poprzedni](app-startup.md)
>[następny](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="72ec0-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
