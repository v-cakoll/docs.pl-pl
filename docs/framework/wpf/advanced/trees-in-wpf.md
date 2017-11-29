---
title: Drzewa w WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56237bccb2bf61994c6114fa01d15c254267ca20
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="trees-in-wpf"></a>Drzewa w WPF
W wielu technologii elementów i składniki są zorganizowane w strukturze drzewa, której deweloperzy bezpośrednio modyfikowania obiektu węzłów w drzewie do renderowania lub zachowanie aplikacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]do zdefiniowania relacji między elementami program używa również kilka metafory struktury drzewa. W większości przypadków WPF deweloperów można utworzyć aplikację w kodzie lub zdefiniuj części aplikacji w języku XAML podczas planowania koncepcyjnie metaphor drzewa obiektu, ale będzie można wywoływanie interfejsu API lub za pomocą oznaczenia celu tak zamiast niektóre ogólne manipulowanie obiektem drzewa interfejsu API np. Możesz użyć w XML modelu DOM. WPF udostępnia dwie klasy pomocy zapewniające widoku drzewa metaphor <xref:System.Windows.LogicalTreeHelper> i <xref:System.Windows.Media.VisualTreeHelper>. Warunki drzewa wizualnego i drzewa logicznego są również używane w dokumentacji programu WPF ponieważ drzewa tego samego te są przydatne w przypadku poznanie zachowania niektóre najważniejsze funkcje WPF. W tym temacie definiuje, jakie reprezentują drzewa wizualnego i drzewa logicznego omówiono powiązań takich drzewa w ogólnej koncepcji drzewa obiektów i wprowadza <xref:System.Windows.LogicalTreeHelper> i <xref:System.Windows.Media.VisualTreeHelper>s.  
  

  
<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>Drzewa w WPF  
 Najbardziej kompleksowe struktury drzewa w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest drzewa obiektów. W przypadku definiowania strony aplikacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , a następnie załadować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], struktura drzewa jest tworzone w oparciu zagnieżdżenia relacje elementów w znaczniku. Jeśli zdefiniujesz aplikacji lub części aplikacji w kodzie, a następnie struktura drzewa jest tworzony oparte na sposób przypisywania wartości właściwości dla właściwości, które implementują modelu zawartości dla danego obiektu. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], istnieją dwa sposoby, które drzewo cały obiekt jest conceptualized i mogą być zgłaszane do jego publiczny interfejs API: jako drzewa logicznego, a drzewa wizualnego. Różnice między drzewa logicznego i drzewa wizualnego nie zawsze są zawsze ważne, ale czasami mogą powodować problemy z niektórymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystemów i wpłynąć na wybór w znaczników lub kod.  
  
 Chociaż nie zawsze manipulować drzewa logicznego lub drzewa wizualnego bezpośrednio, zrozumienie pojęcia interakcje drzewa jest przydatne w przypadku opis WPF jako technologia. Myśląc WPF metaphor drzewa, pewnego rodzaju również jest niezwykle istotne dla zrozumienia, jak działają dziedziczenie właściwości i zdarzenia routingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
