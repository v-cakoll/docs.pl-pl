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
ms.openlocfilehash: 4383492157191f61cf04a2fdd6ce27e9183bda8b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744418"
---
# <a name="wpf-xaml-namescopes"></a>Zakresy nazw WPF XAML
XAML Zakresy nazw WPF to koncepcja, która identyfikuje obiekty zdefiniowane w języku XAML. Nazwy w namescope języka XAML mogą służyć do ustanawiania relacji między nazwami obiektów zdefiniowanymi w języku XAML a ich odpowiednikami wystąpień w drzewie obiektów. Zazwyczaj Zakresy nazw WPF języka XAML w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodzie zarządzanym są tworzone podczas ładowania pojedynczych katalogów głównych stron XAML dla aplikacji XAML. KOD XAML Zakresy nazw WPF jako obiekt programistyczny jest definiowany przez interfejs <xref:System.Windows.Markup.INameScope> i są również implementowane przez praktyczne klasy <xref:System.Windows.NameScope>.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Zakresy nazw WPF w załadowanych aplikacjach XAML  
 W szerszym kontekście programowania lub nauki komputerowym koncepcje programowania często obejmują zasadę unikatowego identyfikatora lub nazwy, która może być używana do uzyskiwania dostępu do obiektu. W przypadku systemów, które używają identyfikatorów lub nazw, namescope definiuje granice, w których proces lub technika będą przeszukiwane, jeśli zażądano obiektu o tej nazwie lub że są wymuszane ograniczenia unikatowości tożsamości nazw. Te ogólne zasady są prawdziwe w przypadku języka XAML Zakresy nazw WPF. W programie WPF Zakresy nazw WPF języka XAML są tworzone na elemencie głównym strony XAML podczas ładowania strony. Każda nazwa określona na stronie XAML rozpoczynająca się od elementu głównego strony jest dodawana do odpowiednich NameScope języka XAML.  
  
 W języku XAML WPF elementy, które są wspólnymi elementami głównymi (takie jak <xref:System.Windows.Controls.Page>i <xref:System.Windows.Window>), zawsze kontrolują namescope języka XAML. Jeśli element taki jak <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> jest głównym elementem strony w znaczniku, procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dodaje <xref:System.Windows.Controls.Page> główny, tak aby <xref:System.Windows.Controls.Page> mógł udostępnić działające namescope języka XAML.  
  
> [!NOTE]
> Akcje kompilacji WPF tworzą namescope XAML dla produkcji XAML, nawet jeśli atrybuty `Name` lub `x:Name` nie są zdefiniowane dla żadnych elementów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczniku.  
  
 Jeśli spróbujesz użyć tej samej nazwy dwa razy w dowolnym namescope języka XAML, zostanie zgłoszony wyjątek. W przypadku języka XAML WPF, który zawiera kod i jest częścią skompilowanej aplikacji, wyjątek jest wywoływany w czasie kompilacji przez akcje kompilacji WPF, podczas tworzenia wygenerowanej klasy dla strony podczas początkowej kompilacji znaczników. W przypadku języka XAML, który nie jest kompilowany do znaczników przez żadną akcję kompilacji, wyjątki związane z problemami z namescope XAML mogą zostać zgłoszone podczas ładowania XAML. Projektanci XAML mogą również przewidzieć problemy namescope języka XAML w czasie projektowania.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Dodawanie obiektów do drzew obiektów środowiska uruchomieniowego  
 Moment, w którym kod XAML jest analizowany, wskazuje moment, w którym jest tworzony i definiowany namescope języka XAML WPF. W przypadku dodania obiektu do drzewa obiektów w punkcie w czasie po przeanalizowaniu kodu XAML, który wygenerował to drzewo, wartość `Name` lub `x:Name` w nowym obiekcie nie aktualizuje automatycznie informacji w języku XAML namescope. Aby dodać nazwę obiektu do elementu WPF XAML namescope po załadowaniu kodu XAML, należy wywołać odpowiednią implementację <xref:System.Windows.Markup.INameScope.RegisterName%2A> na obiekcie, który definiuje namescope XAML, który jest zazwyczaj głównym katalogiem strony XAML. Jeśli nazwa nie jest zarejestrowana, do dodanego obiektu nie można odwoływać się za pomocą metod, takich jak <xref:System.Windows.FrameworkElement.FindName%2A>, i nie można użyć tej nazwy dla celów animacji.  
  
 Najbardziej typowym scenariuszem dla deweloperów aplikacji jest użycie <xref:System.Windows.FrameworkElement.RegisterName%2A> do zarejestrowania nazw w języku XAML namescope w bieżącym katalogu głównym strony. <xref:System.Windows.FrameworkElement.RegisterName%2A> jest częścią ważnego scenariusza dla scenorysów, które są obiektami docelowymi dla animacji. Aby uzyskać więcej informacji, zobacz [Omówienie scenorysów](../graphics-multimedia/storyboards-overview.md).  
  
 Jeśli wywołasz <xref:System.Windows.FrameworkElement.RegisterName%2A> na obiekcie innym niż obiekt definiujący namescope języka XAML, nazwa jest nadal zarejestrowana w kodzie XAML namescope, w którym znajduje się obiekt wywołujący, tak jakby był on wywoływany <xref:System.Windows.FrameworkElement.RegisterName%2A> na obiekcie języka XAML namescope.  
  
