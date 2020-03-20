---
title: Następstwo zależności wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 1d7c644c7f7581a96ffff1a0fe1fcf2adfe071e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186146"
---
# <a name="dependency-property-value-precedence"></a>Następstwo zależności wartości właściwości
<a name="introduction"></a>W tym temacie wyjaśniono, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jak działanie systemu właściwości może mieć wpływ na wartość właściwości zależności i opisuje pierwszeństwo, przez które aspekty systemu właściwości mają zastosowanie do efektywnej wartości właściwości.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz właściwości zależności z perspektywy konsumenta istniejących właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasach i masz dowiesz się o [przeglądzie właściwości zależności.](dependency-properties-overview.md) Aby postępować zgodnie z przykładami w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tym temacie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy również zrozumieć i wiedzieć, jak pisać aplikacje.  
  
<a name="intro"></a>
## <a name="the-wpf-property-system"></a>System właściwości WPF  
 System [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości oferuje potężny sposób, aby wartość właściwości zależności być określone przez wiele czynników, włączając funkcje, takie jak sprawdzanie poprawności właściwości w czasie rzeczywistym, późne powiązanie i powiadamiania powiązanych właściwości zmian wartości dla innych właściwości. Dokładna kolejność i logika, która jest używana do określania wartości właściwości zależności jest dość skomplikowane. Znajomość tej kolejności pomoże Ci uniknąć niepotrzebnego ustawienia właściwości, a także może wyjaśnić zamieszanie dotyczące dokładnie dlaczego niektóre próby wpływania lub przewidywania wartości właściwości zależności nie zakończyły się wynikiem oczekiwanej wartości.  
  
<a name="multiple_sets"></a>
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Właściwości zależności mogą być "Ustaw" w wielu miejscach  
 Oto przykład, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gdzie ta<xref:System.Windows.Controls.Control.Background%2A>sama właściwość ( ) ma trzy różne operacje "set", które mogą mieć wpływ na wartość.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 W tym miejscu, który kolor, którego oczekujesz, będzie miał zastosowanie — czerwony, zielony lub niebieski?  
  
 Z wyjątkiem animowanych wartości i przymusu, lokalne zestawy właściwości są ustawione na najwyższym priorytecie. Jeśli ustawisz wartość lokalnie można oczekiwać, że wartość zostanie uwzględniona, nawet powyżej wszystkich stylów lub szablonów formantów. W tym miejscu <xref:System.Windows.Controls.Control.Background%2A> w przykładzie jest ustawiona na Czerwony lokalnie. W związku z tym styl zdefiniowany w tym zakresie, mimo że jest to niejawny styl, który w przeciwnym <xref:System.Windows.Controls.Control.Background%2A> razie stosuje się do wszystkich elementów tego typu w tym zakresie, nie jest najwyższy priorytet nadając właściwości jego wartość.  Jeśli usunięto wartość lokalną Red z tego Button wystąpienia, styl będzie miał pierwszeństwo i przycisk będzie uzyskać background wartość ze stylu.  W stylu wyzwalacze mają pierwszeństwo, więc przycisk będzie niebieski, jeśli mysz jest nad nim, a zielony w przeciwnym razie.  
  
<a name="listing"></a>
## <a name="dependency-property-setting-precedence-list"></a>Lista priorytetów ustawienia właściwości zależności  
 Poniżej znajduje się ostateczna kolejność, która używa system właściwości podczas przypisywania wartości czasu wykonywania właściwości zależności. Najwyższy priorytet jest wymieniony jako pierwszy. Ta lista rozszerza się na niektóre uogólnienia dokonane w [przeglądzie właściwości zależności](dependency-properties-overview.md).  
  
1. **Przymus systemu własności.** Aby uzyskać szczegółowe informacje na temat przymusu, zobacz [Przymus, Animacja i Wartość podstawowa](#animations) w dalszej części tego tematu.  
  
2. **Aktywne animacje lub animacje z zachowaniem Hold.** Aby uzyskać jakiekolwiek praktyczne skutki, animacja właściwości musi mieć pierwszeństwo przed wartością podstawową (bezanimowana), nawet jeśli ta wartość została ustawiona lokalnie. Aby uzyskać szczegółowe informacje, zobacz [Przymus, Animacja i Wartość podstawowa](#animations) w dalszej części tego tematu.  
  
3. **Wartość lokalna.** Wartość lokalna może być ustawiona za pomocą wygody właściwości "otoka", która również równa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]się ustawieniu jako <xref:System.Windows.DependencyObject.SetValue%2A> atrybutu lub elementu właściwości w , lub wywołanie interfejsu API przy użyciu właściwości określonego wystąpienia. Jeśli ustawisz wartość lokalną przy użyciu powiązania lub zasobu, każdy z nich działa w priorytecie, tak jakby ustawiono wartość bezpośrednią.  
  
4. **Właściwości szablonu TemplatedParent.** Element <xref:System.Windows.FrameworkElement.TemplatedParent%2A> ma, jeśli został utworzony jako część <xref:System.Windows.Controls.ControlTemplate> szablonu (a lub <xref:System.Windows.DataTemplate>). Aby uzyskać szczegółowe informacje na temat tego, kiedy ma to zastosowanie, zobacz [TemplatedParent](#templatedparent) w dalszej części tego tematu. W szablonie stosuje się następujące pierwszeństwo:  
  
    1. Wyzwalacze z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu.  
  
    2. Zestawy właściwości (zazwyczaj [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] za pomocą <xref:System.Windows.FrameworkElement.TemplatedParent%2A> atrybutów) w szablonie.  
  
5. **Styl niejawny.** Dotyczy tylko `Style` obiektu. Właściwość jest wypełniona `Style` przez dowolny zasób stylu z kluczem, który pasuje do typu tego elementu. Ten zasób stylu musi istnieć na stronie lub w aplikacji; wyszukiwanie zasobu stylu niejawnego nie przechodzi do tematów.  
  
6. **Wyzwalacze stylu.** Wyzwalacze w stylach ze strony lub aplikacji (style te mogą być jawne lub niejawne style, ale nie od domyślnych stylów, które mają niższy priorytet).  
  
7. **Wyzwalacze szablonów.** Dowolny wyzwalacz z szablonu w obrębie stylu lub bezpośrednio zastosowany szablon.  
  
8. **Ustawianie stylu.** Wartości z <xref:System.Windows.Setter> w obrębie stylów ze strony lub aplikacji.  
  
9. **Domyślny (motyw).** Aby uzyskać szczegółowe informacje o tym, kiedy ma to zastosowanie i jak style motywów odnoszą się do szablonów w stylach motywów, zobacz [Domyślne style (motyw)](#themestyles) w dalszej części tego tematu. W ramach domyślnego stylu obowiązuje następująca kolejność pierwszeństwa:  
  
    1. Aktywne wyzwalacze w stylu motywu.  
  
    2. Setters w stylu motywu.  
  
10. **Dziedziczenia.** Kilka właściwości zależności dziedziczą swoje wartości z elementu nadrzędnego do elementów podrzędnych, tak, że nie muszą być ustawione specjalnie na każdy element w całej aplikacji. Aby uzyskać szczegółowe informacje, zobacz [Dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
11. **Wartość domyślna z metadanych właściwości zależności.** Każda dana właściwość zależności może mieć wartość domyślną ustaloną przez rejestrację systemu właściwości tej konkretnej właściwości. Ponadto klasy pochodne, które dziedziczą właściwość zależności mają możliwość zastąpienia tych metadanych (w tym wartości domyślnej) na podstawie typu. Aby uzyskać więcej informacji, zobacz [Metadane właściwości zależności.](dependency-property-metadata.md) Ponieważ dziedziczenie jest sprawdzane przed wartością domyślną, dla właściwości dziedziczonej wartość domyślna elementu nadrzędnego ma pierwszeństwo przed elementem podrzędnym.  W związku z tym jeśli dziedziczna właściwość nie jest ustawiona w dowolnym miejscu, wartość domyślna określona w katalogu głównym lub nadrzędnym jest używana zamiast wartości domyślnej elementu podrzędnego.  
  
<a name="templatedparent"></a>
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako element pierwszeństwa nie ma zastosowania do żadnej właściwości elementu, który deklarujesz bezpośrednio w standardowych znaczników aplikacji. TemplatedParent pojęcie istnieje tylko dla elementów podrzędnych w drzewie wizualnym, które powstają za pośrednictwem aplikacji szablonu. Gdy system właściwości <xref:System.Windows.FrameworkElement.TemplatedParent%2A> przeszukuje szablon w poszukiwaniu wartości, przeszukuje szablon, który utworzył ten element. Wartości właściwości z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> szablonu zazwyczaj działają tak, jakby zostały ustawione jako wartość lokalna w elemencie podrzędnym, ale ten mniejszy priorytet w porównaniu do wartości lokalnej istnieje, ponieważ szablony są potencjalnie współużytkowane. Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>
## <a name="the-style-property"></a>Właściwość Style  
 Kolejność wyszukiwania opisane wcześniej stosuje się do wszystkich możliwych właściwości zależności <xref:System.Windows.FrameworkElement.Style%2A> z wyjątkiem jednego: właściwości. Właściwość jest unikatowa, <xref:System.Windows.FrameworkElement.Style%2A> ponieważ nie można sama stylizować, więc elementy pierwszeństwa od 5 do 8 nie mają zastosowania. Ponadto animowanie lub wymuszanie <xref:System.Windows.FrameworkElement.Style%2A> nie jest zalecane <xref:System.Windows.FrameworkElement.Style%2A> (a animowanie wymagałoby niestandardowej klasy animacji). Pozostawia to trzy <xref:System.Windows.FrameworkElement.Style%2A> sposoby, które można ustawić właściwość:  
  
- **Styl jawny.** Obiekt <xref:System.Windows.FrameworkElement.Style%2A> znajduje się bezpośrednio. W większości scenariuszy styl nie jest zdefiniowany w linii, ale zamiast tego odwołuje się jako zasób, przez jawny klucz. W tym przypadku Style właściwość sama działa tak, jakby była wartość lokalna, pierwszeństwo element 3.  
  
- **Styl niejawny.** Właściwość <xref:System.Windows.FrameworkElement.Style%2A> nie jest ustawiona bezpośrednio. Jednak <xref:System.Windows.FrameworkElement.Style%2A> istnieje na pewnym poziomie w sekwencji wyszukiwania zasobów (strona, aplikacja) i jest kluczem przy użyciu klucza zasobu, który pasuje do typu styl ma być stosowany do. W takim przypadku <xref:System.Windows.FrameworkElement.Style%2A> sama właściwość działa przez pierwszeństwo określone w sekwencji jako element 5. Ten warunek można wykryć przy użyciu <xref:System.Windows.DependencyPropertyHelper> względem <xref:System.Windows.FrameworkElement.Style%2A> właściwości i szuka <xref:System.Windows.BaseValueSource.ImplicitStyleReference> w wynikach.  
  
- **Styl domyślny**, znany również jako **styl motywu.** Właściwość <xref:System.Windows.FrameworkElement.Style%2A> nie jest ustawiona bezpośrednio, a `null` w rzeczywistości będzie odczytywana jako do czasu wykonywania. W takim przypadku styl pochodzi z oceny motywu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] czasie wykonywania, która jest częścią aparatu prezentacji.  
  
 W przypadku stylów niejawnych, które nie są `MyButton` `Button`w motywach, typ musi być `Button`dokładnie zgodny — klasa pochodna nie będzie niejawnie używać stylu dla .  
  
<a name="themestyles"></a>
## <a name="default-theme-styles"></a>Style domyślne (motyw)  
 Każdy formant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostarczany z ma domyślny styl. Ten domyślny styl potencjalnie różni się w zależności od motywu, dlatego ten styl domyślny jest czasami określany jako styl motywu.  
  
 Najważniejsze informacje, które znajduje się w domyślnym stylu formantu jest jego szablon formantu, <xref:System.Windows.Controls.Control.Template%2A> który istnieje w stylu motywu jako ustawiacz dla jego właściwości. Jeśli nie było szablonu ze stylów domyślnych, formant bez szablonu niestandardowego jako część stylu niestandardowego nie miałby żadnego wyglądu. Szablon ze stylu domyślnego nadaje wyglądowi każdego formantu podstawową strukturę, a także definiuje połączenia między właściwościami zdefiniowanymi w drzewie wizualnym szablonu i odpowiedniej klasy formantu. Każdy formant udostępnia zestaw właściwości, które mogą mieć wpływ na wygląd formantu bez całkowitego zastąpienia szablonu. Rozważmy na przykład domyślny <xref:System.Windows.Controls.Primitives.Thumb> wygląd formantu, który <xref:System.Windows.Controls.Primitives.ScrollBar>jest składnikiem elementu .  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> ma pewne właściwości konfigurowalne. Domyślny szablon <xref:System.Windows.Controls.Primitives.Thumb> tworzy podstawową strukturę / drzewo <xref:System.Windows.Controls.Border> wizualne z kilkoma zagnieżdżonymi komponentami, aby utworzyć wygląd skosu. Jeśli właściwość, która jest częścią szablonu jest przeznaczona <xref:System.Windows.Controls.Primitives.Thumb> do naświetlone do dostosowania przez klasę, a następnie właściwość musi być widoczna przez [TemplateBinding](templatebinding-markup-extension.md), w szablonie. W przypadku <xref:System.Windows.Controls.Primitives.Thumb>różnych właściwości tych granic współużytkuje szablon <xref:System.Windows.Controls.Border.Background%2A> powiązanie z właściwościami, takimi jak lub <xref:System.Windows.Controls.Border.BorderThickness%2A>. Jednak niektóre inne właściwości lub układy wizualne są zakodowane na skróty w szablonie formantu lub są powiązane z wartościami, które pochodzą bezpośrednio z motywu i nie można ich zmienić, zastępując cały szablon. Ogólnie rzecz biorąc, jeśli właściwość pochodzi z elementem nadrzędnym szablonu i nie jest narażony przez powiązanie szablonu, nie można dostosować za pomocą stylów, ponieważ nie ma łatwego sposobu kierowania go. Ale na tę właściwość nadal może mieć wpływ dziedziczenie wartości właściwości w zastosowanym szablonie lub wartość domyślna.  
  
 Style motywu używają typu jako klucza w swoich definicjach. Jednak gdy motywy są stosowane do danego wystąpienia elementu, wyszukiwanie motywów dla <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> tego typu jest wykonywane przez sprawdzenie właściwości na formancie. Jest to w przeciwieństwie do korzystania z literału Type, jak style niejawne zrobić. Wartość <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> będzie dziedziczyć do klas pochodnych, nawet jeśli realizator nie zmienił go (zamierzonym sposobem zmiany właściwości nie jest zastąpienie go na poziomie właściwości, ale zamiast tego zmienić jego wartość domyślną w metadanych właściwości). Ta pośrednia umożliwia klas podstawowych do definiowania stylów motywu dla elementów pochodnych, które w przeciwnym razie nie mają stylu (lub co ważniejsze, nie mają szablonu w tym stylu, a zatem nie mają domyślnego wyglądu w ogóle). W związku `MyButton` z tym <xref:System.Windows.Controls.Button> można wyprowadzić <xref:System.Windows.Controls.Button> z i nadal będzie uzyskać szablon domyślny. Jeśli użytkownik jest autorem formantu `MyButton` i chcesz innego zachowania, można zastąpić <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> metadane właściwości zależności `MyButton` na, aby zwrócić inny `MyButton` klucz, a następnie `MyButton` zdefiniować odpowiednie style motywu, w tym szablon, który należy spakować z formantem. Aby uzyskać więcej informacji na temat motywów, stylów i tworzenia formantów, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>
## <a name="dynamic-resource-references-and-binding"></a>Dynamiczne odwołania do zasobów i powiązanie  
 Dynamiczne odwołania do zasobów i operacje wiązania są zgodne z pierwszeństwem lokalizacji, w której są ustawione. Na przykład zasób dynamiczny zastosowany do wartości lokalnej działa na element pierwszeństwa 3, powiązanie dla ustawiającego właściwości w stylu motywu stosuje się w pozycji pierwszeństwa 9 i tak dalej. Ponieważ odwołania do zasobów dynamicznych i powiązania musi być zarówno w stanie uzyskać wartości ze stanu czasu wykonywania aplikacji, oznacza to, że rzeczywisty proces określania pierwszeństwa wartości właściwości dla danej właściwości rozciąga się również w czasie wykonywania.  
  
 Odwołania do zasobów dynamicznych nie są ściśle mówiąc część systemu właściwości, ale mają kolejność wyszukiwania własnych, który współdziała z sekwencji wymienionych powyżej. Pierwszeństwo to jest dokładniej udokumentowane w [zasobach XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md). Podstawowe podsumowanie tego pierwszeństwa to: element do strony root, aplikacja, temat, system.  
  
 Dynamiczne zasoby i powiązania mają pierwszeństwo, gdzie zostały ustawione, ale wartość jest odroczona. Jedną z konsekwencji jest to, że jeśli ustawisz zasób dynamiczny lub powiązanie z wartością lokalną, wszelkie zmiany wartości lokalnej zastępuje zasób dynamiczny lub powiązanie całkowicie. Nawet jeśli wywołasz metodę, <xref:System.Windows.DependencyObject.ClearValue%2A> aby wyczyścić wartość ustawioną lokalnie, zasób dynamiczny lub powiązanie nie zostanie przywrócone. W rzeczywistości jeśli <xref:System.Windows.DependencyObject.ClearValue%2A> wywołasz na właściwość, która ma zasób dynamiczny lub powiązanie w <xref:System.Windows.DependencyObject.ClearValue%2A> miejscu (bez literalnej wartości lokalnej), są one czyszczone przez wywołanie zbyt.  
  
<a name="setcurrentvalue"></a>
## <a name="setcurrentvalue"></a>Wartość setcurrentvalue  
 Metoda <xref:System.Windows.DependencyObject.SetCurrentValue%2A> jest inny sposób, aby ustawić właściwość, ale nie jest w kolejności pierwszeństwa. Zamiast tego <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umożliwia zmianę wartości właściwości bez zastępowania źródła poprzedniej wartości. Można użyć <xref:System.Windows.DependencyObject.SetCurrentValue%2A> w dowolnym momencie, który ma być ustawiony wartość bez nadanie tej wartości pierwszeństwo wartości lokalnej. Na przykład jeśli właściwość jest ustawiona przez wyzwalacz, a następnie przypisana inna wartość za pośrednictwem <xref:System.Windows.DependencyObject.SetCurrentValue%2A>systemu właściwości nadal respektuje wyzwalacz i właściwość zmieni się, jeśli wystąpi akcja wyzwalacza. <xref:System.Windows.DependencyObject.SetCurrentValue%2A>umożliwia zmianę wartości właściwości bez nadanie jej źródła o wyższym priorytecie. Podobnie można zmienić <xref:System.Windows.DependencyObject.SetCurrentValue%2A> wartość właściwości bez zastępowania powiązania.  
  
<a name="animations"></a>
## <a name="coercion-animations-and-base-value"></a>Przymus, animacje i wartość podstawowa  
 Przymus i animacja działają na wartość, która jest określana jako "wartość podstawowa" w tym sdk. Wartość bazowa jest zatem niezależnie od wartości jest określana poprzez ocenę w górę w towarach, aż do osiągnięcia pozycji 2.  
  
 Dla animacji wartość podstawowa może mieć wpływ na wartość animowaną, jeśli ta animacja nie określa zarówno "Od" i "Do" dla niektórych zachowań lub jeśli animacja celowo powraca do wartości podstawowej po zakończeniu. Aby wyświetlić to w praktyce, uruchom [przykład wartości docelowych Od, Do i Według animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues). Spróbuj ustawienie wartości lokalnych wysokości prostokąta w przykładzie, tak, że początkowa wartość lokalna różni się od dowolnego "Od" w animacji. Należy zauważyć, że animacje zaczynają się od razu przy użyciu wartości "Od" i zastąpić wartość podstawową po uruchomieniu. Animacja może określać, aby powrócić do wartości znalezionej przed <xref:System.Windows.Media.Animation.FillBehavior>animacją po jej zakończeniu, określając stop . Następnie normalny priorytet jest używany dla oznaczania wartości podstawowej.  
  
 Wiele animacji mogą być stosowane do jednej właściwości, z każdej z tych animacji ewentualnie zostały zdefiniowane z różnych punktów w priorytecie wartości. Jednak te animacje potencjalnie kompozytują swoje wartości, a nie tylko stosowanie animacji z wyższego priorytetu. Zależy to dokładnie od tego, jak zdefiniowane są animacje i typu wartości, która jest animowana. Aby uzyskać więcej informacji na temat animowania właściwości, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
 Przymus ma zastosowanie na najwyższym poziomie ze wszystkich. Nawet już uruchomiona animacja podlega przymusowi wartości. Niektóre istniejące właściwości zależności [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w mają wbudowane przymusu. Dla właściwości zależności niestandardowej, można zdefiniować zachowanie przymusu dla <xref:System.Windows.CoerceValueCallback> właściwości zależności niestandardowej, zapisując i przekazując wywołanie zwrotne jako część metadanych podczas tworzenia właściwości. Można również zastąpić zachowanie przymusu istniejących właściwości, zastępując metadane na tej właściwości w klasie pochodnej. Przymus współdziała z wartością podstawową w taki sposób, że ograniczenia przymusu są stosowane, ponieważ te ograniczenia istnieją w tym czasie, ale wartość podstawowa jest nadal zachowywana. W związku z tym jeśli ograniczenia w przymusie są później zniesione, przymus zwróci najbliższą możliwą wartość do tej wartości podstawowej i potencjalnie wpływ przymusu na właściwość ustanie, gdy tylko wszystkie ograniczenia zostaną zniesione. Aby uzyskać więcej informacji na temat zachowania przymusu, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>
## <a name="trigger-behaviors"></a>Zachowania wyzwalaczy  
 Formanty często definiują zachowania wyzwalaczy jako część ich domyślnego stylu w motywach. Ustawienie właściwości lokalnych na formanty może uniemożliwić wyzwalacze z możliwości reagowania na zdarzenia sterowane przez użytkownika wizualnie lub behawioralnie. Najczęstszym zastosowaniem wyzwalacza właściwości jest kontrola lub <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>właściwości stanu, takie jak . Na przykład domyślnie, <xref:System.Windows.Controls.Button> gdy jest <xref:System.Windows.UIElement.IsEnabled%2A> wyłączona (wyzwalacz dla jest) `false`to <xref:System.Windows.Controls.Control.Foreground%2A> wartość w stylu motywu jest to, co powoduje, że formant pojawia się "wyszarzone". Ale jeśli ustawiono <xref:System.Windows.Controls.Control.Foreground%2A> wartość lokalną, że normalny kolor szary-out zostanie unieważniony w pierwszeństwo przez zestaw właściwości lokalnych, nawet w tym scenariuszu wyzwalane właściwości. Należy zachować ostrożność ustawiania wartości dla właściwości, które mają zachowania wyzwalacza na poziomie motywu i upewnij się, że nie są nadmiernie zakłócania środowiska zamierzonego użytkownika dla tego formantu.  
  
<a name="clearvalue"></a>
## <a name="clearvalue-and-value-precedence"></a>ClearValue i pierwszeństwo wartości  
 Metoda <xref:System.Windows.DependencyObject.ClearValue%2A> zapewnia celowe środki, aby wyczyścić dowolną wartość stosowane lokalnie z właściwości zależności, która jest ustawiona na element. Jednak wywołanie <xref:System.Windows.DependencyObject.ClearValue%2A> nie jest gwarancją, że domyślne, jak ustalono w metadanych podczas rejestracji właściwości jest nowa wartość efektywna. Wszystkie inne uczestników w pierwszeństwo wartości są nadal aktywne. Tylko lokalnie ustawiona wartość została usunięta z sekwencji pierwszeństwa. Na przykład jeśli <xref:System.Windows.DependencyObject.ClearValue%2A> wywołasz właściwość, w której ta właściwość jest również ustawiona przez styl motywu, wartość motywu jest stosowana jako nowa wartość, a nie domyślnie oparta na metadanych. Jeśli chcesz wyjąć wszystkich uczestników wartości właściwości z procesu i ustawić wartość domyślnie zarejestrowanych metadanych, można uzyskać tę wartość domyślną ostatecznie, odwołując się do <xref:System.Windows.DependencyObject.SetValue%2A>metadanych właściwości zależności, a następnie można użyć wartości domyślnej, aby lokalnie ustawić właściwość z wywołaniem .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Wywołania zwrotne i weryfikacja właściwości zależności](dependency-property-callbacks-and-validation.md)
