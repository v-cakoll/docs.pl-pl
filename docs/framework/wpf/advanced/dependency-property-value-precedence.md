---
title: Następstwo zależności wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 9adcd19ea48d62f4fdcab3380252ae8ec8398296
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315689"
---
# <a name="dependency-property-value-precedence"></a>Następstwo zależności wartości właściwości
<a name="introduction"></a> W tym temacie opisano sposób pracy z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system właściwości mogą mieć wpływ na wartość właściwości zależności i opisuje pierwszeństwa, które cechy właściwości systemu zastosowania do skutecznego wartości właściwości.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, a po ich przeczytaniu [Przegląd właściwości zależności](dependency-properties-overview.md). Aby skorzystać z przykładów w tym temacie, należy również mieć świadomość [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>System właściwości WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] System właściwości oferuje zaawansowane możliwości. wartość właściwości zależności można określić za pomocą różnych czynników, włączenie funkcji, takich jak sprawdzania poprawności właściwości w czasie rzeczywistym, późne powiązania i powiadamianie powiązane właściwości zmiany wartości Aby uzyskać inne właściwości. Dokładnej kolejności i logiki, która służy do określania zależności wartości właściwości jest względnie złożone. To zamówienie pomóc w uniknięciu ustawienie właściwości niepotrzebne i może również usunąć pomyłek za pośrednictwem dokładnie Dlaczego niektóre próba wpływ lub przewidywać wartość właściwości zależności nie zakończył się wynikiem wartość, które miały.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Właściwości zależności mogą być "Set" w kilku miejscach  
 Poniżej przedstawiono przykład [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gdzie tę samą właściwość (<xref:System.Windows.Controls.Control.Background%2A>) ma trzy różne "set" operacje, które mogą mieć wpływ na wartość.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 W tym miejscu, jaki kolor spodziewasz się zastosuje — czerwony, zielony i niebieski?  
  
 Z wyjątkiem animowany wartości i wymuszenia ustawia właściwość lokalną są ustawione na najwyższy priorytet. Jeśli ustawisz wartość lokalnie można oczekiwać, że wartość będzie honorowane, nawet powyżej wszystkie style lub szablony kontrolek. Oto przykład <xref:System.Windows.Controls.Control.Background%2A> jest ustawiony na czerwony lokalnie. Dlatego style zdefiniowane w tym zakresie, mimo że jest to styl niejawny, w przeciwnym razie będą stosowane do wszystkich elementów tego typu, w tym zakresie nie jest najwyższy priorytet, do udzielania <xref:System.Windows.Controls.Control.Background%2A> właściwości jego wartość.  Jeśli lokalna wartość czerwonego została usunięta z tego wystąpienia przycisku, następnie styl będzie mają pierwszeństwo przed i uzyskać wartość tła przycisku z stylu.  W obrębie stylu wyzwalacze pierwszeństwo, dlatego ten przycisk jest niebieski, gdy wskaźnik myszy znajduje się nad nią i zielony w przeciwnym razie.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Lista pierwszeństwo ustawienie właściwości zależności  
 Poniżej znajduje się ostateczny kolejności, używany w systemie właściwości do przypisywania wartości czasu wykonywania właściwości zależności. Najwyższy priorytet jest wymienione jako pierwsze. Ta lista rozszerza niektóre generalizacje wprowadzone w [Przegląd właściwości zależności](dependency-properties-overview.md).  
  
1. **Właściwość systemu wymuszenia.** Szczegółowe informacje na temat wymuszenia, [wymuszenia, animacji i wartość Base](#animations) w dalszej części tego tematu.  
  
2. **Aktywne animacji i animacji z zachowaniem wstrzymania.** Aby można było ma praktycznego wpływu, animacji właściwości musi można mają pierwszeństwo przed (unanimated) wartość bazową, nawet wtedy, gdy ta wartość została ustawiona lokalnie. Aby uzyskać więcej informacji, zobacz [wymuszenia, animacji i wartość Base](#animations) w dalszej części tego tematu.  
  
3. **Lokalna wartość.** Lokalna wartość może być ustawione za pośrednictwem wygody właściwości "otoki", co również ustawienie jako atrybut lub właściwość elementu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], lub przez wywołanie <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] za pomocą właściwości określonego wystąpienia. Jeśli ustawisz wartość lokalnego przy użyciu powiązania lub zasobu, te każdego działania w pierwszeństwo tak, jakby bezpośrednich wartość została ustawiona.  
  
4. **Właściwości szablonu TemplatedParent.** Element ma <xref:System.Windows.FrameworkElement.TemplatedParent%2A> Jeśli został utworzony jako część szablonu ( <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.DataTemplate>). Szczegółowe informacje na temat gdy ma to zastosowanie, [TemplatedParent](#templatedparent) w dalszej części tego tematu. W szablonie dotyczy następującej kolejności:  
  
    1.  Wyzwalacze — od <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu.  
  
    2.  Zestawy właściwości (zwykle za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów) w <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu.  
  
5. **Styl niejawny.** Ma zastosowanie tylko do `Style` właściwości. `Style` Właściwość jest wypełniana przez dowolny zasób stylu z kluczem, który jest zgodny z typem elementu. Że zasobu stylu muszą istnieć w stronę lub aplikacji; Wyszukiwanie zasób stylu niejawnego niemożliwa do tematów.  
  
6. **Wyzwalacze w stylu.** Wyzwalacze w ramach stylów ze strony lub aplikacji (te style może być jawne lub niejawne stylów, ale nie z domyślnych stylów, które mają niższy priorytet).  
  
7. **Wyzwalaczy szablonu.** Dowolny wyzwalającej wydanie na podstawie szablonu w ramach stylu lub bezpośrednio zastosowany szablon.  
  
8. **Styl metod ustawiających.** Wartości z kolekcji <xref:System.Windows.Setter> w ramach stylów ze strony lub aplikacji.  
  
9. **Styl domyślny (motyw).** Szczegółowe informacje na temat gdy ma to zastosowanie, a jak style motyw odnoszą się do szablonów w ramach stylów motywu, [domyślnych (motyw) stylów](#themestyles) w dalszej części tego tematu. W ramach domyślnego stylu mają zastosowanie następujące kolejność według priorytetu:  
  
    1.  Aktywne Wyzwalacze w stylu motywu.  
  
    2.  Metody ustawiające w stylu motywu.  
  
10. **Dziedziczenie.** Kilka właściwości zależności dziedziczy wartości elementu nadrzędnego do elementów podrzędnych taki sposób, że nie należy można ustawić szczegółowe informacje dotyczące każdego elementu w całej aplikacji. Aby uzyskać szczegółowe informacje, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
11. **Wartość domyślna z metadanych właściwości zależności.** Wszelkie danej właściwości zależności mogą mieć wartość domyślną, zgodnie z ustaleniami rejestracji systemu właściwości określonej właściwości. Ponadto klasy pochodne, które dziedziczą właściwości zależności istnieje możliwość zastąpienia tych metadanych (łącznie z wartością domyślną) na podstawie typu. Zobacz [metadane zależności właściwości](dependency-property-metadata.md) Aby uzyskać więcej informacji. Ponieważ dziedziczenia jest sprawdzany przed wartość domyślna to właściwość dziedziczona wartość domyślną elementu nadrzędnego mają pierwszeństwo przed nie zawiera elementu podrzędnego.  W związku z tym jeśli właściwości dziedziczonych nie jest ustawiona w dowolnym miejscu, a nie wartość domyślna elementu podrzędnego jest używana wartość domyślna, zgodnie z instrukcjami na główny lub element nadrzędny.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako element pierwszeństwo nie ma zastosowania do żadnej właściwości elementu, który został zadeklarowany bezpośrednio w znaczniku standardowej aplikacji. Koncepcja TemplatedParent istnieje tylko dla elementów podrzędnych w obrębie drzewa wizualnego, które dochodzą do istnienia przez zastosowanie szablonu. Podczas wyszukiwania system właściwość <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu dla wartości, jego wyszukuje szablonu, który utworzony tego elementu. Właściwość wartości z kolekcji <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu zazwyczaj działa tak, jakby zostały ustawione jako wartości lokalnej na element podrzędny, ale tego pierwszeństwo mniejsze niż wartość lokalnego nie istnieje, ponieważ szablony są potencjalnie udostępnione. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Właściwości stylu  
 Kolejność wyszukiwania opisanej wcześniej ma zastosowanie do wszystkich właściwości możliwe zależności, z wyjątkiem jednego: <xref:System.Windows.FrameworkElement.Style%2A> właściwości. <xref:System.Windows.FrameworkElement.Style%2A> Właściwości są unikatowe w jej nie może sam być różne, więc elementy pierwszeństwo 5 do 8 nie mają zastosowania. Ponadto animowanie albo coercing — <xref:System.Windows.FrameworkElement.Style%2A> nie jest zalecane (i animowanie <xref:System.Windows.FrameworkElement.Style%2A> wymagałoby animacji niestandardowej klasy). Spowoduje to, że trzy sposoby, <xref:System.Windows.FrameworkElement.Style%2A> może być ustawiona właściwość:  
  
-   **Style jawne.** <xref:System.Windows.FrameworkElement.Style%2A> Zostaje ustalona bezpośrednio. W większości przypadków styl nie jest zdefiniowano w tekście, ale zamiast tego odwołuje się jako zasób, jawna klucza. W tym przypadku samej właściwości stylu działa tak, jakby był to lokalna wartość elementu pierwszeństwo 3.  
  
-   **Styl niejawny.** <xref:System.Windows.FrameworkElement.Style%2A> Nie ustawiono właściwości bezpośrednio. Jednak <xref:System.Windows.FrameworkElement.Style%2A> na pewien poziom w kolejności wyszukiwania zasobów (strony, aplikacji) istnieje i jest kluczem utworzonym na podstawie przy użyciu klucza zasobu, który jest zgodny z typem jest to styl ma zostać zastosowany do. W tym przypadku <xref:System.Windows.FrameworkElement.Style%2A> samej właściwości działa według pierwszeństwa, określone w sekwencji jako element 5. Ten stan może zostać wykryte przy użyciu <xref:System.Windows.DependencyPropertyHelper> względem <xref:System.Windows.FrameworkElement.Style%2A> właściwości i szuka <xref:System.Windows.BaseValueSource.ImplicitStyleReference> w wynikach.  
  
-   **Domyślny styl**, znane również jako **stylów kompozycji.** <xref:System.Windows.FrameworkElement.Style%2A> Właściwość nie jest ustawiony bezpośrednio, a w rzeczywistości zostanie odczytany jako `null` aż do czasu wykonywania. W tym przypadku styl pochodzi z wersji ewaluacyjnej motyw, który jest częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparatu prezentacji.  
  
 Niejawna style nie znajduje się w motywy, typ musi odpowiadać dokładnie - `MyButton` `Button`— Klasa pochodna nie użyje niejawnie styl `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Style domyślne (motyw)  
 Każdy formant, który jest dostarczany z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma domyślnego stylu. Czy domyślny styl potencjalnie jest zależna od motywu, co jest Dlaczego ten styl domyślny jest czasami określane jako stylów kompozycji.  
  
 Najważniejsze informacje można znaleźć w stylu domyślnym dla formantu jest jego szablon kontrolki, który istnieje w stylu motywu jako setter dla jego <xref:System.Windows.Controls.Control.Template%2A> właściwości. Gdyby nie szablonu z domyślnych stylów kontrolki bez szablonu niestandardowego, jako część styl niestandardowy musi nie wygląd na wszystkich. Szablon z domyślnego stylu udostępnia wygląd każdej kontrolki podstawowej struktury, a następnie definiuje również połączenia między właściwości zdefiniowane w drzewie wizualnym szablonu i odpowiednią klasę formantu. Każdy formant ujawnia zestaw właściwości, które mogą mieć wpływ na wygląd kontrolki bez całkowicie zastępowania szablonu. Rozważmy na przykład domyślny wygląd <xref:System.Windows.Controls.Primitives.Thumb> formant, który jest składnikiem programu <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Element <xref:System.Windows.Controls.Primitives.Thumb> zawiera niektóre możliwe do dostosowania właściwości. Domyślny szablon <xref:System.Windows.Controls.Primitives.Thumb> tworzy podstawową strukturę / zagnieżdżone drzewa wizualnego, za pomocą kilku <xref:System.Windows.Controls.Border> składniki, aby nadać wygląd skos. Jeśli właściwość, która jest częścią szablonu jest przeznaczona do uwidocznienia dla możliwości dostosowywania <xref:System.Windows.Controls.Primitives.Thumb> klasy, a następnie tej właściwości musi być wystawiony przez [TemplateBinding](templatebinding-markup-extension.md), w ramach szablonu. W przypadku właściwości <xref:System.Windows.Controls.Primitives.Thumb>, różne właściwości tych granic udostępniają powiązanie szablonu z właściwości, takie jak <xref:System.Windows.Controls.Border.Background%2A> lub <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ale niektórych właściwości lub ustalenia visual są zakodowane w szablonie kontrolki lub są powiązane z wartości, które pochodzą bezpośrednio z motywu i nie może być ograniczony zastępując cały szablon. Ogólnie rzecz biorąc, jeśli właściwość jest dostarczany z szablonem elementu nadrzędnego i nie są udostępniane przez powiązanie szablonu, go nie można go zmienić, style, ponieważ nie istnieje łatwy sposób można określić obiekt docelowy. Jednak nadal mieć wpływ tej właściwości, dziedziczenie wartości właściwości w szablonie zastosowane lub za pomocą wartości domyślnej.  
  
 Style motyw użyć typu jako klucz w ich definicji. Jednak gdy motywy są stosowane do wystąpienia danego elementu, motywy wyszukiwania dla tego typu odbywa się przez sprawdzanie <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> właściwości formantu. Jest to w przeciwieństwie do przy użyciu literału typu, podobnie jak niejawna style. Wartość <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> odziedziczenie dla klasy pochodnej, nawet wtedy, gdy implementujący nie zmienił jego (zamierzony sposób zmieniając właściwość nie ma go zastąpić na poziomie właściwości, ale aby zamiast tego zmiany z domyślnej wartości właściwości metadanych). Tego operatora pośredniego włącza klas bazowych do definiowania stylów motywu dla elementów pochodnych, które w przeciwnym razie nie ma stylu (lub co ważniejsze, nie ma szablonu w obrębie stylu i dlatego miałby nie wygląd domyślny na wszystkich). W efekcie może pochodzić `MyButton` z <xref:System.Windows.Controls.Button> i nadal będą mieć <xref:System.Windows.Controls.Button> szablonu domyślnego. Jeśli jesteś autorem formantu `MyButton` i potrzebowała różne zachowanie, można zastąpić metadane zależności właściwości dla <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> na `MyButton` można zwrócić inny klucz, a następnie zdefiniuj style motyw odpowiednie, w tym szablonie dla `MyButton` , należy spakować przy użyciu usługi `MyButton` kontroli. Aby uzyskać szczegółowe informacje na temat motywy, style i tworzenia kontrolki, zobacz [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Zasób dynamiczny odwołania i powiązania  
 Odwołania do dynamicznego zasobów i operacji powiązanie przestrzegać pierwszeństwo lokalizacji, w którym są ustawione. Na przykład zasób dynamiczny stosowane do wartości lokalnej działa na element priorytet 3, powiązanie dla metody ustawiającej właściwość w ramach stylów motywu stosuje się na pozycji pierwszeństwo 9 i tak dalej. Ponieważ odwołania do zasobów dynamicznych i powiązanie obu, należy mieć możliwość uzyskania wartości ze stanu wykonywania aplikacji dzięki temu, że rzeczywisty proces określania pierwszeństwo wartości właściwości dla dowolnej podanej właściwości rozszerza się w czasie wykonywania.  
  
 Zasób dynamiczny odwołania nie są ściśle rzecz ujmując części systemu, właściwości, ale mają kolejność wyszukiwania własne, który współdziała z sekwencji wymienionych powyżej. Pierwszeństwo tego jest udokumentowany dokładniej w [zasoby XAML](xaml-resources.md). Podstawowe sumą pierwszeństwo tym jest: element główny strony, aplikacji, motyw, system.  
  
 Dynamiczne zasobów i powiązania ma pierwszeństwo, gdy ich stan został ustawiony, ale wartość jest odroczone. W wyniku tego jest to, że jeśli ustawisz zasób dynamiczny lub powiązanie z wartości lokalnej, wszelkie zmiany wartości lokalnej zastępuje zasób dynamiczny lub całkowicie powiązania. Nawet jeśli wywołasz <xref:System.Windows.DependencyObject.ClearValue%2A> metodę, aby wyczyścić lokalnie ustawiony wartość, zasób dynamiczny lub powiązanie nie zostanie przywrócony. W rzeczywistości, jeśli wywołasz <xref:System.Windows.DependencyObject.ClearValue%2A> na właściwość, która zawiera zasób dynamiczny lub powiązania w miejscu (Brak literału wartości lokalnych), są usuwane przez <xref:System.Windows.DependencyObject.ClearValue%2A> zbyt wywołania.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Metody to kolejny sposób ustawiania właściwości, ale nie jest w następującej kolejności priorytetu. Zamiast tego <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umożliwia zmianę wartości właściwości bez zastępowania źródło poprzedniej wartości. Możesz użyć <xref:System.Windows.DependencyObject.SetCurrentValue%2A> za każdym razem, aby ustawić wartość bez podawania wartości priorytetu wartości lokalnej. Na przykład, jeśli właściwość jest ustawiane przez wyzwalacz, a następnie przypisać inną wartością za pomocą <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, system właściwości nadal szanuje wyzwalacza i właściwość ulegnie zmianie, jeśli występuje akcję wyzwalacza. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Umożliwia zmianę wartości właściwości bez nadawania jego źródła o wyższym priorytecie. Podobnie, można użyć <xref:System.Windows.DependencyObject.SetCurrentValue%2A> można zmienić wartość właściwości bez zastępowania powiązania.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Przekształcenie, animacji i wartości bazowej  
 Wymuszanie i animacji, obie działają na wartość, która jest określane jako "wartości bazowej" w całym to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Wartości bazowej jest więc każda wartość jest określana przez dokonanie oceny oprogramowania do góry w elementach aż do osiągnięcia element 2.  
  
 Dla animacji wartości bazowej może mieć wpływ na wartość animowany czy animacji nie określono zarówno "Od" a "Do" dla niektórych zachowań, czy animacja celowo powraca do wartości bazowej po zakończeniu. Aby zobaczyć to w praktyce, uruchom [od, do i przez przykład wartości docelowej animacji](https://go.microsoft.com/fwlink/?LinkID=159988). Spróbuj ustawić wartości lokalnych wysokość prostokąta w tym przykładzie, taki sposób, że początkowe wartości lokalnej różni się od dowolnego "Od" animacji. Można zauważyć, że animacji rozpocząć już teraz korzystanie z wartości "From" i Zastąp wartości bazowej po uruchomieniu. Animacji może określić, aby zwrócić wartość znajdującą się przed animacji, po jego zakończeniu, określając zatrzymania <xref:System.Windows.Media.Animation.FillBehavior>. Później normalny priorytet jest używany do określenia wartości podstawowej.  
  
 Wiele animacji może być stosowana do pojedynczej właściwości, z każdym z tych animacji, prawdopodobnie masz zdefiniowany z różnych miejsc w pierwszeństwo przed wartością. Jednak te animacji będzie potencjalnie złożony ich wartości, a nie po prostu stosowanie animacji z wyższy priorytet. Zależy to dokładnie, jak animacji są definiowane i typ wartości, który jest jest animowany. Aby uzyskać więcej informacji na temat Animowanie właściwości, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
 Wymuszanie stosuje się na najwyższym poziomie wszystkich. Nawet już uruchomionego animacji podlega wymuszenia wartość. Niektóre istniejące właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają wbudowane wymuszenia. Dla właściwości zależności niestandardowych, zdefiniuj zachowanie wymuszenia dla właściwości zależności niestandardowej, pisząc <xref:System.Windows.CoerceValueCallback> i przekazanie wywołania zwrotnego jako część metadanych podczas tworzenia właściwości. Można również zmienić zachowanie wymuszenia istniejących właściwości, poprzez zastąpienie metadanych dla tej właściwości w klasie pochodnej. Wymuszanie wchodzi w interakcję z wartości bazowej w taki sposób, że ograniczenia dotyczące wymuszenia są stosowane zgodnie z tych ograniczeń istnieje w czasie, ale nadal zachowano wartości bazowej. W związku z tym jeśli ograniczenia w wymuszenia są nowsze zniesione, wymuszanie zwróci wartość możliwa do tej wartości bazowej i potencjalnie wpływ wymuszenia we właściwości zostanie zakończone, tak szybko, jak zniesieniem wszystkie ograniczenia. Aby uzyskać więcej informacji na temat zachowania wymuszenia zobacz [zależność wartości wywołania zwrotnego i walidacji](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Zachowania wyzwalacza  
 Formanty często definiują zachowania wyzwalacza jako część ich domyślnego stylu w kompozycji. Ustawienie właściwości lokalne kontrolek może uniemożliwić wyzwalacze do reagowania na zdarzenia na podstawie użytkownika, wizualnie lub behaviorally. Najczęściej używane wyzwalacz właściwości jest właściwości formantu lub stan, takich jak <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Na przykład domyślnie podczas <xref:System.Windows.Controls.Button> jest wyłączona (wyzwalaczy dla <xref:System.Windows.UIElement.IsEnabled%2A> jest `false`), a następnie <xref:System.Windows.Controls.Control.Foreground%2A> wartość w stylu motywu to, co powoduje, że formant wyszarzone "". Ale jeśli ustawisz lokalnie <xref:System.Windows.Controls.Control.Foreground%2A> wartość, że normalny kolor szary w poziomie zostanie zastąpiony w pierwszeństwo zestawu właściwości lokalnej, nawet w przypadku tego scenariusza wyzwalane przez właściwość. Należy zachować ostrożność, ustawiania wartości właściwości, które zachowania wyzwalaczy poziomu motywu i upewnij się, że nie są nadmiernie zakłóca ze środowiskiem użytkownika przeznaczone dla tej kontrolki.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>Pierwszeństwo wartość i ClearValue  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Metoda zapewnia wskazane oznacza, że wyczyszczenie wszelkich lokalnie stosowane wartości z właściwości zależności, który jest ustawiony na element. Jednak podczas wywoływania <xref:System.Windows.DependencyObject.ClearValue%2A> nie jest gwarancją to nową, efektywną wartość domyślną występującej w metadanych w trakcie rejestracji właściwości. Wszystkie innych uczestników pierwszeństwo wartości są nadal aktywne. Tylko lokalnie ustawiony wartość została usunięta z sekwencji pierwszeństwo. Na przykład, jeśli wywołasz <xref:System.Windows.DependencyObject.ClearValue%2A> we właściwości, w których ta właściwość jest również ustawiona przez style motyw, a następnie wartość motyw jest stosowany jako nową wartość, a nie domyślnej na podstawie metadanych. Jeśli chcesz podjęcia wszyscy uczestnicy wartość właściwości poza procesem, a następnie ustaw wartość domyślną zarejestrowanych metadanych można uzyskać, wartość domyślna ostatecznie Sondując metadane zależności właściwości, a następnie użyć wartość domyślną, aby lokalnie Ustaw właściwość z wywołaniem <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Zależność wartości wywołania zwrotnego i walidacji](dependency-property-callbacks-and-validation.md)
