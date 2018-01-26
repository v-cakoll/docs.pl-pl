---
title: "Przegląd XAML (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "57"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce83713d2483320569bde0d5c9a677f0b357ebf2
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="xaml-overview-wpf"></a>Przegląd XAML (WPF)
W tym temacie opisano funkcje języka XAML oraz przedstawiono sposób użycia XAML do zapisu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym temacie szczegółowo opisano XAML wykonane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XAML sam to pojęcie języka większych niż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>Co to jest XAML?  
 XAML to deklaratywne język. Jak stosować do [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] modelu programowania, XAML upraszcza tworzenie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji. Możesz utworzyć widoczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów w deklaratywne znaczników XAML, a następnie oddzielne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definicji z logiki czasu wykonywania przy użyciu plików z kodem, przyłączone do znaczników za pośrednictwem definicji klasy częściowej. XAML reprezentuje bezpośrednie tworzenie wystąpień obiektów w określonych typów zdefiniowanych w zestawy kopii. Jest to w przeciwieństwie do większości innych znaczników języków, które są zazwyczaj interpretacji języka bez bezpośredniego rozwiązany systemowi typ zapasowy. XAML umożliwia przepływu pracy, gdzie osobnych stron może pracować nad [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i logikę aplikacji, za pomocą różnych narzędzi.  
  
 Gdy reprezentowane jako tekst, plików XAML są pliki XML, które mają zwykle `.xaml` rozszerzenia. Pliki mogą być kodowane przez żadnego kodu XML, kodowania, ale kodowania UTF-8 jest typowy.  
  
 W poniższym przykładzie pokazano, jak można utworzyć przycisk jako część [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. W tym przykładzie tylko ma umożliwić wersję jak XAML reprezentuje typowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] programowania metafory (nie jest on kompletnego przykładu).  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Składnia języka XAML w Brief  
 W poniższych sekcjach opisano formy podstawowa składnia języka XAML i podać przykład krótkich znaczników. Poniższe sekcje mają nie udostępniają pełnych informacji na temat każdego formularza składni, takich jak jak są one reprezentowane w bazowego typu systemu. Aby uzyskać więcej informacji o szczegółowe informacje na temat składni języka XAML dla każdego z formy składni opisanymi w tym temacie, zobacz [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Wiele materiałów w kolejnych sekcjach kilka będzie podstawowe, jeśli masz poprzedniej znajomość języka XML. Jest to konsekwencją zasady projektowania podstawowe języka XAML.  Pojęcia związane z własną definiuje języka XAML, ale tych pojęć działa w formularzu języka i znaczników XML.  
  
### <a name="xaml-object-elements"></a>Elementy obiektu XAML  
 Element obiektu zwykle deklaruje wystąpienia typu. Ten typ jest zdefiniowany w zestawy, które zapewniają typy zapasowy technologii, która używa jako języka XAML.  
  
 Składnia elementu obiektu zawsze rozpoczyna się od otwierającego nawiasu ostrego (\<). To następuje nazwa typu której chcesz utworzyć wystąpienia. (Nazwa prawdopodobnie może zawierać prefiks, pojęcie później można wyjaśnić bardziej.) Po to można opcjonalnie zadeklarować atrybuty w elemencie obiektu. Aby ukończyć tagu elementu object, kończyć się zamykającego nawiasu ostrego (>). Zamiast tego można użyć samozamykającego formularz, który nie ma żadnej zawartości, skonfiguruj tag kreską ukośną i zamykającego nawiasu ostrego w przedziale czasu (/ >). Na przykład przyjrzeć się fragment znacznika wcześniej wyświetlane ponownie:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Określa obiekt dwóch elementów: `<StackPanel>` (z zawartości, a później tag zamykający) i `<Button .../>` (samozamykającego formularz, kilka atrybutów). Elementy obiektu `StackPanel` i `Button` każdej mapy na nazwę klasy, która jest definiowana za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i jest częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów. Po określeniu tagu elementu obiekt tworzenia instrukcji dla XAML przetwarzanie w celu utworzenia nowego wystąpienia. Każde wystąpienie została utworzona przez wywołanie domyślnego konstruktora podstawowego typu podczas analizowania i ładowanie pliku XAML.  
  
### <a name="attribute-syntax-properties"></a>Składnia atrybutu (właściwości)  
 Właściwości obiektu można często wyrażane jako atrybuty elementu obiekt. Składnia atrybutu nazwy właściwości, która jest ustawiona w składni atrybutu, a następnie operator przypisania (=). Wartość atrybutu zawsze jest określony jako ciąg, który jest zawarty w cudzysłowie.  
  
 Składnia atrybutu jest najbardziej prostsze składni ustawienie właściwości i najbardziej intuicyjnego składnia dla deweloperów, którzy użyli języków znaczników w przeszłości. Na przykład następujący kod tworzy przycisk czerwony tekst i niebieskie tło oprócz wyświetlany tekst określony jako `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Składni elementu właściwości  
 W przypadku niektórych właściwości elementu obiektu Składnia atrybutu nie jest możliwe, ponieważ informacje niezbędne do zapewnienia wartość właściwości lub obiekt nie odpowiednio można wyrazić w cudzysłów i ograniczenia ciąg Składnia atrybutu. W tych przypadkach można używać różnych składni, znany jako składni elementu właściwości.  
  
 Składnia dla tagu początkowym elementu właściwości `<` *typeName*`.`*propertyName*`>`. Ogólnie rzecz biorąc zawartości tagu jest elementem obiektu typu, który ma właściwość jako jego wartość. Po określeniu zawartości, należy zamknąć element właściwości z tagu końcowego. Składnia tag końcowy jest `</` *typeName*`.`*propertyName*`>`.  
  
 Składnia atrybutu jest możliwe, przy użyciu składni atrybutu jest zazwyczaj bardziej wygodne i umożliwia mniejszych znaczników, ale najczęściej jest wystarczy stylu nie ograniczeń technicznych. W poniższym przykładzie przedstawiono te same właściwości ustawiany jak w poprzednim przykładzie Składnia atrybutu, lecz tym razem przy użyciu składni elementu właściwości dla wszystkich właściwości `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Składnia kolekcji  
 Języka XAML zawiera niektóre optymalizacji, które powodują powstanie bardziej czytelny dla człowieka znaczników. Jeden taki optymalizacji jest to, że jeśli określoną właściwość przyjmuje typ kolekcji, a następnie elementy, które można zadeklarować w znaczniku jako elementy podrzędne w ramach tej właściwości wartość staną się częścią kolekcji. W takim przypadku kolekcję elementów podrzędnych obiektu jest to wartość ustawioną dla właściwości kolekcji.  
  
 W poniższym przykładzie przedstawiono składnię kolekcji ustawiania wartości <xref:System.Windows.Media.GradientBrush.GradientStops%2A> właściwości:  
  
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
 XAML określa funkcji języka, zgodnie z którymi klasy można określić dokładnie jedną z właściwości jako właściwość content XAML. Elementy podrzędne tego elementu obiektu są używane do ustawiania wartości właściwości zawartości. Innymi słowy dla właściwości content jednoznacznie, można pominąć elementu właściwości podczas ustawiania właściwości w kodzie XAML i utworzenia bardziej widoczne metaphor nadrzędny/podrzędny w znaczniku.  
  
 Na przykład <xref:System.Windows.Controls.Border> Określa właściwość content <xref:System.Windows.Controls.Decorator.Child%2A>. Następujące dwa <xref:System.Windows.Controls.Border> elementy są traktowane identycznie. Pierwsza z nich korzysta składni właściwości zawartości i pomija `Border.Child` elementu właściwości. Drugi pokazuje `Border.Child` jawnie.  
  
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
  
 Zgodnie z zasadą języka XAML wartość właściwości zawartości XAML należy całkowicie przed lub całkowicie po innych elementów właściwości w elemencie tego obiektu. Na przykład następujący kod nie kompiluje się:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Aby uzyskać więcej informacji dotyczących tego ograniczenia właściwości zawartości XAML, zobacz sekcję "Właściwości zawartości XAML" [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Zawartość tekstu  
 Mała liczba elementów XAML bezpośrednio może przetwarzać tekstu jako ich zawartość. Aby włączyć tę opcję, należy spełnić jedną z następujących przypadków:  
  
-   Klasa musi deklarować właściwość content i tą właściwością zawartości musi być typu można przypisać do ciągu (może być typu <xref:System.Object>). Na przykład żadnego <xref:System.Windows.Controls.ContentControl> używa <xref:System.Windows.Controls.ContentControl.Content%2A> jako swojej właściwości content jest typem <xref:System.Object>, i to obsługuje następujące użycia na praktyczny <xref:System.Windows.Controls.ContentControl> takich jak <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
-   Typ musi zadeklarować konwertera typów, w którym jest używana w przypadku zawartości tekstowej jako tekst inicjowania dla tego konwertera typu. Na przykład `<Brush>Blue</Brush>`. Ten przypadek jest mniej typowych, w praktyce.  
  
-   Typ musi być znane języka XAML pierwotnych.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>Właściwości zawartości i połączeniu składni kolekcji  
 Rozważmy następujący przykład:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 W tym miejscu każdego <xref:System.Windows.Controls.Button> jest elementem podrzędnym <xref:System.Windows.Controls.StackPanel>. Jest to prostsze i intuicyjne znaczników, pomijające dwa tagi dla dwóch różnych przyczyn.  
  
-   **Element właściwości StackPanel.Children pominięcia:** <xref:System.Windows.Controls.StackPanel> pochodną <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>definiuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jego XAML właściwości content.  
  
-   **Pominięty element object UIElementCollection:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> właściwość przyjmuje typ <xref:System.Windows.Controls.UIElementCollection>, który implementuje <xref:System.Collections.IList>. Można pominąć tagu elementu kolekcji, na podstawie reguł XAML do przetwarzania kolekcji, takie jak <xref:System.Collections.IList>. (W tym przypadku <xref:System.Windows.Controls.UIElementCollection> faktycznie nie może zostać utworzona, ponieważ nie ujawnia konstruktora domyślnego i dlatego <xref:System.Windows.Controls.UIElementCollection> object element przedstawiono komentarze out).  
  
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
  
### <a name="attribute-syntax-events"></a>Składnia atrybutu (zdarzeń)  
 Składnia atrybutu mogą służyć do elementów członkowskich, które są zdarzenia, a nie właściwości. W takim przypadku nazwa atrybutu jest nazwą zdarzenia. W implementacji WPF zdarzeń dla XAML wartość atrybutu jest nazwą program obsługi, który implementuje delegowanie dla zdarzenia. Na przykład następujący kod znaczników przypisuje obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia <xref:System.Windows.Controls.Button> utworzone w znaczniku:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Brak zdarzeń i XAML w WPF ponad właśnie w tym przykładzie Składnia atrybutu. Na przykład, być może zastanawiasz się, co `ClickHandler` odwołujesz reprezentuje i jak jest zdefiniowany. To opisano w kolejnych [zdarzenia i kodem XAML](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind) tego tematu.  
  
<a name="case_and_whitespace_in_xaml"></a>   
## <a name="case-and-whitespace-in-xaml"></a>Wielkość liter i spacji w XAML  
 XAML ogólnie rzecz biorąc jest rozróżniana wielkość liter. Do celów rozpoznawania typów zapasowy WPF XAML jest rozróżniana wielkość liter, przez te same zasady, że środowisko CLR jest rozróżniana wielkość liter. Elementy obiektu, elementy właściwości i nazwy atrybutów muszą być wszystkie określone za pomocą liter wielkość liter w porównaniu nazwa podstawowy typ w zestawie lub elementu członkowskiego typu. Słowa kluczowe języka XAML i podstawowych jest również wielkość liter. Wartości nie są zawsze z uwzględnieniem wielkości liter. Uwzględnianie wielkości liter w wartości będzie zależeć od zachowania konwertera typu związanego z właściwością, która przyjmuje wartość lub typ wartości właściwości. Na przykład, właściwości, które przyjmują <xref:System.Boolean> typu może zająć jedną `true` lub `True` jako równoważne wartości, ale tylko wtedy, ponieważ Konwersja ciągu do typu natywnego analizator WPF XAML <xref:System.Boolean> już pozwala je jako odpowiedniki.  
  
 WPF XAML procesorów i serializatorów zignoruje lub porzucić wszystkie nonsignificant spacji i będzie normalizacji żadnych znaczącym odstępem. Jest to zgodne z zaleceniami zachowanie domyślne odstępu specyfikacji języka XAML. To zachowanie jest zwykle tylko z konsekwencji w przypadku określenia ciągów wewnątrz właściwości zawartości XAML. Najprostsza warunków XAML konwertuje miejsca, wysuwu wiersza i kartę znaków spacji, a następnie zachowuje jedną miejsce, jeśli znaleziono na końcu ciągu ciągłe. Pełne wyjaśnienie Obsługa spacji w XAML nie zostało opisane w tym temacie. Aby uzyskać więcej informacji, zobacz [przetwarzanie spacji w XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 Rozszerzenia znaczników są pojęcia języka XAML. W przypadku zastosowania do podania wartości atrybutu składni, nawiasy klamrowe (`{` i `}`) wskazuje użycie rozszerzenia znaczników. To użycie kieruje XAML przetwarzania, aby wyjść z ogólne traktowanie wartości atrybutów jako ciąg literału lub wartość możliwe do przekonwertowania ciągu.  
  
 Najczęstsze rozszerzenia znacznika używany w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania aplikacji są [powiązania](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), używana dla wyrażenia wiązania danych, a odwołania do zasobów [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) i [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Za pomocą rozszerzeń znaczników Składnia atrybutu służy do Podaj wartości dla właściwości, nawet jeśli tej właściwości nie obsługuje ogólnie Składnia atrybutu. Rozszerzenia znaczników często używane typy pośredniego wyrażenia, aby włączyć funkcje, takie jak odkładanie wartości lub odwołania do innych obiektów, które istnieją tylko w czasie wykonywania.  
  
 Na przykład następujący kod ustawia wartość <xref:System.Windows.FrameworkElement.Style%2A> właściwości przy użyciu składni atrybutu. <xref:System.Windows.FrameworkElement.Style%2A> Właściwość przyjmuje wystąpienia <xref:System.Windows.Style> klasy, która domyślnie nie mogła zostać utworzona przez ciąg Składnia atrybutu. Ale w takim przypadku atrybut odwołuje się do rozszerzenie znaczników w szczególności [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Podczas przetwarzania tego rozszerzenia znacznika zwraca odwołanie do stylu, który został wcześniej skonkretyzowany jako zasób kluczem w słowniku zasobów.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Odwołanie do wyświetlania list wszystkich rozszerzeń znaczników dla XAML zaimplementowana w szczególności na platformie WPF, zobacz [WPF XAML rozszerzenia](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md). Aby uzyskać listę rozszerzeń znaczników, które są definiowane przez System.Xaml i są bardziej dostępna w przypadku implementacji programu .NET Framework XAML, zobacz [Namespace XAML (x:) Funkcje języka](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Aby uzyskać więcej informacji o pojęciach rozszerzenia znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Konwertery typu  
 W [składni języka XAML w Brief](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief) sekcji stwierdzono, że wartość atrybutu musi być można ustawić przez ciąg. Podstawowe, natywnej obsługi jak ciągi są konwertowane na inne typy obiektów lub pierwotne wartości jest oparta na <xref:System.String> sam typ, oprócz macierzystą przetwarzania dla niektórych typów takich jak <xref:System.DateTime> lub <xref:System.Uri>. Jednak wiele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów albo elementów członkowskich tych typów rozszerzyć atrybut ciągu podstawowe przetwarzanie zachowanie w taki sposób, że wystąpień bardziej złożone typy obiektów można określić jako ciągi i atrybutów.  
  
 <xref:System.Windows.Thickness> Struktura jest przykładem takiego typu, który został włączony dla XAML użycia konwersji typu. <xref:System.Windows.Thickness>Wskazuje pomiarów w prostokącie zagnieżdżonych i jest używany jako wartość właściwości, takie jak <xref:System.Windows.FrameworkElement.Margin%2A>. Umieszczając konwertera typów w <xref:System.Windows.Thickness>, wszystkie właściwości, które używają <xref:System.Windows.Thickness> są łatwiejsze do określenia w języku XAML, ponieważ może być określona jako atrybuty. W poniższym przykładzie użyto składnia konwersji oraz atrybut typu, aby podać wartość dla <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 W poprzednim przykładzie Składnia atrybutu jest odpowiednikiem następujące pełniejsze przykład składni, gdzie <xref:System.Windows.FrameworkElement.Margin%2A> zamiast tego jest ustawiany za pomocą składni elementu właściwości zawierająca <xref:System.Windows.Thickness> object element. Właściwości klucza cztery <xref:System.Windows.Thickness> na nowe wystąpienie są ustawione jako atrybuty:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Istnieje ograniczona liczba obiektów, których konwersji typu jest tylko publiczne sposób ustawiania właściwości dla tego typu nie angażując podklasy, ponieważ sam typ nie ma domyślnego konstruktora. Na przykład <xref:System.Windows.Input.Cursor>.  
  
 Aby uzyskać więcej informacji na temat sposobu konwersji typu i jego użycia dla atrybutu składnia jest obsługiwana, zobacz [TypeConverters i języka XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>Elementy główne XAML i przestrzeni nazw XAML  
 Plik XAML musi mieć tylko jeden element główny, aby mogła być zarówno poprawnie sformułowanym [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] plików i prawidłowego pliku XAML. W typowych scenariuszach WPF, użyj elementu głównego, który ma znaczenie widocznych w modelu aplikacji WPF (na przykład <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> ze stroną, <xref:System.Windows.ResourceDictionary> zewnętrznego słownika lub <xref:System.Windows.Application> definicji aplikacji). W poniższym przykładzie przedstawiono typowe pliku XAML dla elementu głównego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony z elementem głównym <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Element główny zawiera także atrybuty `xmlns` i `xmlns:x`. Te atrybuty wskazać procesora XAML, który przestrzeń nazw XAML zawiera definicje typów dla typów odwołujące znaczników jako elementy kopii. `xmlns` Atrybut wskazuje, w szczególności domyślnej przestrzeni nazw XAML. W domyślnej przestrzeni nazw XAML można określić obiektu elementów w znaczniku bez prefiksu. Dla większości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] scenariuszy aplikacji i prawie wszystkie przykłady podane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sekcje [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], domyślnej przestrzeni nazw XAML jest mapowany na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. `xmlns:x` Atrybut wskazuje dodatkowe nazw XAML, który mapuje przestrzeń nazw języka XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 To użycie `xmlns` do zdefiniowania zakresu użycia i mapowanie namescope jest spójna ze Specyfikacja XML 1.0. XAML namescopes różnią się od XML namescopes tylko w tym XAML namescope oznacza także coś o jak elementy namescope bazują na typy po przejściu do typu rozdzielczość i analiza kodu XAML.  
  
 Należy pamiętać, że `xmlns` atrybutów tylko są niezbędne dla elementu głównego pliku XAML. `xmlns`definicje będą stosowane do wszystkich elementów podrzędnych elementu głównego (to zachowanie jest zgodne z Specyfikacja XML 1.0 dla ponownie `xmlns`.) `xmlns` atrybuty również są dozwolone w przypadku innych elementów poniżej katalogu głównego i powinna zostać zastosowana do żadnych elementów podrzędnych elementu definiującego. Jednak częste definicja lub ponowna definicja przestrzeni nazw XAML może powodować styl znaczników XAML, który jest trudny do odczytania.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementacja jego procesor XAML obejmuje infrastrukturę, która ma pogłębianie wiedzy na temat zestawów podstawowych WPF. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zestawów podstawowych wiadomo, że zawiera typy, które obsługują [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapowania do domyślnej przestrzeni nazw XAML. Ta opcja jest włączona za pomocą konfiguracji, który jest częścią kompilacji projektu pliku WPF kompilacji i projektu systemów. W związku z tym deklarowanie domyślnej przestrzeni nazw XAML domyślnie `xmlns` jest niezbędne, aby można było odwoływać się elementy XAML, które pochodzą od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.  
  
### <a name="the-x-prefix"></a>Prefiks x:  
 W poprzednim przykładzie element główny, prefiks `x:` został użyty do mapowania przestrzeni nazw XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], czyli dedykowanych przestrzeni nazw XAML, który obsługuje języka XAML konstrukcje. To `x:` prefiks jest używany do mapowania tej przestrzeni nazw XAML szablonów dla projektów, przykłady i dokumentacja w całym to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Przestrzeń nazw XAML dla języka XAML zawiera kilka narzędzi programistycznych, które będą bardzo często używane w sieci XAML. Poniżej znajduje się lista najczęściej `x:` prefiksu narzędzi programistycznych, które będą używane:  
  
-   [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md): ustawia Unikatowy klucz dla każdego zasobu w <xref:System.Windows.ResourceDictionary> (lub podobny koncepcji słownika w innych platform). `x:Key`prawdopodobnie będzie konto do 90% `x:` użycia zobaczysz w znaczniku typowych aplikacji WPF.  
  
-   [x: Class](../../../../docs/framework/xaml-services/x-class-directive.md): Określa [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw i nazwę klasy dla klasy, która udostępnia CodeBehind dla strony XAML. Musi mieć klasę do obsługi kodem na model programowania WPF i w związku z tym prawie zawsze widzieć `x:` mapowane, nawet jeśli nie ma żadnych zasobów.  
  
-   [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md): Określa nazwę obiektu środowiska wykonawczego dla wystąpienia, który istnieje w czasie wykonywania kod po przetworzeniu element object. Ogólnie rzecz biorąc, często użyje zdefiniowane WPF równoważne właściwość [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Takie właściwości mapowany przeznaczony do tworzenia kopii właściwość CLR, w związku z tym wygodniejsze programowania aplikacji, gdzie jest często używana kodu w czasie wykonywania do znajdowania nazwanych elementów z zainicjowane XAML. Najbardziej typowe takich właściwości jest <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Może nadal używać [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) podczas równoważne poziomie struktury WPF <xref:System.Windows.FrameworkElement.Name%2A> właściwość nie jest obsługiwana w określonego typu. Dzieje się tak w niektórych scenariuszach animacji.  
  
-   [x: Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): umożliwia odwołanie, które zwraca wartość statyczną, która nie jest w przeciwnym razie właściwości zgodnego XAML.  
  
-   [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): tworzy <xref:System.Type> odwołanie opartego na nazwie typu. Służy do określania atrybutów, które przyjmują <xref:System.Type>, takich jak <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, chociaż często właściwość ma natywnej ciąg-do-<xref:System.Type> konwersji w taki sposób, który [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) jest użycie rozszerzenia znaczników opcjonalne.  
  
 Istnieją dodatkowe programowania konstrukcje w `x:` prefiksu/XAML przestrzeni nazw, które nie są jako wspólne. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Prefiksy niestandardowe i niestandardowe typy w języku XAML  
 Zestawy niestandardowe lub zestawów poza rdzeniem WPF PresentationCore, PresentationFramework i WindowsBase, można określić zestaw jako część niestandardowego `xmlns` mapowania. Następnie można odwoływać się typy z tego zestawu w Twojej XAML tak długo, jak tego typu jest poprawnie zaimplementowana do obsługi użycia XAML, który próbujesz.  
  
 Poniżej znajduje się bardzo prosty przykład niestandardowych pracy prefiksów w kodzie XAML. Prefiks `custom` jest zdefiniowany w tagu elementu głównego i mapowane do określonego zestawu, który spakowane i jest dostępny z aplikacją. Ten zestaw zawiera typ `NumericUpDown`, którego jest stosowana do obsługi ogólne użycie języka XAML, a także używanie dziedziczenia klasy, która pozwala na jego wstawiania w tym punkcie określonego modelu zawartości WPF XAML. Wystąpienie tego elementu `NumericUpDown` kontroli jest zadeklarowany jako elementu obiektu, za pomocą prefiks, dzięki czemu analizator XAML wie, które XAML przestrzeń nazw zawiera typ i w związku z tym w przypadku zestawu zapasowy zawiera definicji typu.  
  
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
  
 Aby uzyskać więcej informacji o niestandardowych typów w języku XAML, zobacz [XAML oraz klas niestandardowych dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
 Aby uzyskać więcej informacji dotyczących sposobu związane z przestrzeni nazw XML i przestrzenie nazw kodu zapasowy w zestawach, zobacz [przestrzeń nazw XAML i Namespace mapowanie WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Zdarzenia i kodem XAML  
 Większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje składają się znaczników XAML i kodem. W ramach projektu, XAML są zapisywane jako `.xaml` pliku, a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] języka, takich jak [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] lub [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] jest używana podczas zapisu pliku CodeBehind. Plik XAML po kompilacji jako część modele programowania i aplikacji WPF znaczników lokalizacji kodu XAML powiązanego pliku dla pliku XAML jest identyfikowany przez określenie przestrzeni nazw i klasy `x:Class` atrybutu elementu głównego XAML.  
  
 W przykładach wykonanej do tej pory kilka przycisków jak już wspomniano, ale żaden z tych przycisków ma wszelkie zachowanie logicznej jeszcze skojarzonych z nimi. Dodawanie zachowanie dla obiekt elementu podstawowego mechanizmu poziomie aplikacji jest użyć istniejącego zdarzenia klasy elementów i zapisywania określony program obsługi dla tego zdarzenia, które jest wywoływane, gdy zdarzenie jest zgłaszane w czasie wykonywania. Nazwa zdarzenia i nazwę programu obsługi do użycia są określone w znaczników, kod, który zawiera implementację programu obsługi jest zdefiniowane w CodeBehind.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Powiadomienie, że plik CodeBehind używa przestrzeni nazw CLR `ExampleNamespace` i deklaruje `ExamplePage` jako częściowej klasy w tej przestrzeni nazw. To równoleżnikami `x:Class` wartość atrybutu `ExampleNamespace`.`ExamplePage` który podano w folderze głównym znaczników. Kompilator znaczników WPF utworzy klasę częściową dla dowolnego skompilowanego pliku XAML przez wyprowadzanie klasy z typie elementu głównego. Po podaniu kodem, definiujący tej samej klasy częściowe wynikowy kod są łączone w tej samej przestrzeni nazw i klasy skompilowanej aplikacji.  
  
 Aby uzyskać więcej informacji na temat wymagań dotyczących programowania CodeBehind na platformie WPF, zobacz sekcję "związane z kodem, program obsługi zdarzeń i wymagania klasy częściowej" [CodeBehind i języka XAML w WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
 Jeśli nie chcesz utworzyć plik oddzielne kodem, możesz również wbudowanego kodu w pliku XAML. Kodu wbudowanego jest jednak mniej elastyczne metody, która ma istotne ograniczenia. Aby uzyskać więcej informacji, zobacz [CodeBehind i języka XAML w WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Kierowane zdarzenia  
 Funkcja konkretnego zdarzenia, który stanowi podstawę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest kierowanego zdarzenia. Kierowane zdarzenia Włącz element do obsługi zdarzeń, które zostało zgłoszone przez inny element, tak długo, jak elementy są połączone za pośrednictwem relacji drzewa. Podczas określania obsługi z atrybutem XAML zdarzeń, kierowanego zdarzenia można nasłuch dla i obsługiwane w dowolnym elemencie, w tym elementów, których nie wymieniono w tabeli elementów członkowskich klasy danego zdarzenia. Jest to osiągane przez kwalifikowanie atrybutu nazwy zdarzenia z jego nazwą klasy. Na przykład element nadrzędny `StackPanel` w bieżących `StackPanel`  /  `Button` przykładzie można zarejestrować obsługi dla przycisku element podrzędny <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia przez określenie atrybutu `Button.Click` na `StackPanel` element Object nazwą programu obsługi, jako wartość atrybutu. Aby uzyskać więcej informacji na temat sposobu kierowanego zdarzenia, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>O nazwie elementy XAML  
 Domyślnie wystąpienia obiektu utworzonego na wykresie obiektu przez przetwarzanie XAML object element nie posiada unikatowego identyfikatora lub odwołanie do obiektu. Z kolei w kodzie można wywołać konstruktora, prawie zawsze używać konstruktora wyniku Aby ustawić zmienną skonstruowane wystąpienie, aby wystąpienie można odwoływać się w dalszej części kodu. W celu zapewnienia standardowych dostępu do obiektów, które zostały utworzone za pośrednictwem definicji znaczników, definiuje XAML [atrybut x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Można ustawić wartości `x:Name` atrybutu w dowolnym elemencie obiektu. W Twojej związane z kodem identyfikator wybranego jest odpowiednikiem zmienna wystąpienia, która odwołuje się do skonstruowane wystąpienie. We wszystkich aspektach o nazwie funkcja elementy tak, jakby były wystąpienia obiektu (nazwa odwołuje się do tego wystąpienia), a elementy o do obsługi interakcji środowiska wykonawczego w aplikacji może odwoływać się z kodem. To połączenie między wystąpieniami i zmienne odbywa się przez kompilator znaczników WPF XAML i więcej w szczególności obejmują funkcje i wzorce takich jak <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> który nie zostanie omówiona szczegółowo w tym temacie.  
  
 Dziedzicz WPF framework XAML elementów <xref:System.Windows.FrameworkElement.Name%2A> właściwość, która jest odpowiednikiem XAML zdefiniowane `x:Name` atrybutu. Niektóre inne klasy udostępniają odpowiedniki właściwości poziomu `x:Name`, która zazwyczaj także została zdefiniowana jako `Name` właściwości. Ogólnie rzecz biorąc, jeśli nie możesz znaleźć `Name` właściwości tabeli elementów członkowskich dla wybranego elementu/typu, użyj `x:Name` zamiast tego. `x:Name` Wartości zapewni identyfikatora elementu XAML, który może służyć w czasie wykonywania określonych podsystemów lub metody narzędziowe takich jak <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 W poniższym przykładzie <xref:System.Windows.FrameworkElement.Name%2A> na <xref:System.Windows.Controls.StackPanel> elementu. Następnie program obsługi na <xref:System.Windows.Controls.Button> w tym <xref:System.Windows.Controls.StackPanel> odwołania <xref:System.Windows.Controls.StackPanel> za pośrednictwem jego odwołania do wystąpienia `buttonContainer` jako ustawione przez <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Podobnie jak w zmiennej nazwy XAML dla wystąpienia obiektu podlega postanowieniom koncepcji zakresu, tak, aby nazwy można wymusić być unikatowe w obrębie niektórych zakres, który jest atrybutem wartości prognozowanych. Podstawowy kod znaczników, który definiuje stronę oznacza jeden unikatowy namescope XAML z granicą namescope XAML jest elementem głównym tej strony. Jednak inne źródła znaczników mogą współdziałać ze stroną w czasie wykonywania, takie jak style lub szablonów w ramach stylów, i takich źródeł znaczników często mają własne namescopes XAML, który nie musi nawiązać połączenia z namescope XAML strony. Aby uzyskać więcej informacji na temat `x:Name` i XAML namescopes, zobacz <xref:System.Windows.FrameworkElement.Name%2A>, [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md), lub [WPF XAML Namescopes](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Dołączone właściwości i dołączone zdarzenia  
 XAML określa funkcja języka, która umożliwia niektórych właściwości lub zdarzenia należy określić w dowolnym elemencie, niezależnie od tego, czy istnieje właściwość lub zdarzenie w definicji typu dla elementu, który jest ustawiany na. Wersja właściwości ta funkcja jest wywoływana dołączona właściwość, nosi nazwę wersji zdarzenia dołączone zdarzenie. Koncepcyjnie możesz można traktować dołączone właściwości i dołączone zdarzenia jako Członkowie globalni, które można ustawić na wystąpienie elementu/obiektu języka XAML. Jednak element/klasy lub większej infrastruktury musi obsługiwać zapasowy magazyn właściwości dla wartości dołączone.  
  
 Dołączone właściwości w języku XAML są zazwyczaj używane za pośrednictwem Składnia atrybutu. W składni atrybutu określ dołączona właściwość w formie *ownerType*. *propertyName*.  
  
 Pozornie przypomina to użycie elementu właściwości, ale w takim przypadku *ownerType* możesz określić będzie zawsze inny element type niż object element których wartość dołączona właściwość. *ownerType* jest typ, który udostępnia metody dostępu, które są wymagane przez procesor XAML, aby można było pobrać lub ustawić wartości właściwości dołączone.  
  
 Najbardziej typowym scenariuszem dla dołączone właściwości jest umożliwienie elementy podrzędne zgłoszenia wartości właściwości do swojego elementu nadrzędnego.  
  
 Poniższy przykład przedstawia <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączona właściwość. <xref:System.Windows.Controls.DockPanel> Klasa definiuje metody dostępu dla <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> i dlatego jest właścicielem dołączona właściwość. <xref:System.Windows.Controls.DockPanel> Klasa zawiera także logiki iteruje po jego elementów podrzędnych i w szczególności sprawdza każdego elementu, dla ustaw wartość elementu <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Jeśli wartość zostanie znaleziona, ta wartość jest używany podczas układu położenie elementów podrzędnych. Użycie <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączona właściwość i tej możliwości pozycjonowania jest w rzeczywistości motywujące scenariusz <xref:System.Windows.Controls.DockPanel> klasy.  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], większość lub wszystkie dołączone właściwości również są zaimplementowane jako właściwości zależności. Aby uzyskać więcej informacji, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Dołączone zdarzenia użycia podobnej *ownerType*. *eventName* formularza Składnia atrybutu. Podobnie jak zdarzenia niedołączoną wartością atrybutu dołączone zdarzenie w języku XAML Określa nazwę metody obsługi, które jest wywoływane, gdy zdarzenie jest obsługiwane w elemencie. Dołączone zdarzenie użycia w WPF XAML są mniej typowe. Aby uzyskać więcej informacji, zobacz [dołączony Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Typy podstawowe i języka XAML  
 Podstawowy WPF XAML i jego przestrzeni nazw XAML jest kolekcją typów, które odpowiadają [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów oprócz elementów kodu znaczników dla XAML. Jednak nie wszystkie klasy mogą być mapowane na elementy. Abstrakcyjnej klasy, takich jak <xref:System.Windows.Controls.Primitives.ButtonBase>, i niektórych nieabstrakcyjnej klasy podstawowej są używane do dziedziczenia w [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] modelu obiektów. Klasy podstawowej, w tym abstrakcyjny te są nadal ważne programowanie XAML, ponieważ członków poszczególnych konkretnych elementów XAML dziedziczy niektóre klasy podstawowej w swojej hierarchii. Często tych elementów członkowskich zawierają właściwości, które można ustawić jako atrybuty w elemencie lub zdarzeń, które są obsługiwane. <xref:System.Windows.FrameworkElement>podstawowy konkretnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na poziomie framework WPF. Podczas projektowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], będzie używać różnych kształtu, panelu, dekoratora lub pochodną klasy formantów, wszystkie <xref:System.Windows.FrameworkElement>. Powiązane klasy podstawowej <xref:System.Windows.FrameworkContentElement>, obsługuje zorientowane na dokument elementów również na prezentacji układ przepływu, za pomocą [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] które celowo duplikatów [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] w <xref:System.Windows.FrameworkElement>. Kombinację atrybutów na poziomie elementu, a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] modelu obiektu zawiera zestaw wspólnych właściwości, które są można ustawić w najbardziej konkretnych elementów XAML, niezależnie od tego, czy konkretny element XAML i jego typem podstawowym.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>Zabezpieczenia XAML  
 XAML jest język bezpośrednio reprezentuje podczas tworzenia wystąpienia obiektu i wykonywanie. W związku z tym elementy utworzone w języku XAML ma tego samego możliwość interakcji z zasobami systemu (na przykład sieci dostępu do pliku systemu We/Wy) jako równoważne, generowany jest kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] strukturę zabezpieczeń [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]. Oznacza to, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości w strefie internet ma ograniczone uprawnienia wykonywania. "Luźno XAML" (strony XAML Nieskompilowane interpretowana w czasie ładowania przez Podgląd XAML) i [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] są zazwyczaj uruchamiane w tej strefie internet i ten sam zestaw uprawnień.  Jednak XAML załadowany w pełni zaufany aplikacji ma takie same prawa dostępu do zasobów systemowych, jak hostingu aplikacji. Aby uzyskać więcej informacji, zobacz [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>Ładowanie z kodu XAML  
 XAML może służyć do definiowania wszystkie interfejsu użytkownika, ale czasami jest również należy zdefiniować tylko część interfejsu użytkownika w języku XAML. Ta funkcja może posłużyć do włączenia dostosowywania częściowe, lokalnego magazynu danych przy użyciu kodu XAML obiektu biznesowego lub różne możliwe scenariusze. Klucz do tych scenariuszy jest <xref:System.Windows.Markup.XamlReader> klasy i jej <xref:System.Windows.Markup.XamlReader.Load%2A> metody. Dane wejściowe są pliku XAML, a dane wyjściowe to obiekt, który reprezentuje wszystkie drzewa środowiska wykonawczego obiektów, który został utworzony na podstawie tego znacznika. Następnie można wstawić obiektu właściwość innego obiektu, który już istnieje w aplikacji. Tak długo, jak właściwość jest odpowiednie właściwości w modelu zawartości, która ma możliwości wyświetlania ostatecznego i który powiadomi aparat wykonywania czy nowej zawartości został dodany do aplikacji, można bardzo łatwo modyfikować zawartości uruchomionej aplikacji przez ładowanie w języku XAML. Należy pamiętać, że ta funkcja zwykle tylko dostępne w aplikacjach pełnego zaufania, z powodu oczywiste ryzyko związane z ładowanie plików do aplikacji podczas ich działania.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Co to jest dalej  
 Ten temat zawiera podstawowe wprowadzenie do pojęcia składni języka XAML i terminologię mają zastosowanie w WPF. Aby uzyskać więcej informacji na temat terminów używanych w tym miejscu, zobacz [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Jeśli jeszcze nie zostało to zrobione, spróbuj ćwiczeń opisanych w temacie samouczek [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Podczas tworzenia aplikacji skoncentrowane znaczników opisanego przez samouczek wykonywania może pomóc w zapamiętaniu wiele pojęć opisanych w tym temacie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przy użyciu określonej aplikacji modelu opartego na <xref:System.Windows.Application> klasy. Aby uzyskać więcej informacji, zobacz [omówienie zarządzania aplikacji](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
 [Tworzenie aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) zapewnia więcej informacji o sposobie tworzenia aplikacji włącznie XAML z wiersza polecenia i z [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) zawiera więcej informacji o wszechstronność właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i pojęcia związane z właściwości zależności.  
  
## <a name="see-also"></a>Zobacz też  
 [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [Klasy XAML i niestandardowe dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Przestrzeń nazw XAML (x:) — funkcje językowe](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozszerzenia WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