> [!NOTE]
>  Drzewa obiektów jest więcej koncepcji niż rzeczywista interfejsu API, można wziąć pod uwagę pojęcia w inny sposób i dlatego jako wykres obiektu. W praktyce istnieją relacje między obiektami w czasie wykonywania, gdzie będzie rozbicie metaphor drzewa. Niemniej jednak zwłaszcza w przypadku interfejsu użytkownika zdefiniowane w języku XAML, metaphor drzewa ma zastosowanie wystarczająco większość dokumentacji WPF użyje drzewa obiektów termin podczas odwoływania się do tej reguły ogólne.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>Drzewie logicznym  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dodać zawartości do elementów interfejsu użytkownika przez ustawienie właściwości obiektów, które wykonują kopie tych elementów. Na przykład dodać elementy do <xref:System.Windows.Controls.ListBox> kontroli manipulowanie jego <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości. Dzięki temu umieszcza się elementy do <xref:System.Windows.Controls.ItemCollection> czyli <xref:System.Windows.Controls.ItemsControl.Items%2A> wartości właściwości. Podobnie, aby dodać obiekty do <xref:System.Windows.Controls.DockPanel>, manipulować jego <xref:System.Windows.Controls.Panel.Children%2A> wartości właściwości. W tym miejscu są Dodawanie obiektów do <xref:System.Windows.Controls.UIElementCollection>. Na przykład kod, zobacz [Dodaj Element dynamicznie](http://msdn.microsoft.com/en-us/d00f258a-7973-4de7-bc54-a3fc1f638419).  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], po umieszczeniu elementów listy w <xref:System.Windows.Controls.ListBox> lub formanty lub inne elementy interfejsu użytkownika w <xref:System.Windows.Controls.DockPanel>, możesz również użyć <xref:System.Windows.Controls.ItemsControl.Items%2A> i <xref:System.Windows.Controls.Panel.Children%2A> właściwości, jawnie lub niejawnie, jak w poniższym przykładzie.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Jeśli zostały do przetworzenia tego XAML jako XML w modelu obiektu dokumentu, i jeśli były uwzględniane tagi oznaczone jako out jako niejawne (który byłby prawne), a następnie drzewie XML DOM wynikowy będzie uwzględnione elementy dla `<ListBox.Items>` i inne niejawne elementy. Ale XAML nie przetwarza w ten sposób, gdy znaczników do odczytu i zapisu do obiektów, wynikowy wykres obiektu nie ma dosłownie `ListBox.Items`. Jednak mieć <xref:System.Windows.Controls.ListBox> właściwości o nazwie `Items` zawierający <xref:System.Windows.Controls.ItemCollection>oraz że <xref:System.Windows.Controls.ItemCollection> został zainicjowany, ale pusta, gdy <xref:System.Windows.Controls.ListBox> XAML jest przetwarzany. Następnie każdy obiekt element podrzędny, która istnieje jako zawartość dla <xref:System.Windows.Controls.ListBox> jest dodawany do <xref:System.Windows.Controls.ItemCollection> wywołań analizator `ItemCollection.Add`. Ten przykład przetwarzania XAML do drzewa obiektów do tej pory pozornie przykładem jest gdzie drzewa utworzony obiekt jest zasadniczo drzewa logicznego.  
  
 Drzewa logicznego nie jest jednak wykresu cały obiekt, który nie istnieje dla aplikacji, które interfejsu użytkownika w czasie wykonywania, nawet w przypadku elementy składni niejawne XAML wzięciu pod uwagę limit. Główną przyczyną tego jest elementów wizualnych i szablony. Rozważmy na przykład <xref:System.Windows.Controls.Button>. Raporty drzewa logicznego <xref:System.Windows.Controls.Button> obiektu, a także parametrach `Content`. Występuje więcej na ten przycisk, w drzewie obiektów czasu wykonywania. W szczególności przycisku jest wyświetlany tylko na ekranie sposób tak, ponieważ określony <xref:System.Windows.Controls.Button> stosowania kontroli szablonu. Elementy wizualne, które pochodzą z zastosowanego szablonu (takie jak szablon zdefiniowany <xref:System.Windows.Controls.Border> ciemny szarości wokół przycisku visual) nie są zgłaszane w drzewie logicznym, nawet jeśli przeglądasz drzewa logicznego w czasie wykonywania (takich jak Obsługa wprowadzania zdarzenie z widoczne interfejsu użytkownika, a następnie odczytując drzewa logicznego). Aby znaleźć elementy wizualne szablonu, zamiast tego należy zbadać drzewa wizualnego.  
  
 Aby uzyskać więcej informacji o tym, jak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mapy składni utworzony obiekt Wykres i Składnia niejawna w języku XAML, zobacz [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) lub [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>Celem drzewie logicznym  
 Tak, aby zawartości modeli można łatwo przejść przez ich obiektów podrzędnych możliwe i aby umożliwić modeli zawartości określonych extensible istnieje drzewa logicznego. Ponadto drzewa logicznego zapewnia platformę dla niektórych powiadomień, takie jak kiedy są ładowane wszystkich obiektów w drzewie logicznym. Zasadniczo drzewa logicznego jest przybliżeniem wykres obiektu czas wykonywania na poziomie framework, co wyklucza elementy wizualne, ale jest odpowiednia dla wielu operacji podczas badania przed kompozycji własnej aplikacji czasie wykonywania.  
  
 Ponadto odwołania do obu statycznych i dynamicznych zasobów są rozwiązywane przeglądając górę drzewa logicznego dla <xref:System.Windows.FrameworkElement.Resources%2A> kolekcje w początkowej obiektu żądającego, a następnie kontynuowanie w górę drzewa logicznego i sprawdzania każdego <xref:System.Windows.FrameworkElement> (lub <xref:System.Windows.FrameworkContentElement>) dla innej `Resources` wartości, która zawiera <xref:System.Windows.ResourceDictionary>, prawdopodobnie zawierającej tego klucza. Drzewa logicznego służy do wyszukiwania zasobów, gdy istnieją zarówno w drzewie logicznym, jak i w drzewie wizualnym. Aby uzyskać więcej informacji na słownikach zasobów i wyszukiwania, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Kompozycja drzewie logicznym  
 Drzewa logicznego jest zdefiniowana na poziomie WPF framework, co oznacza, że element base WPF najbardziej odpowiedniego dla operacji drzewa logicznego jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Jednak jako możesz zobaczyć faktycznie użycie <xref:System.Windows.LogicalTreeHelper> interfejsu API, drzewa logicznego czasami zawiera węzły, które nie są albo <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Na przykład raporty drzewa logicznego <xref:System.Windows.Controls.TextBlock.Text%2A> wartość <xref:System.Windows.Controls.TextBlock>, który jest ciągiem.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Zastępowanie drzewie logicznym  
 Autorzy formantu zaawansowanego można zastąpić drzewa logicznego przez zastąpienie kilka [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] definiującą jak ogólne obiektów lub modelu zawartości dodaje lub usuwa obiektów w drzewie logicznym. Na przykład sposobu zastąpienia drzewa logicznego zobacz [zastąpienia drzewa logicznego](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Przejęcie wartości właściwości  
 Dziedziczenie właściwości wartość działa za pośrednictwem drzewa hybrydowego. Rzeczywiste metadanych, które zawiera <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> właściwość, która umożliwia dziedziczenia jest WPF poziomie struktury <xref:System.Windows.FrameworkPropertyMetadata> klasy. W związku z tym zarówno nadrzędnego, który przechowuje oryginalnej wartości i obiekt podrzędny, która dziedziczy tej wartości muszą być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, i muszą one jednocześnie być częścią niektórych drzewa logicznego. Jednak dla istniejącej właściwości WPF, które obsługuje dziedziczenia, dziedziczenie wartość właściwości jest w stanie widoczny przy obsłudze często za pośrednictwem pośredniczące obiektu, który nie znajduje się w drzewie logicznym. Przede wszystkim jest istotne, występowania elementów szablonu, użyj wartości właściwości dziedziczone ustawiać albo wystąpienia, które jest szablonem lub na nadal wyższego poziomu z poziomu strony kompozycji i w związku z tym wyżej w drzewie logicznym. Aby dziedziczenie wartości właściwości do działać spójnie takie granicy właściwości dziedziczących musi zostać zarejestrowany jako dołączona właściwość, a tego wzorca należy wykonać, jeśli zamierzasz zdefiniować właściwości niestandardowe zależności z właściwością zachowanie dziedziczenia. Dokładne drzewa, używany do dziedziczenia właściwości nie można całkowicie oczekiwać przez metodę pomocnika klasy narzędzie nawet w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>Drzewa wizualnego  
 Oprócz koncepcji drzewa logicznego jest również pojęcie drzewo wizualne w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Drzewa wizualnego opisuje strukturę obiektów visual reprezentowany przez <xref:System.Windows.Media.Visual> klasy podstawowej. Podczas pisania szablonu dla formantu są Definiowanie lub ponowne definiowanie drzewa wizualnego, która ma zastosowanie do tego formantu. Drzewa wizualnego jest również przydatne dla deweloperów, którzy chcą niższego poziomu kontrolę nad rysunku ze względu na wydajność i optymalizacji. Jeden narażenia drzewa wizualnego w ramach konwencjonalnej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania aplikacji jest, że trasy zdarzenia dla kierowanego zdarzenia przede wszystkim przenoszone wraz z drzewa wizualnego drzewa logicznego. To subtlety zachowanie kierowanego zdarzenia może nie być oczywista, chyba że autor kontroli. Routing za pośrednictwem drzewa wizualnego zdarzenia umożliwia formantach, które implementują kompozycji na poziomie visual obsługi zdarzeń lub utworzyć zdarzenia setters.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>Drzewa, elementy zawartości i hosty zawartości  
 Elementy zawartości (klasy, które pochodzą z <xref:System.Windows.ContentElement>) nie są częścią drzewa wizualnego; nie dziedziczą z <xref:System.Windows.Media.Visual> i nie mają wizualnej reprezentacji. Aby można było wyświetlana w Interfejsie gwarancja, <xref:System.Windows.ContentElement> musi być obsługiwana przez hosta zawartości, który jest jednocześnie <xref:System.Windows.Media.Visual> i uczestnika drzewa logicznego. Zazwyczaj taki obiekt jest <xref:System.Windows.FrameworkElement>. Można conceptualize, że host zawartości jest nieco takich jak "przeglądarki" dla zawartości i wybierze w sposób wyświetlania tej zawartości w obrębie regionu ekranu, która kontroluje hosta. W przypadku hostowana jest zawartość, zawartość można zapewnić uczestnika w konkretnych procesach drzewa, które są zwykle skojarzone z drzewa wizualnego. Ogólnie rzecz biorąc <xref:System.Windows.FrameworkElement> klasy obsługującej zawiera kod implementacji, który dodaje wszelkie hostowanej <xref:System.Windows.ContentElement> do trasy zdarzenia za pośrednictwem węzły podrzędne drzewa logicznego zawartości, mimo że hostowana zawartość nie jest częścią drzewa wizualnego wartość true. Jest to konieczne, aby <xref:System.Windows.ContentElement> może pobierać kierowanego zdarzenia, który kieruje do dowolnego elementu innego niż sam.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Przechodzenie drzewa  
 <xref:System.Windows.LogicalTreeHelper> Klasa udostępnia <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>, i <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> metody przechodzenia drzewa logicznego. W większości przypadków, nie trzeba przechodzenia drzewa logicznego istniejących formantów, ponieważ prawie zawsze tych kontrolek uwidocznić ich elementów potomnych logicznej jako właściwość dedykowanych kolekcji, która obsługuje dostęp kolekcji, takie jak `Add`, indeksatora i tak dalej. Przechodzenie drzewa jest głównie scenariusz, w którym jest używany przez formant autorami wybrać nie pochodzi od wzorce kontrolnych, takich jak <xref:System.Windows.Controls.ItemsControl> lub <xref:System.Windows.Controls.Panel> gdzie są już zdefiniowane właściwości kolekcji i którzy mają zamiar podać własne kolekcji Obsługa właściwości.  
  
 Drzewa wizualnego obsługuje również Klasa pomocy dla operacji przechodzenia drzewa wizualnego, <xref:System.Windows.Media.VisualTreeHelper>. Drzewa wizualnego nie jest uwidaczniana jako wygodny sposób za pomocą właściwości specyficzne dla formantu, więc <xref:System.Windows.Media.VisualTreeHelper> klasy jest zalecanym sposobem przechodzenia drzewa wizualnego, jeżeli jest to konieczne w przypadku danego scenariusza programowania. Aby uzyskać więcej informacji, zobacz [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
>  Czasami jest niezbędne do sprawdzenia szablonu zastosowane w drzewie wizualnym. Należy zachować ostrożność, korzystając z tej metody. Nawet jeśli są przechodzenie drzewie wizualnym kontrolki, gdzie należy zdefiniować szablon, konsumentów formantu zawsze można zmienić szablonu przez ustawienie <xref:System.Windows.Controls.Control.Template%2A> właściwości wystąpienia, a nawet użytkownik końcowy może mieć wpływ szablonu zastosowane, zmieniając motyw systemu.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>Trasy dla kierowane zdarzenia jako "Drzewa"  
 Jak wspomniano wcześniej, trasy danego zdarzenia routingiem porusza się na ścieżce jedno- i ustalonej drzewa, który jest hybrydowego reprezentacje drzewa wizualnego i logicznych. Trasy zdarzenia mogą być przesyłane w górę lub w dół instrukcjami w obrębie drzewa w zależności od tego, czy jest tunelowania lub propagacji kierowane zdarzenia. Pojęcie trasy zdarzeń nie ma obsługi bezpośrednio Klasa pomocy, która może służyć do "objaśniono" trasy zdarzenia niezależnie od wywoływanie zdarzeń, które faktycznie kieruje. Istnieje klasa, która reprezentuje trasy, <xref:System.Windows.EventRoute>, ale metody tej klasy są zwykle tylko do użytku wewnętrznego.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Słownikach zasobów i drzewa.  
 Wyszukiwania słownika zasobów dla wszystkich `Resources` zdefiniowane na stronie są przesyłane za pośrednictwem zasadniczo drzewa logicznego. Obiekty, które nie znajdują się w drzewie logicznym może odwoływać się kluczem zasobów, ale sekwencji wyszukiwania zasobów zaczyna się od punktu, w której dany obiekt jest podłączona do drzewa logicznego. Na platformie WPF, może mieć tylko węzły drzewa logicznego `Resources` właściwość, która zawiera <xref:System.Windows.ResourceDictionary>, dlatego nie przynosi żadnej w przechodzących przez wyszukiwanie kluczem zasobów z drzewa wizualnego <xref:System.Windows.ResourceDictionary>.  
  
 Jednak wyszukiwania zasobów można rozszerzać poza natychmiastowego drzewa logicznego. Dla znaczników aplikacji wyszukiwania zasobów można następnie nadal ponownego udostępnienia słowniki zasobów na poziomie aplikacji, a następnie wartości pomocy technicznej i systemu motywu, które są używane jako właściwości statycznej lub kluczy. Kompozycje, same można także odwoływać systemu wartości spoza drzewa logicznego motywu, jeśli odwołania do zasobów są dynamiczne. Aby uzyskać więcej informacji na słownikach zasobów i logika wyszukiwania, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dane wejściowe — omówienie](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Omówienie kierowane zdarzenia](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Inicjowanie dla obiekt elementy nie znajduje się w drzewie obiektu](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
