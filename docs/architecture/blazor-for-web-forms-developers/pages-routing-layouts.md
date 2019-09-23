---
title: Strony, Routing i układy
description: Dowiedz się, jak tworzyć strony w Blazor, korzystać z routingu po stronie klienta i zarządzać układami stron.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 3e0b9bc277c9b554083eec35646480fd08759080
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183813"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="45224-103">Strony, Routing i układy</span><span class="sxs-lookup"><span data-stu-id="45224-103">Pages, routing, and layouts</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="45224-104">Aplikacje ASP.NET Web Forms składają się ze stron zdefiniowanych w plikach *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="45224-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="45224-105">Adres każdej strony jest oparty na fizycznej ścieżce pliku w projekcie.</span><span class="sxs-lookup"><span data-stu-id="45224-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="45224-106">Gdy przeglądarka wysyła żądanie do strony, zawartość strony jest dynamicznie renderowana na serwerze.</span><span class="sxs-lookup"><span data-stu-id="45224-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="45224-107">Konta renderowania zarówno dla znacznika HTML strony, jak i jego formantów serwerowych.</span><span class="sxs-lookup"><span data-stu-id="45224-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="45224-108">W programie Blazor każda Strona w aplikacji jest składnikiem, zazwyczaj zdefiniowanym w pliku *. Razor* , z co najmniej jedną określoną trasą.</span><span class="sxs-lookup"><span data-stu-id="45224-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="45224-109">Routing głównie odbywa się po stronie klienta bez udziału określonego żądania serwera.</span><span class="sxs-lookup"><span data-stu-id="45224-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="45224-110">Przeglądarka najpierw wysyła żądanie do adresu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45224-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="45224-111">Składnik główny `Router` w aplikacji Blazor, a następnie obsługuje przechwycone żądania nawigacji i są do poprawnego składnika.</span><span class="sxs-lookup"><span data-stu-id="45224-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

