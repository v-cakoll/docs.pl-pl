---
title: Zakresy nazw WPF XAML
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
ms.openlocfilehash: c13dba48d21235c57be64d90b6547902e0428a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-xaml-namescopes"></a>Zakresy nazw WPF XAML
XAML namescopes to pojęcie, który identyfikuje obiekty, które zostały zdefiniowane w języku XAML. Nazwy XAML namescope może służyć do ustanawiania relacji między nazwami zdefiniowane XAML obiektów i ich odpowiedniki wystąpienia drzewa obiektów. Zazwyczaj XAML namescopes w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod zarządzany są tworzone podczas ładowania strony XAML poszczególnych katalogów głównych dla aplikacji XAML. Namescopes XAML jako obiekt programowania są definiowane przez <xref:System.Windows.Markup.INameScope> interfejsu i są również zaimplementowany przez klasę praktyczne <xref:System.Windows.NameScope>.  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Namescopes w aplikacjach załadować XAML  
 W szerszym programowania lub w kontekście nauki komputera pojęcia dotyczące programowania często zawierają zasady unikatowego identyfikatora lub nazwy, która może służyć do dostępu do obiektu. Dla systemów, które używają nazwy lub identyfikatory, namescope definiuje granic w ramach którego proces lub metoda umożliwia wyszukiwanie, jeśli wymagany jest obiekt o tej nazwie lub granice, w którym jest wymuszana unikatowość identyfikacji nazwy. Te zasady ogólne mają wartość true dla XAML namescopes. Na platformie WPF XAML namescopes są tworzone w elemencie głównym dla strony XAML podczas ładowania strony. Każda nazwa określona w strony XAML, zaczynając od strony głównej jest dodawany do odpowiednich namescope XAML.  
  
 W języku XAML WPF, elementy, które są wspólne elementy główne (takich jak <xref:System.Windows.Controls.Page>, i <xref:System.Windows.Window>) zawsze kontrolować XAML namescope. Jeśli element, takich jak <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> jest elementem głównym strony w znaczniku, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor dodaje <xref:System.Windows.Controls.Page> niejawnie główny, aby <xref:System.Windows.Controls.Page> zapewniają namescope XAML pracy.  
  
> [!NOTE]
>  Akcje kompilacji WPF utworzyć namescope XAML do produkcji XAML nawet wtedy, gdy nie `Name` lub `x:Name` na żadnego z elementów w zdefiniowanych atrybutów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 Jeśli spróbujesz użyć takiej samej nazwie dwa razy w dowolnym namescope XAML wyjątek. Dla WPF XAML ma związane z kodem, który jest częścią skompilowanej aplikacji jest wyjątek w czasie kompilacji przez akcje kompilacji WPF, tworząc wygenerowanej klasy strony podczas kompilacji znaczników początkowej. Dla języka XAML, który nie jest skompilowany znaczników przez działanie kompilacji wyjątki związane z XAML namescope problemów może zostać wywołane po załadowaniu pliku XAML. Projektant XAML może również przewidywać problemy namescope XAML w czasie projektowania.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Dodawanie obiektów do drzewa obiektu środowiska wykonawczego  
 Obecnie analizy XAML reprezentuje moment w czasie, tworzona i zdefiniowane namescope WPF XAML. Jeśli obiekt zostanie dodany do drzewa obiektów w punkcie w czasie po XAML, wytworzonego tego drzewa analizy, `Name` lub `x:Name` wartość dla nowego obiektu nie jest aktualizowana automatycznie informacje w XAML namescope. Aby dodać nazwę obiektu do namescope WPF XAML po załadowaniu XAML, należy wywołać wprowadzenia <xref:System.Windows.Markup.INameScope.RegisterName%2A> dla obiektu, który definiuje XAML namescope, co jest typowe głównego strony XAML. Jeśli nazwa nie jest zarejestrowany, dodany obiekt nie może odwoływać się nazwy za pomocą metody takie jak <xref:System.Windows.FrameworkElement.FindName%2A>, i nie można użyć tej nazwy do użycia z animacji.  
  
 Najbardziej typowym scenariuszem dla deweloperów aplikacji jest, który będzie używany <xref:System.Windows.FrameworkElement.RegisterName%2A> do rejestracji nazw w namescope XAML w katalogu głównym bieżącej strony. <xref:System.Windows.FrameworkElement.RegisterName%2A> jest częścią scenariusza ważne dla scenorys tego obiektów docelowych dla animacji. Aby uzyskać więcej informacji, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Jeśli wywołujesz <xref:System.Windows.FrameworkElement.RegisterName%2A> do obiektu innego niż obiekt, który definiuje XAML namescope, nazwa jest nadal zarejestrowany na namescope XAML, przechowywana obiekt wywołujący, tak, jakby były nazywane <xref:System.Windows.FrameworkElement.RegisterName%2A> na namescope XAML Definiowanie obiektu.  
  
