---
title: Kody nazw XAML
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: f9d4439c6b102d0d430b5201e3649985daee0b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186274"
---
# <a name="wpf-xaml-namescopes"></a>Zakresy nazw WPF XAML
Namescopes XAML to koncepcja identyfikujących obiekty zdefiniowane w języku XAML. Nazwy w namescope XAML mogą służyć do ustanawiania relacji między nazwami obiektów zdefiniowanymi przez XAML a ich odpowiednikami wystąpień w drzewie obiektów. Zazwyczaj numery nazw XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w kodzie zarządzanym są tworzone podczas ładowania poszczególnych katalogów głównych stron XAML dla aplikacji XAML. XAML namescopes jako obiekt programowania <xref:System.Windows.Markup.INameScope> są definiowane przez interfejs i <xref:System.Windows.NameScope>są również implementowane przez klasę praktyczną .  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>
## <a name="namescopes-in-loaded-xaml-applications"></a>Namescopes w załadowanych aplikacjach XAML  
 W szerszym kontekście programowania lub informatyki pojęcia programowania często zawierają zasadę unikatowego identyfikatora lub nazwy, które mogą być używane do uzyskiwania dostępu do obiektu. W przypadku systemów, które używają identyfikatorów lub nazw, namescope definiuje granice, w których proces lub technika będą wyszukiwać, jeśli żądany jest obiekt o tej nazwie, lub granice, w których unikatowość identyfikujących nazw jest wymuszana. Te ogólne zasady są prawdziwe dla nazw XAML. W WPF WPF XAML namescopes są tworzone na elemencie głównym dla strony XAML po załadowaniu strony. Każda nazwa określona na stronie XAML, zaczynając od katalogu głównego strony, jest dodawana do odpowiedniego kodu nazw XAML.  
  
 W WPF XAML elementy, które są <xref:System.Windows.Controls.Page>typowe <xref:System.Windows.Window>elementy główne (takie jak i ) zawsze kontrolować xaml namescope. Jeśli element, <xref:System.Windows.FrameworkElement> taki <xref:System.Windows.FrameworkContentElement> jak lub jest elementem głównym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony w <xref:System.Windows.Controls.Page> znacznikach, procesor <xref:System.Windows.Controls.Page> dodaje katalog główny niejawnie, dzięki czemu można podać działający namescope XAML.  
  
> [!NOTE]
> Akcje kompilacji WPF utworzyć xaml namescope dla produkcji `Name` `x:Name` XAML, nawet jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie lub atrybuty są zdefiniowane na żadnych elementów w znacznikach.  
  
 Jeśli spróbujesz użyć tej samej nazwy dwa razy w dowolnym askopie nazw XAML, zostanie zgłoszony wyjątek. Dla WPF XAML, który ma związane z kodem i jest częścią skompilowaną aplikację, wyjątek jest wywoływany w czasie kompilacji przez akcje kompilacji WPF podczas tworzenia wygenerowanej klasy dla strony podczas kompilacji znaczników początkowych. W przypadku języka XAML, który nie jest skompilowany przez żadną akcję kompilacji, wyjątki związane z problemami z zakresu nazw XAML mogą być wywoływane podczas ładowania kodu XAML. Projektanci XAML mogą również przewidywać problemy z emocie XAML w czasie projektowania.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Dodawanie obiektów do drzew obiektów środowiska wykonawczego  
 Moment, w którym XAML jest analizowany reprezentuje moment w czasie, że WPF XAML namescope jest tworzony i definiowany. Jeśli obiekt zostanie dodany do drzewa obiektów w momencie po przeanalizowaniu kodu XAML, w tym pliku XAML, wartość `Name` lub `x:Name` wartość nowego obiektu nie spowoduje automatycznej aktualizacji informacji w oskopie nazw XAML. Aby dodać nazwę obiektu do namescope WPF XAML po załadowaniu XAML, <xref:System.Windows.Markup.INameScope.RegisterName%2A> należy wywołać odpowiednią implementację na obiekcie, który definiuje xaml namescope, który jest zazwyczaj katalog główny strony XAML. Jeśli nazwa nie jest zarejestrowana, dodany obiekt nie może <xref:System.Windows.FrameworkElement.FindName%2A>odwoływać się za pomocą nazwy za pomocą metod, takich jak , i nie można użyć tej nazwy do kierowania animacji.  
  
 Najbardziej typowym scenariuszem dla deweloperów <xref:System.Windows.FrameworkElement.RegisterName%2A> aplikacji jest to, że będzie używany do rejestrowania nazw w xaml namescope w bieżącym katalogu głównym strony. <xref:System.Windows.FrameworkElement.RegisterName%2A>jest częścią ważnego scenariusza dla scenoki, które są przeznaczone dla obiektów animacji. Aby uzyskać więcej informacji, zobacz [Omówienie scenoki .](../graphics-multimedia/storyboards-overview.md)  
  
 Jeśli wywołasz <xref:System.Windows.FrameworkElement.RegisterName%2A> obiekt inny niż obiekt definiujący xaml namescope, nazwa jest nadal zarejestrowana w obiekcie nazw XAML, <xref:System.Windows.FrameworkElement.RegisterName%2A> w którego znajduje się obiekt wywołujący, tak jak w przypadku wywołania obiektu definiującego nazwę XAML.  
  
