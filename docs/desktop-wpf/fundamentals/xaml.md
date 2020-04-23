---
title: Przegląd XAML
description: Dowiedz się, jak język XAML jest skonstruowany i zaimplementowany przez Program Windows Presentation Foundation (WPF) dla platformy .NET Core.
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "82071788"
---
# <a name="xaml-overview-in-wpf"></a>Omówienie XAML w wyw.

W tym artykule opisano funkcje języka XAML i pokazano, jak można używać XAML do pisania aplikacji Windows Presentation Foundation (WPF). W tym artykule opisano w szczególności XAML zaimplementowane przez WPF. Sam XAML jest pojęciem większego języka niż WPF.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>Co to jest XAML

XAML jest deklaratywnym językiem znaczników. W przypadku modelu programowania .NET Core kod XAML upraszcza tworzenie interfejsu użytkownika dla aplikacji .NET Core. Można utworzyć widoczne elementy interfejsu użytkownika w deklaratywne znaczniki XAML, a następnie oddzielić definicję interfejsu użytkownika od logiki czasu wykonywania przy użyciu plików związanych z kodem, które są przyłączane do znaczników za pomocą definicji klasy częściowej. XAML bezpośrednio reprezentuje tworzenie wystąpienia obiektów w określonym zestawie typów kopii zdefiniowanych w zestawach. Jest to w przeciwieństwie do większości innych języków znaczników, które są zazwyczaj interpretowany język bez takiego bezpośredniego powiązania z systemem typu kopii zapasowej. XAML umożliwia przepływ pracy, gdzie oddzielne strony mogą pracować na interfejs użytkownika i logiki aplikacji, przy użyciu potencjalnie różnych narzędzi.

Pliki XAML, które są reprezentowane jako tekst, `.xaml` są plikami XML, które zazwyczaj mają rozszerzenie. Pliki mogą być kodowane przez dowolne kodowanie XML, ale kodowanie jako UTF-8 jest typowe.

W poniższym przykładzie pokazano, jak można utworzyć przycisk jako część interfejsu użytkownika. W tym przykładzie ma na celu zapewnienie smaku jak XAML reprezentuje wspólne metafory programowania interfejsu użytkownika (nie jest kompletnym przykładem).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Składnia XAML w skrócie