### <a name="xaml-namescopes-in-code"></a>Namescopes XAML w kodzie  
 Można utworzyć, a następnie użyj XAML namescopes w kodzie. Interfejsy API i pojęcia związane z XAML namescope tworzenia są takie same, nawet w przypadku użycia czystym kodzie, ponieważ procesor XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa tych interfejsów API i koncepcje podczas przetwarzania XAML samej siebie. Koncepcje i interfejsu API istnieje głównie na potrzeby możliwość znalezienia obiektów o nazwie w obrębie drzewa obiektu, który zazwyczaj jest zdefiniowany częściowo lub całkowicie w języku XAML.  
  
 Dla aplikacji, które są tworzone programowo, a nie z załadować XAML, obiekt, który definiuje XAML namescope musi implementować <xref:System.Windows.Markup.INameScope>, lub być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> pochodnej klasy, aby zapewnić obsługę tworzenia XAML namescope na jego wystąpienia.  
  
 Ponadto dla każdego elementu, który nie jest załadowane, a przetworzonych przez procesor XAML, namescope XAML dla obiekt jest nie utworzony lub zainicjowane domyślnie. Jawnie należy utworzyć nowe namescope XAML dla dowolnego obiektu, który ma zostać później zarejestrować nazwy na. Aby utworzyć XAML namescope, należy wywołać statycznych <xref:System.Windows.NameScope.SetNameScope%2A> metody. Określ obiekt, który jest właścicielem go jako `dependencyObject` parametr, a nowy <xref:System.Windows.NameScope.%23ctor%2A> wywołania konstruktora jako `value` parametru.  
  
 Jeśli obiekt jako `dependencyObject` dla <xref:System.Windows.NameScope.SetNameScope%2A> nie jest <xref:System.Windows.Markup.INameScope> implementacji <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, wywoływania <xref:System.Windows.FrameworkElement.RegisterName%2A> na wszystkich podrzędnych elementów nie odniesie żadnego skutku. Jeśli nie można jawnie utworzyć nowe namescope XAML, następnie wywołuje do <xref:System.Windows.FrameworkElement.RegisterName%2A> zgłosi wyjątek.  
  
 Na przykład przy użyciu języka XAML namescope interfejsów API w kodzie, zobacz [definiowanie zakresu nazw](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Namescopes XAML, style i szablony  
 Style i szablonów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferują możliwość ponownego wykorzystania i ponownie zastosuj zawartości w łatwe. Jednak style i szablony może również zawierać elementy o nazwach XAML zdefiniowane na poziomie szablonu. Na stronie tego samego szablonu mogą być używane wiele razy. Z tego powodu style i szablony Definiowanie własnych namescopes XAML, niezależnie od lokalizacji, niezależnie od drzewa obiektów, w których jest stosowane stylu lub szablonie.  
  
 Rozważmy następujący przykład:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 W tym miejscu tego samego szablonu jest stosowane do dwóch różnych przycisków. Jeśli szablony nie miał odrębny namescopes XAML, `TheBorder` nazwę używaną w szablonie spowodowałoby kolizję nazw w XAML namescope. Podczas tworzenia każdego wystąpienia szablonu ma własną namescope XAML, w tym przykładzie namescope XAML każdego szablonu skonkretyzowanym zawiera dokładnie jedną nazwę.  
  
 Style również definiować własne namescope XAML, przede wszystkim dzięki czemu części scenorys mogą mieć określonej nazwy przypisane. Te nazwy Włącz kontroli zachowania określonych przeznaczonych elementy o tej samej nazwie, nawet jeśli szablon został ponownie zdefiniowane jako część Dostosowywanie formantu.  
  
 Ze względu na oddzielnych XAML namescopes wyszukiwanie nazwanych elementów w szablonie jest trudniejsza, niż wyszukiwanie bez szablonu o nazwie elementu na stronie. Najpierw należy określić szablonu zastosowane, pobierając <xref:System.Windows.Controls.Control.Template%2A> wartość właściwości formantu, w którym szablon jest stosowany. Następnie wywołaj metodę wersję szablonu <xref:System.Windows.FrameworkTemplate.FindName%2A>, przekazywanie formantu, gdy szablon została zastosowana jako drugiego parametru.  
  
 Jeśli autor kontroli i jest generowany Konwencję, w której określonego o nazwie elementu w szablonu zastosowane jest elementem docelowym dla zachowania, które jest definiowana za pomocą samej kontrolce, możesz użyć <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metody z kodu realizacji formantu. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Metody jest chroniony, tylko autor formantu ma do niego dostęp.  
  
 Podczas pracy z wewnątrz szablonu, a potrzeba, aby przejść do XAML namescope, w którym szablon jest stosowany uzyskać wartość <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, a następnie wywołać <xref:System.Windows.FrameworkElement.FindName%2A> istnieje. Przykład pracy w szablonie będą, jeśli piszesz implementację programu obsługi zdarzeń gdy zdarzenie zostanie wygenerowany, w elemencie szablonu zastosowane.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML Namescopes i dotyczące nazwy interfejsów API  
 <xref:System.Windows.FrameworkElement> ma <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> i <xref:System.Windows.FrameworkElement.UnregisterName%2A> metody. Jeśli obiekt, który wywołania tych metod w właścicielem XAML namescope, metody wywołania do metody odpowiednich namescope XAML. W przeciwnym razie wartość elementu nadrzędnego jest sprawdzenie, jeśli jest właścicielem XAML namescope, a ten proces jest kontynuowany cyklicznie, aż do znalezienia XAML namescope (ze względu na zachowanie procesora XAML, jest gwarantowana namescope XAML, w katalogu głównym). <xref:System.Windows.FrameworkContentElement> ma analogiczne zachowania, z wyjątkiem tego, który nie <xref:System.Windows.FrameworkContentElement> kiedykolwiek właścicielem XAML namescope. Metody istnieje na <xref:System.Windows.FrameworkContentElement> tak, aby wywołań, które mogą być przekazywane ostatecznie do <xref:System.Windows.FrameworkElement> elementu nadrzędnego.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> Służy do mapowania nowej namescope XAML do istniejącego obiektu. Możesz wywołać <xref:System.Windows.NameScope.SetNameScope%2A> więcej niż raz w celu resetowania lub wyczyść XAML namescope, ale nie jest użycie wspólnej. Ponadto <xref:System.Windows.NameScope.GetNameScope%2A> zwykle nie jest używany z kodu.  
  
### <a name="xaml-namescope-implementations"></a>Implementacje Namescope XAML  
 Następujące klasy wdrożenie <xref:System.Windows.Markup.INameScope> bezpośrednio:  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> nie używa nazwy XAML lub namescopes; korzysta z kluczy, ponieważ jest on implementacji słownika. Tylko przyczyny <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope> jest więc może wiązać się z kodu użytkownika wyjątki pomagających wyjaśnienie różnicy między true XAML namescope i w jaki sposób <xref:System.Windows.ResourceDictionary> obsługuje kluczy, a także w celu zapewnienia, że XAML namescopes nie są stosowane do <xref:System.Windows.ResourceDictionary> przez elementy nadrzędne.  
  
 <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> zaimplementować <xref:System.Windows.Markup.INameScope> za pośrednictwem interfejsu jawnego definicje. Jawne implementacje Zezwalaj te namescopes XAML tradycyjnie zachowanie, gdy są one dostępne za pośrednictwem <xref:System.Windows.Markup.INameScope> interfejs, czyli sposób XAML namescopes są przekazywane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesami wewnętrznymi. Definicje interfejsu jawnego nie są częścią konwencjonalnej powierzchni interfejsu API, ale <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style>, ponieważ trzeba wywołać rzadko <xref:System.Windows.Markup.INameScope> metod <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> bezpośrednio i zamiast tego użyć innego interfejsu API takie jak <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Poniższe klasy definiują własnych namescope XAML za pomocą <xref:System.Windows.NameScope?displayProperty=nameWithType> Klasa pomocy i połączenia jej implementacja namescope XAML za pośrednictwem <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> dołączona właściwość:  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)  
 [x:Name, dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md)
