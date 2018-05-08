---
title: Niestandardowe właściwości zależności
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: 2623f34418aad7a0b29c52d1310fdc79afced790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-dependency-properties"></a>Niestandardowe właściwości zależności
W tym temacie opisano przyczyny który [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperzy aplikacji autorów składnik może być utworzenie właściwości niestandardowe zależności i opisano kroki implementacji, a także niektóre opcje wdrażania, które może poprawić wydajność, użyteczność lub wszechstronność właściwości.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono zrozumieć właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas i przeczytanie [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) tematu. Aby można było wykonać przykłady w tym temacie, należy również zapoznać się [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
<a name="whatis"></a>   
## <a name="what-is-a-dependency-property"></a>Co to jest właściwością zależności?  
 Można włączyć, co byłoby [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości do obsługi stylów, powiązań danych dziedziczenia, animacji i wartości domyślne zaimplementowanie jako właściwość zależności. Właściwości zależności są właściwości, które są zarejestrowane w usłudze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu przez wywołanie metody <xref:System.Windows.DependencyProperty.Register%2A> — metoda (lub <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), oraz obsługiwanych przez <xref:System.Windows.DependencyProperty> pole identyfikatora. Właściwości zależności, które mogą być używane tylko przez <xref:System.Windows.DependencyObject> typów, ale <xref:System.Windows.DependencyObject> jest dość wysokie w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy hierarchii, dlatego większość klas dostępne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może obsługiwać właściwości zależności. Aby uzyskać więcej informacji na temat właściwości zależności i niektórych terminów i konwencje opisujących je w tym [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="example_dp"></a>   
## <a name="examples-of-dependency-properties"></a>Przykłady właściwości zależności  
 Przykłady właściwości zależności, które są wdrażane na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy mają <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.FrameworkElement.Width%2A> właściwości oraz <xref:System.Windows.Controls.TextBox.Text%2A> właściwości wśród wielu innych. Każda właściwość zależności udostępnianych przez klasę ma odpowiednie pola statycznego publicznego typu <xref:System.Windows.DependencyProperty> widoczne na tej samej klasy. Jest to identyfikator dla właściwości zależności. Identyfikator o nazwie przy użyciu Konwencji: Nazwa właściwości zależności z ciągiem `Property` dołączone do niego. Na przykład odpowiednie <xref:System.Windows.DependencyProperty> pole identyfikatora dla <xref:System.Windows.Controls.Control.Background%2A> jest właściwość <xref:System.Windows.Controls.Control.BackgroundProperty>. Identyfikator przechowuje informacje dotyczące właściwości zależności, został on zarejestrowany, a identyfikator jest następnie używany później na inne operacje dotyczące właściwości zależności, takie jak wywołania <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
 Jak wspomniano w [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md), wszystkie właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (z wyjątkiem najbardziej dołączone właściwości) są również [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości z powodu wykonania "otoki". W związku z tym z kodu, można pobrać lub ustawić właściwości zależności przez wywołanie metody [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] akcesorów definiujące otoki w taki sam sposób, że używasz innych [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. Klientów właściwości ustalonych zależności nie zwykle jest używana <xref:System.Windows.DependencyObject> metody <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A>, które są punkt połączenia źródłowy system właściwości. Zamiast istniejącego wdrożenia [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości ma już wywołana <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> w `get` i `set` implementacje otoki właściwości, korzystając z pola Identyfikator odpowiednio . W przypadku wdrażania właściwości niestandardowe zależności samodzielnie, następnie będzie zdefiniowanie jest otoka w podobny sposób.  
  
<a name="backing_with_dp"></a>   
## <a name="when-should-you-implement-a-dependency-property"></a>Kiedy należy zaimplementować właściwości zależności  
 Podczas implementacji właściwości klasy, tak długo, jak pochodną klasy <xref:System.Windows.DependencyObject>, istnieje możliwość kopii z właściwości o <xref:System.Windows.DependencyProperty> identyfikator i w związku z tym dokonanie właściwości zależności. Wystąpienia użytkownika właściwości być właściwością zależności nie zawsze jest konieczne lub właściwe, zależy od potrzeb scenariusza. Czasami typowe techniki kopii programu właściwość z polem prywatnej jest odpowiedni. Jednak należy zaimplementować z właściwości jako właściwość zależności przy każdym z właściwości do obsługi co najmniej jeden z następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] możliwości:  
  
-   Chcesz, aby Twoje właściwość jako można ustawić w stylu. Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
-   Ma równą obsługuje powiązanie danych. Aby uzyskać więcej informacji na temat właściwości zależności wiązania danych zobacz [powiązanie właściwości formantów dwóch](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).  
  
-   Chcesz, aby Twoje właściwość jako można ustawić z odwołaniem zasobu dynamicznego. Aby uzyskać więcej informacji, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Użytkownik chce automatycznie dziedziczą wartość właściwości z elementu nadrzędnego w drzewie elementu. W takim przypadku Zarejestruj <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody, nawet jeśli tworzysz otokę dla właściwości [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dostępu. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Chcesz, aby Twoje właściwość jako można animować. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Podczas poprzedniej wartości właściwości został zmieniony przez akcje wykonywane przez system właściwości, środowiska lub użytkownik lub odczytywania a za pomocą stylów mają system właściwości do raportu. Przy użyciu metadanych właściwości, z właściwości można określić metody wywołania zwrotnego, które będą wywoływane zawsze, gdy system właściwość określa, że ostatecznie zmieniono wartość właściwości. Powiązane koncepcja jest koercja wartości właściwości. Aby uzyskać więcej informacji, zobacz [wywołania zwrotne właściwości zależności i sprawdzania poprawności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Chcesz użyć konwencje ustalonych metadanych, które są również używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesy, takie jak raportowanie czy zmiana wartości właściwości powinny wymagać systemu układu, aby przeskładać elementy wizualne dla elementu. Lub można było używać zastąpień metadanych, tak aby klas pochodnych można zmienić na podstawie metadanych właściwości, takie jak wartości domyślnej.  
  
-   Ma właściwości formantu niestandardowego do odbierania [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pomocy technicznej, takich jak **właściwości** okno edycji. Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Po sprawdzeniu tych scenariuszy należy również rozważyć, czy można uzyskać scenariusz Zastępowanie metadanych istniejącej właściwości zależności, zamiast wykonania całkowicie nową właściwość. Określa, czy zastąpienie metadanych jest praktyczne zależy od danego scenariusza i jak blisko tego scenariusza jest podobny do implementacji w istniejących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy i właściwości zależności. Aby uzyskać więcej informacji na temat Zastępowanie metadanych właściwości istniejącej, zobacz [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="checklist"></a>   
## <a name="checklist-for-defining-a-dependency-property"></a>Lista kontrolna dotycząca Definiowanie właściwości zależności  
 Definiowanie właściwości zależności składa się z czterech różnych pojęcia. Te pojęcia nie są zawsze strict kroki procedur, ponieważ niektóre z nich łączonych jako pojedynczy wierszy kodu w implementacji:  
  
-   (Opcjonalnie) Utwórz metadanych właściwości dla właściwości zależności.  
  
-   Zarejestruj nazwy właściwości w systemie właściwości, typ właściciela i typ wartości właściwości. Również określić metadanych właściwości, jeśli używana.  
  
-   Zdefiniuj <xref:System.Windows.DependencyProperty> identyfikator `public` `static` `readonly` na typ właściciela.  
  
-   Zdefiniuj [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości "otoki", którego nazwa odpowiada nazwie właściwości zależności. Implementowanie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości "otoki" `get` i `set` metod dostępu do nawiązywania połączenia z właściwością zależności, aby utworzyć jego kopię zapasową.  
  
<a name="registering"></a>   
### <a name="registering-the-property-with-the-property-system"></a>Rejestrowanie właściwość z systemu właściwości  
 Aby dla właściwości z właściwością zależności musisz zarejestrować tej właściwości do obsługiwanego przez system właściwości tabeli i nadaj mu unikatowy identyfikator, który jest używany jako kwalifikator dla późniejszych operacji system właściwości. Te operacje mogą być operacji wewnętrznych lub swoim własnym kodem wywoływanie właściwości systemu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Aby zarejestrować właściwość, należy wywołać <xref:System.Windows.DependencyProperty.Register%2A> metody w treści klasy (wewnątrz klasy, ale poza żadnych definicji elementu członkowskiego). Pole identyfikatora jest również udostępniany przez <xref:System.Windows.DependencyProperty.Register%2A> wywołania metody, jako wartość zwracaną. Powód który <xref:System.Windows.DependencyProperty.Register%2A> wywołania odbywa się poza innego członka definicje są ponieważ zwrócona wartość jest używany do przypisywania i utworzyć `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty> w ramach swojej klasy. To pole staje się na identyfikator sieci właściwości zależności.  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### <a name="dependency-property-name-conventions"></a>Konwencje nazw właściwości zależności  
 Brak ustalonych konwencje nazewnictwa dotyczące właściwości zależności, które należy wykonać we wszystkich ale w wyjątkowych okolicznościach.  
  
 Właściwość zależności mają nazwy podstawowej, "AquariumGraphic", jak w poniższym przykładzie, który jest podawana jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A>. Ta nazwa musi być unikatowa w przypadku każdego typu rejestracji. Właściwości zależności dziedziczone przez typy podstawowe są traktowane jako już częścią typu rejestrowania; Nie można ponownie zarejestrować nazwy właściwości dziedziczone. Istnieje jednak technika Dodawanie klasy jako właściciela właściwości zależności, nawet w przypadku danej właściwości zależności nie jest dziedziczona; Aby uzyskać więcej informacji, zobacz [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Podczas tworzenia w polu identyfikatora nazw to pole, nazwa właściwości zarejestrowanej plus sufiks `Property`. To pole jest identyfikatorem dla właściwości zależności i będzie służyć jako dane wejściowe dla później <xref:System.Windows.DependencyObject.SetValue%2A> i <xref:System.Windows.DependencyObject.GetValue%2A> wywołania zostaną wprowadzone w otoki, przez wszystkie inne kodu dostępu do właściwości w swoim własnym kodem przez kod zewnętrzny dostęp można zezwolić , przez system właściwości oraz potencjalnie przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesorów.  
  
> [!NOTE]
>  Definiowanie właściwości zależności w treści klasy jest typowa implementacja, ale jest również możliwe określenie właściwości zależności w konstruktorze statycznym klasy. Ta metoda może być uzasadnione, jeśli potrzebujesz więcej niż jeden wiersz kodu można zainicjować właściwości zależności.  
  
<a name="wrapper1"></a>   
### <a name="implementing-the-wrapper"></a>Implementowanie "Otoki"  
 Powinny wywoływać implementację programu otoki <xref:System.Windows.DependencyObject.GetValue%2A> w `get` implementacji i <xref:System.Windows.DependencyObject.SetValue%2A> w `set` implementacji (oryginalny wywołanie rejestracji i pola są wyświetlane tutaj zbyt dla jasności).  
  
 W sytuacjach wyjątkowych wszystkie elementy oprócz implementacjach użytkownika otoki należy wykonać tylko <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> akcje, odpowiednio. Przyczyną została szczegółowo opisana w temacie [ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
 Wszystkie istniejące właściwości publicznej zależności, które znajdują się na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy używać tego modelu wdrażania prostego otoki; większość złożoność działania właściwości zależności albo jest z założenia zachowanie systemu właściwości lub jest implementowane za pośrednictwem innych pojęcia, takie jak wywołania zwrotne za pośrednictwem właściwości metadanych o zmianie koercja lub właściwości.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 Ponownie przez Konwencję, nazwa właściwości otoki musi być taka sama jak nazwa, wybrana opcja i podawana jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A> wywołania zarejestrowanego właściwości. Jeśli Twoje właściwość nie jest zgodna z Konwencji, to nie zawsze wyłączyć wszystkie możliwe użycia, ale można napotkać kilka godne uwagi problemy:  
  
-   Niektórych aspektów style i szablony nie będą działać.  
  
-   Większość narzędzi i projektantów muszą polegać na konwencje nazewnictwa prawidłowo serializować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], lub w celu zapewnienia pomocy środowiska projektowego na poziomie poszczególnych właściwości.  
  
-   Bieżąca implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego całkowicie pomijany otoki i korzysta z konwencją nazewnictwa podczas przetwarzania wartości atrybutów. Aby uzyskać więcej informacji, zobacz [ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
<a name="metadata"></a>   
### <a name="property-metadata-for-a-new-dependency-property"></a>Metadane właściwości dla nowych właściwości zależności  
 Podczas rejestrowania właściwości zależności, rejestracja za pomocą właściwości systemu tworzy obiekt metadanych, który przechowuje właściwości właściwości. Wiele z tych właściwości mają wartości domyślne, które są ustawione, jeśli właściwość jest zarejestrowany w prosty sygnatur <xref:System.Windows.DependencyProperty.Register%2A>. Inne sygnatur <xref:System.Windows.DependencyProperty.Register%2A> umożliwiają określenie metadanych, które ma być zarejestrować właściwości. Najbardziej typowe metadane dla właściwości zależności jest nadanie im domyślną wartość, jaka jest stosowana na nowe wystąpienia, które należy użyć właściwości.  
  
 Podczas tworzenia właściwości zależności, który istnieje w klasie pochodnej z <xref:System.Windows.FrameworkElement>, można użyć wyspecjalizowanego klasy metadanych <xref:System.Windows.FrameworkPropertyMetadata> zamiast podstawowym <xref:System.Windows.PropertyMetadata> klasy. Konstruktor <xref:System.Windows.FrameworkPropertyMetadata> klasa ma kilka podpisów, w którym można określić różne właściwości metadanych w połączeniu. Jeśli chcesz określić wartość domyślną tylko Użyj podpisie, który przyjmuje jeden parametr typu <xref:System.Object>. Przekaż parametru obiektu jako wartość domyślną określonego typu z właściwości (podana wartość domyślna musi być typ przekazany jako `propertyType` parametru w <xref:System.Windows.DependencyProperty.Register%2A> wywołania).  
  
 Aby uzyskać <xref:System.Windows.FrameworkPropertyMetadata>, można również określić flagi opcji metadane dla właściwości użytkownika. Te flagi są konwertowane na osobne właściwości metadanych właściwości po rejestracji i są używane do komunikowania się niektórych warunków na inne procesy, takie jak aparatu układu.  
  
#### <a name="setting-appropriate-metadata-flags"></a>Ustawienie flagi odpowiednie metadane  
  
-   Jeśli właściwość (lub zmiany jego wartości) wpływa na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], i w szczególności wpływa na sposób system układu powinien rozmiaru lub renderowania, nazwę elementu na stronie ustawić co najmniej jeden z następujących flag: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> Wskazuje, że zmiana ta właściwość wymaga zmiany [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderowania, w którym obiektu zawierającego konieczność więcej lub mniej miejsca nadrzędnym. Na przykład właściwość "Width" powinien mieć ten zestaw flagi.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> Wskazuje, że zmiana ta właściwość wymaga zmiany [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderowania, które zwykle nie wymaga zmian w dedykowanym miejsca, ale wskazują, że zmieniła położenie w przestrzeni. Na przykład "Wyrównania" powinna mieć ten zestaw flagi.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> Wskazuje, że wystąpił kilka dodatkowych zmian, który nie wpłynie na układ i miary, ale wymagają innego renderowania. Przykładem może być właściwością zmienia kolor istniejącego elementu, takie jak "Tła".  
  
    -   Te flagi są często używane jako protokół w metadanych własne implementacji zastąpienie właściwości systemu lub układu wywołań zwrotnych. Na przykład może być <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> wywołania zwrotnego, które wywoła <xref:System.Windows.UIElement.InvalidateArrange%2A> żadnej właściwości wystąpienia raporty zmiany wartości i czy przypisano <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> jako `true` w metadanych.  
  
-   Niektóre właściwości może wpłynąć na charakterystykę renderowania zawierającego elementu nadrzędnego, w sposób niż zmiany w wymagany rozmiar wymienionych powyżej. Na przykład <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> właściwości używane w modelu dokumentu przepływu, której zmiany wprowadzone do tej właściwości można zmienić ogólną renderowania dokumentu przepływu, który zawiera akapitu. Użyj <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> lub <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> do identyfikowania podobnych przypadków własnych właściwości.  
  
-   Domyślnie właściwości zależności obsługuje powiązanie danych. Powiązanie danych w przypadkach, można wyłączyć celowo, jeżeli nie nie realistyczne scenariusz wiązania z danymi lub gdy wydajność w powiązaniu danych dla dużego obiektu jest rozpoznawana jako problem.  
  
-   Domyślnie powiązanie danych <xref:System.Windows.Data.Binding.Mode%2A> dla parametrów domyślnych właściwości zależności do <xref:System.Windows.Data.BindingMode.OneWay>. Zawsze można zmienić powiązanie <xref:System.Windows.Data.BindingMode.TwoWay> na wystąpienie obiektu binding; Aby uzyskać więcej informacji, zobacz [określ kierunek powiązania](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md). Ale Autor właściwości zależności, możesz wprowadzić właściwości użyj <xref:System.Windows.Data.BindingMode.TwoWay> tryb wiązania domyślnie. Na przykład z istniejącej właściwości zależności <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; scenariusz dla tej właściwości jest to, że <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> ustawienie logiki i składania kanałów z <xref:System.Windows.Controls.MenuItem> interakcji z domyślnym stylu motywu. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Logiki właściwości wykorzystuje wiązania danych natywnie do zarządzania stanem właściwości zgodnie z innych właściwości stanu i wywołania metody. Inna właściwość przykładzie, który wiąże <xref:System.Windows.Data.BindingMode.TwoWay> domyślnie jest <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.  
  
-   Dziedziczenie właściwości we właściwości niestandardowej zależności można także włączyć, ustawiając <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> flagi. Dziedziczenie właściwości jest przydatne w sytuacji, gdy elementy nadrzędne i podrzędne mają właściwość wspólną i warto dla obiekt podrzędny elementów ma tę wartość określonej właściwości ustawioną taką samą wartość jak ustawić nadrzędnego. Przykład właściwości dziedziczonych jest <xref:System.Windows.FrameworkElement.DataContext%2A>, która jest używana do wiązania operacji scenariusza ważne główny szczegółowy prezentacji danych. Tworząc <xref:System.Windows.FrameworkElement.DataContext%2A> dziedziczona, wszystkie elementy podrzędne dziedziczą tego kontekstu danych również. Ze względu na wartość dziedziczenia mogą określać kontekst danych w katalogu głównym strony lub aplikacji, a nie trzeba respecify go dla powiązania w wszystkie elementy podrzędne możliwe. <xref:System.Windows.FrameworkElement.DataContext%2A> jest również dobrym przykładem w celu zilustrowania dziedziczenia przesłaniać wartość domyślną, że można zawsze można ustawić lokalnie na dowolny element podrzędny określonego; Aby uzyskać więcej informacji, zobacz [Użyj wzorca wzorzec-szczegół z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dziedziczenie właściwości wartość ma na wydajność, możliwości i w związku z tym powinny być używane rzadko; Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Ustaw <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> flagę wskazującą, czy wykryto lub używane przez usługi rejestrowania nawigacji z właściwości zależności. Na przykład <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> właściwości; dowolnego elementu wybranego w wyborze kontroli powinny być zachowywane w przypadku historii rejestrowania jest przejście.  
  
<a name="RODP"></a>   
## <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu  
 Można zdefiniować właściwości zależności, która jest tylko do odczytu. Scenariusze dotyczące Dlaczego można zdefiniować jako tylko do odczytu z właściwości są jednak nieco inny, jak jest to procedura rejestrowania ich w systemie właściwości i udostępnianie identyfikator. Aby uzyskać więcej informacji, zobacz [tylko do odczytu właściwości zależności](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
<a name="CTDP"></a>   
## <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji  
 Typ kolekcji właściwości zależności mają niektórych problemów z implementacją dodatkowe wziąć pod uwagę. Aby uzyskać więcej informacji, zobacz [właściwości zależności typu kolekcji](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md).  
  
<a name="SecurityC"></a>   
## <a name="dependency-property-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń właściwości zależności  
 Właściwości zależności powinien być zadeklarowany jako publiczny właściwości. Pola identyfikatora właściwości zależności powinien być zadeklarowany jako publiczny pola statyczne. Nawet jeśli spróbujesz zadeklarować inne poziomy dostępu (takich jak chroniony), właściwości zależności można uzyskać za pomocą identyfikatora w połączeniu z systemu właściwości [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Nawet pola Identyfikator chronionego jest potencjalnie niedostępny z powodu oznaczenia metadanych raportowania lub wartość [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] będących częścią właściwości systemu, takich jak <xref:System.Windows.LocalValueEnumerator>. Aby uzyskać więcej informacji, zobacz [zabezpieczeń właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
<a name="DPCtor"></a>   
## <a name="dependency-properties-and-class-constructors"></a>Właściwości zależności i konstruktorów klas  
 Brak zasadniczo w programowaniu kodu zarządzanego (często wymuszane przez narzędzi analizy kodu, takie jak FxCop), która klasa konstruktorów nie powinny wywoływać metody wirtualne. To dlatego konstruktorów można wywołać jako podstawowy inicjowania konstruktora klasy pochodnej i wprowadzania metody wirtualnej za pomocą konstruktora może wystąpić w stanie inicjowania niekompletne budowany wystąpienia obiektu. Jeśli pochodzi z dowolną klasę pochodzącą z <xref:System.Windows.DependencyObject>, należy zwrócić uwagę, że system właściwości wywołuje i udostępnia metody wirtualnej wewnętrznie. Te metody wirtualne są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości usług systemowych. Zastępowanie metody umożliwia klas pochodnych brać udziału w określenie wartości. Aby uniknąć potencjalnych problemów z inicjowania w czasie wykonywania, nie należy ustawiać zależności wartości właściwości konstruktorów klas, chyba że zostaną wykonane wzorzec bardzo specyficznego konstruktora. Aby uzyskać więcej informacji, zobacz [bezpieczne wzorce konstruktora dla DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Tworzenie kontrolek — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Właściwości zależności typu kolekcji](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Zabezpieczenia właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [Ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)  
 [Bezpieczne wzorce konstruktora dla obiektów DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
