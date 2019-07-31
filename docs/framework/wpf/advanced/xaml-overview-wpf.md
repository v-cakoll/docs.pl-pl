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
ms.openlocfilehash: ee5318b8ba1284f2805b80b3e41fab3ae739158c
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671997"
---
# <a name="xaml-overview-wpf"></a>Przegląd XAML (WPF)

W tym temacie opisano funkcje języka XAML i pokazano, jak można użyć języka XAML do pisania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym temacie opisano w tym artykule język [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML wdrożony przez program. Język XAML jest większym pojęciem języka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]niż.  

<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>Co to jest XAML?  
 XAML jest deklaratywnym językiem znaczników. Zgodnie z modelem programowania .NET Framework język XAML upraszcza tworzenie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji .NET Framework. Można utworzyć widoczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy w deklaratywnym znaczniku XAML, a następnie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oddzielić definicję od logiki czasu wykonywania przy użyciu plików powiązanych z kodem, które są przyłączone do znaczników przy użyciu częściowych definicji klas. XAML bezpośrednio reprezentuje Tworzenie wystąpienia obiektów w określonym zestawie typów zapasowych zdefiniowanych w zestawach. Jest to w przeciwieństwie do większości innych języków znaczników, które są zwykle interpretowane, bez bezpośredniego powiązania z systemem typów zapasowych. Język XAML umożliwia przepływ pracy, w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] którym osobne strony mogą korzystać z logiki aplikacji, przy użyciu potencjalnie różnych narzędzi.  
  
 Gdy jest reprezentowana jako tekst, pliki XAML są plikami XML, które zwykle `.xaml` mają rozszerzenie. Pliki mogą być kodowane przy użyciu dowolnego kodowania XML, ale kodowanie jako UTF-8 jest typowe.  
  
 Poniższy przykład pokazuje, jak można utworzyć przycisk jako część elementu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Ten przykład jest przeznaczony tylko do zapewnienia, jak język XAML reprezentuje typowy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] metafory programistyczny (nie jest to kompletny przykład).  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Składnia języka XAML w skrócie  
 W poniższych sekcjach objaśniono podstawowe formy składni XAML i przedstawiono przykład krótkiego znacznika. Te sekcje nie są przeznaczone do przekazywania pełnych informacji o poszczególnych formularzach składni, takich jak te reprezentowane w systemie typów zapasowych. Aby uzyskać więcej informacji na temat składni języka XAML dla każdego z formularzy składniowych wprowadzonych w tym temacie, zobacz [Szczegóły składni XAML](xaml-syntax-in-detail.md).  
  
 Większość materiału w kilku następnych sekcjach będzie dla Ciebie częściowa, jeśli masz wcześniejszą wiedzę o języku XML. Jest to jedna z podstawowych zasad projektowania języka XAML.  Język XAML definiuje własne koncepcje, ale te koncepcje działają w postaci języka XML i znaczników.  
  
### <a name="xaml-object-elements"></a>Elementy obiektów XAML  
 Element obiektu zwykle deklaruje wystąpienie typu. Ten typ jest zdefiniowany w zestawach, które dostarczają typy zapasowe dla technologii, która używa języka XAML jako język.  
  
 Składnia elementu obiektu zawsze rozpoczyna się od otwierającego nawiasu\<ostrego (). Następuje nazwa typu, w którym chcesz utworzyć wystąpienie. (Nazwa może zawierać prefiks, koncepcję, która zostanie omówiona później). Następnie można opcjonalnie zadeklarować atrybuty dla elementu Object. Aby zakończyć tag elementu obiektu, koniec z zamykającym nawiasem ostrym (>). Zamiast tego można użyć formularza z samym zamknięciem, który nie ma żadnej zawartości, przez wypełnienie znacznika z ukośnikiem i zamykającym nawiasem ostrym (/>). Na przykład poszukaj wcześniej pokazanego fragmentu znaczników:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Określa dwa elementy obiektów: `<StackPanel>` (z zawartością i tag zamykany później) oraz `<Button .../>` (formularz z własnym zamykaniem z kilkoma atrybutami). Elementy `StackPanel` obiektu i `Button` Każda mapa do nazwy klasy, która jest zdefiniowana przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i jest częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów. Gdy określisz tag elementu obiektu, tworzysz instrukcję przetwarzania XAML, aby utworzyć nowe wystąpienie. Każde wystąpienie jest tworzone przez wywołanie konstruktora bez parametrów bazowego typu podczas analizowania i ładowania XAML.  
  