<span data-ttu-id="45224-112">Blazor obsługuje również *głębokie łączenie*.</span><span class="sxs-lookup"><span data-stu-id="45224-112">Blazor also supports *deep linking*.</span></span> <span data-ttu-id="45224-113">Głębokie łączenie występuje, gdy przeglądarka wysyła żądanie do określonej trasy innej niż główna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45224-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="45224-114">Żądania linków bezpośrednich wysyłanych do serwera są kierowane do aplikacji Blazor, która następnie kieruje żądanie po stronie klienta do właściwego składnika.</span><span class="sxs-lookup"><span data-stu-id="45224-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="45224-115">Prosta strona w formularzach sieci Web ASP.NET może zawierać następujące znaczniki:</span><span class="sxs-lookup"><span data-stu-id="45224-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="45224-116">*Nazwa. aspx*</span><span class="sxs-lookup"><span data-stu-id="45224-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="45224-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="45224-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="45224-118">Odpowiednik strony w aplikacji Blazor będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="45224-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="45224-119">*Nazwa. Razor*</span><span class="sxs-lookup"><span data-stu-id="45224-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    if (name != null)
    {
        Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="45224-120">Tworzenie stron</span><span class="sxs-lookup"><span data-stu-id="45224-120">Create pages</span></span>

<span data-ttu-id="45224-121">Aby utworzyć stronę w Blazor, Utwórz składnik i Dodaj `@page` dyrektywę Razor, aby określić trasę dla składnika.</span><span class="sxs-lookup"><span data-stu-id="45224-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="45224-122">`@page` Dyrektywa przyjmuje jeden parametr, który jest szablonem trasy do dodania do tego składnika.</span><span class="sxs-lookup"><span data-stu-id="45224-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="45224-123">Wymagany jest parametr szablonu trasy.</span><span class="sxs-lookup"><span data-stu-id="45224-123">The route template parameter is required.</span></span> <span data-ttu-id="45224-124">W przeciwieństwie do ASP.NET formularzy sieci Web, trasa do składnika Blazor *nie jest* wywnioskowana z jego lokalizacji pliku (chociaż może to być funkcja dodana w przyszłości).</span><span class="sxs-lookup"><span data-stu-id="45224-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="45224-125">Składnia szablonu trasy jest tą samą składnią podstawową używaną do routingu w ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="45224-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="45224-126">Parametry trasy są określone w szablonie za pomocą nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="45224-126">Route parameters are specified in the template using braces.</span></span> <span data-ttu-id="45224-127">Blazor będzie powiązać wartości tras z parametrami składnika o tej samej nazwie (bez uwzględniania wielkości liter).</span><span class="sxs-lookup"><span data-stu-id="45224-127">Blazor will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="45224-128">Można również określić ograniczenia dotyczące wartości parametru trasy.</span><span class="sxs-lookup"><span data-stu-id="45224-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="45224-129">Na przykład, aby ograniczyć identyfikator produktu do `int`:</span><span class="sxs-lookup"><span data-stu-id="45224-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="45224-130">Pełną listę ograniczeń trasy obsługiwanych przez Blazor można znaleźć w temacie [ograniczenia trasy](/aspnet/core/blazor/routing#route-constraints).</span><span class="sxs-lookup"><span data-stu-id="45224-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="45224-131">Składnik routera</span><span class="sxs-lookup"><span data-stu-id="45224-131">Router component</span></span>

<span data-ttu-id="45224-132">Routing w Blazor jest obsługiwany przez `Router` składnik.</span><span class="sxs-lookup"><span data-stu-id="45224-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="45224-133">Składnik jest zazwyczaj używany w głównym składniku aplikacji (*App. Razor*). `Router`</span><span class="sxs-lookup"><span data-stu-id="45224-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="45224-134">Składnik odnajduje składniki routingu w określonym `AppAssembly` i opcjonalnie określony `AdditionalAssemblies`. `Router`</span><span class="sxs-lookup"><span data-stu-id="45224-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="45224-135">`Router` Gdy przeglądarka nawiguje, przechwytuje nawigację i renderuje zawartość `Found` parametru z wyodrębnionym `RouteData` , jeśli trasa pasuje do adresu, w przeciwnym razie `Router` renderuje swój `NotFound` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="45224-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="45224-136">Składnik obsługuje renderowanie dopasowanego składnika określonego przez jego `RouteData` układ, jeśli go zawiera. `RouteView`</span><span class="sxs-lookup"><span data-stu-id="45224-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="45224-137">Jeśli dopasowany składnik nie ma układu, jest używany opcjonalnie określony `DefaultLayout` .</span><span class="sxs-lookup"><span data-stu-id="45224-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="45224-138">`LayoutView` Składnik renderuje jego zawartość podrzędną w ramach określonego układu.</span><span class="sxs-lookup"><span data-stu-id="45224-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="45224-139">W dalszej części tego rozdziału przejdziemy do bardziej szczegółowych informacji o układach.</span><span class="sxs-lookup"><span data-stu-id="45224-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="45224-140">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="45224-140">Navigation</span></span>

<span data-ttu-id="45224-141">W formularzach sieci Web ASP.NET można wyzwolić nawigację do innej strony, zwracając odpowiedź przekierowania do przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="45224-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="45224-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="45224-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="45224-143">Zwracanie odpowiedzi przekierowania nie jest zazwyczaj możliwe w Blazor.</span><span class="sxs-lookup"><span data-stu-id="45224-143">Returning a redirect response isn't typically possible in Blazor.</span></span> <span data-ttu-id="45224-144">Blazor nie używa modelu żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="45224-144">Blazor doesn't use a request-reply model.</span></span> <span data-ttu-id="45224-145">Można jednak bezpośrednio wyzwalać nawigację przeglądarki, podobnie jak w przypadku języka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="45224-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

<span data-ttu-id="45224-146">Blazor udostępnia `NavigationManager` usługę, która może służyć do:</span><span class="sxs-lookup"><span data-stu-id="45224-146">Blazor provides a `NavigationManager` service that can be used to:</span></span>

* <span data-ttu-id="45224-147">Pobierz bieżący adres przeglądarki</span><span class="sxs-lookup"><span data-stu-id="45224-147">Get the current browser address</span></span>
* <span data-ttu-id="45224-148">Pobierz adres podstawowy</span><span class="sxs-lookup"><span data-stu-id="45224-148">Get the base address</span></span>
* <span data-ttu-id="45224-149">Wywołaj nawigację</span><span class="sxs-lookup"><span data-stu-id="45224-149">Trigger navigations</span></span>
* <span data-ttu-id="45224-150">Otrzymuj powiadomienia o zmianie adresu</span><span class="sxs-lookup"><span data-stu-id="45224-150">Get notified when the address changes</span></span>

<span data-ttu-id="45224-151">Aby przejść do innego adresu, użyj `NavigateTo` metody:</span><span class="sxs-lookup"><span data-stu-id="45224-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="45224-152">Aby uzyskać opis wszystkich `NavigationManager` członków, zobacz [identyfikatory URI i pomocnika stanu nawigacji](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span><span class="sxs-lookup"><span data-stu-id="45224-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="45224-153">Podstawowe adresy URL</span><span class="sxs-lookup"><span data-stu-id="45224-153">Base URLs</span></span>

<span data-ttu-id="45224-154">Jeśli aplikacja Blazor jest wdrażana w ścieżce podstawowej, należy określić podstawowy adres URL w metadanych strony przy użyciu `<base>` tagu dla właściwości Routing do Work.</span><span class="sxs-lookup"><span data-stu-id="45224-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="45224-155">Jeśli strona hosta dla aplikacji jest renderowana na serwerze przy użyciu Razor, można użyć `~/` składni, aby określić adres podstawowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45224-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="45224-156">Jeśli strona hosta jest statycznym kodem HTML, należy jawnie określić podstawowy adres URL.</span><span class="sxs-lookup"><span data-stu-id="45224-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="45224-157">Układ strony</span><span class="sxs-lookup"><span data-stu-id="45224-157">Page layout</span></span>

<span data-ttu-id="45224-158">Układ strony w formularzach sieci Web ASP.NET jest obsługiwany przez strony główne.</span><span class="sxs-lookup"><span data-stu-id="45224-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="45224-159">Strony wzorcowe definiują szablon z co najmniej jednym symbolem zastępczym zawartości, który może zostać dostarczony przez poszczególne strony.</span><span class="sxs-lookup"><span data-stu-id="45224-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="45224-160">Strony wzorcowe są zdefiniowane w plikach *. Master* i zaczynają `<%@ Master %>` się od dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="45224-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="45224-161">Zawartość plików *. Master* jest zakodowana w taki sam sposób, jak na stronie *. aspx* , ale przy dodawaniu `<asp:ContentPlaceHolder>` kontrolek do oznaczania, gdzie strony mogą dostarczać zawartość.</span><span class="sxs-lookup"><span data-stu-id="45224-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="45224-162">*Site. Master*</span><span class="sxs-lookup"><span data-stu-id="45224-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="45224-163">W Blazor można obsłużyć układ strony przy użyciu składników układu.</span><span class="sxs-lookup"><span data-stu-id="45224-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="45224-164">Składniki układu dziedziczą `LayoutComponentBase`z, który definiuje pojedynczą `Body` właściwość typu `RenderFragment`, która może służyć do renderowania zawartości strony.</span><span class="sxs-lookup"><span data-stu-id="45224-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="45224-165">*MainLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="45224-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="45224-166">Gdy jest renderowany Strona z układem, strona jest renderowana w obrębie zawartości określonego układu w lokalizacji, w której układ renderuje swoją `Body` właściwość.</span><span class="sxs-lookup"><span data-stu-id="45224-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="45224-167">Aby zastosować układ do strony, użyj `@layout` dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="45224-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="45224-168">Można określić układ wszystkich składników w folderze i podfolderach przy użyciu pliku *_Imports. Razor* .</span><span class="sxs-lookup"><span data-stu-id="45224-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="45224-169">Możesz również określić układ domyślny dla wszystkich stron przy użyciu [składnika routera](#router-component).</span><span class="sxs-lookup"><span data-stu-id="45224-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="45224-170">Strony wzorcowe mogą definiować wiele symboli zastępczych zawartości, ale układy w Blazor mają tylko `Body` jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="45224-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="45224-171">To ograniczenie składników układu Blazor będzie miejmy nadzieję w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="45224-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="45224-172">Strony wzorcowe w formularzach sieci Web ASP.NET mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="45224-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="45224-173">Oznacza to, że strona wzorcowa może również korzystać z strony wzorcowej.</span><span class="sxs-lookup"><span data-stu-id="45224-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="45224-174">Składniki układu w Blazor mogą być również zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="45224-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="45224-175">Można zastosować składnik układu do składnika układu.</span><span class="sxs-lookup"><span data-stu-id="45224-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="45224-176">Zawartość układu wewnętrznego będzie renderowana w układzie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="45224-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="45224-177">*ChildLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="45224-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="45224-178">*Index. Razor*</span><span class="sxs-lookup"><span data-stu-id="45224-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="45224-179">Wyrenderowane dane wyjściowe dla strony byłyby następujące:</span><span class="sxs-lookup"><span data-stu-id="45224-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="45224-180">Układy w Blazor nie definiują zwykle elementów głównych HTML dla strony (`<html>`, `<body>`, `<head>`, itd.).</span><span class="sxs-lookup"><span data-stu-id="45224-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="45224-181">Główne elementy HTML są definiowane na stronie hosta aplikacji Blazor, która jest używana do renderowania początkowej zawartości HTML dla aplikacji (zobacz [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span><span class="sxs-lookup"><span data-stu-id="45224-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="45224-182">Na stronie hosta można renderować wiele składników głównych aplikacji z otaczającym znacznikiem.</span><span class="sxs-lookup"><span data-stu-id="45224-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="45224-183">Składniki w Blazor, w tym strony, nie `<script>` mogą renderować tagów.</span><span class="sxs-lookup"><span data-stu-id="45224-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="45224-184">To ograniczenie renderowania istnieje, `<script>` ponieważ Tagi są ładowane jednokrotnie, a następnie nie można ich zmienić.</span><span class="sxs-lookup"><span data-stu-id="45224-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="45224-185">Jeśli spróbujesz renderować Tagi dynamicznie przy użyciu składnia Razor, może wystąpić nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="45224-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="45224-186">Zamiast tego należy `<script>` dodać wszystkie Tagi do strony hosta aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45224-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="45224-187">[Poprzedni](components.md)
>[Następny](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="45224-187">[Previous](components.md)
[Next](state-management.md)</span></span>
