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
ms.openlocfilehash: edf5c8a828bea182cd87542276fb7eb2df1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917337"
---
# <a name="wpf-xaml-namescopes"></a>Zakresy nazw WPF XAML
XAML Zakresy nazw WPF to koncepcja, która identyfikuje obiekty zdefiniowane w języku XAML. Nazwy w namescope języka XAML mogą służyć do ustanawiania relacji między nazwami obiektów zdefiniowanymi w języku XAML a ich odpowiednikami wystąpień w drzewie obiektów. Zazwyczaj Zakresy nazw WPF języka XAML w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodzie zarządzanym są tworzone podczas ładowania poszczególnych katalogów głównych stron XAML dla aplikacji XAML. Kod XAML Zakresy nazw WPF jako obiekt programistyczny jest definiowany przez <xref:System.Windows.Markup.INameScope> interfejs i jest również zaimplementowany przez klasę <xref:System.Windows.NameScope>praktyczną.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Zakresy nazw WPF w załadowanych aplikacjach XAML  
 W szerszym kontekście programowania lub nauki komputerowym koncepcje programowania często obejmują zasadę unikatowego identyfikatora lub nazwy, która może być używana do uzyskiwania dostępu do obiektu. W przypadku systemów, które używają identyfikatorów lub nazw, namescope definiuje granice, w których proces lub technika będą przeszukiwane, jeśli zażądano obiektu o tej nazwie lub że są wymuszane ograniczenia unikatowości tożsamości nazw. Te ogólne zasady są prawdziwe w przypadku języka XAML Zakresy nazw WPF. W programie WPF Zakresy nazw WPF języka XAML są tworzone na elemencie głównym strony XAML podczas ładowania strony. Każda nazwa określona na stronie XAML rozpoczynająca się od elementu głównego strony jest dodawana do odpowiednich NameScope języka XAML.  
  
 W języku XAML WPF elementy, które są wspólnymi elementami głównymi <xref:System.Windows.Controls.Page>(takie <xref:System.Windows.Window>jak i), zawsze kontrolują namescope języka XAML. Jeśli element taki jak <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> jest elementem głównym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony w znaczniku <xref:System.Windows.Controls.Page> , <xref:System.Windows.Controls.Page> procesor dodaje element główny niejawnie, aby można było udostępnić działające namescope języka XAML.  
  
> [!NOTE]
> Akcje kompilacji WPF tworzą namescope języka XAML dla produkcji XAML, nawet jeśli żadne `Name` `x:Name` atrybuty nie są zdefiniowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] we wszystkich elementach znacznika.  
  
 Jeśli spróbujesz użyć tej samej nazwy dwa razy w dowolnym namescope języka XAML, zostanie zgłoszony wyjątek. W przypadku języka XAML WPF, który zawiera kod i jest częścią skompilowanej aplikacji, wyjątek jest wywoływany w czasie kompilacji przez akcje kompilacji WPF, podczas tworzenia wygenerowanej klasy dla strony podczas początkowej kompilacji znaczników. W przypadku języka XAML, który nie jest kompilowany do znaczników przez żadną akcję kompilacji, wyjątki związane z problemami z namescope XAML mogą zostać zgłoszone podczas ładowania XAML. Projektanci XAML mogą również przewidzieć problemy namescope języka XAML w czasie projektowania.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Dodawanie obiektów do drzew obiektów środowiska uruchomieniowego  
 Moment, w którym kod XAML jest analizowany, wskazuje moment, w którym jest tworzony i definiowany namescope języka XAML WPF. W przypadku dodania obiektu do drzewa obiektów w punkcie w czasie po przeanalizowaniu kodu XAML, który wygenerował to drzewo, `Name` lub `x:Name` wartość w nowym obiekcie nie aktualizuje automatycznie informacji w języku XAML namescope. Aby dodać nazwę dla obiektu do elementu WPF XAML namescope po załadowaniu XAML, należy wywołać odpowiednią implementację <xref:System.Windows.Markup.INameScope.RegisterName%2A> dla obiektu, który definiuje namescope XAML, który jest zazwyczaj głównym katalogiem strony XAML. Jeśli nazwa nie jest zarejestrowana, do dodanego obiektu nie można odwoływać się za pomocą <xref:System.Windows.FrameworkElement.FindName%2A>metod, takich jak, i nie można użyć tej nazwy dla celów animacji.  
  
 Najbardziej typowym scenariuszem dla deweloperów aplikacji jest użycie <xref:System.Windows.FrameworkElement.RegisterName%2A> do rejestracji nazw w języku XAML namescope w bieżącym katalogu głównym strony. <xref:System.Windows.FrameworkElement.RegisterName%2A>jest częścią ważnego scenariusza dla scenorysów, które są obiektami docelowymi dla animacji. Aby uzyskać więcej informacji, zobacz [Omówienie scenorysów](../graphics-multimedia/storyboards-overview.md).  
  
 Jeśli wywołasz <xref:System.Windows.FrameworkElement.RegisterName%2A> obiekt inny niż obiekt definiujący namescope języka XAML, nazwa jest wciąż zarejestrowana w kodzie XAML namescope, w którym znajduje się obiekt wywołujący w, tak jakby był wywoływany <xref:System.Windows.FrameworkElement.RegisterName%2A> w obiekcie języka XAML namescope.  
  