### <a name="attribute-syntax-properties"></a>Składnia atrybutu (właściwości)  
 Właściwości obiektu często można wyrazić jako atrybuty elementu Object. Składnia atrybutu nazywa właściwość, która jest ustawiana w składni atrybutów, a po niej operator przypisania (=). Wartość atrybutu jest zawsze określona jako ciąg, który jest zawarty w cudzysłowie.  
  
 Składnia atrybutu jest najbardziej ulepszoną składnią ustawień właściwości i jest najbardziej intuicyjną składnią używaną dla deweloperów, którzy używali języków oznakowania w przeszłości. Na przykład poniższy znacznik tworzy przycisk, który ma czerwony tekst i niebieskie tło, a także wyświetla tekst określony jako `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Składnia elementu właściwości  
 W przypadku niektórych właściwości elementu obiektu składnia atrybutu nie jest możliwa, ponieważ obiekt lub informacje niezbędne do podania wartości właściwości nie mogą być odpowiednio wyrażone w cudzysłowie i ograniczeniach ciągu składni atrybutu. W takich przypadkach można użyć innej składni znanej jako składni elementu właściwości.  
  
 Składnia tagu początkowego elementu Property `<`to *TypeName*`.`*PropertyName*`>`. Ogólnie rzecz biorąc zawartość tego tagu jest elementem obiektu typu, który Właściwość przyjmuje jako wartość. Po określeniu zawartości należy zamknąć element właściwości z tagiem końcowym. Składnia tagu końcowego `</`to *TypeName*`.`*PropertyName*`>`.  
  
 Jeśli składnia atrybutu jest możliwa, użycie składni atrybutu jest zwykle wygodniejsze i zapewnia bardziej zwarte znaczniki, ale często jest to kwestia stylu, a nie ograniczenia techniczne. W poniższym przykładzie pokazano te same właściwości, które są ustawiane jako w poprzednim przykładzie składni atrybutów, ale tym razem z użyciem składni elementu właściwości dla wszystkich właściwości `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Składnia kolekcji  
 Język XAML zawiera pewne optymalizacje, które generują więcej czytelnych znaczników. Taka optymalizacja polega na tym, że jeśli dana właściwość przyjmuje typ kolekcji, elementy zadeklarowane w znaczniku jako elementy podrzędne w obrębie tej właściwości stają się częścią kolekcji. W tym przypadku Kolekcja elementów podrzędnych obiektu jest ustawiana na Właściwość kolekcji.  
  
 Poniższy przykład przedstawia składnię kolekcji dla wartości <xref:System.Windows.Media.GradientBrush.GradientStops%2A> ustawienia właściwości:  
  
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
 XAML określa funkcję języka, za pomocą której Klasa może wyznaczyć dokładnie jedną z jej właściwości jako właściwość zawartości XAML. Elementy podrzędne tego elementu obiektu są używane do ustawiania wartości tej właściwości zawartości. Inaczej mówiąc, aby właściwość content była unikatowa, można pominąć element właściwości podczas ustawiania tej właściwości w znaczniku XAML i utworzyć bardziej widoczny element nadrzędny/podrzędny metaphor w znaczniku.  
  
 Na przykład <xref:System.Windows.Controls.Border> określa <xref:System.Windows.Controls.Decorator.Child%2A>Właściwość zawartości. Poniższe dwa <xref:System.Windows.Controls.Border> elementy są traktowane identycznie. Pierwszy z nich wykorzystuje składnię właściwości zawartości i pomija `Border.Child` element właściwości. Druga z nich jest `Border.Child` jawnie wyświetlana.  
  
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
  
 Jako reguła języka XAML, wartość właściwości zawartości XAML musi zostać podaną całkowicie przed lub całkowicie po jakimkolwiek innym elementom właściwości w tym elemencie obiektu. Na przykład następujące znaczniki nie kompilują:  
  
