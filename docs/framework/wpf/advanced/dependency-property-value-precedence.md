---
title: Następstwo zależności wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 7719c39c82b69421477cadf9ae5caf9f9f55b457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-property-value-precedence"></a>Następstwo zależności wartości właściwości
<a name="introduction"></a> W tym temacie opisano sposób działaniem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system właściwości mogą mieć wpływ na wartość właściwości zależności oraz opis pierwszeństwa, przez które aspektów właściwości systemu dotyczą wprowadzenia wartości właściwości.  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono zrozumieć właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas i przeczytanie [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Aby użyć przykłady w tym temacie, należy również zapoznać się [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>System właściwości WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Właściwość system oferuje zaawansowane metody mają wartość właściwości zależności będzie określany przez różnych czynników, włączenie funkcji, takich jak sprawdzanie poprawności właściwości w czasie rzeczywistym, późne wiązanie i powiadamiania powiązane właściwości zmiany wartości dla innych właściwości. Dokładne kolejności i logiki, który służy do określania wartości właściwości zależności jest rozsądnych złożone. To zamówienie pomóc w uniknięciu ustawienie właściwości niepotrzebnych i może również wyczyszczone pomyłek za pośrednictwem dokładnie Dlaczego niektóre próba wpływ lub przewiduje się wartość właściwości zależności nie zakończył się co do wartości, które miały.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Właściwości zależności może być "Set" w kilku miejscach  
 Poniżej przedstawiono przykład [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gdzie tę samą właściwość (<xref:System.Windows.Controls.Control.Background%2A>) ma trzy różne "set" operacje, które mogą mieć wpływ na wartość.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 W tym miejscu kolor spodziewasz zastosuje — czerwony, zielony lub niebieski?  
  
 Z wyjątkiem animowany wartości i wymuszenia zestawy lokalne właściwości są ustawione na najwyższy priorytet. Jeśli ustawisz wartość lokalnie można oczekiwać, że wartość będą honorowane, nawet powyżej wszystkie style lub szablony formantu. Tutaj w tym przykładzie <xref:System.Windows.Controls.Control.Background%2A> jest ustawiona na czerwony lokalnie. W związku z tym style zdefiniowane w tym zakresie, nawet jeśli komputer jest niejawne stylu, które w przeciwnym razie powinna zostać zastosowana do wszystkich elementów tego typu w tym zakresie nie jest najwyższym priorytecie do udzielania <xref:System.Windows.Controls.Control.Background%2A> właściwości jego wartość.  Jeśli wartości lokalnej czerwonego zostały usunięte z tego wystąpienia przycisk, styl będzie mieć pierwszeństwo i przycisk uzyskać wartość tła z stylu.  W obrębie stylu wyzwalaczy mają pierwszeństwo, dlatego ten przycisk jest blue, gdy wskaźnik myszy znajduje się nad nim, a na zielono w przeciwnym razie wartość.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Lista pierwszeństwo ustawienie właściwości zależności  
 Poniżej przedstawiono kolejność ostateczne używanym przez system właściwości podczas przypisywania wartości czasu wykonywania właściwości zależności. Najwyższy priorytet jest wyświetlana na początku listy. Tej listy rozwijane dla niektórych generalizacji w [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
1.  **Właściwość koercja systemu.** Aby uzyskać szczegółowe informacje na koercja, zobacz [koercja, animacji i wartość Base](#animations) dalszej części tego tematu.  
  
2.  **Active animacje lub animacje z zachowaniem blokady.** Aby wpływają praktyczne, animacji właściwość musi mieć możliwość mają pierwszeństwo przed wartości podstawowej (unanimated), nawet wtedy, gdy ta wartość została ustawiona lokalnie. Aby uzyskać więcej informacji, zobacz [koercja, animacji i wartość Base](#animations) dalszej części tego tematu.  
  
3.  **Wartości lokalnej.** Wartości lokalnej może być ustawiony za pomocą wygody właściwości "otoki", która również jest równa ustawienie jako elementu lub atrybutu właściwości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], lub przez wywołanie do <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] przy użyciu właściwości określonego wystąpienia. Jeśli ustawisz wartość lokalnego za pomocą powiązania lub zasób te każdego działania w pierwszeństwo tak, jakby bezpośredniego wartość została ustawiona.  
  
4.  **Właściwości szablonu TemplatedParent.** Element ma <xref:System.Windows.FrameworkElement.TemplatedParent%2A> Jeśli został on utworzony w ramach szablonu ( <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.DataTemplate>). Aby uzyskać szczegółowe informacje na kiedy ma to zastosowanie, zobacz [TemplatedParent](#templatedparent) dalszej części tego tematu. W szablonie dotyczy następującej kolejności:  
  
    1.  Wyzwala z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu.  
  
    2.  Zestawy właściwości (zazwyczaj za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów) w <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu.  
  
5.  **Niejawne styl.** Dotyczy tylko `Style` właściwości. `Style` Właściwości jest wypełniony przez dowolnego zasobu styl klucz, który jest zgodny z typem tego elementu. Ten zasób stylu musi istnieć w strony lub aplikacji; Wyszukiwanie zasobów niejawne stylu nie przebiega w kompozycji.  
  
6.  **Wyzwalacze w stylu.** Wyzwalacze w ramach stylów ze strony lub aplikacji (te style może być jawnych ani niejawnych style, ale nie z domyślne style, które mieć niższego pierwszeństwa).  
  
7.  **Wyzwalacze szablonu.** Dowolny wyzwalacz z szablonu w stylu lub bezpośrednio zastosowanego szablonu.  
  
8.  **Style setters.** Wartości z <xref:System.Windows.Setter> w ramach stylów ze strony lub aplikacji.  
  
9. **Styl domyślny (motywu).** Szczegółowe informacje o Jeśli ma to zastosowanie, i jak style kompozycji dotyczą szablonów w ramach stylów motywu, zobacz [(motywu) domyślne style](#themestyles) dalszej części tego tematu. W stylu domyślnym dotyczy następującej kolejności:  
  
    1.  Aktywne Wyzwalacze w stylu motywu.  
  
    2.  Metody ustawiające w stylu motywu.  
  
10. **Dziedziczenie.** Kilka właściwości zależności dziedziczy wartości elementu nadrzędnego do elementów podrzędnych, tak, aby nie wymagają można ustawić specjalnie dla każdego elementu w całej aplikacji. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
11. **Wartość domyślna z metadanych właściwości zależności.** Wszelkie danej właściwości zależności może mieć wartości domyślnej, zgodnie z ustaleniami rejestracji systemu właściwości tej konkretnej właściwości. Ponadto klasy pochodne, które dziedziczą właściwości zależności dostępna opcja zastąpienie tych metadanych (łącznie z wartością domyślną) na podstawie-type. Zobacz [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) Aby uzyskać więcej informacji. Ponieważ dziedziczenia jest sprawdzany przed wartość domyślna to właściwość dziedziczona wartość domyślną element nadrzędny ma pierwszeństwo przed elementu podrzędnego.  W związku z tym jeśli właściwości dziedziczone nie ustawiono dowolnego miejsca, a wartość domyślna elementu podrzędnego zostanie użyta domyślna wartość określonego w katalogu głównym lub nadrzędnej.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako element pierwszeństwo nie ma zastosowania do żadnej właściwości elementu Zadeklaruj bezpośrednio w znaczniku standardowej aplikacji. Istnieje pojęcie TemplatedParent tylko dla elementów podrzędnych w drzewie wizualnym przychodzące na istnienie za pośrednictwem aplikacji szablonu. Podczas wyszukiwania system właściwości <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu dla wartości, jego wyszukuje szablonu służącego do utworzenia tego elementu. Właściwość wartości z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu zazwyczaj działa tak, jakby ich stan został ustawiony jako wartości lokalnej na element podrzędny, ale nie istnieje tego niższego pierwszeństwa i wartości lokalnej, ponieważ szablony są potencjalnie udostępnione. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Właściwości stylu  
 Kolejność wyszukiwania opisanych wcześniej ma zastosowanie do wszystkich możliwych zależności właściwości z wyjątkiem jednego: <xref:System.Windows.FrameworkElement.Style%2A> właściwości. <xref:System.Windows.FrameworkElement.Style%2A> Właściwości jest unikatowy w tym go nie może sam być stylem, więc elementy pierwszeństwo 5 – 8 nie są stosowane. Ponadto animacji albo coercing — <xref:System.Windows.FrameworkElement.Style%2A> nie jest zalecane (i animowanie <xref:System.Windows.FrameworkElement.Style%2A> wymagają animacji niestandardowej klasy). Spowoduje to pozostawienie trzy sposoby który <xref:System.Windows.FrameworkElement.Style%2A> może być ustawiona właściwość:  
  
-   **Jawne styl.** <xref:System.Windows.FrameworkElement.Style%2A> Bezpośrednio ustawiono właściwość. W większości przypadków styl nie zdefiniowano w tekście, ale zamiast tego odwołuje się jako zasób, jawne klucza. W takim przypadku samej właściwości stylu zachowuje się tak, jakby była wartość lokalnego elementu pierwszeństwo 3.  
  
-   **Niejawne styl.** <xref:System.Windows.FrameworkElement.Style%2A> Nie ustawiono właściwości bezpośrednio. Jednak <xref:System.Windows.FrameworkElement.Style%2A> istnieje na określonym poziomie w sekwencji wyszukiwania zasobów (strony, aplikacji) i jest kluczem zasobu, który jest zgodny z typem styl ma być stosowany do korzystającym. W takim przypadku <xref:System.Windows.FrameworkElement.Style%2A> samej właściwości działa przez pierwszeństwa zidentyfikowany w sekwencji jako element 5. Ten warunek może zostać wykryte przy użyciu przy użyciu <xref:System.Windows.DependencyPropertyHelper> przed <xref:System.Windows.FrameworkElement.Style%2A> właściwości i wyszukując <xref:System.Windows.BaseValueSource.ImplicitStyleReference> w wynikach.  
  
-   **Domyślny styl**, znanej także jako **stylów motywu.** <xref:System.Windows.FrameworkElement.Style%2A> Właściwości nie ustawiono bezpośrednio, a w rzeczywistości zostanie odczytany jako `null` do uruchomienia. W takim przypadku styl pochodzi z oceny motyw środowiska wykonawczego, który jest częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparat prezentacji.  
  
 Niejawne style nie w kompozycji, typ musi odpowiadać dokładnie — `MyButton``Button`— Klasa pochodna nie użyje niejawnie styl `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Style domyślne (motywu)  
 Każdego formantu, który jest dostarczany z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma domyślny styl. Czy domyślny styl potencjalnie jest zależna od motywu, który jest Dlaczego ten styl domyślny jest czasami określane jako styl motywu.  
  
 Najważniejsze informacje, która znajduje się w stylu domyślnym dla formantu jest jego szablonu formantu, który istnieje w stylu motywu jako metoda ustawiająca dla jego <xref:System.Windows.Controls.Control.Template%2A> właściwości. Jeśli nie było żadnych szablonu z domyślnych stylów, kontroli bez szablonu niestandardowego jako część styl niestandardowy może nie mieć Brak wygląd w. Szablonu z domyślnym stylu daje wygląd każdej kontrolki podstawowej struktury i definiuje także połączenia między właściwości zdefiniowane w drzewie wizualnym szablonu i odpowiedniej klasy formantu. Każdej kontrolki przedstawia zbiór właściwości, które mogą mieć wpływ wygląd formantu bez całkowicie zastępowania szablonu. Rozważmy na przykład domyślny wygląd <xref:System.Windows.Controls.Primitives.Thumb> formant, który jest składnikiem programu <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> ma niektórych właściwości można dostosować. Domyślny szablon <xref:System.Windows.Controls.Primitives.Thumb> tworzy podstawową strukturę / zagnieżdżone drzewo wizualne z kilku <xref:System.Windows.Controls.Border> składniki, aby utworzyć wygląd fazy. Jeśli właściwość, która jest częścią szablonu ma być udostępniane dla możliwości dostosowywania <xref:System.Windows.Controls.Primitives.Thumb> klasy, a następnie tej właściwości musi być wystawiony przez [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), w szablonie. W przypadku liczby <xref:System.Windows.Controls.Primitives.Thumb>, takich jak udostępniać różne właściwości tych granic powiązanie szablonu z właściwości <xref:System.Windows.Controls.Border.Background%2A> lub <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ale niektórych właściwości lub visual uzgodnienia są zakodowane na stałe w kontroli szablonu lub są powiązane z wartości, które pochodzi bezpośrednio z motywu i nie można zmienić zastępuje całą szablonu. Ogólnie rzecz biorąc Jeśli właściwość pochodzi z szablonem nadrzędnego i nie jest udostępniana przez powiązanie szablonu, nie można dostosować przez style ponieważ nie ma łatwego sposobu na stosowanie ich. Jednak nadal mieć wpływ tej właściwości, dziedziczenie wartości właściwości szablonu zastosowane lub wartości domyślnej.  
  
 Style kompozycji Użyj typu jako klucz w ich definicje. Jednak kompozycji są stosowane do wystąpienia danego elementu, kompozycje wyszukiwania dla tego typu jest wykonywane przez sprawdzanie <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> właściwości w formancie. Dzięki temu nie trzeba przy użyciu literału typu w sposób niejawny style. Wartość <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> odziedziczenie dla klasy pochodnej, nawet jeśli implementujący nie została zmieniona jego (zamierzonego sposobu zmiany właściwości nie ma zastąpić na poziomie właściwości, ale aby zamiast tego zmiany domyślnej wartości w metadanych właściwości). Tego operatora pośredniego włącza klas podstawowych do definiowania stylów motywu elementy pochodne, które w przeciwnym razie nie mają stylu (lub co ważniejsze, nie ma szablonu w stylu i czy w związku z tym nie mieć Brak wygląd domyślny co). W związku z tym mogą pochodzić `MyButton` z <xref:System.Windows.Controls.Button> i będą nadal otrzymywać <xref:System.Windows.Controls.Button> szablon domyślny. Jeśli zostały Autor kontroli `MyButton` i chce inaczej, można zastąpić metadanych właściwości zależności dla <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> na `MyButton` aby zwrócić inny klucz, a następnie zdefiniuj style kompozycji istotne, łącznie z szablonu dla `MyButton` który należy spakować z Twojej `MyButton` formantu. Więcej szczegółów na kompozycje, style i tworzenia kontrolki, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Odwołania do zasobów dynamicznych i powiązania  
 Powiązanie operacji i odwołania do zasobów dynamicznej przestrzegać pierwszeństwo lokalizacji, w którym są ustawione. Na przykład zasobu dynamicznego stosowane do wartości lokalnych działa na element pierwszeństwo 3, powiązania dla określonej metody ustawiającej w stylu motywu zastosuje w pozycji pierwszeństwo 9 i tak dalej. Ponieważ odwołania do zasobów dynamicznych i powiązanie być może uzyskać wartości z stan uruchomienia aplikacji, dzięki temu, że rzeczywisty proces określania pierwszeństwo wartości właściwości dla dowolnej właściwości danego rozszerza w czasie wykonywania.  
  
 Odwołania do zasobów dynamiczne nie są mówiąc ściślej częścią właściwości systemu, ale mają kolejność wyszukiwania własnych, która współdziała z sekwencji wymienionych powyżej. Pierwszeństwo tego opisano dokładniej w [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md). Jest podstawowy podsumowanie tego pierwszeństwo: element główny strony, aplikacji, motywu, system.  
  
 Dynamiczne zasobów i powiązania mają pierwszeństwo gdzie zostały ustawione, ale wartość została odroczona. W wyniku tego jest to, że jeśli ustawisz zasobu dynamicznego lub powiązanie z wartości lokalnej, każda zmiana wartości lokalnej zastępuje zasobu dynamicznego lub całkowicie powiązania. Nawet jeśli wywołujesz <xref:System.Windows.DependencyObject.ClearValue%2A> metodę, aby wyczyścić lokalnie ustawiony wartość, zasobu dynamicznego lub powiązanie nie zostanie przywrócony. W rzeczywistości, jeśli wywołujesz <xref:System.Windows.DependencyObject.ClearValue%2A> dla właściwości, która ma powiązania lub zasobu dynamicznego w miejscu (nie literał lokalnych), są usuwane przez <xref:System.Windows.DependencyObject.ClearValue%2A> zbyt wywołania.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Jest inny sposób ustawiania właściwości, ale nie jest w kolejności priorytetu. Zamiast tego <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umożliwia zmianę wartości właściwości bez zastępowania źródło poprzedniej wartości. Można użyć <xref:System.Windows.DependencyObject.SetCurrentValue%2A> za każdym razem, aby ustawić wartość bez nadawania tej wartości priorytetu wartości lokalnej. Na przykład, jeśli właściwość jest ustawiony przez wyzwalacz, a następnie przypisać inną wartością za pomocą <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, system właściwość nadal szanuje wyzwalacza i właściwość ulegnie zmianie, jeśli zaistnieje akcja wyzwalacza. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Umożliwia zmianę wartości właściwości bez nadanie mu źródło o wyższym priorytecie. Analogicznie, można użyć <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Aby zmienić wartość właściwości bez zastępowania powiązania.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Koercja, animacji i wartości podstawowej  
 Koercja i animacji działa zarówno na wartość, która jest określane jako "podstawowej wartości" w całym to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. W związku z tym wartości podstawowej jest niezależnie od wartości jest określany za pośrednictwem górę oceny w elementy aż do osiągnięcia element 2.  
  
 Dla animacji wartości podstawowej mogą mieć wpływ na wartość animowany czy animacji nie określono zarówno "Od" a "Do" dla niektórych zachowań, czy animacja celowo zostanie przywrócona wartość podstawową po zakończeniu. Aby wyświetlić to w praktyce, uruchom [z, aby i przykładowe wartości docelowej animacji](http://go.microsoft.com/fwlink/?LinkID=159988). Spróbuj ustawić wartości lokalne wysokość prostokąta w tym przykładzie, taki sposób, że wartość początkowa lokalnego różni się od żadnego "Od" animacji. Można zauważyć, że animacji rozpocząć od razu używać wartości "Od" i Zastąp wartości podstawowej po uruchomieniu. Animacja może określać Aby przywrócić wartość znajdującą się przed animacji po ukończeniu przez określenie zatrzymania <xref:System.Windows.Media.Animation.FillBehavior>. Później normalnym priorytecie służy do określenia wartości podstawowej.  
  
 Wiele animacji może odnosić się do jednej właściwości z każdym z tych animacji prawdopodobnie o został zdefiniowany z różnych miejsc pierwszeństwo wartość. Jednak te animacji zostanie potencjalnie złożonego ich wartości, zamiast zwykłego zastosowania animacji z wyższy priorytet. Zależy to dokładnie sposób definiowania animacji i wprowadź wartość, która jest animowanej. Aby uzyskać więcej informacji na temat właściwości animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Koercja stosowana na najwyższym poziomie wszystkich. Nawet już uruchomiona Animacja podlega koercja wartość. Niektóre istniejące właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają wbudowane wymuszenia. Dla właściwości zależności niestandardowych, zdefiniuj zachowanie koercja dla właściwości zależności niestandardowych pisząc <xref:System.Windows.CoerceValueCallback> i przekazywanie wywołania zwrotnego jako część metadanych podczas tworzenia właściwości. Możesz też przesłonić zachowanie koercja istniejących właściwości przez zastępowanie metadanych dla tej właściwości w klasie pochodnej. Koercja współdziała z wartości podstawowej w taki sposób, że ograniczenia dotyczące koercja są stosowane zgodnie z tych warunków ograniczających istnieją w czasie, ale nadal jest zachowywana wartości podstawowej. W związku z tym jeśli ograniczenia w koercja są nowsze podnoszone, koercja zwróci wartość możliwych do tej wartości podstawowej i potencjalnie wpływ koercja we właściwości zostanie zakończone, jak unosiło są wszystkie ograniczenia. Aby uzyskać więcej informacji dotyczących zachowania koercja, zobacz [wywołania zwrotne właściwości zależności i sprawdzania poprawności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Wyzwalacz zachowania  
 Formanty często definiowania zachowań wyzwalacza jako część ich domyślny styl w kompozycji. Ustawienie właściwości lokalnego w formantach może uniemożliwić wyzwalaczy na odpowiadanie na zdarzenia zmiennych użytkownika wizualnie lub behaviorally. Najczęściej wyzwalacza właściwości jest formant lub stan właściwości takich jak <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Na przykład domyślnie podczas <xref:System.Windows.Controls.Button> jest wyłączone (wywołać <xref:System.Windows.UIElement.IsEnabled%2A> jest `false`), a następnie <xref:System.Windows.Controls.Control.Foreground%2A> wartość w stylu motywu to, co powoduje, że formant wyszarzone "". Ale jeśli zdefiniowano lokalnym <xref:System.Windows.Controls.Control.Foreground%2A> wartość pominięte w pierwszeństwo przez zestaw właściwości lokalnej, nawet w tym scenariuszu wyzwalane właściwości normalne kolor szary w poziomie. Należy zachować ostrożność ustawiania wartości właściwości, które zachowania wyzwalaczy poziomu motywu i upewnij się, że użytkownik nie nadmiernie zakłócają czynności użytkownika przeznaczone dla tego formantu.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue i wartość priorytetu  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Metoda zapewnia wskazane oznacza, że wyczyść lokalnie zastosowane wartości ustawionej dla elementu właściwości zależności. Jednak podczas wywoływania <xref:System.Windows.DependencyObject.ClearValue%2A> nie ma gwarancji, że wartość domyślna ustalone w metadanych podczas rejestracji właściwości jest nową, efektywną wartość. Wszystkie innych uczestników pierwszeństwo wartości są nadal aktywne. Tylko lokalnie ustaw wartość została usunięta z sekwencji pierwszeństwo. Na przykład, jeśli wywołujesz <xref:System.Windows.DependencyObject.ClearValue%2A> we właściwości, których tej właściwości zostanie również ustawiona przez styl motywu, a następnie wartość motywu jest stosowany jako nowa wartość zamiast domyślnego na podstawie metadanych. Jeśli chcesz wykonać wszystkich uczestników wartości właściwości poza proces i ustaw wartość domyślną zarejestrowanych metadanych można uzyskać, że wartość domyślna ostatecznie badając metadanych właściwości zależności, a następnie można użyć wartość domyślną do lokalnie Ustaw właściwość wywołaniem <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Wywołania zwrotne i weryfikacja właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