W poniższych sekcjach wyjaśniono podstawowe formy składni XAML i podano przykład krótkiego znaczników. Te sekcje nie są przeznaczone do dostarczania pełnych informacji o każdym formularzu składni, takich jak sposób ich reprezentowania w systemie typu zapasowego. Aby uzyskać więcej informacji na temat specyfiki składni XAML, zobacz Szczegółowo [składnię XAML](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

Większość materiałów w następnych kilku sekcjach będzie dla Ciebie elementarna, jeśli znasz wcześniej język XML. Jest to konsekwencja jednej z podstawowych zasad projektowania XAML. Język XAML definiuje pojęcia własne, ale te pojęcia działają w języku XML i formularzu znaczników.

### <a name="xaml-object-elements"></a>Elementy obiektu XAML

Element obiektu zazwyczaj deklaruje wystąpienie typu. Ten typ jest zdefiniowany w zestawach, do których odwołuje się technologia, która używa języka XAML.

Składnia elementu obiektu zawsze zaczyna się od`<`nawiasu kątowego otwarcia ( ). Po tym następuje nazwa typu, w którym chcesz utworzyć wystąpienie. (Nazwa może zawierać prefiks, pojęcie, które zostanie wyjaśnione później.) Następnie można opcjonalnie zadeklarować atrybuty na element obiektu. Aby zakończyć znacznik elementu obiektu, zakończ`>`nawiasem kątowym zamknięcia ( ). Zamiast tego można użyć formularza samozamykającego się, który nie ma żadnej zawartości, wypełniając`/>`znacznik ukośnikiem i nawiasem kątowym zamykającym po kolei ( ). Na przykład ponownie przyjrzyj się wcześniej pokazanej fragmentowi kodu znaczników.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Określa dwa elementy obiektu: `<StackPanel>` (z zawartością i tagiem zamykającym później) i `<Button .../>` (formularz samozamykania się z kilkoma atrybutami). Elementy `StackPanel` obiektu `Button` i każdej mapie do nazwy klasy, która jest zdefiniowana przez WPF i jest częścią WPF zestawy. Po określeniu znacznika elementu obiektu należy utworzyć instrukcję przetwarzania XAML w celu utworzenia nowego wystąpienia typu źródłowego. Każde wystąpienie jest tworzone przez wywołanie konstruktora bez parametrów typu źródłowego podczas analizowania i ładowania XAML.

### <a name="attribute-syntax-properties"></a>Składnia atrybutów (właściwości)

Właściwości obiektu często mogą być wyrażone jako atrybuty elementu obiektu. Składnia atrybutu nazywa ustawioną właściwość obiektu, a następnie operator przypisania (=). Wartość atrybutu jest zawsze określona jako ciąg, który jest zawarty w cudzysłowie.

Składnia atrybutów jest najbardziej usprawniona składnia ustawień właściwości i jest najbardziej intuicyjną składnią do użycia dla deweloperów, którzy używali języków znaczników w przeszłości. Na przykład poniższy znacznik tworzy przycisk, który ma czerwony tekst i niebieskie `Content`tło oprócz wyświetlania tekstu określonego jako .

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Składnia elementu właściwości

W przypadku niektórych właściwości elementu obiektu składnia atrybutu nie jest możliwa, ponieważ obiekt lub informacje niezbędne do dostarczenia wartości właściwości nie mogą być odpowiednio wyrażone w cudzysłowie i ograniczeniach ciągu składni atrybutu. W takich przypadkach można użyć innej składni znanej jako składnia elementu właściwości.

Składnia znacznika początkowego elementu `<TypeName.PropertyName>`właściwości to . Ogólnie rzecz biorąc zawartość tego tagu jest elementem obiektu typu, który właściwość przyjmuje jako swoją wartość. Po określeniu zawartości należy zamknąć element właściwości tagiem końcowym. Składnia znacznika końcowego `</TypeName.PropertyName>`to .

Jeśli składnia atrybutów jest możliwa, użycie składni atrybutu jest zazwyczaj wygodniejsze i umożliwia bardziej kompaktowe znaczniki, ale często jest to tylko kwestia stylu, a nie ograniczenia techniczne. W poniższym przykładzie przedstawiono te same właściwości ustawione, co w przykładzie składni poprzedniego atrybutu, ale `Button`tym razem przy użyciu składni elementu właściwości dla wszystkich właściwości . .

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Składnia kolekcji

Język XAML zawiera pewne optymalizacje, które generują więcej znaczników czytelnych dla człowieka. Jedną z takich optymalizacji jest to, że jeśli określona właściwość przyjmuje typ kolekcji, a następnie elementy, które deklarujesz w znacznikach jako elementy podrzędne w ramach tej właściwości wartości stają się częścią kolekcji. W tym przypadku kolekcja elementów obiektu podrzędnego jest wartością ustawioną na właściwość kolekcji.

Poniższy przykład przedstawia składnię kolekcji <xref:System.Windows.Media.GradientBrush.GradientStops%2A> dla ustawiania wartości właściwości.

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.GradientStops>
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->
    <GradientStop Offset="0.0" Color="Red" />
    <GradientStop Offset="1.0" Color="Blue" />
  </LinearGradientBrush.GradientStops>
</LinearGradientBrush>
```

### <a name="xaml-content-properties"></a>Właściwości zawartości XAML

XAML określa funkcję języka, zgodnie z którą klasa może wyznaczyć dokładnie jedną z jego właściwości jako właściwość _zawartości_ XAML. Elementy podrzędne tego elementu obiektu są używane do ustawiania wartości tej właściwości zawartości. Innymi słowy dla właściwości zawartości unikatowo można pominąć element właściwości podczas ustawiania tej właściwości w znacznikach XAML i utworzyć bardziej widoczną metaforę nadrzędną/podrzędną w znacznikach.

Na przykład <xref:System.Windows.Controls.Border> określa właściwość <xref:System.Windows.Controls.Decorator.Child%2A> _zawartości_ . Następujące dwa <xref:System.Windows.Controls.Border> elementy są traktowane identycznie. Pierwszy z nich korzysta ze składni właściwości zawartości `Border.Child` i pomija element właściwości. Drugi pokazuje `Border.Child` jawnie.

```xaml
<Border>
  <TextBox Width="300"/>
</Border>
<!--explicit equivalent-->
<Border>
  <Border.Child>
    <TextBox Width="300"/>
  </Border.Child>
</Border>
```

Z reguły języka XAML wartość właściwości zawartości XAML musi być podana całkowicie przed lub całkowicie po innych elementów właściwości w tym elemencie obiektu. Na przykład następujące znaczniki nie kompiluje.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

Aby uzyskać więcej informacji na temat specyfiki składni XAML, zobacz Szczegółowo [składnię XAML](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Zawartość tekstowa

Niewielka liczba elementów XAML może bezpośrednio przetwarzać tekst jako ich zawartość. Aby włączyć tę funkcję, musi być spełniony jeden z następujących przypadków:

- Klasa musi zadeklarować właściwość zawartości, a właściwość content musi być typu przypisywanego do ciągu (typ może być). <xref:System.Object> Na przykład <xref:System.Windows.Controls.ContentControl> wszelkie <xref:System.Windows.Controls.ContentControl.Content%2A> zastosowania jako jego właściwości <xref:System.Object>zawartości i jest to typ <xref:System.Windows.Controls.ContentControl> , <xref:System.Windows.Controls.Button>a `<Button>Hello</Button>`to obsługuje następujące użycie na takie jak: .

- Typ musi zadeklarować konwerter typów, w którym to przypadku zawartość tekstowa jest używana jako tekst inicjowania dla tego typu konwertera. Na przykład `<Brush>Blue</Brush>` konwertuje wartość `Blue` zawartości na pędzel. Ten przypadek jest mniej powszechny w praktyce.

- Typ musi być znany język XAML pierwotny.

### <a name="content-properties-and-collection-syntax-combined"></a>Właściwości zawartości i składnia kolekcji połączone

Rozważmy ten przykład.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Tutaj każdy <xref:System.Windows.Controls.Button> jest elementem <xref:System.Windows.Controls.StackPanel>podrzędnym . Jest to usprawniony i intuicyjny znacznik, który pomija dwa tagi z dwóch różnych powodów.

- **Pominięty Element właściwości StackPanel.Children:** <xref:System.Windows.Controls.StackPanel> pochodzi od <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>definiuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jako jego właściwość zawartości XAML.

- **Pominięty element obiektu UIElementCollection:** Właściwość <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> przyjmuje <xref:System.Windows.Controls.UIElementCollection>typ , <xref:System.Collections.IList>który implementuje . Tag elementu kolekcji można pominąć na podstawie reguł XAML do <xref:System.Collections.IList>przetwarzania kolekcji, takich jak . (W takim <xref:System.Windows.Controls.UIElementCollection> przypadku faktycznie nie można utworzyć wystąpienia, ponieważ nie udostępnia konstruktora bez parametrów i dlatego element <xref:System.Windows.Controls.UIElementCollection> obiektu jest wyświetlany skomentowane).

```xaml
<StackPanel>
  <StackPanel.Children>
    <!--<UIElementCollection>-->
    <Button>First Button</Button>
    <Button>Second Button</Button>
    <!--</UIElementCollection>-->
  </StackPanel.Children>
</StackPanel>
```

### <a name="attribute-syntax-events"></a>Składnia atrybutów (zdarzenia)

Składnia atrybutów może być również używana dla elementów członkowskich, które są zdarzeniami, a nie właściwościami. W takim przypadku nazwa atrybutu jest nazwą zdarzenia. W implementacji WPF dla XAML wartość atrybutu jest nazwą programu obsługi, który implementuje delegata tego zdarzenia. Na przykład następujące znaczniki przypisuje program <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi dla <xref:System.Windows.Controls.Button> zdarzenia do utworzonego w znacznikach:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

Istnieje więcej zdarzeń i XAML w WPF niż tylko w tym przykładzie składni atrybutu. Na przykład można się `ClickHandler` zastanawiać, co reprezentuje w tym miejscu, do którego odwołuje się i jak jest zdefiniowany. Zostanie to wyjaśnione w nadchodzącej sekcji [Wydarzenia i XAML związane z kodem](#events-and-xaml-code-behind) tego artykułu.

## <a name="case-and-white-space-in-xaml"></a>Obudowa i biały znak w XAML

Ogólnie rzecz biorąc, W języku XAML jest rozróżniana wielkość liter. Na potrzeby rozwiązywania typów kopii zapasowej WPF XAML jest rozróżniana wielkość liter przez te same reguły, że CLR jest rozróżniana wielkość liter. Elementy obiektu, elementy właściwości i nazwy atrybutów muszą być określone przy użyciu czułej wielkości liter w porównaniu według nazwy do typu źródłowego w zestawie lub do elementu członkowskiego typu. W językach XAML i w językach pierwotnych rozróżniana jest również wielkość liter. W wartościach nie zawsze jest rozróżniana wielkość liter. Wielkość liter dla wartości zależy od zachowania konwertera typu skojarzonego z właściwością, która przyjmuje wartość lub typem wartości właściwości. Na przykład właściwości, które <xref:System.Boolean> przyjmują typ `true` `True` może mieć jedną lub równoważne wartości, ale tylko dlatego, że <xref:System.Boolean> natywne WPF XAML konwersji typu parsera dla ciągu już zezwala na te jako odpowiedniki.

Procesory I serializatory WPF XAML ignorują lub upuszczają wszystkie nieistotne białe znaki i normalizują wszelkie znaczące odstępy. Jest to zgodne z domyślnymi zaleceniami zachowania odstępu specyfikacji XAML. To zachowanie jest tylko konsekwencji podczas określania ciągów we właściwościach zawartości XAML. W najprostszych słowach XAML konwertuje spację, wysuw liniowy i znaki tabulacji na spacje, a następnie zachowuje jedną spację, jeśli zostanie znaleziony na obu końcach ciągłego ciągu. Pełne wyjaśnienie obsługi odstępu XAML nie jest omówione w tym artykule. Aby uzyskać więcej informacji, zobacz [Przetwarzanie odstępów w języku XAML](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>Rozszerzenia struktury znaczników

Rozszerzenia znaczników są pojęciem języka XAML. Używane do dostarczania wartości składni atrybutów, nawiasy klamrowe (`{` i `}`) wskazują użycie rozszerzenia znaczników. To użycie kieruje przetwarzania XAML do ucieczki od ogólnego traktowania wartości atrybutów jako ciąg literał lub wartość konwersacyjną ciąg.

Najczęstsze rozszerzenia znaczników używane w programowaniu [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)aplikacji WPF są używane do wyrażeń wiązania danych oraz odwołań [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) do zasobów i [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Za pomocą rozszerzeń znaczników, można użyć składni atrybutów, aby podać wartości właściwości, nawet jeśli ta właściwość nie obsługuje składni atrybutu w ogóle. Rozszerzenia znaczników często używają typów wyrażeń pośrednich, aby włączyć funkcje, takie jak odracanie wartości lub odwoływanie się do innych obiektów, które są obecne tylko w czasie wykonywania.

Na przykład następujące znaczniki ustawia wartość <xref:System.Windows.FrameworkElement.Style%2A> właściwości przy użyciu składni atrybutu. Właściwość <xref:System.Windows.FrameworkElement.Style%2A> przyjmuje wystąpienie <xref:System.Windows.Style> klasy, które domyślnie nie może być tworzone przez ciąg składni atrybutu. Ale w tym przypadku atrybut odwołuje się do `StaticResource`określonego rozszerzenia znaczników, . Podczas przetwarzania tego rozszerzenia znaczników zwraca odwołanie do stylu, który został wcześniej szebrany jako zasób z kluczem w słowniku zasobów.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Aby uzyskać listę odwołań wszystkich rozszerzeń znaczników dla XAML zaimplementowanych specjalnie w WPF, zobacz [rozszerzenia WPF XAML](../../framework/wpf/advanced/wpf-xaml-extensions.md). Aby uzyskać listę odwołań do rozszerzeń znaczników zdefiniowanych przez system.Xaml i które są szerzej dostępne dla implementacji XAML .NET Core, zobacz [obszar nazw XAML (x:) Funkcje językowe](../xaml-services/namespace-language-features.md). Aby uzyskać więcej informacji na temat pojęć rozszerzenia znaczników, zobacz [Rozszerzenia znaczników i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Konwertery typów

W [składni XAML w](#xaml-syntax-in-brief) sekcji Krótki stwierdzono, że wartość atrybutu musi być ustawiona przez ciąg. Podstawowa, natywna obsługa sposobu konwertowania ciągów na inne <xref:System.String> typy obiektów lub wartości pierwotne jest <xref:System.DateTime> <xref:System.Uri>oparta na samym typie, oprócz przetwarzania natywnego dla niektórych typów, takich jak lub . Ale wiele typów WPF lub członków tych typów rozszerzyć podstawowe zachowanie przetwarzania atrybutów ciągu w taki sposób, że wystąpienia bardziej złożonych typów obiektów można określić jako ciągi i atrybuty.

Struktura <xref:System.Windows.Thickness> jest przykładem typu, który ma włączoną konwersję typu dla użycia XAML. <xref:System.Windows.Thickness>wskazuje pomiary w zagnieżdżonym prostokącie i jest <xref:System.Windows.FrameworkElement.Margin%2A>używana jako wartość właściwości, takich jak . Umieszczając konwerter typów <xref:System.Windows.Thickness>na , wszystkie <xref:System.Windows.Thickness> właściwości, które używają są łatwiejsze do określenia w XAML, ponieważ mogą być określone jako atrybuty. W poniższym przykładzie użyto składni konwersji typu i <xref:System.Windows.FrameworkElement.Margin%2A>atrybutu, aby podać wartość dla:

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

Przykład składni poprzedniego atrybutu jest odpowiednikiem następującego przykładu składni bardziej <xref:System.Windows.FrameworkElement.Margin%2A> szczegółowej, gdzie zamiast tego jest <xref:System.Windows.Thickness> ustawiane za pomocą składni elementu właściwości zawierającego element obiektu. Cztery kluczowe właściwości <xref:System.Windows.Thickness> są ustawiane jako atrybuty w nowym wystąpieniu:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Istnieje również ograniczona liczba obiektów, gdzie konwersja typu jest jedynym publicznym sposobem, aby ustawić właściwość do tego typu bez angażowania podklasy, ponieważ sam typ nie ma konstruktora bez parametrów. Może to być na przykład <xref:System.Windows.Input.Cursor>.

Aby uzyskać więcej informacji na temat konwersji typów, zobacz [TypeConverters i XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>Elementy główne XAML i przestrzenie nazw XAML

Plik XAML musi mieć tylko jeden element główny, aby był zarówno dobrze sformułowanym plikiem XML, jak i prawidłowym plikiem XAML. W typowych scenariuszach WPF należy użyć elementu głównego, który ma znaczenie widoczne <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> w modelu <xref:System.Windows.ResourceDictionary> aplikacji WPF (na <xref:System.Windows.Application> przykład lub dla strony, dla słownika zewnętrznego lub definicji aplikacji). Poniższy przykład przedstawia element główny typowego pliku XAML dla strony WPF, z elementem głównym <xref:System.Windows.Controls.Page>.

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

Element główny zawiera również `xmlns` `xmlns:x`atrybuty i . Te atrybuty wskazują procesorowi XAML, które obszary nazw XAML zawierają definicje typów typów kopii zapasowych, do których znaczniki będą odwoływać się jako elementy. Atrybut `xmlns` wskazuje w szczególności domyślną przestrzeń nazw XAML. W domyślnej przestrzeni nazw XAML elementy obiektów w znacznikach można określić bez prefiksu. W przypadku większości scenariuszy aplikacji WPF i dla prawie wszystkich przykładów podanych w sekcjach WPF SDK domyślny obszar `http://schemas.microsoft.com/winfx/2006/xaml/presentation`nazw XAML jest mapowany do obszaru nazw WPF . Atrybut `xmlns:x` wskazuje dodatkową przestrzeń nazw XAML, która mapuje obszar `http://schemas.microsoft.com/winfx/2006/xaml`nazw języka XAML .

To użycie `xmlns` do definiowania zakresu użycia i mapowania namescope jest zgodne ze specyfikacją XML 1.0. Namescopes XAML różnią się od nazw XML tylko w tym, że xaml namescope oznacza również coś o tym, jak namescope elementy są obsługiwane przez typy, jeśli chodzi o rozpoznawanie typów i analizowanie XAML.

Atrybuty `xmlns` są ściśle niezbędne tylko w elemencie głównym każdego pliku XAML. `xmlns`definicje będą miały zastosowanie do wszystkich elementów podrzędnych elementu głównego (to zachowanie jest `xmlns`ponownie zgodne ze specyfikacją XML 1.0 dla .) `xmlns` atrybuty są również dozwolone na innych elementów pod katalogiem głównym i będzie stosowany do wszystkich elementów podrzędnych elementu definiującego. Jednak częste definiowanie lub ponowne definiowanie obszarów nazw XAML może spowodować styl znaczników XAML, który jest trudny do odczytania.

Implementacja WPF jego procesor XAML zawiera infrastrukturę, która ma świadomość WPF zestawy rdzenia. WPF core zestawy są znane zawierają typy, które obsługują mapowania WPF do domyślnego obszaru nazw XAML. Jest to włączone za pośrednictwem konfiguracji, która jest częścią pliku kompilacji projektu i systemów kompilacji i projektu WPF. W związku z tym deklarowanie domyślnej przestrzeni `xmlns` nazw XAML jako domyślne jest wszystko, co jest niezbędne do odwoływania się do elementów XAML, które pochodzą z wpf.

### <a name="the-x-prefix"></a>Prefiks x:

W przykładzie poprzedniego elementu głównego `x:` prefiks został użyty `http://schemas.microsoft.com/winfx/2006/xaml`do mapowania obszaru nazw XAML, który jest dedykowaną przestrzenią nazw XAML obsługującą konstrukcje języka XAML. Ten `x:` prefiks jest używany do mapowania tej przestrzeni nazw XAML w szablonach dla projektów, w przykładach i w dokumentacji w tym zestawie SDK. Obszar nazw XAML dla języka XAML zawiera kilka konstrukcji programowania, które będą często używane w języku XAML. Poniżej znajduje się lista `x:` najczęściej używanych konstrukcji programowania prefiksów:

- [x:Key:](../xaml-services/xkey-directive.md)Ustawia unikatowy klucz dla <xref:System.Windows.ResourceDictionary> każdego zasobu w (lub podobnych pojęć słownika w innych ramach). `x:Key`prawdopodobnie będzie stanowić 90 `x:` procent użycia, które zobaczysz w typowych znaczników aplikacji WPF.

- [x:Klasa:](../xaml-services/xclass-directive.md)Określa obszar nazw CLR i nazwę klasy dla klasy, która udostępnia kod dla strony XAML. Musisz mieć taką klasę do obsługi związane z kodem na modelu programowania `x:` WPF i dlatego prawie zawsze widzisz mapowane, nawet jeśli nie ma żadnych zasobów.

- [x:Name](../xaml-services/xname-directive.md): Określa nazwę obiektu w czasie wykonywania dla wystąpienia, które istnieje w kodzie w czasie wykonywania po przetworzyniu elementu obiektu. Ogólnie rzecz biorąc, często będziesz używać właściwości równoważnej zdefiniowanej przez WPF dla [x:Name](../xaml-services/xname-directive.md). Takie właściwości mapują specjalnie do właściwości kopii CLR i w związku z tym są wygodniejsze w programowaniu aplikacji, gdzie często używasz kodu czasu wykonywania, aby znaleźć nazwane elementy z zainicjowanego XAML. Najczęstszą taką właściwością jest <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Nadal można użyć [x:Name,](../xaml-services/xname-directive.md) gdy równoważne <xref:System.Windows.FrameworkElement.Name%2A> WPF framework-level właściwość nie jest obsługiwana w określonym typie. Dzieje się tak w niektórych scenariuszach animacji.

- [x:Static](../xaml-services/xstatic-markup-extension.md): Włącza odwołanie, które zwraca wartość statyczną, która nie jest w przeciwnym razie właściwością kompatybilną z XAML.

- [x:Type](../xaml-services/xtype-markup-extension.md): Tworzy <xref:System.Type> odwołanie na podstawie nazwy typu. Służy do określania atrybutów, <xref:System.Type> <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>które zajmują , takich jak ,<xref:System.Type> chociaż często właściwość ma natywnego ciąg do konwersji w taki sposób, że [x:Type](../xaml-services/xtype-markup-extension.md) znaczników rozszerzenia rozszerzenia jest opcjonalne.

Istnieją dodatkowe konstrukcje programowania `x:` w przestrzeni nazw prefiks/XAML, które nie są tak powszechne. Aby uzyskać szczegółowe informacje, zobacz [Obszar nazw XAML (x:) Funkcje językowe](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Niestandardowe prefiksy i typy niestandardowe w języku XAML

Dla własnych zestawów niestandardowych lub dla zestawów poza rdzeniem WPF **PresentationCore**, **PresentationFramework** i **WindowsBase**, można określić zestaw jako część mapowania niestandardowego. `xmlns` Następnie można odwoływać się do typów z tego zestawu w xaml, tak długo, jak ten typ jest poprawnie zaimplementowana do obsługi użycia XAML, które próbujesz.

Poniżej przedstawiono podstawowy przykład działania prefiksów niestandardowych w znacznikach XAML. Prefiks `custom` jest zdefiniowany w tagu elementu głównego i mapowane do określonego zestawu, który jest spakowany i dostępny z aplikacją. Ten zestaw zawiera `NumericUpDown`typ , który jest implementowany do obsługi ogólnego użycia XAML, a także przy użyciu dziedziczenia klasy, który umożliwia jego wstawienie w tym określonym punkcie w modelu zawartości WPF XAML. Wystąpienie tego `NumericUpDown` formantu jest zadeklarowany jako element obiektu, przy użyciu prefiksu, tak aby analizator XAML wie, który obszar nazw XAML zawiera typ i dlatego, gdzie zestaw zapasowy jest, który zawiera definicję typu.

```xaml
<Page
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"
    >
  <StackPanel Name="LayoutRoot">
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>
...
  </StackPanel>
</Page>
```

Aby uzyskać więcej informacji na temat typów niestandardowych w języku XAML, zobacz [XAML i Klasy niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

Aby uzyskać więcej informacji na temat powiązanych obszarów nazw XML i obszarów nazw kodu w zestawach, zobacz [XAML Obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Zdarzenia i kod XAML

Większość aplikacji WPF składa się zarówno z znaczników XAML i związanych z kodem. W ramach projektu kod XAML jest `.xaml` zapisywany jako plik, a język CLR, taki jak Microsoft Visual Basic lub C#, jest używany do pisania pliku zawierającego kod. Gdy plik XAML jest znaczników skompilowanych jako część programowania WPF i modeli aplikacji, lokalizacja pliku związanego z kodem XAML dla pliku `x:Class` XAML jest identyfikowany przez określenie obszaru nazw i klasy jako atrybut elementu głównego XAML.

W przykładach do tej pory widziałeś kilka przycisków, ale żaden z tych przycisków nie miał jeszcze żadnego logicznego zachowania skojarzonego z nimi. Podstawowy mechanizm na poziomie aplikacji do dodawania zachowania dla elementu obiektu jest użycie istniejącego zdarzenia klasy elementu i napisać określonego programu obsługi dla tego zdarzenia, który jest wywoływany, gdy to zdarzenie jest wywoływane w czasie wykonywania. Nazwa zdarzenia i nazwa programu obsługi do użycia są określone w znacznikach, podczas gdy kod, który implementuje program obsługi jest zdefiniowany w kodzie.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Należy zauważyć, że plik związany z kodem używa obszaru `ExampleNamespace` nazw CLR i deklaruje `ExamplePage` jako klasę częściową w tym obszarze nazw. Jest to `x:Class` równoległe do `ExampleNamespace`wartości atrybutu .`ExamplePage` który został podany w katalogu głównym znaczników. Kompilator znaczników WPF utworzy klasę częściową dla dowolnego skompilowanego pliku XAML, wyprowadzając klasę z typu elementu głównego. Po podaniu kodu, który definiuje również tę samą klasę częściową, wynikowy kod jest łączony w tym samym obszarze nazw i klasy skompilowaną aplikację.

Aby uzyskać więcej informacji na temat wymagań dotyczących programowania bez kodu w WPF, zobacz [Code-behind, Event Handler i Częściowe wymagania klasy w WPF.](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf)

Jeśli nie chcesz utworzyć oddzielny plik związany z kodem, można również wbudowany kod w pliku XAML. Jednak kod wbudowany jest mniej wszechstronną techniką, która ma znaczne ograniczenia. Aby uzyskać więcej informacji, zobacz [Code-Behind i XAML w WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

### <a name="routed-events"></a>Kierowane zdarzenia

Funkcja określonego zdarzenia, która ma podstawowe dla WPF jest kierowane zdarzenie. Kierowane zdarzenia umożliwiają element do obsługi zdarzenia, które zostało podniesione przez inny element, tak długo, jak elementy są połączone za pośrednictwem relacji drzewa. Podczas określania obsługi zdarzeń z atrybutem XAML, kierowane zdarzenie można nasłuchiwał i obsługiwał na dowolnym elemencie, w tym elementy, które nie zawierają tej konkretnej zdarzenia w tabeli członków klasy. Jest to realizowane przez zakwalifikowanie atrybutu nazwa zdarzenia z nazwą klasy własnej. Na przykład element `StackPanel` nadrzędny `StackPanel`  /  `Button` w trwającym przykładzie może zarejestrować program obsługi dla `Button.Click` zdarzenia `StackPanel` przycisku elementu podrzędnego, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> określając atrybut elementu obiektu, z nazwą programu obsługi jako wartością atrybutu. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń trasowych](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>Elementy o nazwie XAML

Domyślnie wystąpienie obiektu utworzone na wykresie obiektu przez przetworzenie elementu obiektu XAML nie posiada unikatowego identyfikatora ani odwołania do obiektu. Z drugiej strony, jeśli wywołasz konstruktora w kodzie, prawie zawsze używasz wyniku konstruktora, aby ustawić zmienną na skonstruowane wystąpienie, dzięki czemu można odwoływać się do wystąpienia później w kodzie. Aby zapewnić znormalizowany dostęp do obiektów utworzonych za pomocą definicji znaczników, XAML definiuje [atrybut x:Name](../xaml-services/xname-directive.md). Można ustawić wartość atrybutu `x:Name` na dowolnym elemencie obiektu. W przypadku kodu, który wybierzesz identyfikator jest odpowiednikiem zmiennej wystąpienia, która odwołuje się do skonstruowanego wystąpienia. Pod każdym względem nazwane elementy działają tak, jakby były wystąpieniami obiektów (nazwy odwołań do tego wystąpienia), a kod związany może odwoływać się do nazwanych elementów do obsługi interakcji w czasie wykonywania w aplikacji. To połączenie między wystąpieniami i zmiennymi jest realizowane przez kompilator znaczników WPF XAML, <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> a w szczególności obejmują funkcje i wzorce, takie jak te nie zostaną omówione szczegółowo w tym artykule.

Elementy XAML na poziomie struktury <xref:System.Windows.FrameworkElement.Name%2A> WPF dziedziczą właściwość, `x:Name` która jest równoważna atrybutowi zdefiniowanemu przez XAML. Niektóre inne klasy również zapewniają odpowiedniki na poziomie właściwości `x:Name`dla `Name` programu , który jest również ogólnie zdefiniowany jako właściwość. Ogólnie rzecz biorąc, jeśli nie `Name` można znaleźć właściwości w tabeli członków `x:Name` dla wybranego elementu/typu, użyj zamiast tego. Wartości `x:Name` będą stanowić identyfikator elementu XAML, który może być używany w czasie wykonywania, przez określone podsystemy lub za pomocą metod narzędziowych, takich jak <xref:System.Windows.FrameworkElement.FindName%2A>.

Poniższy przykład <xref:System.Windows.FrameworkElement.Name%2A> ustawia <xref:System.Windows.Controls.StackPanel> na element. Następnie program obsługi <xref:System.Windows.Controls.Button> w <xref:System.Windows.Controls.StackPanel> obrębie, <xref:System.Windows.Controls.StackPanel> który odwołuje `buttonContainer` się do <xref:System.Windows.FrameworkElement.Name%2A>odwołania poprzez jego wystąpienie, zgodnie z zestawem przez .

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Podobnie jak zmienna, nazwa XAML dla wystąpienia jest regulowana przez pojęcie zakresu, dzięki czemu nazwy mogą być wymuszane jako unikatowe w określonym zakresie, który jest przewidywalny. Znacznik podstawowy definiujący stronę oznacza jeden unikatowy zakres nazw XAML, przy czym granica xaml namescope jest elementem głównym tej strony. Jednak inne źródła znaczników mogą wchodzić w interakcje ze stroną w czasie wykonywania, takie jak style lub szablony w stylach, a takie źródła znaczników często mają własne identyfikatory nazw XAML, które niekoniecznie łączą się z identyfikatorem XAML strony. Aby uzyskać `x:Name` więcej informacji na temat i <xref:System.Windows.FrameworkElement.Name%2A>xAML namescopes, zobacz , [x:Name Directive](../xaml-services/xname-directive.md)lub [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Dołączone właściwości i dołączone zdarzenia

XAML określa funkcję języka, która umożliwia określenie niektórych właściwości lub zdarzeń na dowolnym elemencie, niezależnie od tego, czy właściwość lub zdarzenie istnieje w definicjach typu dla elementu, na który jest ustawiany. Wersja właściwości tej funkcji jest nazywana dołączoną właściwością, wersja zdarzeń jest nazywana dołączonym zdarzeniem. Koncepcyjnie można myśleć o dołączonych właściwości i dołączonych zdarzeń jako globalnych elementów członkowskich, które można ustawić na dowolnym wystąpieniu elementu XAML/obiektu. Jednak ten element/klasa lub większa infrastruktura musi obsługiwać zapas właściwości kopii zapasowej dla dołączonych wartości.

Dołączone właściwości w XAML są zwykle używane za pośrednictwem składni atrybutów. W składni atrybutu należy określić dołączoną `ownerType.propertyName`właściwość w formularzu .

Powierzchownie przypomina użycie elementu właściwości, ale w `ownerType` tym przypadku określić jest zawsze inny typ niż element obiektu, w którym jest ustawiona dołączone właściwość. `ownerType`jest typem, który udostępnia metody akcesora, które są wymagane przez procesor XAML w celu uzyskania lub ustawić wartość dołączonej właściwości.

Najbardziej typowym scenariuszem dla dołączonych właściwości jest włączenie elementów podrzędnych do raportowania wartości właściwości do ich elementu nadrzędnego.

Poniższy przykład ilustruje dołączoną <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> właściwość. Klasa <xref:System.Windows.Controls.DockPanel> definiuje akcesory dla <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> i dlatego jest właścicielem dołączonej właściwości. Klasa <xref:System.Windows.Controls.DockPanel> zawiera również logikę, która iteruje jego elementy podrzędne <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>i w szczególności sprawdza każdy element dla ustawionej wartości . Jeśli wartość zostanie znaleziona, ta wartość jest używana podczas układu do położenia elementów podrzędnych. Korzystanie z <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączonej właściwości i tej zdolności pozycjonowania <xref:System.Windows.Controls.DockPanel> jest w rzeczywistości scenariusz motywacyjny dla klasy.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

W WPF WPF większość lub wszystkie dołączone właściwości są również implementowane jako właściwości zależności. Aby uzyskać więcej informacji, zobacz [Omówienie załączonych właściwości](../../framework/wpf/advanced/attached-properties-overview.md).

Dołączone zdarzenia używają `ownerType.eventName` podobnej formy składni atrybutów. Podobnie jak zdarzenia niezałączone, wartość atrybutu dla dołączonego zdarzenia w XAML określa nazwę metody obsługi, która jest wywoływana, gdy zdarzenie jest obsługiwane w elemencie. Dołączone użycia zdarzeń w WPF XAML są mniej powszechne. Aby uzyskać więcej informacji, zobacz [Omówienie załączonych zdarzeń](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Typy podstawowe i kod XAML

Podstawowe WPF XAML i jego przestrzeni nazw XAML jest zbiorem typów, które odpowiadają clr obiektów oprócz elementów znaczników dla XAML. Jednak nie wszystkie klasy mogą być mapowane na elementy. Klasy abstrakcyjne, <xref:System.Windows.Controls.Primitives.ButtonBase>takie jak , i niektóre nieseparskie klasy podstawowe, są używane do dziedziczenia w modelu obiektów CLR. Klasy podstawowe, w tym abstrakcyjne, są nadal ważne dla rozwoju XAML, ponieważ każdy z konkretnych elementów XAML dziedziczy członków z niektórych klas podstawowych w hierarchii. Często te elementy członkowskie obejmują właściwości, które można ustawić jako atrybuty elementu lub zdarzenia, które mogą być obsługiwane. <xref:System.Windows.FrameworkElement>jest betonową bazą UI klasy WPF na poziomie framework WPF. Podczas projektowania interfejsu użytkownika, można użyć różnych kształtów, panel, dekorator, lub klasy sterowania, które pochodzą z <xref:System.Windows.FrameworkElement>. Powiązana klasa <xref:System.Windows.FrameworkContentElement>podstawowa obsługuje elementy zorientowane na dokument, które działają dobrze w przypadku prezentacji układu <xref:System.Windows.FrameworkElement>przepływu, przy użyciu interfejsów API, które celowo odzwierciedlają interfejsy API w programie . Kombinacja atrybutów na poziomie elementu i modelu obiektu CLR zapewnia zestaw wspólnych właściwości, które są ustawione na większości elementów XAML betonu, niezależnie od określonego elementu XAML i jego typ podstawowy.

## <a name="xaml-security"></a>Zabezpieczenia XAML

XAML jest językiem znaczników, który bezpośrednio reprezentuje tworzenie i wykonywanie wystąpienia i obiektu. W związku z tym elementy utworzone w XAML mają taką samą możliwość interakcji z zasobami systemowymi (dostęp do sieci, system plików We/Wy, na przykład) jak równoważny wygenerowany kod. XAML załadowany do w pełni zaufanej aplikacji ma taki sam dostęp do zasobów systemowych, jak aplikacja hostingowa.

### <a name="code-access-security-cas-in-wpf"></a>Zabezpieczenia dostępu do kodu (CAS) w WPF

**Ta sekcja dotyczy tylko programu .NET Framework. WPF WPF dla platformy .NET Core nie obsługuje cas. Aby uzyskać więcej informacji, zobacz [Różnice zabezpieczeń dostępu do kodu](../migration/differences-from-net-framework.md#code-access-security).**

WPF DLA platformy .NET Framework obsługuje zabezpieczenia dostępu do kodu (CAS). Oznacza to, że zawartość WPF uruchomiona w strefie internetowej zmniejszyła uprawnienia do wykonywania. "Loose XAML" (strony niekompilowanego XAML interpretowane w czasie ładowania przez przeglądarkę XAML) i XBAP są zwykle uruchamiane w tej strefie internetowej i używają tego samego zestawu uprawnień. Jednak XAML załadowany do w pełni zaufanej aplikacji ma taki sam dostęp do zasobów systemowych, jak aplikacja hostingowa. Aby uzyskać więcej informacji, zobacz [WPF Częściowe zabezpieczenia zaufania](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Ładowanie kodu XAML z kodu

XAML może służyć do definiowania wszystkich interfejsu użytkownika, ale czasami jest również odpowiednie do zdefiniowania tylko kawałek interfejsu użytkownika w języku XAML. Ta funkcja może służyć do umożliwienia częściowego dostosowywania, lokalnego przechowywania informacji, przy użyciu XAML w celu zapewnienia obiektu biznesowego lub różnych możliwych scenariuszy. Kluczem do tych scenariuszy <xref:System.Windows.Markup.XamlReader> jest <xref:System.Windows.Markup.XamlReader.Load%2A> klasa i jej metoda. Dane wejściowe są plikiem XAML, a dane wyjściowe są obiektem reprezentującym wszystkie drzewa wykonywania obiektów utworzonych na podstawie tego znaczników. Następnie można wstawić obiekt jako właściwość innego obiektu, który już istnieje w aplikacji. Tak długo, jak właściwość jest odpowiednią właściwością w modelu zawartości, która ma możliwości wyświetlania, które mają możliwość wyświetlania i która powiadomi aparat wykonywania, że nowa zawartość została dodana do aplikacji, można łatwo zmodyfikować zawartość uruchomionej aplikacji, ładując w języku XAML. W przypadku platformy .NET Framework ta funkcja jest ogólnie dostępna tylko w aplikacjach pełnego zaufania, ze względu na oczywiste implikacje bezpieczeństwa ładowania plików do aplikacji podczas ich uruchamiania.

## <a name="see-also"></a>Zobacz też

- [Szczegóły składni XAML](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [Klasy XAML i niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Przestrzeń nazw XAML (x:) Funkcje językowe](../xaml-services/namespace-language-features.md)
- [Rozszerzenia WPF XAML](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Przegląd Elementy bazy](../../framework/wpf/advanced/base-elements-overview.md)
- [Drzewa w WPF](../../framework/wpf/advanced/trees-in-wpf.md)
