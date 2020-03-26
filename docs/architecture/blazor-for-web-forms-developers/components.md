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
# <a name="build-reusable-ui-components-with-blazor"></a>Tworzenie komponentów interfejsu użytkownika wielokrotnego wykorzystania za pomocą blazora

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jedną z pięknych rzeczy na temat ASP.NET formularzy sieci Web jest to, jak umożliwia hermetyzację fragmentów interfejsu użytkownika wielokrotnego dostępu (UI) do formantów interfejsu użytkownika wielokrotnegoużytnia. Niestandardowe formanty użytkownika można zdefiniować w znacznikach przy użyciu plików *ascx.* Można również tworzyć rozbudowane formanty serwera w kodzie z pełną obsługą projektanta.

Blazor obsługuje również hermetyzację interfejsu użytkownika za pomocą *komponentów.* Składnik:

- Jest samodzielnym fragmentem interfejsu użytkownika.
- Zachowuje swój własny stan i logiki renderowania.
- Można zdefiniować programy obsługi zdarzeń interfejsu użytkownika, powiązać z danymi wejściowymi i zarządzać własnym cyklem życia.
- Jest zazwyczaj zdefiniowany w pliku *.brzytwa* przy użyciu składni Razor.

## <a name="an-introduction-to-razor"></a>Wprowadzenie do Razor

Razor to lekki język tworzenia znaczników oparty na HTML i C#. Za pomocą razor można bezproblemowo przejść między znacznikami i kodem Języka C#, aby zdefiniować logikę renderowania składników. Po skompilowaniu pliku *.brzytwa* logika renderowania jest przechwytywany w sposób strukturalny w klasie .NET. Nazwa skompilowana klasa jest pobierana od nazwy pliku *.brzytwa.* Obszar nazw jest pobierana z domyślnego obszaru nazw dla projektu i ścieżki folderu `@namespace` lub można jawnie określić obszar nazw przy użyciu dyrektywy (więcej na temat dyrektyw Razor poniżej).

Logika renderowania składnika jest tworzone przy użyciu normalnego znaczników HTML z logiką dynamiczną dodaną przy użyciu języka C#. Znak `@` jest używany do przejścia do języka C#. Razor jest zazwyczaj inteligentny w wymyślaniu po przełączeniu z powrotem do HTML. Na przykład następujący składnik renderuje `<p>` znacznik z bieżącym czasem:

```razor
<p>@DateTime.Now</p>
```

Aby jawnie określić początek i koniec wyrażenia C#, należy użyć nawiasów:

```razor
<p>@(DateTime.Now)</p>
```

Razor ułatwia również korzystanie z przepływu sterowania języka C# w logice renderowania. Na przykład można warunkowo renderować niektóre html w ten sposób:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Lub można wygenerować listę elementów `foreach` przy użyciu normalnej pętli C#:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Dyrektywy razor, takie jak dyrektywy w ASP.NET formularzy sieci Web, kontrolują wiele aspektów sposobu kompilowania komponentu Razor. Przykłady obejmują składnik:

- Przestrzeń nazw
- Klasa podstawowa
- Zaimplementowane interfejsy
- Parametry ogólne
- Importowane przestrzenie nazw
- Trasy

Dyrektywy razor zaczynają `@` się od znaku i są zwykle używane na początku nowego wiersza na początku pliku. Na przykład `@namespace` dyrektywa definiuje obszar nazw składnika:

```razor
@namespace MyComponentNamespace
```

W poniższej tabeli podsumowano różne dyrektywy Razor używane w blazor i ich odpowiedniki ASP.NET Web Forms, jeśli istnieją.

|Dyrektywy    |Opis|Przykład|Odpowiednik formularzy sieci Web|
|-------------|-----------|-------|--------------------|
|`@attribute` |Dodaje atrybut na poziomie klasy do składnika|`@attribute [Authorize]`|Brak|
|`@code`      |Dodaje elementy członkowskie klasy do składnika|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implementuje określony interfejs|`@implements IDisposable`|Korzystanie z kodu|
|`@inherits`  |Dziedziczy z określonej klasy podstawowej|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Wstrzykuje usługę do składnika|`@inject IJSRuntime JS`|Brak|
|`@layout`    |Określa składnik układu dla komponentu|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Ustawia obszar nazw dla składnika|`@namespace MyNamespace`|Brak|
|`@page`      |Określa trasę dla komponentu|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Określa parametr typu ogólnego dla składnika|`@typeparam TItem`|Korzystanie z kodu|
|`@using`     |Określa obszar nazw, który ma być wprowadzany do zakresu|`@using MyComponentNamespace`|Dodawanie obszaru nazw w *witrynie web.config*|