### <a name="xaml-namescopes-in-code"></a>Kod XAML Zakresy nazw WPF w kodzie  
 Możesz tworzyć i używać Zakresy nazw WPF języka XAML w kodzie. Interfejsy API i koncepcje związane z tworzeniem namescope języka XAML są takie same, nawet w przypadku czystego użycia kodu, ponieważ procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML używa tych interfejsów API i koncepcji, gdy przetwarzają one kod XAML. Pojęcia i interfejs API są przeznaczone głównie do znajdowania obiektów według nazwy w drzewie obiektów, które są zwykle zdefiniowane częściowo lub w całości w języku XAML.  
  
 W przypadku aplikacji, które są tworzone programowo, a nie z załadowanego kodu XAML, obiekt definiujący namescope <xref:System.Windows.Markup.INameScope>XAML musi implementować <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> być klasą pochodną, aby obsługiwała tworzenie namescope XAML w jego Liczba.  
  
 Ponadto dla każdego elementu, który nie jest ładowany i przetwarzany przez procesor XAML, namescope XAML dla obiektu nie jest tworzony ani inicjowany domyślnie. Musisz jawnie utworzyć nowy kod XAML namescope dla każdego obiektu, który zamierza zarejestrować nazwy w późniejszym czasie. Aby utworzyć namescope XAML, należy wywołać metodę statyczną <xref:System.Windows.NameScope.SetNameScope%2A> . Określ obiekt, który będzie jego właocicielem jako `dependencyObject` parametr, oraz nowe <xref:System.Windows.NameScope.%23ctor%2A> wywołanie konstruktora jako `value` parametr.  
  
 Jeśli obiekt dostarczony jako `dependencyObject` dla <xref:System.Windows.NameScope.SetNameScope%2A> nie jest <xref:System.Windows.Markup.INameScope> implementacją, <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>wywołanie <xref:System.Windows.FrameworkElement.RegisterName%2A> dowolnego elementu podrzędnego nie będzie miało żadnego efektu. Jeśli nie można jawnie utworzyć nowego języka XAML namescope, wywołanie <xref:System.Windows.FrameworkElement.RegisterName%2A> zostanie zgłoszone jako wyjątek.  
  
 Przykład używania interfejsów API namescope języka XAML w kodzie można znaleźć w temacie [Definiowanie zakresu nazw](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Zakresy nazw WPF języka XAML w stylach i szablonach  
 Style i szablony w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programie zapewniają możliwość wielokrotnego użycia i ponownego zastosowania zawartości w prosty sposób. Jednak style i szablony mogą również zawierać elementy z nazwami XAML zdefiniowanymi na poziomie szablonu. Ten sam szablon może być używany wiele razy na stronie. Z tego powodu style i szablony definiują własne Zakresy nazw WPF języka XAML niezależnie od lokalizacji w drzewie obiektów, w której zastosowano styl lub szablon.  
  
 Rozważmy następujący przykład:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Ten sam szablon jest stosowany do dwóch różnych przycisków. Jeśli szablony nie zawierały dyskretnych Zakresy nazw wpfów XAML `TheBorder` , Nazwa użyta w szablonie spowodowałaby kolizję nazw w namescope XAML. Każde wystąpienie szablonu ma własne namescope języka XAML, więc w tym przykładzie każdy kod XAML namescope szablonu, który będzie zawierał dokładnie jedną nazwę.  
  
 Style również definiują własne namescope kodu XAML, aby części scenorysów mogły mieć przypisane określone nazwy. Te nazwy umożliwiają kontrolę określonych zachowań, które będą elementami docelowymi tej nazwy, nawet jeśli szablon został ponownie zdefiniowany w ramach dostosowywania kontroli.  
  
 Ze względu na oddzielne zakresy nazw WPF języka XAML wyszukiwanie nazwanych elementów w szablonie jest trudniejsze niż znalezienie elementu o nazwie nieopartego na szablonie na stronie. Najpierw należy określić zastosowany szablon, pobierając wartość <xref:System.Windows.Controls.Control.Template%2A> właściwości kontrolki, w której jest stosowany szablon. Następnie należy wywołać wersję <xref:System.Windows.FrameworkTemplate.FindName%2A>szablonu, przekazując kontrolkę, w której szablon został zastosowany jako drugi parametr.  
  
 Jeśli jesteś autorem kontrolki i tworzysz Konwencję, w której konkretny nazwany element w zastosowanym szablonie jest obiektem docelowym dla zachowania zdefiniowanego przez sam formant, możesz użyć <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metody z kodu implementacji formantu. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Metoda jest chroniona, dlatego tylko autor formantu ma do niego dostęp.  
  
 Jeśli pracujesz z poziomu szablonu i chcesz uzyskać dostęp do NameScope języka XAML, w którym szablon jest zastosowany, Pobierz wartość <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, a następnie Wywołaj <xref:System.Windows.FrameworkElement.FindName%2A> ją. Przykładem działania w ramach szablonu jest zapisanie implementacji programu obsługi zdarzeń, w której zdarzenie zostanie podniesione z elementu w zastosowaniu szablonu.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Zakresy nazw WPF języka XAML i interfejsy API związane z nazwami  
 <xref:System.Windows.FrameworkElement>ma <xref:System.Windows.FrameworkElement.FindName%2A>metodyi. <xref:System.Windows.FrameworkElement.RegisterName%2A> <xref:System.Windows.FrameworkElement.UnregisterName%2A> Jeśli obiekt wywołuje te metody na własność namescope języka XAML, metody wywołują metody odpowiednich namescope XAML. W przeciwnym razie element nadrzędny jest sprawdzany, aby zobaczyć, czy jest właścicielem namescope języka XAML, i ten proces jest kontynuowany cyklicznie do momentu znalezienia namescope XAML (z powodu zachowania procesora XAML, zagwarantowany jest namescope XAML w katalogu głównym). <xref:System.Windows.FrameworkContentElement>ma analogiczne zachowania, z wyjątkiem tego, <xref:System.Windows.FrameworkContentElement> że nie będzie nigdy własnością namescope języka XAML. Metody istnieją <xref:System.Windows.FrameworkContentElement> tak, aby wywołania mogły być przekazywane ostatecznie <xref:System.Windows.FrameworkElement> do elementu nadrzędnego.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>służy do mapowania nowego namescope języka XAML na istniejący obiekt. Możesz wywołać <xref:System.Windows.NameScope.SetNameScope%2A> więcej niż jeden raz, aby zresetować lub wyczyścić namescope XAML, ale nie jest to typowe użycie. Ponadto nie <xref:System.Windows.NameScope.GetNameScope%2A> jest zazwyczaj używany w kodzie.  
  
### <a name="xaml-namescope-implementations"></a>Implementacje języka XAML namescope  
 Następujące klasy implementują <xref:System.Windows.Markup.INameScope> się bezpośrednio:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>nie używa nazw XAML ani Zakresy nazw WPF; Zamiast tego używa kluczy, ponieważ jest implementacją słownika. Jedyną przyczyną, która <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope> , jest to, że może ona zgłaszać wyjątki do kodu użytkownika, który ułatwia wyjaśnienie rozróżnienia między prawdziwym <xref:System.Windows.ResourceDictionary> namescope języka XAML a sposobem obsługi kluczy, a także gwarantuje, że zakresy nazw WPF XAML nie są stosowane do <xref:System.Windows.ResourceDictionary> według elementów nadrzędnych.  
  
 <xref:System.Windows.FrameworkTemplate>i <xref:System.Windows.Style> implementowanie <xref:System.Windows.Markup.INameScope> za poorednictwem jawnych definicji interfejsu. Jawne implementacje zezwalają, aby te zakresy nazw WPF języka XAML działały zwyczajowo, gdy <xref:System.Windows.Markup.INameScope> dostęp do nich odbywa się za pomocą interfejsu, co jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sposobem komunikacji Zakresy nazw WPF języka XAML przez procesy wewnętrzne. Jednak jawne definicje <xref:System.Windows.FrameworkTemplate> interfejsu nie są częścią konwencjonalnej powierzchni interfejsu API i <xref:System.Windows.Style>, ponieważ <xref:System.Windows.Markup.INameScope> rzadko trzeba wywołać metody w <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> bezpośrednio, a zamiast tego używać innego interfejsu API takie jak <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Poniższe klasy definiują własne namescope języka XAML, używając <xref:System.Windows.NameScope?displayProperty=nameWithType> klasy pomocnika i łącząc się z implementacją namescope języka XAML <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> za pomocą dołączonej właściwości:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Zobacz także

- [Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name, dyrektywa](../../xaml-services/x-name-directive.md)