### <a name="xaml-namescopes-in-code"></a>Kod XAML Zakresy nazw WPF w kodzie  
 Możesz tworzyć i używać Zakresy nazw WPF języka XAML w kodzie. Interfejsy API i koncepcje związane z tworzeniem namescope języka XAML są takie same, nawet w przypadku czystego użycia kodu, ponieważ procesor XAML dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa tych interfejsów API i koncepcji, gdy przetwarzają one kod XAML. Pojęcia i interfejs API są przeznaczone głównie do znajdowania obiektów według nazwy w drzewie obiektów, które są zwykle zdefiniowane częściowo lub w całości w języku XAML.  
  
 W przypadku aplikacji, które są tworzone programowo, a nie z załadowanego kodu XAML, obiekt definiujący namescope języka XAML musi implementować <xref:System.Windows.Markup.INameScope>lub być klasą pochodną <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, aby obsługiwała tworzenie namescope XAML w jego wystąpieniach.  
  
 Ponadto dla każdego elementu, który nie jest ładowany i przetwarzany przez procesor XAML, namescope XAML dla obiektu nie jest tworzony ani inicjowany domyślnie. Musisz jawnie utworzyć nowy kod XAML namescope dla każdego obiektu, który zamierza zarejestrować nazwy w późniejszym czasie. Aby utworzyć namescope XAML, należy wywołać metodę <xref:System.Windows.NameScope.SetNameScope%2A> statycznej. Określ obiekt, który będzie jego właocicielem jako parametr `dependencyObject`, oraz nowe wywołanie konstruktora <xref:System.Windows.NameScope.%23ctor%2A> jako parametr `value`.  
  
 Jeśli obiekt udostępniony jako `dependencyObject` dla <xref:System.Windows.NameScope.SetNameScope%2A> nie jest implementacją <xref:System.Windows.Markup.INameScope> <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, wywołanie <xref:System.Windows.FrameworkElement.RegisterName%2A> na wszystkich elementach podrzędnych nie będzie miało żadnego wpływu. Jeśli nie można jawnie utworzyć nowego języka XAML namescope, wywołania do <xref:System.Windows.FrameworkElement.RegisterName%2A> spowodują wystąpienie wyjątku.  
  
 Przykład używania interfejsów API namescope języka XAML w kodzie można znaleźć w temacie [Definiowanie zakresu nazw](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Zakresy nazw WPF języka XAML w stylach i szablonach  
 Za pomocą stylów i szablonów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można w prosty sposób ponownie używać i stosować zawartość. Jednak style i szablony mogą również zawierać elementy z nazwami XAML zdefiniowanymi na poziomie szablonu. Ten sam szablon może być używany wiele razy na stronie. Z tego powodu style i szablony definiują własne Zakresy nazw WPF języka XAML niezależnie od lokalizacji w drzewie obiektów, w której zastosowano styl lub szablon.  
  
 Rozważmy następujący przykład:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Ten sam szablon jest stosowany do dwóch różnych przycisków. Jeśli szablony nie zawierały dyskretnych Zakresy nazw wpfów XAML, nazwa `TheBorder` użyta w szablonie spowoduje kolizję nazw w namescope XAML. Każde wystąpienie szablonu ma własne namescope języka XAML, więc w tym przykładzie każdy kod XAML namescope szablonu, który będzie zawierał dokładnie jedną nazwę.  
  
 Style również definiują własne namescope kodu XAML, aby części scenorysów mogły mieć przypisane określone nazwy. Te nazwy umożliwiają kontrolę określonych zachowań, które będą elementami docelowymi tej nazwy, nawet jeśli szablon został ponownie zdefiniowany w ramach dostosowywania kontroli.  
  
 Ze względu na oddzielne zakresy nazw WPF języka XAML wyszukiwanie nazwanych elementów w szablonie jest trudniejsze niż znalezienie elementu o nazwie nieopartego na szablonie na stronie. Najpierw należy określić zastosowany szablon, pobierając <xref:System.Windows.Controls.Control.Template%2A> wartość właściwości kontrolki, w której jest stosowany szablon. Następnie należy wywołać wersję szablonu <xref:System.Windows.FrameworkTemplate.FindName%2A>, przekazując kontrolkę, w której szablon został zastosowany jako drugi parametr.  
  
 Jeśli jesteś autorem kontrolki i tworzysz Konwencję, w której konkretny nazwany element w zastosowanym szablonie jest obiektem docelowym dla zachowania zdefiniowanego przez sam formant, możesz użyć metody <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> z kodu implementacji formantu. Metoda <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> jest chroniona, dlatego tylko autor formantu ma do niego dostęp.  
  
 Jeśli pracujesz z poziomu szablonu i chcesz uzyskać dostęp do NameScope języka XAML, w którym szablon jest stosowany, Pobierz wartość <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, a następnie Wywołaj <xref:System.Windows.FrameworkElement.FindName%2A> w tym miejscu. Przykładem działania w ramach szablonu jest zapisanie implementacji programu obsługi zdarzeń, w której zdarzenie zostanie podniesione z elementu w zastosowaniu szablonu.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Zakresy nazw WPF języka XAML i interfejsy API związane z nazwami  
 <xref:System.Windows.FrameworkElement> ma metody <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> i <xref:System.Windows.FrameworkElement.UnregisterName%2A>. Jeśli obiekt wywołuje te metody na własność namescope języka XAML, metody wywołują metody odpowiednich namescope XAML. W przeciwnym razie element nadrzędny jest sprawdzany, aby zobaczyć, czy jest właścicielem namescope języka XAML, i ten proces jest kontynuowany cyklicznie do momentu znalezienia namescope XAML (z powodu zachowania procesora XAML, zagwarantowany jest namescope XAML w katalogu głównym). <xref:System.Windows.FrameworkContentElement> ma analogiczne zachowania, z wyjątkiem tego, że żaden <xref:System.Windows.FrameworkContentElement> nie będzie miał namescope języka XAML. Metody istnieją w <xref:System.Windows.FrameworkContentElement> tak, aby wywołania mogły być przekazywane ostatecznie do <xref:System.Windows.FrameworkElement> elementu nadrzędnego.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> jest używany do mapowania nowego namescope języka XAML na istniejący obiekt. Możesz wywołać <xref:System.Windows.NameScope.SetNameScope%2A> więcej niż raz, aby zresetować lub wyczyścić namescope XAML, ale nie jest to typowe użycie. Ponadto <xref:System.Windows.NameScope.GetNameScope%2A> nie jest zazwyczaj używany w kodzie.  
  
### <a name="xaml-namescope-implementations"></a>Implementacje języka XAML namescope  
 Następujące klasy implementują <xref:System.Windows.Markup.INameScope> bezpośrednio:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> nie używa nazw XAML ani Zakresy nazw WPF; Zamiast tego używa kluczy, ponieważ jest implementacją słownika. Jedynym powodem, który <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope>, jest to, że może on zgłaszać wyjątki do kodu użytkownika, który pomaga wyjaśnić rozróżnienie między prawdziwym namescope języka XAML a <xref:System.Windows.ResourceDictionary> obsługuje klucze, a także zapewnić, że zakresy nazw WPF XAML nie są stosowane do <xref:System.Windows.ResourceDictionary> przez elementy nadrzędne.  
  
 <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> Implementuj <xref:System.Windows.Markup.INameScope> za poorednictwem jawnych definicji interfejsu. Jawne implementacje zezwalają, aby te zakresy nazw WPF języka XAML działały zwyczajowo, gdy dostęp do nich odbywa się za pomocą interfejsu <xref:System.Windows.Markup.INameScope>, który jest sposobem komunikacji Zakresy nazw WPF w języku XAML przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesów wewnętrznych. Jednak jawne definicje interfejsu nie są częścią konwencjonalnej powierzchni interfejsu API <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style>, ponieważ rzadko trzeba wywołać metody <xref:System.Windows.Markup.INameScope> na <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> bezpośrednio, a zamiast tego użyć innego interfejsu API, takiego jak <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Poniższe klasy definiują własne namescope języka XAML, używając klasy pomocnika <xref:System.Windows.NameScope?displayProperty=nameWithType> i łącząc się z implementacją namescope języka XAML za pomocą dołączonej właściwości <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Zobacz także

- [Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name, dyrektywa](../../../desktop-wpf/xaml-services/xname-directive.md)