Składniki razor również szeroko używać *atrybutów dyrektywy* na elementy do kontrolowania różnych aspektów, jak składniki są kompilowane (obsługa zdarzeń, powiązanie danych, składnik & odwołania do elementów i tak dalej). Wszystkie atrybuty dyrektywy są zgodne ze wspólną składnią rodzajową, w której wartości w nawiasie są opcjonalne:

```razor
@directive(-suffix(:name))(="value")
```

W poniższej tabeli podsumowano różne atrybuty dyrektyw Razor używanych w Blazor.

|Atrybut    |Opis|Przykład|
|-------------|-----------|-------|
|`@attributes`|Renderuje słownik atrybutów|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Tworzy dwukierunkowe powiązanie danych    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Dodaje program obsługi zdarzeń dla określonego zdarzenia|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Określa klucz, który ma być używany przez algorytm różnicowania do zachowywania elementów w kolekcji|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Przechwytuje odwołanie do składnika lub elementu HTML|`<MyDialog @ref="myDialog" />`|

Różne atrybuty dyrektywy używane`@onclick`przez `@bind` `@ref`Blazora ( , , i tak dalej) są opisane w poniższych sekcjach i w późniejszych rozdziałach.

Wiele składni używanych w plikach *.aspx* i *.ascx* ma równoległe składni w Razor. Poniżej znajduje się proste porównanie składni dla ASP.NET formularzy sieci Web i Razor.