### <a name="xaml-namescopes-in-code"></a>Nameoskopy XAML w kodzie  
 W kodzie można tworzyć, a następnie używać nazw XAML. Interfejsy API i pojęcia związane z tworzeniem xaml namescope są takie same nawet dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użycia czystego kodu, ponieważ procesor XAML używa tych interfejsów API i pojęć podczas przetwarzania samego kodu XAML. Pojęcia i interfejs API istnieją głównie w celu znalezienia obiektów według nazwy w drzewie obiektów, który jest zazwyczaj zdefiniowany częściowo lub całkowicie w XAML.  
  
 W przypadku aplikacji, które są tworzone programowo, a nie z załadowanego XAML, <xref:System.Windows.Markup.INameScope>obiekt definiujący namescope XAML musi implementować lub być klasą lub <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> pochodną, aby obsługiwać tworzenie identyfikatora XAML w jego wystąpieniach.  
  
 Ponadto dla każdego elementu, który nie jest ładowany i przetwarzany przez procesor XAML, xaml namescope dla obiektu nie jest tworzony lub inicjowany domyślnie. Należy jawnie utworzyć nowy identyfikator XAML dla dowolnego obiektu, który ma zarejestrować nazwy później. Aby utworzyć namescope XAML, należy <xref:System.Windows.NameScope.SetNameScope%2A> wywołać metodę statyczną. Określ obiekt, który będzie `dependencyObject` właścicielem go <xref:System.Windows.NameScope.%23ctor%2A> jako parametr i `value` nowy wywołać konstruktora jako parametr.  
  
 Jeśli obiekt przewidziany jako `dependencyObject` <xref:System.Windows.Markup.INameScope> nie <xref:System.Windows.FrameworkElement> <xref:System.Windows.NameScope.SetNameScope%2A> jest <xref:System.Windows.FrameworkContentElement>implementacją lub , wywołanie <xref:System.Windows.FrameworkElement.RegisterName%2A> żadnych elementów podrzędnych nie będzie miało wpływu. Jeśli nie uda się utworzyć nowego kodu nazw XAML jawnie, następnie wywoła <xref:System.Windows.FrameworkElement.RegisterName%2A> wyjątek.  
  
 Na przykład użycia interfejsów API xaml namescope w kodzie zobacz [Definiowanie zakresu nazw](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>
## <a name="xaml-namescopes-in-styles-and-templates"></a>Nameoskopy XAML w stylach i szablonach  
 Style i szablony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwiają ponowne użycie i ponowne naliżenie zawartości w prosty sposób. Jednak style i szablony mogą również zawierać elementy z nazwami XAML zdefiniowanymi na poziomie szablonu. Ten sam szablon może być używany wiele razy na stronie. Z tego powodu style i szablony definiują własne identyfikatory XAML, niezależnie od lokalizacji w drzewie obiektów, w którym stosowany jest styl lub szablon.  
  
 Rozważmy następujący przykład:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 W tym miejscu ten sam szablon jest stosowany do dwóch różnych przycisków. Jeśli szablony nie miały dyskretnych nazw XAML, `TheBorder` nazwa używana w szablonie spowodowałaby kolizję nazw w oskopie nazw XAML. Każde wystąpienie szablonu ma swój własny identyfikator XAML, więc w tym przykładzie każdy koliilat szablonu XAML namescope będzie zawierać dokładnie jedną nazwę.  
  
 Style definiują również własny iemoskop XAML, głównie po to, aby części scenokreślonych mogły mieć przypisane określone nazwy. Nazwy te umożliwiają kontrolowanie określonych zachowań, które będą kierowane na elementy tej nazwy, nawet jeśli szablon został ponownie zdefiniowany jako część dostosowywania formantu.  
  
 Ze względu na oddzielne identyfikatory XAML znajdowanie nazwanych elementów w szablonie jest trudniejsze niż znalezienie elementu o nazwie nieprzy szablonach na stronie. Najpierw należy określić zastosowany szablon, <xref:System.Windows.Controls.Control.Template%2A> uzyskując wartość właściwości formantu, w którym szablon jest stosowany. Następnie należy wywołać wersję <xref:System.Windows.FrameworkTemplate.FindName%2A>szablonu , przekazując formant, w którym szablon został zastosowany jako drugi parametr.  
  
 Jeśli jesteś autorem formantu i generujesz konwencję, w której określony nazwany element w zastosowanym szablonie jest <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> obiektem docelowym dla zachowania zdefiniowanego przez sam formant, możesz użyć tej metody z kodu implementacji formantu. Metoda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> jest chroniona, więc tylko autor formantu ma do niej dostęp.  
  
 Jeśli pracujesz z poziomu szablonu i musisz przejść do kodu nazw XAML, w <xref:System.Windows.FrameworkElement.TemplatedParent%2A>którym zastosowano szablon, uzyskaj wartość programu , a następnie zadzwoń <xref:System.Windows.FrameworkElement.FindName%2A> tam. Przykładem pracy w szablonie byłoby, jeśli piszesz implementacji programu obsługi zdarzeń, gdzie zdarzenie zostanie podniesione z elementu w szablonie zastosowane.  
  
<a name="Namescopes_and_Name_related_APIs"></a>
## <a name="xaml-namescopes-and-name-related-apis"></a>Namescopes XAML i interfejsy API związane z nazwami  
 <xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkElement.RegisterName%2A> i <xref:System.Windows.FrameworkElement.FindName%2A> <xref:System.Windows.FrameworkElement.UnregisterName%2A> metod. Jeśli obiekt, który wywoływasz te metody na posiada namescope XAML, metody wywołać metody odpowiedniego namescope XAML. W przeciwnym razie element nadrzędny jest sprawdzany, aby sprawdzić, czy jest właścicielem zakresu nazw XAML, a ten proces jest kontynuowany rekurencyjnie, dopóki nie zostanie znaleziony namescope XAML (ze względu na zachowanie procesora XAML, istnieje gwarancję, że w katalogu głównym znajduje się xaml namescope). <xref:System.Windows.FrameworkContentElement>ma analogiczne zachowania, z wyjątkiem <xref:System.Windows.FrameworkContentElement> tego, że nikt nigdy nie będzie właścicielem namescope XAML. Metody istnieją <xref:System.Windows.FrameworkContentElement> na tak, że wywołania mogą <xref:System.Windows.FrameworkElement> być przekazywane po pewnym czasie do elementu nadrzędnego.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>służy do mapowania nowego miernika nazw XAML na istniejący obiekt. Można wywołać <xref:System.Windows.NameScope.SetNameScope%2A> więcej niż jeden raz, aby zresetować lub wyczyścić xaml namescope, ale nie jest to typowe użycie. Ponadto <xref:System.Windows.NameScope.GetNameScope%2A> nie jest zwykle używany z kodu.  
  
### <a name="xaml-namescope-implementations"></a>Implementacje xaml namescope  
 Następujące klasy <xref:System.Windows.Markup.INameScope> implementują bezpośrednio:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>nie używa nazw XAML ani nazw; zamiast tego używa kluczy, ponieważ jest to implementacja słownika. Jedynym <xref:System.Windows.ResourceDictionary> powodem, <xref:System.Windows.Markup.INameScope> który implementuje jest więc może podnieść wyjątki do kodu użytkownika, które <xref:System.Windows.ResourceDictionary> pomagają wyjaśnić rozróżnienie między true XAML namescope i jak <xref:System.Windows.ResourceDictionary> obsługuje klucze, a także w celu zapewnienia, że xaml namescopes nie są stosowane do elementów nadrzędnych.  
  
 <xref:System.Windows.FrameworkTemplate>i <xref:System.Windows.Style> <xref:System.Windows.Markup.INameScope> implementować za pomocą jawnych definicji interfejsu. Jawne implementacje pozwalają te xaml namescopes zachowywać się <xref:System.Windows.Markup.INameScope> konwencjonalnie, gdy są one dostępne za [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pośrednictwem interfejsu, który jest jak XAML namescopes są przekazywane przez procesy wewnętrzne. Ale jawne definicje interfejsu nie są częścią <xref:System.Windows.FrameworkTemplate> <xref:System.Windows.Style>konwencjonalnej powierzchni interfejsu API <xref:System.Windows.Markup.INameScope> i <xref:System.Windows.FrameworkTemplate> , <xref:System.Windows.Style> ponieważ rzadko trzeba wywołać metody <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>i bezpośrednio, a zamiast tego użyje innych interfejsów API, takich jak .  
  
 Następujące klasy definiują własne namescope XAML, przy użyciu klasy <xref:System.Windows.NameScope?displayProperty=nameWithType> pomocnika i łączenie <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> się z jego implementacji xaml namescope za pośrednictwem dołączonej właściwości:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Zobacz też

- [Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name — dyrektywa](../../../desktop-wpf/xaml-services/xname-directive.md)
