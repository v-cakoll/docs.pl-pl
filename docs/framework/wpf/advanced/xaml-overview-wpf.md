---
title: Przegląd XAML (WPF)
ms.date: 03/30/2017
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
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
ms.openlocfilehash: ec7072e7af15bdff373962f776abf0aad89361bb
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220779"
---
# <a name="xaml-overview-wpf"></a>Przegląd XAML (WPF)
W tym temacie opisano funkcje języka XAML oraz pokazano, jak można użyć XAML można zapisać [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym temacie opisano szczegółowo XAML jako implementowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XAML, sama jest pojęciem języka większych niż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>Co to jest XAML?  
 XAML jest deklaratywnym językiem znaczników. Jakie mają zastosowanie do modelu programowania .NET Framework, XAML upraszcza tworzenie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla aplikacji .NET Framework. Można tworzyć widoczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów w oznaczeniu deklaracyjnym XAML, a następnie oddzielne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definicji od logiki czasu wykonywania przy użyciu plików z kodem, przyłączone do znaczników za pomocą częściowych definicji klasy. XAML reprezentuje bezpośrednio utworzyć wystąpienia obiektów w określonych typów zdefiniowanych w zestawach kopii. Jest to w przeciwieństwie do większości innych znaczników języków, które są zazwyczaj interpretowanych języka, bez bezpośredniego tie systemu typów zapasowy. XAML włącza przepływ pracy, w którym osobnych stron może pracować nad [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i logikę aplikacji, za pomocą różnych narzędzi.  
  
 Gdy reprezentowane jako tekst, pliki XAML znajdują się pliki XML, które zwykle mają `.xaml` rozszerzenia. Pliki mogą być kodowane przez żadnego kodu XML, kodowania, lecz kodowanie UTF-8 jest typowy.  
  
 W poniższym przykładzie pokazano, jak można utworzyć przycisk w ramach [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. W tym przykładzie po prostu jest przeznaczona do umożliwiają wersję jak XAML reprezentuje typowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] programowania metafory (nie jest pełny przykład).  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Składnia XAML w skrócie  
 W poniższych sekcjach opisano podstawowe formy składnia XAML i podać przykład krótka adiustację. Poniższe sekcje nie są przeznaczone do zapewniają pełne informacje na temat każdego forma składni, np. jak te są reprezentowane w systemie typów zapasowy. Aby uzyskać więcej informacji o szczegóły składni XAML dla każdego formami składni opisanymi w tym temacie, zobacz [składnia XAML w szczegółów](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Wiele materiałów w kolejnych sekcjach zostanie podstawowych, w przypadku poprzedniego znajomość języka XML. Jest to konsekwencją podstawowe zasady projektowania z XAML.  Język XAML definiuje swój własny pojęcia, ale te pojęcia działa w obrębie formularza języka i znaczników XML.  
  
### <a name="xaml-object-elements"></a>Elementy obiektu XAML  
 Element obiektu zwykle deklaruje wystąpienie typu. Ten typ jest zdefiniowany w zestawy, które zawierają typy zapasowy technologii, która używa XAML jako język.  
  
 Składnia elementu obiekt zawsze rozpoczyna się od nawias otwierający (\<). To następuje nazwa typu potrzebne do utworzenia wystąpienia. (Nazwa prawdopodobnie może zawierać prefiks pojęcia, które zostaną wyjaśnione później.) Po tym można opcjonalnie zadeklarować atrybutów w elemencie obiektu. Aby ukończyć tagu elementu obiektu, kończy się zamykającego nawiasu ostrego (>). Zamiast tego można użyć samozamykającego formularz, który nie ma żadnej zawartości, Trwa uzupełnianie tagu ukośnikiem i zamykającego nawiasu ostrego w odstępie czasu (/ >). Na przykład Przyjrzyj się fragment kodu znaczników wcześniej pokazano ponownie:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Określa obiekt dwa elementy: `<StackPanel>` (z zawartością, a tag zamykający w dalszej części), a `<Button .../>` (samozamykającego formularz, za pomocą kilku atrybutów). Elementy obiektu `StackPanel` i `Button` każdej mapie, aby nazwa klasy, który jest definiowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i jest częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów. Po określeniu tagu elementu obiektu, utworzysz instrukcję dla XAML przetwarzanie w celu utworzenia nowego wystąpienia. Każde wystąpienie jest tworzony przez wywołanie konstruktora domyślnego typu podstawowego podczas analizowania i ładowania XAML.  
  
### <a name="attribute-syntax-properties"></a>Składnia atrybutów (właściwości)  
 Właściwości obiektu często może być wyrażona jako atrybuty elementu obiektu. Składnia atrybutu nazwy właściwości, która jest ustawiany w składni atrybutów, a następnie operator przypisania (=). Wartość atrybutu jest zawsze określony jako ciąg, który jest zawarty w znaki cudzysłowu.  
  
 Składnia atrybutów jest najbardziej usprawnione składnia ustawienie właściwości i najbardziej intuicyjnej składni do użycia dla deweloperów, którzy korzystali z języków znaczników w przeszłości. Na przykład, następujący kod tworzy przycisk, który posiada czerwony tekst i niebieskim tle oprócz wyświetlany tekst określony jako `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Składnia elementu właściwości  
 Niektórych właściwości elementu obiektu składni atrybutów jest to możliwe, ponieważ obiektu lub informacje niezbędne do zapewnienia wartość właściwości nie może być odpowiednio wyrażany w cudzysłów i ciąg ograniczenia składni atrybutów. W takich przypadkach można używać różnych składni, znane jako składni elementu właściwości.  
  
 Składnia służąca do tagu początkowym elementu właściwości jest `<` *typeName*`.`*propertyName*`>`. Ogólnie rzecz biorąc zawartość tego tagu jest elementem obiektu typu, który właściwość przyjmuje jako jego wartość. Po określeniu zawartości, należy zamknąć element właściwości z tagu końcowego. Składnia służąca do tagu końcowego jest `</` *typeName*`.`*propertyName*`>`.  
  
 Składnia atrybutów jest możliwe, przy użyciu składni atrybutu jest zazwyczaj bardziej wygodne i umożliwia bardziej zwarty znaczników, ale najczęściej jest to kwestia stylu, nie ograniczenia techniczne. W poniższym przykładzie pokazano te same właściwości ustawiany jak w poprzednim przykładzie atrybut w składni, ale tym razem przy użyciu składni elementu właściwości dla wszystkich właściwości `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Składnia kolekcji  
 Język XAML zawiera niektóre optymalizacje, które generują bardziej czytelny dla człowieka znaczników. Takiej optymalizacji jest to, że jeśli określona właściwość przyjmuje typ kolekcji, a następnie elementy, które deklarują w znacznikach jako elementy podrzędne w ramach tej właściwości wartość stają się częścią kolekcji. W tym przypadku kolekcję elementów podrzędnych do obiektu jest wartość zostanie ustawiona właściwość kolekcji.  
  
 Poniższy przykład pokazuje składnię kolekcji do ustawiania wartości <xref:System.Windows.Media.GradientBrush.GradientStops%2A> właściwości:  
  
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
 XAML określa funkcji języka, według której klasy można wyznaczyć dokładnie jeden z jej właściwości na właściwość zawartości XAML. Elementy podrzędne tego elementu obiektu są używane do ustawiania wartości właściwości zawartości. Innymi słowy dla właściwości zawartości jednoznacznie, można pominąć element właściwości podczas ustawiania właściwości w znaczniku XAML i utworzyć bardziej widoczne metaphor nadrzędne/podrzędne w znaczniku.  
  
 Na przykład <xref:System.Windows.Controls.Border> Określa właściwość content <xref:System.Windows.Controls.Decorator.Child%2A>. Następujące dwa <xref:System.Windows.Controls.Border> elementy są traktowane identycznie. Pierwsza z nich korzysta ze składni właściwość zawartości i pomija `Border.Child` elementu właściwości. Drugi pokazuje `Border.Child` jawnie.  
  
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
  
 Reguły języka XAML wartość właściwości zawartości XAML należy całkowicie przed lub w całości po innych elementów właściwości w elemencie tego obiektu. Na przykład następujące znaczniki nie kompiluje:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Aby uzyskać więcej informacji na temat tego ograniczenia właściwości zawartości XAML, zobacz sekcję "Properties zawartości XAML" [składnia XAML w szczegółów](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Zawartość tekstowa  
 Niewielka liczba elementów XAML bezpośrednio może przetwarzać tekst jako swojej zawartości. Aby je włączyć, należy spełnić jedną z następujących przypadkach:  
  
-   Klasa musi deklarować właściwość zawartości i tę właściwość zawartości musi być typu można przypisać do ciągu (typ może być <xref:System.Object>). Na przykład dowolny <xref:System.Windows.Controls.ContentControl> używa <xref:System.Windows.Controls.ContentControl.Content%2A> jako jej właściwości zawartości jest typem <xref:System.Object>, i w ten sposób realizowany następujące użycie w praktyczny <xref:System.Windows.Controls.ContentControl> takich jak <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
-   Typ musi deklarować konwertera typów, w którym przypadku zawartości tekstowej jest używany jako tekst inicjowania dla tego konwertera typów. Na przykład `<Brush>Blue</Brush>`. Ten przypadek jest mniej typowe w praktyce.  
  
-   Typ musi być znane pierwotne języka XAML.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>Połączone składnia zawartości właściwości i kolekcji  
 Rozważmy następujący przykład:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 W tym miejscu każdego <xref:System.Windows.Controls.Button> jest elementem podrzędnym <xref:System.Windows.Controls.StackPanel>. Jest to prostsze i intuicyjne znaczników, które pomija dwoma tagami w dwóch różnych powodów.  
  
-   **Property — element został pominięty StackPanel.Children:** <xref:System.Windows.Controls.StackPanel> pochodzi od klasy <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel> definiuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jako jego XAML zawartości właściwości.  
  
-   **Object — element został pominięty UIElementCollection:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> właściwość przyjmuje typ <xref:System.Windows.Controls.UIElementCollection>, który implementuje <xref:System.Collections.IList>. Można pominąć tagu elementu kolekcji, na podstawie reguł XAML do przetwarzania kolekcji, takie jak <xref:System.Collections.IList>. (W tym przypadku <xref:System.Windows.Controls.UIElementCollection> faktycznie nie może zostać utworzona, ponieważ nie uwidacznia konstruktora domyślnego i dlatego <xref:System.Windows.Controls.UIElementCollection> element obiektu jest wyświetlany skomentowanej out).  
  
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
 Składnia atrybutów może również dla elementów członkowskich, które są zdarzenia, a nie właściwości. W takim przypadku nazwa ten atrybut jest nazwa zdarzenia. W implementacji WPF zdarzenia dla XAML wartość atrybutu jest nazwą programu obsługi, która implementuje delegata tego zdarzenia. Na przykład, następujący kod przypisuje obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia <xref:System.Windows.Controls.Button> utworzone w znaczników:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Brak zdarzeń i XAML w WPF ponad właśnie w tym przykładzie składni atrybutów. Na przykład, być może zastanawiasz się, jakie `ClickHandler` odwołujesz reprezentuje i jak jest zdefiniowany. Zostanie to wyjaśnione w przyszłych [zdarzeń i kodem XAML](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind) części tego tematu.  
  
<a name="case_and_white space_in_xaml"></a>   
## <a name="case-and-white-space-in-xaml"></a>Wielkość liter i biały znak w XAML  
 XAML ogólnie rzecz biorąc jest uwzględniana wielkość liter. Do celów rozpoznawania typów zapasowy WPF XAML jest uwzględniana wielkość liter, przez te same zasady, że środowisko CLR jest uwzględniana wielkość liter. Elementów obiektu, elementy właściwości i nazw atrybutów muszą być wszystkie określone za pomocą liter małych i wielkich liter w porównaniu z według nazwy do bazowego typu w zestawie lub do składowej typu. Słowa kluczowe języka XAML i podstawowych są również z uwzględnieniem wielkości liter. Wartości nie są zawsze z uwzględnieniem wielkości liter. Uwzględnianie wielkości liter w wartości będzie zależeć od zachowania konwertera typu skojarzony z właściwością, która przyjmuje wartość lub typ wartości właściwości. Na przykład, właściwości, które przyjmują <xref:System.Boolean> typu może zająć, albo `true` lub `True` jako równoważne wartości, ale tylko wtedy, ponieważ natywnych analizatora WPF XAML typ konwersji ciągu na <xref:System.Boolean> już pozwala je jako odpowiedniki.  
  
 Procesory WPF XAML i serializatorów zignoruje lub porzucić wszystkie nonsignificant biały znak i będzie normalizacji żadnych istotnych białych. Jest to zgodne z zaleceniami domyślne zachowanie spacji specyfikacji XAML. To zachowanie jest zwykle tylko z wynikiem po określeniu parametrów w ramach właściwości zawartości XAML. Mówiąc najprościej XAML konwertuje znaki spacji, wysuw wiersza lub tabulatora do miejsca do magazynowania, a następnie zachowuje jedną spację, jeśli znalezione na końcu ciągu ciągłych. Pełne wyjaśnienie Obsługa białych XAML nie pasuje do tego tematu. Aby uzyskać więcej informacji, zobacz [biały znak przetwarzanie w XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 Rozszerzenia znaczników są koncepcji języka XAML. W przypadku zastosowania do podania wartości składni atrybutów, nawiasy klamrowe (`{` i `}`) wskazują użycie rozszerzenia znaczników. Użycie tych poleca XAML przetwarzania uciekały z ogólnych traktowanie wartości atrybutów jako ciąg literału lub wartość przekonwertować ciąg.  
  
 Najbardziej typowe rozszerzenia znaczników używane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania aplikacji są [powiązania](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), który jest używany dla wyrażenia wiązania danych i odwołania do zasobów [staticresource —](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) i [Dynamicresource —](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Za pomocą rozszerzenia znaczników, można użyć składni atrybutów o podanie wartości właściwości, nawet jeśli ta właściwość nie obsługuje składni atrybutów ogólnie rzecz biorąc. Rozszerzenia znaczników często używają typów wyrażeń pośrednich do włączania funkcji, takich jak opóźnienie wartości lub odwołania do innych obiektów, które istnieją tylko w czasie wykonywania.  
  
 Na przykład, następujący kod ustawia wartość <xref:System.Windows.FrameworkElement.Style%2A> właściwości przy użyciu składni atrybutów. <xref:System.Windows.FrameworkElement.Style%2A> Właściwość przyjmuje wystąpienie klasy <xref:System.Windows.Style> klasy, która domyślnie nie mogła zostać utworzona przez ciąg Składnia atrybutu. Ale w tym przypadku atrybut odwołuje się rozszerzeniem znacznika określonego [staticresource —](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Podczas przetwarzania tego rozszerzenia znaczników zwraca odwołanie do stylu, który został wcześniej uruchomiony jako zasób z kluczem w słowniku zasobów.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Aby uzyskać odwołanie lista wszystkie rozszerzenia znaczników dla XAML jest zaimplementowana w szczególności na platformie WPF, zobacz [WPF XAML rozszerzenia](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md). Aby uzyskać listę rozszerzeń znaczników, które są definiowane przez System.Xaml i są bardziej dostępna dla implementacji .NET Framework XAML, zobacz [Namespace XAML (x:) Funkcje języka](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Aby uzyskać więcej informacji na temat pojęć związanych z rozszerzenia znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Konwertery typu  
 W [składnia XAML w skrócie](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief) sekcji stwierdzono, że wartość atrybutu musi być może ustawić przez ciąg. Podstawowa, natywnej obsługi jak ciągi są konwertowane na inne typy obiektów lub wartości pierwotnych opiera się na <xref:System.String> samego typu, dodatkowo do kodu natywnego przetwarzania dla niektórych typów takich jak <xref:System.DateTime> lub <xref:System.Uri>. Jednak wiele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy lub elementy członkowskie z tych typów rozszerzyć atrybutu podstawowego ciągu przetwarzania zachowanie w taki sposób, że wystąpienia bardziej złożonych typów obiektów można określić jako ciągi i atrybutów.  
  
 <xref:System.Windows.Thickness> Struktury jest przykładem typu, który został włączony dla XAML użycia konwersji typu. <xref:System.Windows.Thickness> Wskazuje pomiarów w obrębie zagnieżdżonych prostokąta i jest używana jako wartość właściwości, takie jak <xref:System.Windows.FrameworkElement.Margin%2A>. Umieszczając konwertera typów na <xref:System.Windows.Thickness>, wszystkie właściwości, które używają <xref:System.Windows.Thickness> łatwiej określić w XAML, ponieważ mogą być określone jako atrybuty. W poniższym przykładzie użyto składni atrybut i konwersji typu, aby podać wartość dla <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 Poprzedni przykład atrybutu w składni jest odpowiednikiem następujących bardziej szczegółowy przykład składni, gdzie <xref:System.Windows.FrameworkElement.Margin%2A> zamiast tego jest ustawiony za pomocą właściwości elementu składni zawierający <xref:System.Windows.Thickness> element obiektu. Cztery klucza właściwości <xref:System.Windows.Thickness> są ustawione jako atrybuty w nowym wystąpieniu:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Istnieje ograniczona liczba obiektów, gdzie konwersji typu jest tylko publiczne sposób, aby przypisać właściwość do tego typu nie angażując podklasy, ponieważ sam typ nie ma domyślnego konstruktora. Na przykład <xref:System.Windows.Input.Cursor>.  
  
 Aby uzyskać więcej informacji na temat sposobu konwersji typu i jego użycia dla atrybutu składnia jest obsługiwana, zobacz [TypeConverters i XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>Elementy główne XAML i przestrzeni nazw XAML  
 Plik XAML musi mieć tylko jeden element główny, aby obie sformułowany [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] plików i prawidłowy plik XAML. Typowe scenariusze WPF, możesz użyć elementu głównego, który ma znaczenie widocznych w modelu aplikacji WPF (na przykład <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> dla strony sieci <xref:System.Windows.ResourceDictionary> dla zewnętrznego słownika lub <xref:System.Windows.Application> definicji aplikacji). W poniższym przykładzie pokazano element główny typowy plik XAML dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony z elementem głównym <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Element główny zawiera też atrybuty `xmlns` i `xmlns:x`. Te atrybuty wskazuje procesora XAML, który XAML przestrzenie nazw zawierają definicje typów dla kopii typów odwołujących znaczników jako elementy. `xmlns` Atrybut specjalnie wskazuje domyślną przestrzeń nazw XAML. W domyślnej przestrzeni nazw XAML można określić elementów obiektu w znaczniku bez prefiksu. Dla większości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] scenariuszy aplikacji i dla prawie wszystkich przykłady zamieszczone w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sekcje [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], domyślna przestrzeń nazw XAML jest mapowany na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. `xmlns:x` Atrybut wskazuje dodatkowych nazw XAML, który mapuje przestrzeń nazw języka XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 To użycie `xmlns` Aby zdefiniować zakres użycia i mapowanie namescope jest spójna ze Specyfikacja XML 1.0. Zakresy nazw XAML różnią się od zakresy nazw XML tylko dlatego, że coś o jak namescope elementy są objęte typów, jeśli chodzi o typ rozdzielczość i analiza kodu XAML oznacza również XAML namescope.  
  
 Należy pamiętać, że `xmlns` atrybuty tylko są niezbędne dla elementu głównego pliku XAML. `xmlns` definicje zostaną zastosowane do wszystkich elementów podrzędnych elementu głównego (to zachowanie jest ponownie zgodne z Specyfikacja XML 1.0 `xmlns`.) `xmlns` atrybuty są również dozwolone na inne elementy poniżej katalogu głównego i zastosowanie do wszelkich elementów podrzędnych elementu definiujące. Jednak często definicja lub ponowna definicja przestrzeni nazw XAML może spowodować styl znaczników XAML, który jest trudny do odczytania.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementacja jego procesor XAML obejmuje infrastrukturę, która ma rozpoznawania zestawów podstawowych WPF. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Wiadomo, że podstawowe zestawy zawierają typy obsługujące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapowania do domyślnej przestrzeni nazw XAML. Ta opcja jest włączona za pośrednictwem konfiguracji, który jest częścią kompilacji projektu pliku WPF kompilacji i systemy projektów. W związku z tym, deklarowanie domyślna przestrzeń nazw XAML jako domyślny `xmlns` to wszystko, co jest niezbędne, aby można było odwoływać się do elementów XAML, które pochodzą z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.  
  
### <a name="the-x-prefix"></a>Prefiks x:  
 W poprzednim przykładzie element główny, prefiks `x:` został użyty do mapowania przestrzeni nazw XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], czyli dedykowanej przestrzeni nazw XAML, który obsługuje język XAML konstrukcji. To `x:` prefiks jest używany do mapowania tej przestrzeni nazw XAML szablonów dla projektów, przykłady i dokumentację w całym to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Przestrzeń nazw XAML dla języka XAML zawiera kilka narzędzi programistycznych, które będą bardzo często używane w Twojej XAML. Poniżej przedstawiono listę najbardziej typowych `x:` narzędzi programistycznych, będzie używać prefiksu:  
  
-   [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md): ustawia Unikatowy klucz dla każdego zasobu w <xref:System.Windows.ResourceDictionary> (lub podobny pojęcia słownika w innych platform). `x:Key` prawdopodobnie będziesz konta przez 90% `x:` użycia będą widoczne w Typowa aplikacja WPF znaczników.  
  
-   [x: Class](../../../../docs/framework/xaml-services/x-class-directive.md): Określa [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw i nazwę klasy dla klasy, która udostępnia związany z kodem dla strony XAML. Konieczne jest posiadanie klasy do obsługi związanym z kodem na model programowania WPF, a w związku z tym prawie zawsze widać `x:` mapowane, nawet jeśli nie ma żadnych zasobów.  
  
-   [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md): Określa nazwę obiektów czasu wykonywania dla tego wystąpienia, która istnieje w czasie wykonywania kodu, po przetworzeniu elementu obiektu. Ogólnie rzecz biorąc, często użyje zdefiniowane WPF równoważne właściwość [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Takie właściwości mapowania specjalnie w celu CLR kopii właściwości i dlatego są bardziej wygodne do programowania aplikacji, gdzie jest często używana kodu w czasie wykonywania do znajdowania nazwanych elementów z XAML zainicjowane. Najczęściej jest taką właściwość <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Może być nadal używane [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) podczas równoważne poziomie struktury WPF <xref:System.Windows.FrameworkElement.Name%2A> właściwość nie jest obsługiwana w określonego typu. Dzieje się w niektórych scenariuszach animacji.  
  
-   [x: Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): umożliwia odwołanie zwracające wartość statyczna, która nie jest w przeciwnym razie właściwość zgodnego z XAML.  
  
-   [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): tworzy <xref:System.Type> odwołanie oparte na nazwie typu. Służy do określania atrybutów, które przyjmują <xref:System.Type>, takich jak <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, chociaż często właściwość ma parametry natywnych-do-<xref:System.Type> konwersji w taki sposób, [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) jest użycie rozszerzenia znaczników Opcjonalnie.  
  
 Istnieją dodatkowe programowania konstrukcje w `x:` prefiks/XAML przestrzeni nazw, które nie są jako wspólne. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Prefiksy niestandardowe i niestandardowych typów w XAML  
 Zestawy niestandardowe lub zestawów poza podstawowe WPF PresentationCore, PresentationFramework i WindowsBase, możesz określić zestaw jako część niestandardowego `xmlns` mapowania. Następnie można odwoływać się typów z tego zestawu w Twojej XAML, tak długo, jak tego typu jest implementowana prawidłowo do obsługi użycia XAML, którą próbujesz.  
  
 Poniżej znajduje się bardzo prosty przykład niestandardowych pracy prefiksy w znaczniku XAML. Prefiks `custom` jest zdefiniowany w tagu elementu głównego i mapowany do określonego zestawu, który jest spakowane i dostępna z aplikacją. Ten zestaw zawiera typ `NumericUpDown`, które jest implementowane w celu obsługi ogólne użycie XAML, a także za pomocą dziedziczenia klas, który zezwala na jego wstawiania na tym etapie określonego w modelu zawartości WPF XAML. Wystąpienie tego elementu `NumericUpDown` kontroli jest zadeklarowany jako element obiektu, przy użyciu prefiksu, XAML, który wie, analizator składni XAML przestrzeń nazw zawiera typ i w związku z tym w przypadku zestawu zapasowy zawierający definicję typu.  
  
```  
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
  
 Aby uzyskać więcej informacji na temat niestandardowych typów w XAML, zobacz [XAML klasy i niestandardowe dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
 Aby uzyskać więcej informacji na temat sposobu związane z przestrzeni nazw XML i przestrzenie nazw kodu zapasowy w zestawach, zobacz [przestrzeni nazw XAML i Namespace mapowania dla WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Zdarzenia i kodem XAML  
 Większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje składają się ze znaczników XAML i kodem. W projekcie w języku XAML jest zapisywany jako `.xaml` pliku, a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] języka, takich jak Microsoft Visual Basic lub C# jest używany do zapisywania pliku CodeBehind. Plik XAML po kompilacji w ramach modeli programowania i aplikacji WPF znaczników lokalizacji kodu związanego z XAML pliku dla pliku XAML jest identyfikowany przez określenie przestrzeni nazw i klasy `x:Class` atrybutu element główny XAML.  
  
 W przykładach do tej pory wiesz już kilka przycisków, ale żaden z tych przycisków miał każde zachowanie logicznej jeszcze skojarzone z nimi. Zachowanie obiektu elementu Dodawanie podstawowym mechanizmem dodatku poziomu aplikacji jest aby użyć istniejącego zdarzenia klasy elementów i do zapisu określonego programu obsługi dla tego zdarzenia, które jest wywoływane, gdy zdarzenie jest zgłaszane w czasie wykonywania. Nazwa zdarzenia i nazwę programu obsługi, aby użyć są określone w znaczników, kod, który implementuje programu obsługi jest zdefiniowane w związanym z kodem.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Zwróć uwagę, że plik związany z kodem używa przestrzeni nazw CLR `ExampleNamespace` i deklaruje `ExamplePage` jako częściowe klasy w tej przestrzeni nazw. To równoleżnikami `x:Class` wartość atrybutu `ExampleNamespace`.`ExamplePage` która została dostarczona w katalogu głównym znaczników. Kompilator znaczników WPF utworzy klasę częściową dla dowolnego skompilowany plik XAML, wyprowadzanie klasy z typem elementu głównego. Po podaniu związanym z kodem definiujący tej samej klasy częściowej wynikowy kod jest łączony w ramach tej samej przestrzeni nazw i klasy skompilowanej aplikacji.  
  
 Aby uzyskać więcej informacji na temat wymagań dotyczących programowania związane z kodem w WPF, zobacz sekcję "związany z kodem, program obsługi zdarzeń i ich wymagania klasy częściowej" [związanym z kodem i XAML w WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
 Jeśli chcesz utworzyć plik oddzielne związanym z kodem, możesz również wbudowany kod w pliku XAML. Wbudowany kod jest jednak mniej wszechstronna technika, która ma znaczące ograniczenia. Aby uzyskać więcej informacji, zobacz [związanym z kodem i XAML w WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Zdarzenia trasowane  
 Funkcja konkretnego zdarzenia, który ma podstawowe znaczenie dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zdarzenie trasowane. Kierowane Włącz zdarzenia elementu, aby obsłużyć zdarzenie, który został zgłoszony przez inny element, tak długo, jak elementy są połączone za pomocą relacji drzewa. Podczas określania obsługi za pomocą atrybutu XAML zdarzeń, można posłuchaliśmy dla zdarzenia trasowanego i obsługiwane w dowolnym elemencie, w tym elementy, które nie umieszczaj danego zdarzenia w tabeli składowych klasy. Jest to realizowane przez kwalifikujących się atrybut nazwy zdarzenia będącego nazwą klasy. Na przykład element nadrzędny `StackPanel` w listę bieżących `StackPanel`  /  `Button` przykładu można zarejestrować program obsługi dla przycisku element podrzędny <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń przez określenie atrybutu `Button.Click` na `StackPanel` element Object z Twoją nazwą programu obsługi, jako wartość atrybutu. Aby uzyskać więcej informacji na temat sposobu trasowane pracy zdarzenia, zobacz [Przegląd zdarzeń kierowane](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>O nazwie elementów XAML  
 Domyślnie wystąpienie obiektu, do utworzenia wykresu obiektu przez przetwarzanie elementu obiektu XAML nie posiada unikatowego identyfikatora lub odwołanie do obiektu. Z kolei jeśli wywołujesz konstruktora w kodzie, prawie zawsze używać konstruktora wyniku Aby ustawić zmienną do skonstruowanego wystąpienia tak, aby później w kodzie można odwoływać się wystąpienia. Aby można było zapewnić standardowe dostęp do obiektów, które zostały utworzone za pośrednictwem definicji znaczników, XAML definiuje [atrybut x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Można ustawić wartość `x:Name` atrybutu w dowolnym elemencie obiektu. W swojej związanym z kodem identyfikator, który wybierzesz odpowiada zmienną instance, która odwołuje się do skonstruowanego wystąpienia. We wszystkich aspektach o nazwie elementy działają tak, jakby były one wystąpienia obiektu (nazwa odwołuje się do tego wystąpienia) i usługi związane z kodem można odwoływać się do nazwanych elementów do obsługi interakcji środowiska wykonawczego w aplikacji. To połączenie między wystąpieniami i zmienne odbywa się przez kompilator znaczników WPF XAML i więcej specjalnie obejmują funkcje i wzorców takich jak <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> , nie będzie omówiono szczegółowo w tym temacie.  
  
 Dziedziczenie elementów XAML na poziomie struktury WPF <xref:System.Windows.FrameworkElement.Name%2A> właściwość, która jest odpowiednikiem XAML zdefiniowane `x:Name` atrybutu. Niektóre inne klasy udostępniają odpowiedniki właściwości poziomu `x:Name`, która została również ogólnie zdefiniowana jako `Name` właściwości. Ogólnie rzecz biorąc, jeśli nie możesz znaleźć `Name` właściwości w tabeli składowych dla wybranego elementu/typu, użyj `x:Name` zamiast tego. `x:Name` Wartości zapewni identyfikatora elementu XAML, który może być używany w czasie wykonywania określonych podsystemów lub metody narzędziowe takich jak <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 Poniższy przykład ustawia <xref:System.Windows.FrameworkElement.Name%2A> na <xref:System.Windows.Controls.StackPanel> elementu. Następnie program obsługi na <xref:System.Windows.Controls.Button> w tym <xref:System.Windows.Controls.StackPanel> odwołania <xref:System.Windows.Controls.StackPanel> za pośrednictwem jego odwołania do wystąpienia `buttonContainer` jako ustawione przez <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Podobnie jak zmienna nazwy XAML dla wystąpienia podlega koncepcji zakresu, tak, aby nazwy można wymusić być unikatowe w obrębie niektórych zakres, który jest przewidywalne. Podstawowy kod znaczników, który definiuje stronę wskazuje, że jeden unikatowy namescope XAML z granicą namescope XAML jest głównym elementem tej strony. Jednak inne źródła znaczników mogą wchodzić w interakcje ze stroną w czasie wykonywania, takie jak style lub szablony w ramach stylów, i źródeł, takich znaczników często mają własne zakresy nazw XAML, która niekoniecznie nie są połączone z namescope XAML strony. Aby uzyskać więcej informacji na temat `x:Name` i zakresy nazw XAML, zobacz <xref:System.Windows.FrameworkElement.Name%2A>, [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md), lub [zakresy WPF XAML nazw](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Dołączone właściwości i zdarzenia dołączone  
 XAML określa funkcję języka, która umożliwia niektórych właściwości lub zdarzenia, należy określić w dowolnym elemencie, niezależnie od tego, czy istnieje właściwość lub zdarzenie w definicji typu dla elementu, który jest ustawiony na. Właściwości wersji ta funkcja jest wywoływana dołączoną właściwość, nosi nazwę wersji zdarzenia dołączone zdarzenie. Model można traktować dołączonych właściwości i zdarzeń dołączonych jako globalne elementy członkowskie, które mogą być ustawione na dowolne wystąpienie elementu/obiekt XAML. Jednak element/class lub większych infrastruktury musi obsługiwać zapasowy magazyn właściwości dla wartości dołączone.  
  
 Właściwości dołączone w XAML są zwykle używane przy użyciu składni atrybutów. W składni atrybutów, należy określić dołączoną właściwość w postaci *ownerType*. *propertyName*.  
  
 Pozornie przypomina użycie elementu właściwości, ale w takim przypadku *ownerType* określasz, że zawsze jest innego typu niż object element gdzie ustawiany jest dołączona właściwość. *ownerType* to typ, który udostępnia metody dostępu, które są wymagane przez procesor XAML, aby można było pobrać lub ustawić wartość właściwości dołączone.  
  
 Najbardziej typowym scenariuszem w przypadku dołączonych właściwości jest umożliwienie elementów podrzędnych do zgłaszania wartości właściwości do swojego elementu nadrzędnego.  
  
 W poniższym przykładzie pokazano <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączona właściwość. <xref:System.Windows.Controls.DockPanel> Klasa definiuje metody dostępu dla <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> i dlatego jest właścicielem dołączona właściwość. <xref:System.Windows.Controls.DockPanel> Klasa zawiera także logiki, który iteruje po jego elementów podrzędnych i specjalnie sprawdza każdy element, dla ustaw wartość <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Jeśli wartość zostanie znaleziona, ta wartość jest używany podczas układ pozycjonować elementy podrzędne. Korzystanie z <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączonej właściwości i tej możliwości pozycjonowania jest w rzeczywistości motywującego scenariusz <xref:System.Windows.Controls.DockPanel> klasy.  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], większość lub wszystkie załączonych właściwości również są implementowane jako właściwości zależności. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Zdarzenia dołączone Użyj podobny *ownerType*. *eventName* formy Składnia atrybutu. Podobnie jak zdarzenia niedołączonych wartością atrybutu dołączone zdarzenia w XAML Określa nazwę metody obsługi, które jest wywoływane, gdy zdarzenie jest obsługiwane w elemencie. Dołączone zdarzenie użycia w programie WPF XAML są mniej typowe. Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń dołączonych](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Typy podstawowe i XAML  
 Podstawowy WPF XAML i jego przestrzeń nazw XAML jest kolekcją typów, które odpowiadają [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów oprócz elementów kodu znaczników dla XAML. Jednak nie wszystkie klasy mogą być mapowane do elementów. Abstrakcyjne klasy, takie jak <xref:System.Windows.Controls.Primitives.ButtonBase>, a niektóre nieabstrakcyjnej klasy podstawowej są używane do obsługi dziedziczenia w [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] modelu obiektów. Klas bazowych, w tym abstrakcyjne, są nadal ważne do programowania XAML, ponieważ dziedziczy poszczególnych elementów XAML konkretne elementy członkowskie, aby niektóre klasy podstawowej w jego hierarchii. Często te elementy Członkowskie zawierają właściwości, które można ustawić jako atrybuty w elemencie lub zdarzenia, które są obsługiwane. <xref:System.Windows.FrameworkElement> podstawowy konkretnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na poziomie framework WPF. Podczas projektowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], będzie używać różnych kształtów, panel, dekoratora lub dziedziczyć klasy kontrolek, którym wszystkie <xref:System.Windows.FrameworkElement>. Pokrewne klasy bazowej, <xref:System.Windows.FrameworkContentElement>, obsługuje elementy korzystający z dokumentów, które działają dobrze sprawdza się w prezentacji układ przepływu, za pomocą [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] celowo odzwierciedlające [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] w <xref:System.Windows.FrameworkElement>. Kombinacja atrybuty na poziomie elementu, a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] object model zawiera zestaw typowych właściwości, które są można ustawić w najbardziej konkretnych elementów XAML, niezależnie od tego, czy określony element XAML i jej typ podstawowy.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>Zabezpieczenia XAML  
 XAML jest językiem znaczników, który bezpośrednio reprezentuje tworzenia wystąpienia obiektu, jak i wykonywania. Elementy tworzone w XAML więc ten sam możliwość interakcji z zasobami systemu (na przykład sieci dostępu do pliku systemu We/Wy) jako równoważne, generowany jest kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] struktury zabezpieczeń [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]. Oznacza to, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obniżyła uprawnień Wykonywanie zawartości w strefie internet. "Luźno XAML" (stron XAML Nieskompilowane interpretowany w czasie ładowania przez Podgląd XAML) i [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] są zazwyczaj uruchamiane w ramach tej strefy internet i ten sam zestaw uprawnień.  Jednak XAML załadowane w pełni zaufanych aplikacji ma taki sam dostęp do zasobów systemowych, jak hostingu aplikacji. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>Ładowanie XAML z kodu  
 XAML może służyć do definiowania wszystkich interfejsu użytkownika, ale czasami jest również zdefiniowanie po prostu element interfejsu użytkownika w XAML. Ta funkcja może służyć do umożliwiają dostosowanie częściowe, lokalny magazyn danych obiektu biznesowego lub różne możliwe scenariusze przy użyciu XAML. Kluczem do tych scenariuszy jest <xref:System.Windows.Markup.XamlReader> klasy i jego <xref:System.Windows.Markup.XamlReader.Load%2A> metody. Dane wejściowe są w pliku XAML, a dane wyjściowe jest obiektem, który reprezentuje wszystkie drzewa środowiska wykonawczego obiektów, który został utworzony na podstawie tego znacznika. Możesz wstawić obiektu właściwość innego obiektu, który już istnieje w aplikacji. Tak długo, jak właściwość jest właściwością odpowiednią w modelu zawartości, która ma możliwości wyświetlania ostatecznej i który powiadomi o tym aparat wykonywania że dodano nową zawartość do aplikacji, możesz bardzo łatwo modyfikować zawartości uruchomionej aplikacji przez ładowanie w XAML. Należy pamiętać, że ta funkcja jest ogólnie dostępna tylko w aplikacje pełnego zaufania, z powodu skutków bezpieczeństwa ładowanie plików do aplikacji podczas ich działania.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Jaka jest przyszłość  
 Ten temat zawiera wstęp do XAML składnia pojęcia i terminologia, ponieważ mają zastosowanie do platformy WPF. Aby uzyskać więcej informacji na temat terminy używane w tym miejscu, zobacz [składnia XAML w szczegółów](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Jeśli jeszcze nie zostało to zrobione, spróbuj ćwiczeń opisanych w temacie samouczka [Instruktaż: Mój pierwszy aplikacji klasycznej WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Podczas tworzenia aplikacji przetwarzających znaczników, opisanego przez samouczek ćwiczenie pomoże wzmocnienia wiele pojęcia opisane w tym temacie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] korzysta z modelu konkretnej aplikacji, który jest oparty na <xref:System.Windows.Application> klasy. Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
 [Kompilowanie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) znajdziesz więcej szczegółów o tym, jak tworzyć aplikacje włącznie XAML w wierszu polecenia i [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) daje więcej informacji na temat wszechstronności odpowiedniej właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i pojęcia związane z właściwości zależności.  
  
## <a name="see-also"></a>Zobacz także  
 [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [Klasy XAML i niestandardowe dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Przestrzeń nazw XAML (x:) — funkcje językowe](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozszerzenia WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