|Funkcja                      |Formularze sieci Web           |Składnia               |Razor         |Składnia |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Dyrektyw                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Bloki kodu                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Wyrażenia<br>(zakodowane w formacie HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Niejawne:`@`<br>Jawne:`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Komentarze                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Powiązanie danych                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Aby dodać elementy członkowskie do klasy `@code` komponentu Razor, należy użyć dyrektywy. Ta technika jest `<script runat="server">...</script>` podobna do używania bloku w ASP.NET formantu użytkownika lub strony formularzy sieci Web.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Ponieważ razor jest oparty na języku C#, musi być skompilowany z poziomu projektu C# (*.csproj*). Nie można skompilować plików *.brzytwa* z projektu języka Visual Basic (*.vbproj*). Nadal można odwoływać się do projektów języka Visual Basic z projektu Blazor. Jest też odwrotnie.

Aby uzyskać pełne odwołanie do składni Razor, zobacz [Odwołanie do składni Razor dla ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Użyj komponentów

Oprócz normalnego kodu HTML, składniki mogą również używać innych składników jako części ich logiki renderowania. Składnia przy użyciu składnika w Razor jest podobny do korzystania z formantu użytkownika w aplikacji ASP.NET Web Forms. Komponenty są określane przy użyciu znacznika elementu, który pasuje do nazwy typu składnika. Na przykład można dodać `Counter` składnik w ten sposób:

```razor
<Counter />
```

W przeciwieństwie do ASP.NET formularzy sieci Web, składniki w Blazor:

- Nie używaj prefiksu elementu `asp:`(na przykład).
- Nie wymaga rejestracji na stronie lub w *web.config*.

Pomyśl o komponentach Razor, takich jak typy .NET, ponieważ to jest dokładnie to, czym są. Jeśli odwołuje się do złożenia zawierającego komponent, komponent jest dostępny do użycia. Aby wprowadzić obszar nazw składnika do `@using` zakresu, zastosuj dyrektywę:

```razor
@using MyComponentLib

<Counter />
```

Jak widać w domyślnych projektach Blazor, `@using` często umieszcza się dyrektywy w pliku *_Imports.brzytwa,* aby były importowane do wszystkich plików *.brzytwa* w tym samym katalogu i w katalogach podrzędnych.

Jeśli obszar nazw składnika nie znajduje się w zakresie, można określić składnik przy użyciu jego pełnej nazwy typu, tak jak w języku C#:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Parametry komponentu

W ASP.NET formularzy sieci Web można przesyłać parametry i dane do formantów przy użyciu właściwości publicznych. Właściwości te można ustawić w znacznikach przy użyciu atrybutów lub ustawić bezpośrednio w kodzie. Składniki Blazor działają w podobny sposób, chociaż właściwości komponentu `[Parameter]` muszą być również oznaczone atrybutem, który ma być uważany za parametry komponentu.

Następujący `Counter` składnik definiuje parametr składnika o nazwie, `IncrementAmount` który może `Counter` służyć do określenia kwoty, która powinna być zwiększana za każdym razem, gdy przycisk jest klikany.

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

Aby określić parametr składnika w blazorze, użyj atrybutu tak, jak w ASP.NET formularzy sieci Web:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Procedury obsługi zdarzeń

Zarówno ASP.NET formularze sieci Web, jak i blazor zapewniają model programowania oparty na zdarzeniach do obsługi zdarzeń interfejsu użytkownika. Przykładami takich zdarzeń są kliknięcia przycisków i wprowadzanie tekstu. W ASP.NET formularzy sieci Web służy kontrolki serwera HTML do obsługi zdarzeń interfejsu użytkownika udostępniane przez dom lub można obsługiwać zdarzenia udostępniane przez formanty serwera sieci web. Zdarzenia są ujmowany na serwerze za pośrednictwem żądania post-back formularza. Rozważmy następujący przykład kliknięcia przycisku Formularze sieci Web:

*Licznik.ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

W blazorze można zarejestrować programy obsługi zdarzeń interfejsu użytkownika DOM `@on{event}`bezpośrednio przy użyciu atrybutów dyrektywy formularza . Symbol `{event}` zastępczy reprezentuje nazwę zdarzenia. Na przykład można nasłuchiić kliknięć przycisków w ten sposób:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Programy obsługi zdarzeń mogą akceptować opcjonalny argument specyficzny dla zdarzenia, aby uzyskać więcej informacji na temat zdarzenia. Na przykład zdarzenia myszy `MouseEventArgs` można wziąć argument, ale nie jest wymagane.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Zamiast odwoływać się do grupy metod dla programu obsługi zdarzeń, można użyć wyrażenia lambda. Wyrażenie lambda umożliwia zamknięcie innych wartości w zakresie.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Programy obsługi zdarzeń można wykonywać synchronicznie lub asynchronicznie. Na przykład następujący `OnClick` program obsługi zdarzeń wykonuje asynchronicznie:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Po obsłudze zdarzenia składnik jest renderowany w celu uwzględnienia zmian stanu składnika. W przypadku programów obsługi zdarzeń asynchronicznych składnik jest renderowany natychmiast po zakończeniu wykonywania programu obsługi. Składnik jest renderowany *ponownie* po zakończeniu `Task` asynchronii. Ten tryb wykonywania asynchronii zapewnia możliwość renderowania niektórych odpowiednich `Task` interfejsu użytkownika, podczas gdy asynchroniczne jest nadal w toku.

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

Komponenty mogą również definiować własne zdarzenia, `EventCallback<TValue>`definiując parametr komponentu typu . Wywołania zwrotne zdarzeń obsługują wszystkie odmiany programów obsługi zdarzeń interfejsu użytkownika DOM: opcjonalne argumenty, synchroniczne lub asynchroniczne, grupy metod lub wyrażenia lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Powiązanie danych

Blazor zapewnia prosty mechanizm powiązania danych ze składnika interfejsu użytkownika ze stanem składnika. Takie podejście różni się od funkcji w ASP.NET formularzy sieci Web dla powiązania danych ze źródeł danych do formantów interfejsu użytkownika. Omówimy obsługę danych z różnych źródeł danych w sekcji [Radzenie sobie z danymi.](data.md)

Aby utworzyć dwukierunkowe powiązanie danych ze składnika interfejsu użytkownika `@bind` ze stanem składnika, należy użyć atrybutu dyrektywy. W poniższym przykładzie wartość pola wyboru jest `isChecked` powiązana z polem.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Podczas renderowania składnika wartość pola wyboru jest ustawiona na `isChecked` wartość pola. Gdy użytkownik przełączy to pole wyboru, `onchange` zdarzenie jest `isChecked` uruchamiane, a pole jest ustawione na nową wartość. Składnia `@bind` w tym przypadku jest równoważna następującej znaczników:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Aby zmienić zdarzenie używane dla `@bind:event` powiązania, użyj atrybutu.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Składniki mogą również obsługiwać powiązanie danych z ich parametrami. Aby związać dane, zdefiniuj parametr wywołania zwrotnego zdarzenia o takiej samej nazwie jak parametr, który można powiązać. Sufiks "Zmieniono" jest dodawany do nazwy.

*Pole do golenia w pliku PasswordBox*

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

Aby łańcuch powiązania danych do podstawowego elementu interfejsu użytkownika, ustawić wartość i obsługiwać zdarzenie `@bind` bezpośrednio na element interfejsu użytkownika zamiast przy użyciu atrybutu.

Aby powiązać z parametrem `@bind-{Parameter}` składnika, należy użyć atrybutu, aby określić parametr, z którym chcesz powiązać.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Zmiany stanu

Jeśli stan składnika uległ zmianie poza normalnym zdarzeniem interfejsu użytkownika lub wywołaniem zwrotnym zdarzenia, składnik musi ręcznie sygnalizować, że musi być renderowany ponownie. Aby zasygnalizować, że stan `StateHasChanged` składnika uległ zmianie, należy wywołać metodę na składniku.

W poniższym przykładzie składnik wyświetla `AppState` komunikat z usługi, które mogą być aktualizowane przez inne części aplikacji. Składnik rejestruje jego `StateHasChanged` metody `AppState.OnChange` ze zdarzeniem, tak aby składnik jest renderowany za każdym razem, gdy wiadomość zostanie zaktualizowana.

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

## <a name="component-lifecycle"></a>Cykl życia komponentu

Struktura ASP.NET formularzy sieci Web ma dobrze zdefiniowane metody cyklu życia modułów, stron i formantów. Na przykład następujący formant implementuje programy `Init` `Load`obsługi `UnLoad` zdarzeń dla zdarzeń , i cyklu życia:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Komponenty Blazor mają również dobrze zdefiniowany cykl życia. Cykl życia składnika może służyć do inicjowania stanu składnika i implementowania zaawansowanych zachowań składników.

Wszystkie metody cyklu życia komponentów Blazora mają zarówno wersje synchroniczne, jak i asynchroniczne. Renderowanie składników jest synchroniczne. Nie można uruchomić logiki asynchroniczowej jako część renderowania składnika. Wszystkie logiki asynchroniczne musi `async` wykonać jako część metody cyklu życia.

### <a name="oninitialized"></a>OnInitialized

Metody `OnInitialized` `OnInitializedAsync` i metody są używane do inicjowania składnika. Składnik jest zazwyczaj inicjowany po jego pierwszym renderowaniu. Po zainicjowaniu składnika może być renderowany wiele razy, zanim zostanie ostatecznie usunięty. Metoda `OnInitialized` jest podobna `Page_Load` do zdarzenia w ASP.NET stron i formantów formularzy sieci Web.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

Metody `OnParametersSet` `OnParametersSetAsync` i są wywoływane, gdy składnik odebrał parametry od jego elementu nadrzędnego, a wartość jest przypisywana do właściwości. Metody te są wykonywane po inicjalizacji komponentu i *za każdym razem, gdy komponent jest renderowany*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender (OnAfterRender)

Metody `OnAfterRender` `OnAfterRenderAsync` i są wywoływane po zakończeniu renderowania składnika. Odwołania do elementów i składników są wypełniane w tym momencie (więcej na temat tych pojęć poniżej). Interaktywność z przeglądarką jest włączona w tym momencie. Interakcje z wykonaniem DOM i JavaScript mogą odbywać się bezpiecznie.

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

`OnAfterRender`i `OnAfterRenderAsync` *nie są wywoływane podczas prerendering na serwerze*.

Parametr `firstRender` jest `true` pierwszym renderowaniem składnika; w przeciwnym razie `false`jego wartość wynosi .

### <a name="idisposable"></a>Idisposable

Składniki Blazor `IDisposable` można zaimplementować do usuwania zasobów, gdy składnik jest usuwany z interfejsu użytkownika. Składnik Razor można `IDispose` zaimplementować przy użyciu `@implements` dyrektywy:

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

## <a name="capture-component-references"></a>Przechwytywanie odwołań do składników

W ASP.NET formularzy sieci Web jest wspólne do manipulowania wystąpienie formantu bezpośrednio w kodzie, odwołując się do jego identyfikatora. W Blazor, jest również możliwe do przechwytywania i manipulowania odniesienie do składnika, choć jest to znacznie mniej powszechne.

Aby przechwycić odwołanie do `@ref` składnika w Blazor, należy użyć atrybutu dyrektywy. Wartość atrybutu powinna być zgodna z nazwą pola settable o tym samym typie co składnik, do którego istnieje odwołanie.

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

Podczas renderowania składnika nadrzędnego pole jest wypełniane wystąpieniem komponentu podrzędnego. Następnie można wywołać metody na lub w inny sposób manipulować wystąpienie składnika.

Manipulowanie stanem komponentu bezpośrednio przy użyciu odwołań do składników nie jest zalecane. Zapobiega to renderowaniu komponentu automatycznie w odpowiednim czasie.

## <a name="capture-element-references"></a>Przechwytywanie odwołań do elementów

Komponenty Blazora mogą przechwytywać odwołania do elementu. W przeciwieństwie do kontrolek serwera HTML w ASP.NET formularzy sieci Web, nie można manipulować dom bezpośrednio przy użyciu odwołania do elementu w Blazor. Blazor obsługuje większość interakcji DOM za pomocą algorytmu różnicowania DOM. Przechwycone odniesienia do elementów w Blazor są nieprzezroczyste. Jednak są one używane do przekazywania odwołania do określonego elementu w wywołaniu interop JavaScript. Aby uzyskać więcej informacji na temat interop JavaScript, zobacz [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Składniki z szablonami

W ASP.NET formularzy sieci Web można tworzyć *formanty szablonowe*. Formanty szablonu umożliwiają deweloperowi określenie części kodu HTML używanej do renderowania formantu kontenera. Mechanika tworzenia formantów serwera szablonów są złożone, ale umożliwiają zaawansowane scenariusze renderowania danych w sposób dostosowywany przez użytkownika. Przykłady formantów `Repeater` szablonów obejmują i `DataList`.

Komponenty Blazora można również szablonować, `RenderFragment` definiując parametry komponentów typu lub `RenderFragment<T>`. A `RenderFragment` reprezentuje fragment znaczników Razor, które następnie mogą być renderowane przez składnik. A `RenderFragment<T>` jest fragment znaczników Razor, który przyjmuje parametr, który może być określony podczas renderowania fragmentu renderowania.

### <a name="child-content"></a>Zawartość podrzędna

Składniki Blazora mogą przechwytywać zawartość podrzędną jako zawartość podrzędną `RenderFragment` i renderować tę zawartość jako część renderowania składnika. Aby przechwycić zawartość podrzędną, należy zdefiniować parametr komponentu typu `RenderFragment` i nazwać go `ChildContent`.

*DzieckoContentComponent.brzytwa*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Składnik nadrzędny może następnie dostarczyć zawartość podrzędną przy użyciu normalnej składni Razor.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Parametry szablonu

Szablonowy komponent Blazora może również definiować wiele parametrów komponentu typu `RenderFragment` lub `RenderFragment<T>`. Parametr dla `RenderFragment<T>` a można określić, gdy jest wywoływany. Aby określić parametr typu ogólnego dla `@typeparam` składnika, należy użyć dyrektywy Razor.

*SimpleListView.brzytwa*

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

Podczas korzystania z składnika szablonu parametry szablonu można określić przy użyciu elementów podrzędnych, które pasują do nazw parametrów. Argumenty komponentu `RenderFragment<T>` typu przekazywane jako elementy `context`mają parametr niejawny o nazwie . Można zmienić nazwę tego parametru `Context` implementacji przy użyciu atrybutu na elemencie podrzędnym. Wszystkie parametry typu ogólnego można określić przy użyciu atrybutu, który pasuje do nazwy parametru typu. Parametr typu zostanie wywnioskowany, jeśli to możliwe:

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

Dane wyjściowe tego składnika wygląda następująco:

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Zakodowane

Składnik Blazor jest zazwyczaj autorstwa w jednym pliku *.brzytwa.* Jednak jest również możliwe do oddzielenia kodu i znaczników przy użyciu pliku związane z kodem. Aby użyć pliku składnika, dodaj plik C#, który pasuje do nazwy pliku składnika, ale z dodanym rozszerzeniem *cs* *(Counter.razor.cs*). Użyj pliku C#, aby zdefiniować klasę podstawową dla składnika. Klasę podstawową można nazwać wszystkim, co chcesz, ale często nazywasz klasę taką samą `Base` jak`CounterBase`klasa składnika, ale z dodanym rozszerzeniem ( ). Klasa oparta na składniku `ComponentBase`musi również pochodzić z . Następnie w pliku komponentu Razor `@inherits` dodaj dyrektywę, aby określić klasę podstawową dla komponentu (`@inherits CounterBase`).

*Counter.brzytwa*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

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

Widoczność elementów członkowskich komponentu w klasie `protected` `public` podstawowej musi być lub być widoczna dla klasy komponentu.

## <a name="additional-resources"></a>Zasoby dodatkowe

Poprzednie nie jest wyczerpujące traktowanie wszystkich aspektów elementów Blazor. Aby uzyskać więcej informacji na temat [tworzenia i używania ASP.NET podstawowych komponentów razor,](/aspnet/core/blazor/components)zobacz dokumentację Blazor.

>[!div class="step-by-step"]
>[Poprzedni](app-startup.md)
>[następny](pages-routing-layouts.md)
