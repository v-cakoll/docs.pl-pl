---
title: Następstwo zależności wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 178145b06cb937fb677b8454357bed774ed3003b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740849"
---
# <a name="dependency-property-value-precedence"></a>Następstwo zależności wartości właściwości
<a name="introduction"></a>W tym temacie wyjaśniono, w jaki sposób działania systemu właściwości [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mogą wpływać na wartość właściwości zależności, a także określać priorytety, według których aspekty systemu właściwości mają zastosowanie do wartości efektywnej właściwości.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących właściwości zależności dla klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i ma [Przegląd właściwości zależności](dependency-properties-overview.md)odczytu. Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak pisać aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>System właściwości WPF  
 System właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje zaawansowany sposób, aby wartość właściwości zależności była określana przez różne czynniki, włączając funkcje takie jak Walidacja właściwości czasu rzeczywistego, późne wiązanie i powiadamianie powiązanych właściwości zmian wartości dla inne właściwości. Dokładna kolejność i logika, która jest używana do określania wartości właściwości zależności, jest rozsądnie skomplikowana. Wiedząc, że to zamówienie pomoże uniknąć niepotrzebnego ustawienia właściwości i może również usunąć pomyłkę w porównaniu z tym, dlaczego niektóre próby mają wpływ na lub przewidzieć wartość właściwości zależności, która nie została zakończona w wyniku oczekiwanej wartości.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Właściwości zależności mogą być ustawione w wielu miejscach  
 Poniżej znajduje się przykład [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], gdzie ta sama Właściwość (<xref:System.Windows.Controls.Control.Background%2A>) ma trzy różne operacje "Set", które mogą mieć wpływ na tę wartość.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 W tym miejscu można zastosować oczekiwany kolor — czerwony, zielony lub niebieski?  
  
 Z wyjątkiem wartości animowanych i przymusu, lokalne zestawy właściwości są ustawiane przy najwyższym priorytecie. Jeśli wartość jest ustawiona lokalnie, można oczekiwać, że wartość zostanie wykorzystana, nawet nad wszystkimi stylami lub szablonami kontrolki. W tym przykładzie <xref:System.Windows.Controls.Control.Background%2A> jest ustawiona na czerwony lokalnie. W związku z tym styl zdefiniowany w tym zakresie, pomimo tego, że jest stylem niejawnym, który w przeciwnym razie będzie stosowany do wszystkich elementów tego typu w tym zakresie, nie jest najwyższym pierwszeństwem do nadawania właściwości <xref:System.Windows.Controls.Control.Background%2A> jej wartości.  Jeśli usunięto wartość lokalną czerwieni z tego wystąpienia przycisku, styl będzie miał pierwszeństwo, a przycisk uzyska wartość tła z stylu.  W stylu wyzwalacz ma pierwszeństwo, dlatego przycisk będzie niebieski, gdy wskaźnik myszy znajduje się nad nim, a zielony w przeciwnym razie.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Lista pierwszeństwa ustawienia właściwości zależności  
 Poniżej znajduje się ostateczna kolejność wykorzystywana przez system właściwości podczas przypisywania wartości właściwości zależności. Najwyższy priorytet jest wymieniony jako pierwszy. Ta lista rozwijana na niektórych generalizacjach wykonanych we [właściwościach zależności przegląd](dependency-properties-overview.md).  
  
1. **Wymuszone przekształcenie systemu właściwości.** Aby uzyskać szczegółowe informacje dotyczące przymusu, zobacz temat [przekształcenia, animacji i wartości bazowej](#animations) w dalszej części tego tematu.  
  
2. **Aktywne animacje lub animacje z zachowaniem blokady.** Aby zapewnić praktyczny efekt, animacja właściwości musi mieć pierwszeństwo przed wartością bazową (nieanimowaną), nawet jeśli ta wartość została ustawiona lokalnie. Aby uzyskać szczegółowe informacje, zobacz [przekształcenie, animację i wartość bazową](#animations) w dalszej części tego tematu.  
  
3. **Wartość lokalna.** Wartość lokalna może być ustawiona za pośrednictwem wygody właściwości "otoka", która również jest równa ustawieniu jako atrybut lub element właściwości w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lub przez wywołanie interfejsu API <xref:System.Windows.DependencyObject.SetValue%2A> przy użyciu właściwości konkretnego wystąpienia. Jeśli wartość lokalna zostanie ustawiona przy użyciu powiązania lub zasobu, każda z nich działa w kolejności, tak jakby była ustawiona wartość bezpośrednia.  
  
4. **Właściwości szablonu TemplatedParent.** Element ma <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, jeśli został utworzony jako część szablonu (<xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.DataTemplate>). Aby uzyskać szczegółowe informacje na temat tego zastosowania, zobacz [TemplatedParent](#templatedparent) w dalszej części tego tematu. W ramach szablonu obowiązuje następujący priorytet:  
  
    1. Wyzwalacze z szablonu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
    2. Zestawy właściwości (zwykle za pomocą atrybutów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) w szablonie <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
5. **Styl niejawny.** Dotyczy tylko właściwości `Style`. Właściwość `Style` jest wypełniana przez dowolny zasób stylu z kluczem zgodnym z typem tego elementu. Ten zasób stylu musi znajdować się na stronie lub aplikacji; Wyszukiwanie niejawnego zasobu stylu nie powoduje przejścia do motywów.  
  
6. **Wyzwalacze stylu.** Wyzwalacze w ramach stylów ze strony lub aplikacji (te style mogą być jawnymi lub niejawnymi stylami, ale nie z domyślnych stylów, które mają niższy priorytet).  
  
7. **Wyzwalacze szablonu.** Dowolny wyzwalacz z szablonu w stylu lub bezpośrednio zastosowany szablon.  
  
8. **Metodyki stylów.** Wartości z <xref:System.Windows.Setter> w ramach stylów ze strony lub aplikacji.  
  
9. **Domyślny styl (motyw).** Aby uzyskać szczegółowe informacje o tym, kiedy ma to zastosowanie, oraz o tym, jak style motywów odnoszą się do szablonów w ramach stylów motywu, zobacz [domyślne style (motyw)](#themestyles) w dalszej części tego tematu W stylu domyślnym obowiązuje następująca kolejność pierwszeństwa:  
  
    1. Aktywne Wyzwalacze w stylu motywu.  
  
    2. Metody ustawiające w stylu motywu.  
  
10. **Strukturze.** Niektóre właściwości zależności dziedziczą wartości z elementu nadrzędnego do elementów podrzędnych, w taki sposób, że nie muszą być ustawione na każdy element w aplikacji. Aby uzyskać szczegółowe informacje, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
11. **Wartość domyślna z metadanych właściwości zależności.** Każda dana właściwość zależności może mieć wartość domyślną ustaloną przez rejestrację systemu właściwości danej właściwości. Ponadto klasy pochodne, które dziedziczą właściwość zależności, mają opcję przesłaniania metadanych (w tym wartości domyślnej) dla poszczególnych typów. Aby uzyskać więcej informacji, zobacz [metadane właściwości zależności](dependency-property-metadata.md) . Ponieważ dziedziczenie jest sprawdzane przed wartością domyślną, dla dziedziczonej właściwości, wartość domyślna elementu nadrzędnego ma pierwszeństwo nad elementem podrzędnym.  W związku z tym, jeśli właściwość dziedziczna nie jest ustawiona w dowolnym miejscu, zamiast wartości domyślnej elementu podrzędnego zostanie użyta wartość domyślna określona w elemencie głównym lub nadrzędnym.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako element pierwszeństwa nie ma zastosowania do żadnej właściwości elementu zadeklarowanego bezpośrednio w standardowym znaczniku aplikacji. Koncepcja TemplatedParent istnieje tylko dla elementów podrzędnych w drzewie wizualnym, które są dostępne w ramach aplikacji szablonu. Gdy system właściwości przeszukuje szablon <xref:System.Windows.FrameworkElement.TemplatedParent%2A> dla wartości, przeszukuje szablon, który utworzył ten element. Wartości właściwości szablonu <xref:System.Windows.FrameworkElement.TemplatedParent%2A> na ogół działają tak, jakby były ustawione jako wartość lokalna w elemencie podrzędnym, ale ma to mniejsze pierwszeństwo, a wartość lokalna istnieje, ponieważ szablony są potencjalnie udostępniane. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Właściwość stylu  
 Kolejność wyszukiwania opisana wcześniej stosuje się do wszystkich możliwych właściwości zależności, z wyjątkiem jednego: Właściwość <xref:System.Windows.FrameworkElement.Style%2A>. Właściwość <xref:System.Windows.FrameworkElement.Style%2A> jest unikatowa, ponieważ nie może być sama stylem, więc elementy pierwszeństwa od 5 do 8 nie mają zastosowania. Nie zaleca się również animowania ani przekształcania <xref:System.Windows.FrameworkElement.Style%2A>, a animowanie <xref:System.Windows.FrameworkElement.Style%2A> wymaga niestandardowej klasy animacji). Pozostawi to trzy sposoby, aby Właściwość <xref:System.Windows.FrameworkElement.Style%2A> mogła być ustawiona:  
  
- **Styl jawny.** Właściwość <xref:System.Windows.FrameworkElement.Style%2A> jest ustawiana bezpośrednio. W większości scenariuszy styl nie jest zdefiniowany w wierszu, ale zamiast tego jest przywoływany jako zasób, przez jawny klucz. W tym przypadku Właściwość Style działa tak, jakby była wartością lokalną, element priorytetu 3.  
  
- **Styl niejawny.** Właściwość <xref:System.Windows.FrameworkElement.Style%2A> nie jest ustawiona bezpośrednio. Jednak <xref:System.Windows.FrameworkElement.Style%2A> istnieje na pewnym poziomie w sekwencji wyszukiwania zasobów (stronie, aplikacji) i jest określany przy użyciu klucza zasobu zgodnego z typem, do którego ma zostać zastosowany styl. W tym przypadku Właściwość <xref:System.Windows.FrameworkElement.Style%2A> działa zgodnie z pierwszeństwem określonym w sekwencji jako elementem 5. Ten warunek może zostać wykryty przy użyciu <xref:System.Windows.DependencyPropertyHelper> względem właściwości <xref:System.Windows.FrameworkElement.Style%2A> i szuka <xref:System.Windows.BaseValueSource.ImplicitStyleReference> w wynikach.  
  
- **Styl domyślny**, znany również jako **styl motywu.** Właściwość <xref:System.Windows.FrameworkElement.Style%2A> nie jest ustawiona bezpośrednio, a w rzeczywistości zostanie odczytana jako `null` do czasu wykonania. W tym przypadku styl pochodzi od oceny motywu wykonawczego, która jest częścią aparatu prezentacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 W przypadku niejawnych stylów, które nie są w motywach, typ musi być zgodny dokładnie — `MyButton` `Button`Klasa pochodna nie będzie niejawnie używać stylu dla `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Domyślne style (motyw)  
 Każda kontrolka, która jest dostarczana z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma styl domyślny. Domyślny styl może być różny w zależności od motywu, co oznacza, że domyślny styl jest czasami określany jako styl motywu.  
  
 Najważniejsze informacje, które znajdują się w domyślnym stylu kontrolki, to jego szablon kontrolki, który istnieje w stylu motywu jako Metoda ustawiająca dla właściwości <xref:System.Windows.Controls.Control.Template%2A>. Jeśli nie ma szablonu na podstawie domyślnych stylów, formant bez szablonu niestandardowego w ramach stylu niestandardowego nie będzie w ogóle widoczny. Szablon z stylu domyślnego zapewnia wizualnemu wyglądowi poszczególnych kontrolek, a także definiuje połączenia między właściwościami zdefiniowanymi w drzewie wizualnym szablonu i odpowiednią klasą formantów. Każda kontrolka uwidacznia zestaw właściwości, które mogą mieć wpływ na wygląd formantu, bez całkowitego zastępowania szablonu. Rozważmy na przykład domyślny wygląd formantu <xref:System.Windows.Controls.Primitives.Thumb>, który jest składnikiem <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 <xref:System.Windows.Controls.Primitives.Thumb> ma pewne właściwości, które można dostosowywać. Szablon domyślny <xref:System.Windows.Controls.Primitives.Thumb> tworzy podstawową strukturę/drzewo wizualne z kilkoma składnikami zagnieżdżonych <xref:System.Windows.Controls.Border> do tworzenia wyglądu skosu. Jeśli właściwość będąca częścią szablonu ma być udostępniona do dostosowania przez klasę <xref:System.Windows.Controls.Primitives.Thumb>, ta właściwość musi być udostępniona przez [szablonbinding](templatebinding-markup-extension.md)w ramach szablonu. W przypadku <xref:System.Windows.Controls.Primitives.Thumb>różne właściwości tych obramowań współdzielą powiązanie szablonu z właściwościami, takimi jak <xref:System.Windows.Controls.Border.Background%2A> lub <xref:System.Windows.Controls.Border.BorderThickness%2A>. Jednak niektóre inne właściwości lub elementy wizualne są na stałe kodowane w szablonie kontrolki lub są powiązane z wartościami, które pochodzą bezpośrednio z motywu, i nie mogą być zmieniane krótko od zastąpienia całego szablonu. Ogólnie rzecz biorąc, jeśli właściwość pochodzi z szablonu nadrzędnego i nie jest udostępniana przez powiązanie szablonu, nie może być dostosowywana przez style, ponieważ nie istnieje łatwy sposób na jego kierowanie. Jednak ta właściwość może mieć wpływ na dziedziczenie wartości właściwości w zastosowaniu szablonu lub przez wartość domyślną.  
  
 Style motywów używają typu jako klucza w ich definicjach. Jeśli jednak motywy są stosowane do danego wystąpienia elementu, wyszukiwanie motywów dla tego typu jest wykonywane przez sprawdzenie właściwości <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> w kontrolce. Jest to w przeciwieństwie do używania typu literału, jako style niejawne. Wartość <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> dziedziczyć do klas pochodnych, nawet jeśli realizator nie zmienił się (zamierzony sposób zmiany właściwości nie zastępuje go na poziomie właściwości, ale zamiast zmienić wartość domyślną w metadanych właściwości). To pośrednika umożliwia klasom bazowym Definiowanie stylów motywu dla elementów pochodnych, które w przeciwnym razie nie mają stylu (lub co ważniejsze, nie mają szablonu w tym stylu i w rezultacie nie mają domyślnego wyglądu wizualizacji). W tym celu można utworzyć `MyButton` z <xref:System.Windows.Controls.Button> i nadal będzie <xref:System.Windows.Controls.Button> szablon domyślny. Jeśli jesteś autorem formantu `MyButton` i chcesz mieć inne zachowanie, możesz zastąpić metadane właściwości zależności dla <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> na `MyButton`, aby zwracały inny klucz, a następnie zdefiniować odpowiednie style motywu, w tym szablon dla `MyButton` musisz spakować swój pakiet z kontrolką `MyButton`. Aby uzyskać więcej informacji na temat motywów, stylów i tworzenia formantów, zobacz temat [Tworzenie kontroli — Omówienie](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dynamiczne odwołania i powiązania zasobów  
 Odwołania do zasobów dynamicznych i operacje powiązania respektują pierwszeństwo lokalizacji, w której są ustawione. Na przykład zasób dynamiczny zastosowany do wartości lokalnej działa na element priorytet 3, powiązanie dla metody ustawiającej właściwość w stylu motywu stosuje się do elementu pierwszeństwa 9 i tak dalej. Ponieważ dynamiczne odwołania i powiązania zasobów muszą być w stanie uzyskać wartości z stanu czasu wykonywania aplikacji, oznacza to, że rzeczywisty proces określania pierwszeństwa wartości właściwości dla danej właściwości rozciąga się również na czas wykonywania.  
  
 Odwołania do zasobów dynamicznych nie są ściśle wymawiane jako część systemu właściwości, ale mają kolejność wyszukiwania, które współdziałają z sekwencją wymienioną powyżej. Ten priorytet jest udokumentowany dokładniej w [zasobach XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md). Podstawowe podsumowanie tego pierwszeństwa to: element do strony głównej, aplikacja, motyw, system.  
  
 Zasoby dynamiczne i powiązania mają pierwszeństwo w miejscu, w którym zostały ustawione, ale wartość jest odroczona. Jedną z konsekwencji tego jest to, że jeśli ustawisz zasób dynamiczny lub powiązanie z wartością lokalną, każda zmiana wartości lokalnej spowoduje całkowite zastąpienie zasobu dynamicznego lub powiązania. Nawet jeśli wywołasz metodę <xref:System.Windows.DependencyObject.ClearValue%2A>, aby wyczyścić wartość ustawienia lokalnie, zasób dynamiczny lub powiązanie nie zostaną przywrócone. W rzeczywistości, jeśli wywołasz <xref:System.Windows.DependencyObject.ClearValue%2A> na właściwości, która ma zasób dynamiczny lub powiązanie w miejscu (bez literału wartości lokalnej), są one wyczyszczone przez wywołanie <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 Metoda <xref:System.Windows.DependencyObject.SetCurrentValue%2A> jest innym sposobem ustawiania właściwości, ale nie jest w kolejności pierwszeństwa. Zamiast tego <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umożliwia zmianę wartości właściwości bez zastępowania źródła poprzedniej wartości. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> można użyć w dowolnym momencie, gdy chcesz ustawić wartość bez nadawania tej wartości pierwszeństwa wartości lokalnej. Na przykład, jeśli właściwość jest ustawiona przez wyzwalacz, a następnie przypisano kolejną wartość za pośrednictwem <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, system właściwości nadal uwzględnia wyzwalacz i właściwość zostanie zmieniona w przypadku wystąpienia akcji wyzwalacza. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umożliwia zmianę wartości właściwości bez podawania jej źródła o wyższym priorytecie. Analogicznie, można użyć <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, aby zmienić wartość właściwości bez zastępowania powiązania.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Wymuszone, animacje i wartość podstawowa  
 Wymuszone i animacje działają na wartości, która jest określana jako "wartość podstawowa" w tym zestawie SDK. Wartość podstawowa jest tak samo, jak każda wartość jest określana za pomocą oceny w górę elementów do momentu osiągnięcia elementu 2.  
  
 W przypadku animacji wartość podstawowa może mieć wpływ na wartość animowaną, jeśli animacja nie określa zarówno "od", jak i "do" w przypadku niektórych zachowań, lub jeśli animacja celowo wraca do wartości podstawowej po zakończeniu. Aby to sprawdzić, należy uruchomić [przykład z wartościami docelowymi od, do i przez animację](https://go.microsoft.com/fwlink/?LinkID=159988). Spróbuj ustawić wartości lokalne wysokości prostokąta w przykładzie, tak że początkowa wartość lokalna różni się od dowolnego "od" w animacji. Zauważ, że animacje zaczynają od razu przy użyciu wartości "od" i Zastąp wartość bazową po rozpoczęciu. Animacja może wskazywać na powrót do wartości znalezionej przed wykonaniem animacji przez określenie <xref:System.Windows.Media.Animation.FillBehavior>zatrzymania. Następnie normalne pierwszeństwo jest używane do określania wartości podstawowych.  
  
 Do pojedynczej właściwości można zastosować wiele animacji, a każde z tych animacji prawdopodobnie zostało zdefiniowane z różnych punktów w pierwszeństwie wartości. Jednak te animacje będą potencjalnie złożone ich wartości, a nie tylko stosują animację z wyższego poziomu. Jest to zależne od tego, jak są zdefiniowane animacje, i typ wartości, która jest animowana. Aby uzyskać więcej informacji na temat animowania właściwości, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
 Wymuszone zastosowanie jest najwyższego poziomu. Nawet już uruchomione animacje podlegają wykorzystaniu wartości. Niektóre istniejące właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają wbudowane przymusy. Dla właściwości zależności niestandardowej definiuje się zachowanie przymusu dla właściwości zależności niestandardowej przez zapisanie <xref:System.Windows.CoerceValueCallback> i przekazanie wywołania zwrotnego w ramach metadanych podczas tworzenia właściwości. Możesz również zastępować zachowanie przymusu istniejących właściwości, zastępując metadane tej właściwości w klasie pochodnej. Wymuszona interakcja z wartością bazową w taki sposób, że ograniczenia dotyczące przymusu są stosowane, ponieważ te ograniczenia istnieją w danym momencie, ale wartość podstawowa nadal jest zachowywana. W związku z tym, jeśli ograniczenia w wymuszeniu zostaną później zniesione, wymuszone zwróci najbliższą wartość możliwą do tej wartości bazowej, a potencjalnie wpływ przekształcenia na Właściwość przestanie obowiązywać, gdy tylko zostaną zniesione wszystkie ograniczenia. Aby uzyskać więcej informacji o zachowaniu przekształcenia, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Zachowania wyzwalacza  
 Formanty często definiują zachowania wyzwalacza jako część stylu domyślnego w motywach. Ustawienie właściwości lokalnych w kontrolkach może uniemożliwić wyzwalaczom reagowanie na zdarzenia sterowane przez użytkownika albo wizualnie lub w sposób behawioralny. Najbardziej typowym zastosowaniem wyzwalacza właściwości jest właściwości kontrolki lub stanu, takie jak <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Na przykład domyślnie, gdy <xref:System.Windows.Controls.Button> jest wyłączone (wyzwalacz dla <xref:System.Windows.UIElement.IsEnabled%2A> jest `false`), a następnie wartość <xref:System.Windows.Controls.Control.Foreground%2A> w stylu motywu, co powoduje, że kontrolka ma być wyświetlana "wyszarzona". Ale jeśli ustawiono wartość <xref:System.Windows.Controls.Control.Foreground%2A> lokalnego, normalny kolor szary zostanie zastąpiony pierwszeństwem przez lokalny zestaw właściwości, nawet w tym scenariuszu wyzwalanym przez właściwość. Należy zachować ostrożność ustawiania wartości dla właściwości, które mają zachowania wyzwalacza na poziomie motywu i upewnić się, że nie są niesłusznie zakłócane dla zamierzonego środowiska użytkownika dla tego formantu.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue i pierwszeństwo wartości  
 Metoda <xref:System.Windows.DependencyObject.ClearValue%2A> umożliwia wyczyszczenie wszystkich lokalnie zastosowanych wartości z właściwości zależności, która jest ustawiona dla elementu. Wywołanie <xref:System.Windows.DependencyObject.ClearValue%2A> nie jest jednak gwarancją, że wartość domyślna ustalona w metadanych podczas rejestracji właściwości jest nową wartością efektywną. Wszyscy inni uczestnicy w pierwszeństwie wartości są nadal aktywni. Tylko wartość ustawienia lokalnego została usunięta z sekwencji pierwszeństwa. Na przykład jeśli wywołasz <xref:System.Windows.DependencyObject.ClearValue%2A> na właściwości, w której właściwość jest również ustawiana przez styl motywu, wartość motywu zostanie zastosowana jako nowa wartość zamiast wartości domyślnej opartej na metadanych. Jeśli chcesz przyjmować wszystkie uczestnicy wartości właściwości z procesu i ustawić wartość domyślną zarejestrowanej metadanych, możesz uzyskać tę wartość domyślną ostatecznie, wykonując zapytania dotyczące metadanych właściwości zależności, a następnie można użyć wartości domyślnej do lokalnego Ustaw właściwość z wywołaniem do <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Wywołania zwrotne i weryfikacja właściwości zależności](dependency-property-callbacks-and-validation.md)