```xaml
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Aby uzyskać więcej informacji na temat tego ograniczenia dotyczącego właściwości zawartości XAML, zobacz sekcję "właściwości zawartości XAML" [w szczegółach składni języka XAML](xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Zawartość tekstowa  
 Niewielka liczba elementów XAML może bezpośrednio przetwarzać tekst jako zawartość. Aby to umożliwić, należy wykonać jedną z następujących czynności:  
  
- Klasa musi deklarować Właściwość zawartości, a właściwość zawartości musi być typu, który można przypisać do ciągu (może to być <xref:System.Object>typ). Na przykład każdy z <xref:System.Windows.Controls.ContentControl> nich <xref:System.Windows.Controls.ContentControl.Content%2A> używa jako jego właściwości zawartości i jest typem <xref:System.Object>i obsługuje <xref:System.Windows.Controls.Button>następujące użycie w praktyce <xref:System.Windows.Controls.ContentControl> , takiej jak: `<Button>Hello</Button>`.  
  
- Typ musi deklarować konwerter typu, w którym to przypadku zawartość tekstowa jest używana jako tekst inicjujący dla tego konwertera typów. Na przykład `<Brush>Blue</Brush>`. W tym przypadku jest to rzadziej spotykane rozwiązanie.  
  
- Typ musi być znany jako element podstawowy języka XAML.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>Połączone właściwości zawartości i kolekcji  
 Rozważmy następujący przykład:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 W tym miejscu <xref:System.Windows.Controls.Button> każdy jest <xref:System.Windows.Controls.StackPanel>elementem podrzędnym. Jest to usprawnione i intuicyjne znaczniki, które pomija dwa Tagi z dwóch różnych przyczyn.  
  
- **Pominięto element właściwości StackPanel. Children:** <xref:System.Windows.Controls.StackPanel> pochodzi od <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>definiuje <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> jako jej Właściwość zawartości XAML.  
  
- **Pominięto element obiektu UIElementcollection:** Właściwość przyjmuje typ <xref:System.Windows.Controls.UIElementCollection>, który implementuje <xref:System.Collections.IList>. <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> Tag elementu kolekcji można pominąć, opierając się na regułach języka XAML do przetwarzania kolekcji, takich jak <xref:System.Collections.IList>. (W tym przypadku faktycznie <xref:System.Windows.Controls.UIElementCollection> nie można utworzyć wystąpienia, ponieważ nie ujawnia on konstruktora bez parametrów i dlatego, że element obiektu jest pokazywany jako <xref:System.Windows.Controls.UIElementCollection> komentarz).  
  
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
  
### <a name="attribute-syntax-events"></a>Składnia atrybutu (zdarzenia)  
 Składnia atrybutu może być również używana dla elementów członkowskich, które są zdarzeniami, a nie właściwościami. W takim przypadku nazwa atrybutu jest nazwą zdarzenia. W implementacji WPF zdarzeń dla języka XAML wartość atrybutu jest nazwą programu obsługi, który implementuje delegata tego zdarzenia. Na przykład poniższy znacznik przypisuje procedurę obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia <xref:System.Windows.Controls.Button> do utworzonego w znaczniku:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Istnieje więcej informacji o zdarzeniach i języku XAML w WPF niż tylko ten przykład składni atrybutów. Można na przykład zastanowić się, `ClickHandler` co reprezentuje w tym miejscu i jak jest zdefiniowane. Zostanie to wyjaśnione w sekcji nadchodzące [zdarzenia i kod XAML](xaml-overview-wpf.md#events_and_xaml_codebehind) w tym temacie.  
  
<a name="case_and_white space_in_xaml"></a>   
## <a name="case-and-white-space-in-xaml"></a>Wielkość liter i odstępy w języku XAML  
 Język XAML zazwyczaj rozróżnia wielkość liter. Do celów rozpoznawania typów zapasowych w języku XAML WPF rozróżniana jest wielkość liter według tych samych reguł, które w środowisku CLR uwzględnia wielkość liter. Wszystkie elementy obiektów, elementy właściwości i nazwy atrybutów muszą być określone przy użyciu poufnej wielkości liter w porównaniu z nazwą do typu podstawowego w zestawie lub do elementu członkowskiego typu. Słowa kluczowe języka XAML i elementy pierwotne uwzględniają również wielkość liter. Wartości nie zawsze uwzględniają wielkość liter. Uwzględnianie wielkości liter w przypadku wartości będzie zależeć od zachowania konwertera typów skojarzonego z właściwością przyjmującą wartość lub typu wartości właściwości. Na przykład właściwości, które przyjmują <xref:System.Boolean> typ, mogą `true` przyjmować lub `True` jako równoważne wartości, ale tylko ponieważ natywna Konwersja języka XAML WPF dla ciągu, tak <xref:System.Boolean> aby była taka sama jak równoważne.  
  
 Procesory i serializatory języka XAML WPF zignorują lub porzucają cały nieznaczący biały znak i będą normalizować wszelkie znaczące białe znaki. Jest to zgodne z domyślnymi zaleceniami dotyczącymi zachowania odstępów specyfikacji języka XAML. To zachowanie jest zazwyczaj tylko konsekwencją podczas określania ciągów w obrębie właściwości zawartości XAML. W najprostszych warunkach kod XAML konwertuje spacje, znaki wysuwu wiersza i tabulatory na spacje, a następnie zachowuje jedno miejsce, jeśli znajduje się na końcu ciągłego ciągu. Pełne wyjaśnienie obsługi białych znaków XAML nie jest omówione w tym temacie. Aby uzyskać szczegółowe informacje, zobacz [białe miejsce w języku XAML](../../xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 Rozszerzenia znaczników są koncepcją języka XAML. Gdy jest używany do podania wartości składni atrybutów, nawiasy klamrowe (`{` i `}`) wskazują użycie rozszerzenia znaczników. To użycie kieruje przetwarzanie kodu XAML do wyjścia z ogólnej obróbki wartości atrybutów jako ciągu literału lub wartości zamiennej ciągu.  
  
 Najpopularniejsze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozszerzenia znaczników używane w programowaniu aplikacji to [powiązania](binding-markup-extension.md), używane na potrzeby wyrażeń powiązań danych, a zasoby odwołują się do [StaticResource](staticresource-markup-extension.md) i [DynamicResource —](dynamicresource-markup-extension.md). Używając rozszerzeń znaczników, można użyć składni atrybutów, aby podać wartości właściwości, nawet jeśli ta właściwość nie obsługuje ogólnie składni atrybutów. Rozszerzenia znaczników często używają typów wyrażeń pośrednich do włączania funkcji, takich jak odłożone wartości lub odwoływania się do innych obiektów, które są obecne tylko w czasie wykonywania.  
  
 Na przykład następujące znaczniki ustawia wartość <xref:System.Windows.FrameworkElement.Style%2A> właściwości przy użyciu składni atrybutu. Właściwość przyjmuje wystąpienie <xref:System.Windows.Style> klasy, które domyślnie nie można utworzyć wystąpienia przez ciąg składni atrybutów. <xref:System.Windows.FrameworkElement.Style%2A> Ale w tym przypadku atrybut odwołuje się do określonego rozszerzenia znacznika, [StaticResource](staticresource-markup-extension.md). Gdy to rozszerzenie znacznika zostanie przetworzone, zwraca odwołanie do stylu, który został wcześniej utworzony jako zasób z kluczowym kluczem w słowniku zasobów.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Aby zapoznać się z listą odwołań wszystkich rozszerzeń znaczników dla języka XAML zaimplementowanego w środowisku WPF, zobacz [rozszerzenia XAML WPF](wpf-xaml-extensions.md). Aby zapoznać się z listą odwołań do rozszerzeń znaczników, które są zdefiniowane przez system. XAML i które są szeroko dostępne dla .NET Framework implementacji [XAML, zobacz Przestrzeń nazw XAML (x:) Funkcje](../../xaml-services/xaml-namespace-x-language-features.md)językowe. Aby uzyskać więcej informacji o pojęciach dotyczących rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Konwertery typów  
 W [składni XAML w zwięzłej](xaml-overview-wpf.md#xaml_syntax_in_brief) sekcji stwierdzono, że wartość atrybutu musi być możliwa do ustawienia przez ciąg. Podstawowa, natywna obsługa sposobu, w jaki ciągi są konwertowane na inne typy obiektów lub wartości pierwotne, <xref:System.String> jest oparta na typie, oprócz natywnego przetwarzania niektórych typów, takich <xref:System.DateTime> jak <xref:System.Uri>lub. Ale wiele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów lub elementów członkowskich tych typów zwiększa zachowanie podstawowego przetwarzania atrybutów ciągów, w taki sposób, aby wystąpienia bardziej złożonych typów obiektów mogły być określone jako ciągi i atrybuty.  
  
 <xref:System.Windows.Thickness> Struktura jest przykładem typu, który ma włączoną konwersję typu dla użycia XAML. <xref:System.Windows.Thickness>wskazuje miary w obrębie zagnieżdżonego prostokąta i jest używana jako wartość właściwości, takich <xref:System.Windows.FrameworkElement.Margin%2A>jak. Przez umieszczenie konwertera <xref:System.Windows.Thickness>typów, wszystkie właściwości, które używają a <xref:System.Windows.Thickness> są łatwiejsze do określenia w języku XAML, ponieważ można je określić jako atrybuty. W poniższym przykładzie użyto konwersji typu i składni atrybutów, aby podać wartość dla <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 Przykład składni poprzedniej atrybutu jest odpowiednikiem poniższego, bardziej szczegółowego przykładu składni, gdzie <xref:System.Windows.FrameworkElement.Margin%2A> zamiast tego jest ustawiana za pomocą składni elementu <xref:System.Windows.Thickness> właściwości zawierającego element obiektu. Cztery właściwości <xref:System.Windows.Thickness> klucza są ustawiane jako atrybuty dla nowego wystąpienia:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
> Istnieje również ograniczona liczba obiektów, w których konwersja typu jest jedynym publicznym sposobem ustawiania właściwości tego typu bez uwzględniania podklasy, ponieważ sam typ nie ma konstruktora bezparametrycznego. Może to być na przykład <xref:System.Windows.Input.Cursor>.  
  
 Aby uzyskać więcej informacji na temat sposobu konwersji typów i użycia dla składni atrybutów, zobacz [TypeConverters i XAML](typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>Elementy główne XAML i przestrzenie nazw XAML  
 Plik XAML musi mieć tylko jeden element główny, aby można było poprawnie sformułowany [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] plik i prawidłowy plik XAML. W przypadku typowych scenariuszy WPF należy użyć elementu głównego, który ma uwidocznione znaczenie w modelu <xref:System.Windows.Window> aplikacji WPF (na przykład lub <xref:System.Windows.Controls.Page> dla strony, <xref:System.Windows.ResourceDictionary> dla zewnętrznego słownika lub <xref:System.Windows.Application> dla definicji aplikacji). Poniższy przykład pokazuje element główny typowego pliku XAML dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony, z <xref:System.Windows.Controls.Page>elementem głównym.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Element główny zawiera również atrybuty `xmlns` i. `xmlns:x` Te atrybuty wskazują na procesor XAML, który przestrzenie nazw XAML zawierają definicje typów dla typów zapasowych, które znaczniki będą odwoływać się jako elementy. Ten `xmlns` atrybut wskazuje domyślną przestrzeń nazw XAML. W domyślnej przestrzeni nazw XAML elementy obiektu w znaczniku można określić bez prefiksu. W przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] większości scenariuszy aplikacji i dla niemal wszystkich przykładów podano [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w sekcjach [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], domyślna przestrzeń nazw XAML jest zamapowana na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeń nazw [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. Ten `xmlns:x` atrybut wskazuje dodatkową przestrzeń nazw XAML, która mapuje przestrzeń nazw [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)]języka XAML.  
  
 To użycie `xmlns` w celu zdefiniowania zakresu użycia i mapowania namescope jest zgodne ze specyfikacją XML 1,0. Zakresy nazw WPF języka XAML różnią się od Zakresy nazw WPF XML tylko w tym, że namescope XAML określa również sposób, w jaki elementy namescope są obsługiwane przez typy, gdy dochodzi do rozpoznawania typów i analizowania kodu XAML.  
  
 Należy zauważyć, `xmlns` że atrybuty są tylko absolutnie niezbędne dla elementu głównego każdego pliku XAML. `xmlns`definicje zostaną zastosowane do wszystkich elementów podrzędnych elementu głównego (to zachowanie jest ponownie spójne ze specyfikacją XML 1,0 dla `xmlns`). `xmlns` atrybuty są również dozwolone dla innych elementów znajdujących się w katalogu głównym, a następnie stosowane do wszystkich elementów podrzędnych elementu definiującego. Jednak częste Definiowanie lub ponowna definicja przestrzeni nazw XAML może spowodować, że styl znaczników XAML jest trudny do odczytania.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementacja jego procesora XAML obejmuje infrastrukturę, która ma świadomość zestawów rdzeni WPF. Zestawy podstawowe są znane, aby zawierały typy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługujące mapowania do domyślnej przestrzeni nazw XAML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ta funkcja jest włączana za pomocą konfiguracji, która jest częścią pliku kompilacji projektu oraz systemów kompilacji i projektów WPF. W związku z tym deklaruje domyślną przestrzeń nazw XAML `xmlns` , ponieważ jest to wartość domyślna, która jest niezbędna do odwoływania się do elementów języka XAML, które pochodzą z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.  
  
### <a name="the-x-prefix"></a>Prefiks x:  
 W poprzednim przykładzie elementu głównego prefiks `x:` został użyty do mapowania przestrzeni nazw [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)]XAML, która jest dedykowaną przestrzenią nazw XAML, która obsługuje konstrukcje języka XAML. Ten `x:` prefiks jest używany do mapowania tej przestrzeni nazw XAML w szablonach dla projektów, w przykładach i w dokumentacji w [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]tym miejscu. Przestrzeń nazw XAML dla języka XAML zawiera kilka konstrukcji programistycznych, które są często używane w języku XAML. Poniżej znajduje się lista najpopularniejszych `x:` konstrukcji programowania prefiksów, które będą używane:  
  
- [x:Key](../../xaml-services/x-key-directive.md): Ustawia unikatowy klucz dla każdego zasobu w <xref:System.Windows.ResourceDictionary> (lub podobne koncepcje słownika w innych strukturach). `x:Key`prawdopodobnie będzie można obsłużyć 90% `x:` użycia w typowym znaczniku aplikacji WPF.  
  
- [x:Class](../../xaml-services/x-class-directive.md): Określa przestrzeń nazw CLR i nazwę klasy dla klasy, która zawiera kod związany ze stroną XAML. Należy mieć taką klasę, aby obsługiwała kod dla modelu programowania WPF i w związku z tym prawie zawsze widzieć `x:` zamapowane, nawet jeśli nie ma żadnych zasobów.  
  
- [x:Name](../../xaml-services/x-name-directive.md): Określa nazwę obiektu czasu wykonywania dla wystąpienia, które istnieje w kodzie czasu wykonywania po przetworzeniu elementu obiektu. Ogólnie rzecz biorąc często używasz równoważnej właściwości [x:Name](../../xaml-services/x-name-directive.md). Takie właściwości są mapowane w odróżnieniu od właściwości tworzenia kopii zapasowych CLR i w związku z tym są bardziej wygodne w programowaniu aplikacji, w którym często używasz kodu czasu wykonywania, aby znaleźć nazwane elementy z zainicjowanego języka XAML. Najbardziej powszechną właściwością jest <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Można nadal używać [x:Name](../../xaml-services/x-name-directive.md) , gdy równoważna właściwość na poziomie <xref:System.Windows.FrameworkElement.Name%2A> platformy WPF nie jest obsługiwana w określonym typie. Dzieje się tak w niektórych scenariuszach animacji.  
  
- [x:static —](../../xaml-services/x-static-markup-extension.md): Włącza odwołanie, które zwraca wartość statyczną, która nie jest w innym przypadku właściwości zgodną z językiem XAML.  
  
- [x:Type —](../../xaml-services/x-type-markup-extension.md): <xref:System.Type> Tworzy odwołanie na podstawie nazwy typu. Służy do określania atrybutów, które przyjmują <xref:System.Type>, takich jak <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, chociaż często właściwość ma<xref:System.Type> natywny ciąg do konwersji w taki sposób, że użycie rozszerzenia znacznika [x:Type —](../../xaml-services/x-type-markup-extension.md) jest opcjonalne.  
  
 Istnieją dodatkowe konstrukcje programistyczne w `x:` przestrzeni nazw prefix/XAML, które nie są wspólne. Aby uzyskać szczegółowe informacje [, zobacz Przestrzeń nazw XAML (x:) Funkcje](../../xaml-services/xaml-namespace-x-language-features.md)językowe.  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Prefiksy niestandardowe i typy niestandardowe w języku XAML  
 Dla własnych zestawów niestandardowych lub dla zestawów poza rdzeniem WPF 'presentationcore, platformie docelowej i 'windowsbase, można określić zestaw jako część niestandardowego `xmlns` mapowania. Następnie można odwoływać się do typów z tego zestawu w kodzie XAML, tak długo, jak ten typ jest poprawnie zaimplementowany do obsługi użycia kodu XAML, które próbujesz.  
  
 Poniżej znajduje się bardzo podstawowy przykład sposobu działania niestandardowych prefiksów w znacznikach XAML. Prefiks `custom` jest zdefiniowany w tagu elementu głównego i mapowany do określonego zestawu, który jest spakowany i dostępny dla aplikacji. Ten zestaw zawiera typ `NumericUpDown`, który jest implementowany do obsługi ogólnego użycia XAML, a także przy użyciu dziedziczenia klasy, które pozwala na jego wstawienie w tym konkretnym punkcie w modelu zawartości XAML WPF. Wystąpienie tego `NumericUpDown` formantu jest zadeklarowane jako element obiektu, przy użyciu prefiksu, tak aby Analizator XAML wie, która przestrzeń nazw XAML zawiera typ, i w związku z tym, gdzie zestaw zapasowy zawiera definicję typu.  
  
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
  
 Aby uzyskać więcej informacji na temat typów niestandardowych w języku XAML, zobacz sekcję [XAML i klasy niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md).  
  
 Aby uzyskać więcej informacji o tym, jak są powiązane przestrzenie nazw XML i przestrzenie nazw kodu zapasowego w zestawach, zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla języka XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Zdarzenia i kod XAML — za  
 Większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji składa się zarówno z znaczników XAML, jak i kodu. W projekcie kod XAML jest zapisywana jako `.xaml` plik, a język CLR, taki jak Microsoft Visual Basic lub C# jest używany do pisania pliku związanego z kodem. Gdy plik XAML jest kompilowany jako część modelu programowania i aplikacji WPF, lokalizacja pliku z kodem XAML dla pliku XAML jest identyfikowana przez określenie przestrzeni nazw i klasy jako `x:Class` atrybutu głównego elementu XAML.  
  
 W przykładach do tej pory widzisz kilka przycisków, ale żaden z tych przycisków nie ma jeszcze żadnego zachowania logicznego skojarzonego z nimi. Podstawowym mechanizmem na poziomie aplikacji do dodawania zachowań dla elementu obiektu jest użycie istniejącego zdarzenia klasy element i zapisanie konkretnej procedury obsługi dla tego zdarzenia, które jest wywoływane, gdy zdarzenie jest zgłaszane w czasie wykonywania. Nazwa zdarzenia i nazwa programu obsługi są określone w znaczniku, podczas gdy kod implementujący procedurę obsługi jest zdefiniowany w kodzie.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Należy zauważyć, że plik związany z kodem używa przestrzeni nazw `ExampleNamespace` CLR i `ExamplePage` deklaruje jako klasę częściową w tej przestrzeni nazw. Jest `x:Class` to równoległe `ExampleNamespace`wartość atrybutu.`ExamplePage` który został podany w katalogu głównym znaczników. Kompilator znaczników WPF utworzy klasę częściową dla dowolnego skompilowanego pliku XAML, pobierając klasę z typu elementu głównego. Gdy podajesz kod, który definiuje również tę samą klasę częściową, otrzymany kod jest połączony w tej samej przestrzeni nazw i klasie skompilowanej aplikacji.  
  
 Aby uzyskać więcej informacji o wymaganiach związanych z programowaniem związanym z kodem w programie WPF, zobacz sekcję "wymagania dotyczące kodu, procedury obsługi zdarzeń i częściowej klasy" dotyczącej [kodu i języka XAML w programie WPF](code-behind-and-xaml-in-wpf.md).  
  
 Jeśli nie chcesz tworzyć oddzielnego pliku związanego z kodem, możesz również umieścić kod w pliku XAML. Jednak kod wbudowany jest mniej wszechstronną techniką, która ma istotne ograniczenia. Aby uzyskać szczegółowe informacje, zobacz [kod w kodzie i XAML w WPF](code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Zdarzenia kierowane  
 Konkretna funkcja zdarzenia, która jest podstawą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia, jest zdarzeniem kierowanym. Zdarzenia kierowane umożliwiają elementowi obsłużyć zdarzenie, które zostało zgłoszone przez inny element, o ile elementy są połączone za pomocą relacji drzewa. Podczas określania obsługi zdarzeń przy użyciu atrybutu XAML można nasłuchiwać zdarzenia kierowanego i obsługiwać je na dowolnym elemencie, w tym elementy, które nie wyświetlają danego zdarzenia w tabeli elementów członkowskich klasy. Jest to realizowane przez zakwalifikowanie atrybutu Nazwa zdarzenia nazwą klasy będącej właścicielem. Na przykład `StackPanel` element nadrzędny w trakcie ciągłego `StackPanel`  /  `Button` może zarejestrować procedurę obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia przycisku elementu `StackPanel` podrzędnego, określając atrybut `Button.Click` w Element Object z nazwą programu obsługi jako wartością atrybutu. Aby uzyskać więcej informacji na temat działania zdarzeń kierowanych, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>Elementy XAML o nazwach  
 Domyślnie wystąpienie obiektu tworzone w grafie obiektów przez przetwarzanie elementu obiektu XAML nie ma unikatowego identyfikatora lub odwołania do obiektu. Natomiast w przypadku wywołania konstruktora w kodzie niemal zawsze używasz wyniku konstruktora, aby ustawić zmienną dla konstruowanego wystąpienia, tak aby można było odwołać się do wystąpienia później w kodzie. W celu zapewnienia standardowego dostępu do obiektów, które zostały utworzone za pomocą definicji znaczników, XAML definiuje [atrybut x:Name](../../xaml-services/x-name-directive.md). Można ustawić wartość `x:Name` atrybutu dla dowolnego elementu obiektu. W kodzie, wybierany identyfikator jest odpowiednikiem zmiennej wystąpienia, która odwołuje się do skonstruowanego wystąpienia. W każdym przypadku, nazwane elementy działa tak, jakby były wystąpieniami obiektów (nazwa odwołuje się do tego wystąpienia), a jego kod może odwoływać się do nazwanych elementów w celu obsługi interakcji w czasie wykonywania w aplikacji. To połączenie między wystąpieniami i zmiennymi jest realizowane przez kompilator znaczników języka XAML WPF, a dokładniej obejmuje funkcje i wzorce, takie <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> jak nie są szczegółowo omówione w tym temacie.  
  
 Elementy XAML na poziomie platformy WPF dziedziczą <xref:System.Windows.FrameworkElement.Name%2A> właściwość, która jest równoważna z atrybutem `x:Name` zdefiniowanym XAML. Niektóre inne klasy udostępniają również odpowiedniki poziomu właściwości dla `x:Name`, które są również zwykle zdefiniowane `Name` jako właściwość. Ogólnie mówiąc, jeśli nie można znaleźć `Name` właściwości w tabeli Members dla wybranego elementu/typu, użyj `x:Name` zamiast tego. Wartości będą zawierać identyfikator elementu XAML, który może być używany w czasie wykonywania, zgodnie z konkretnymi podsystemami lub metodami narzędzi, takimi jak <xref:System.Windows.FrameworkElement.FindName%2A>. `x:Name`  
  
 Poniższy przykład ustawia <xref:System.Windows.FrameworkElement.Name%2A> <xref:System.Windows.Controls.StackPanel> dla elementu. Następnie program <xref:System.Windows.Controls.Button> obsługi w programie, który <xref:System.Windows.Controls.StackPanel> odwołuje się <xref:System.Windows.Controls.StackPanel> za pomocą jego odwołania `buttonContainer` do wystąpienia zgodnie <xref:System.Windows.FrameworkElement.Name%2A>z ustawieniem.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Podobnie jak zmienna, nazwa XAML dla wystąpienia podlega koncepcji zakresu, dzięki czemu nazwy mogą być wymuszane jako unikatowe w obrębie określonego zakresu, który jest przewidywalny. Podstawowe znaczniki definiujące stronę oznaczają jeden unikatowy namescope języka XAML, przy czym granica namescope XAML jest elementem głównym tej strony. Jednak inne źródła znaczników mogą wchodzić w skład strony w czasie wykonywania, takie jak style lub szablony w stylach, a takie źródła oznaczeń często mają własne Zakresy nazw WPF języka XAML, które nie muszą być połączone z namescopeem XAML strony. Aby uzyskać więcej informacji `x:Name` na temat zakresy nazw WPF języka XAML <xref:System.Windows.FrameworkElement.Name%2A>, zobacz sekcję, [x:Name dyrektywy](../../xaml-services/x-name-directive.md)lub [WPF XAML Zakresy nazw WPF](wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Dołączone właściwości i dołączone zdarzenia  
 XAML określa funkcję języka, która umożliwia określenie pewnych właściwości lub zdarzeń w dowolnym elemencie, niezależnie od tego, czy właściwość lub zdarzenie istnieje w definicjach typu dla elementu, który jest ustawiany. Wersja właściwości tej funkcji jest nazywana dołączoną właściwością, a wersja zdarzenia jest nazywana dołączonym zdarzeniem. Koncepcyjnie można traktować dołączone właściwości i załączone zdarzenia jako elementy członkowskie globalne, które można ustawić dla dowolnego wystąpienia elementu/obiektu XAML. Jednak ten element/Klasa lub większa infrastruktura musi obsługiwać magazyn właściwości zapasowych dla dołączonych wartości.  
  
 Dołączone właściwości w języku XAML są zwykle używane przez składnię atrybutu. W składni atrybutu należy określić dołączoną właściwość w postaci OwnerType. Funkcja *PropertyName*.  
  
 Jest to podobne, co przypomina użycie elementu właściwości, ale w tym przypadku jest on zawsze innym typem niż element obiektu, w którym jest ustawiana dołączona właściwość. *OwnerType* jest typem, który dostarcza metody akcesora wymagane przez procesor XAML w celu uzyskania lub ustawienia wartości właściwości dołączone.  
  
 Najbardziej typowym scenariuszem dla dołączonych właściwości jest włączenie elementów podrzędnych, aby zgłosić wartość właściwości do ich elementu nadrzędnego.  
  
 Poniższy przykład ilustruje <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> przyłączoną właściwość. Klasa definiuje metody dostępu dla <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> i w związku z tym jest właścicielem dołączonej właściwości. <xref:System.Windows.Controls.DockPanel> Klasa zawiera również logikę, która iteruje elementy podrzędne i sprawdza każdy element dla ustawionej <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>wartości. <xref:System.Windows.Controls.DockPanel> Jeśli zostanie znaleziona wartość, ta wartość jest używana podczas układania do położenia elementów podrzędnych. Użycie dołączonej właściwości i tej możliwości pozycjonowania jest w rzeczywistości scenariuszem z motywem <xref:System.Windows.Controls.DockPanel> dla klasy. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>  
  
 [!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie większość lub wszystkie dołączone właściwości są również zaimplementowane jako właściwości zależności. Aby uzyskać szczegółowe informacje, zobacz [Omówienie funkcji dołączone właściwości](attached-properties-overview.md).  
  
 Zdarzenia dołączone używają podobnego typu *OwnerType*. form EventName o składni atrybutów. Podobnie jak zdarzenia niedołączone, wartość atrybutu dla dołączonego zdarzenia w języku XAML określa nazwę metody obsługi, która jest wywoływana, gdy zdarzenie jest obsługiwane w elemencie. Dołączone użycia zdarzeń w języku XAML WPF są mniej popularne. Aby uzyskać więcej informacji, zobacz [Omówienie załączonych zdarzeń](attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Typy podstawowe i XAML  
 Bazowy kod XAML WPF i jego przestrzeń nazw XAML to Kolekcja typów, która odpowiada obiektom CLR, a nie tylko do elementów znaczników dla języka XAML. Jednak nie wszystkie klasy mogą być mapowane do elementów. Klasy abstrakcyjne, takie <xref:System.Windows.Controls.Primitives.ButtonBase>jak i pewne nieabstrakcyjne klasy podstawowe, są używane do dziedziczenia w modelu obiektów CLR. Klasy podstawowe, w tym abstrakcyjne, są nadal ważne dla rozwoju kodu XAML, ponieważ każdy konkretny element XAML dziedziczy elementy członkowskie z pewnej klasy podstawowej w swojej hierarchii. Często te elementy członkowskie zawierają właściwości, które można ustawić jako atrybuty dla elementu, lub zdarzenia, które mogą być obsługiwane. <xref:System.Windows.FrameworkElement>jest konkretną [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasą bazową na poziomie platformy WPF. Podczas projektowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]będziesz używać różnych klas Shape, panel, dekoratora i Control, które pochodzą od <xref:System.Windows.FrameworkElement>. Powiązana Klasa <xref:System.Windows.FrameworkContentElement>bazowa, obsługuje elementy zorientowane na dokumenty, które dobrze działają dla prezentacji układu przepływu, przy użyciu interfejsów API, które w sposób świadomy <xref:System.Windows.FrameworkElement>duplikują interfejsy API w programie. Kombinacja atrybutów na poziomie elementu i modelu obiektów CLR zapewnia zestaw wspólnych właściwości, które są ustawiane jako settable dla większości konkretnych elementów XAML, niezależnie od konkretnego elementu XAML i jego typu podstawowego.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>Zabezpieczenia XAML  
 XAML jest językiem znaczników, który bezpośrednio reprezentuje Tworzenie wystąpienia obiektu i wykonywanie. W związku z tym elementy utworzone w języku XAML mają tę samą możliwość współdziałania z zasobami systemowymi (dostęp do sieci, system plików we/wy) jako równoważny wygenerowany kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje .NET Framework 4 zabezpieczenia dostępu kodu (CAS). Oznacza to, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] że zawartość działająca w strefie Internet ma ograniczone uprawnienia wykonywania. "Luźne XAML" (strony nieskompilowanych kodów XAML w czasie ładowania przez przeglądarkę XAML) i [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] są zwykle uruchamiane w tej strefie internetowej i używają tego samego zestawu uprawnień.  Jednak kod XAML załadowany w w pełni zaufanej aplikacji ma taki sam dostęp do zasobów systemowych, jak aplikacja hostingu. Aby uzyskać więcej informacji, zobacz temat informacje o [zabezpieczeniach częściowej relacji zaufania WPF](../wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>Ładowanie XAML z kodu  
 KOD XAML może służyć do definiowania wszystkich interfejsów użytkownika, ale czasami jest również konieczne zdefiniowanie tylko fragmentu interfejsu użytkownika w języku XAML. Ta funkcja może być używana do włączania częściowego dostosowywania, lokalnego magazynu informacji przy użyciu języka XAML w celu zapewnienia obiektu biznesowego lub różnych możliwych scenariuszy. Klucz do tych scenariuszy jest <xref:System.Windows.Markup.XamlReader> klasą i jej <xref:System.Windows.Markup.XamlReader.Load%2A> metodą. Dane wejściowe to plik XAML, a dane wyjściowe to obiekt reprezentujący wszystkie drzewa czasu wykonywania obiektów, które zostały utworzone na podstawie tego znacznika. Następnie można wstawić obiekt jako właściwość innego obiektu, który już istnieje w aplikacji. Tak długo, jak właściwość jest odpowiednią właściwością w modelu zawartości, który ma możliwości wyświetlania ostatecznego i która powiadomi aparat wykonawczy o tym, że nowa zawartość została dodana do aplikacji, można łatwo modyfikować zawartość uruchomionej aplikacji. przez załadowanie w języku XAML. Należy pamiętać, że ta funkcja jest ogólnie dostępna tylko w aplikacjach z pełnym zaufaniem ze względu na oczywiste implikacje bezpieczeństwa ładowania plików do aplikacji podczas ich uruchamiania.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Co dalej  
 Ten temat zawiera podstawowe informacje o pojęciach dotyczących składni i terminologii języka XAML, które dotyczą platformy WPF. Aby uzyskać więcej informacji na temat terminów używanych w tym miejscu, zobacz [Szczegóły składni języka XAML](xaml-syntax-in-detail.md).  
  
 Jeśli jeszcze tego nie zrobiono, wypróbuj ćwiczenia w temacie [Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md)klasyczna WPF. Podczas tworzenia aplikacji skoncentrowanej na znacznikach opisanej w samouczku ćwiczenie pomogą wzmocnić wiele koncepcji opisanych w tym temacie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa określonego modelu aplikacji, który jest oparty na <xref:System.Windows.Application> klasie. Aby uzyskać szczegółowe informacje, zobacz [Omówienie zarządzania aplikacjami](../app-development/application-management-overview.md).  
  
 [Kompilowanie aplikacji WPF](../app-development/building-a-wpf-application-wpf.md) daje więcej szczegółowych informacji na temat sposobu tworzenia aplikacji w języku XAML z poziomu wiersza polecenia i [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]programu.  
  
 [Przegląd właściwości zależności](dependency-properties-overview.md) zawiera więcej informacji na temat uniwersalności właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i wprowadza koncepcję właściwości zależności.  
  
## <a name="see-also"></a>Zobacz także

- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
- [Przestrzeń nazw XAML (x:) Funkcje języka](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [Przegląd elementów podstawowych](base-elements-overview.md)
- [Drzewa w WPF](trees-in-wpf.md)
