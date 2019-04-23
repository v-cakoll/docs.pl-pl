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
ms.openlocfilehash: a46942188fd417b46ba4feb44d436800e1362098
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225797"
---
# <a name="wpf-xaml-namescopes"></a>Zakresy nazw WPF XAML
Zakresy nazw XAML to pojęcie, który identyfikuje obiekty, które są definiowane w XAML. Nazwy w XAML namescope może służyć do ustanawiania relacji między nazwami zdefiniowane XAML, obiektów i ich odpowiedniki wystąpienia drzewem obiektu. Zazwyczaj zakresy XAML nazw w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zarządzanego kodu są tworzone podczas ładowania strony XAML poszczególnych obiektów głównych dla aplikacji XAML. Zakresy nazw XAML, co obiekt programowania są definiowane przez <xref:System.Windows.Markup.INameScope> interfejsu, a także są implementowane przez klasy praktyczne <xref:System.Windows.NameScope>.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Zakresy nazw w aplikacjach XAML załadowane  
 W szerszym programowania lub komputera do nauki o kontekście pojęcia dotyczące programowania często zawierają zasady unikatowego identyfikatora lub nazwy, która może służyć do dostępu do obiektu. W systemach używających nazwy lub identyfikatory namescope definiuje granic w ramach procesu lub techniki wyszuka, jeśli wymagana jest obiekt o tej nazwie lub granice, w którym unikatowość nazwy identyfikowania jest wymuszany. Te zasady ogólne są względem niego spełnione zakresy nazw XAML. W środowisku WPF zakresy nazw XAML są tworzone dla elementu głównego dla strony XAML podczas ładowania strony. Każda nazwa określona w obrębie strony XAML, począwszy od głównego strony jest dodawany do odpowiednich namescope XAML.  
  
 W WPF XAML, elementy, które są wspólne elementy katalogu głównego (takie jak <xref:System.Windows.Controls.Page>, i <xref:System.Windows.Window>) zawsze kontrolować XAML namescope. Jeśli element, takie jak <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> jest głównym elementem strony w znaczniku, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor dodaje <xref:System.Windows.Controls.Page> główny niejawnie tak, aby <xref:System.Windows.Controls.Page> może zapewnić namescope XAML pracy.  
  
> [!NOTE]
>  Akcje kompilacji WPF tworzenie namescope XAML w celach produkcyjnych XAML nawet, jeśli nie `Name` lub `x:Name` na dowolnych elementów zdefiniowanych atrybutów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 Jeśli spróbujesz użyć takiej samej nazwie dwa razy w dowolnym namescope XAML, zgłaszany jest wyjątek. Dla WPF XAML, ma związanym z kodem, który jest częścią skompilowanej aplikacji zgłaszany jest wyjątek w czasie kompilacji przez akcje kompilacji WPF, tworząc wygenerowanej klasy dla strony podczas kompilacji znaczników początkowej. Dla XAML, który nie jest kompilowana do znaczników przez dowolną akcję kompilacji wyjątków związanych z emisją namescope XAML może zostać wywołane, gdy XAML jest ładowany. Projektantów XAML może również przewidywać problemy namescope XAML w czasie projektowania.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Dodawanie obiektów do drzewa w obiekcie środowiska wykonawczego  
 Obecnie, który jest analizowany XAML reprezentuje moment w czasie, który namescope WPF XAML jest utworzone i zdefiniowane. Jeśli obiekt jest dodawany do drzewa obiektów w punkcie w czasie po XAML, który tree był analizowany, `Name` lub `x:Name` wartość dla nowego obiektu nie jest aktualizowane automatycznie informacje zawarte w XAML namescope. Aby dodać nazwę obiektu do namescope WPF XAML, po załadowaniu XAML, należy wywołać wprowadzenia <xref:System.Windows.Markup.INameScope.RegisterName%2A> na obiekt, który definiuje XAML namescope, który jest zazwyczaj główny strony XAML. Jeśli nazwa nie jest zarejestrowany, dodany obiekt nie może odwoływać się nazwy za pomocą metody takie jak <xref:System.Windows.FrameworkElement.FindName%2A>, i nie możesz użyć tej nazwy języka animacji.  
  
 Najbardziej typowym scenariuszem dla deweloperów aplikacji jest, że używany jest program <xref:System.Windows.FrameworkElement.RegisterName%2A> do rejestracji nazw na namescope XAML w katalogu głównym bieżącej strony. <xref:System.Windows.FrameworkElement.RegisterName%2A> jest to ważne scenorysów tego obiektów docelowych dla animacji. Aby uzyskać więcej informacji, zobacz [Przegląd Scenorysy](../graphics-multimedia/storyboards-overview.md).  
  
 Jeśli wywołasz <xref:System.Windows.FrameworkElement.RegisterName%2A> do obiektu innego niż obiekt, który definiuje XAML namescope, nazwa jest nadal zarejestrowany namescope XAML, przechowywanych w ramach, obiekt wywołujący tak, jakby były nazywane <xref:System.Windows.FrameworkElement.RegisterName%2A> na namescope XAML, definiując obiektu.  
  
### <a name="xaml-namescopes-in-code"></a>Zakresy nazw XAML, w kodzie  
 Można tworzyć i następnie użyć XAML zakresy nazw w kodzie. Interfejsy API i pojęcia związane z XAML namescope tworzenia są takie same, nawet w przypadku użycia czystym kodzie, ponieważ procesor XAML dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa tych interfejsów API i pojęcia, podczas przetwarzania XAML sam. Pojęcia i interfejsu API istnieją głównie na potrzeby z brakiem obiektów według nazwy w obrębie drzewa obiektów, które zwykle definiuje się częściowo lub całkowicie w XAML.  
  
 Dla aplikacji, które są tworzone programowo, a nie z XAML załadowane, obiekt, który definiuje XAML namescope musi implementować <xref:System.Windows.Markup.INameScope>, lub być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> pochodne klasy, w celu obsługi tworzenia XAML namescope na jego wystąpienia.  
  
 Ponadto dla każdego elementu, który nie jest załadowane i przetworzone przez procesor XAML namescope XAML dla tego obiektu nie utworzeniu lub zainicjowana domyślnie. Należy jawnie utworzyć nowe namescope XAML dla dowolnego obiektu, który ma zostać następnie zarejestruj nazwy do. Aby utworzyć XAML namescope, wywołaj statyczną <xref:System.Windows.NameScope.SetNameScope%2A> metody. Określ obiekt, który jest właścicielem go jako `dependencyObject` parametr i nową <xref:System.Windows.NameScope.%23ctor%2A> wywołanie konstruktora jako `value` parametru.  
  
 Jeśli obiekt jest przewidziana `dependencyObject` dla <xref:System.Windows.NameScope.SetNameScope%2A> nie jest <xref:System.Windows.Markup.INameScope> implementacji <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>, wywoływania <xref:System.Windows.FrameworkElement.RegisterName%2A> na wszystkie podrzędne elementy będą miały żadnego wpływu. Jeśli nie zostanie jawnie tworzyć nowe namescope XAML, następnie wywołuje metodę do <xref:System.Windows.FrameworkElement.RegisterName%2A> zgłosi wyjątek.  
  
 Aby uzyskać przykład użycia XAML namescope interfejsów API w kodzie, zobacz [Definiuj zakres nazw](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Zakresy nazw XAML, style i szablony  
 Style i szablony w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewniają możliwość ponownego użycia i ponownie zastosować zawartość w prosty sposób. Jednak — style i szablony mogą również obejmować elementy o nazwach XAML zdefiniowane na poziomie szablonu. Na stronie tego samego szablonu mogą być używane wielokrotnie. Z tego powodu — style i szablony zdefiniować własne zakresy nazw XAML, niezależnie od lokalizacji, niezależnie od drzewa obiektów, w której stosowana jest stylem lub szablonem.  
  
 Rozważmy następujący przykład:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 W tym miejscu tego samego szablonu jest stosowane do dwóch różnych przycisków. Jeśli szablony nie miał kolumną dyskretną XAML zakresy nazw, `TheBorder` nazwa używana w szablonie spowodowałoby kolizję nazw w XAML namescope. Każdego wystąpienia szablonu ma swój własny namescope XAML, więc w tym przykładzie namescope XAML każdego wystąpień szablonu będzie zawierać dokładnie jedną nazwę.  
  
 Style również definiować własne namescope XAML, przede wszystkim, dzięki czemu w części scenorysów mają szczególne nazwy przypisane. Te nazwy Włącz kontroli zachowań określonych przeznaczonych elementów tej samej nazwie, nawet jeśli ponownie zdefiniowano szablon jako część niestandardowe Dostosowywanie formantu.  
  
 Ze względu na oddzielnych XAML zakresy nazw, wyszukiwanie elementów o nazwie w szablonie jest bardziej trudniejsze niż wyszukiwanie bez szablonu o nazwie elementu na stronie. Najpierw musisz określić zastosowany szablon, uzyskując <xref:System.Windows.Controls.Control.Template%2A> wartość właściwości kontrolki, w której jest stosowany szablon. Następnie należy wywołać wersję szablonu <xref:System.Windows.FrameworkTemplate.FindName%2A>, przekazując kontrolę, gdy szablon został zastosowany jako drugi parametr.  
  
 Jeśli jesteś autorem formantu i generują Konwencję, w której określonego o nazwie elementu w szablonie stosowane jest elementem docelowym, do zachowania w zakresie, który jest definiowany przez sam formant, możesz użyć <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metody z kodu realizacji kontroli. <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> Jest chroniony, tylko autor kontrolka ma do niego dostęp.  
  
 Jeśli pracujesz z w ramach szablonu i trzeba przejść do XAML namescope, w którym szablon jest stosowany, należy uzyskać wartość <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, a następnie wywołaj <xref:System.Windows.FrameworkElement.FindName%2A> istnieje. Przykładem pracy w ramach szablonu będzie, jeśli piszesz implementacja programu obsługi zdarzeń gdy zdarzenie zostanie wygenerowany z elementu w szablonie zastosowane.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Zakresy nazw XAML i powiązane z nazwą interfejsy API  
 <xref:System.Windows.FrameworkElement> ma <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> i <xref:System.Windows.FrameworkElement.UnregisterName%2A> metody. Jeśli obiekt, który chcesz wywołać tych metod w uznaje XAML namescope, metody wywołania do metod odpowiednich namescope XAML. W przeciwnym razie elementu nadrzędnego jest sprawdzenie, jeśli jest ona właścicielem XAML namescope, a ten proces jest kontynuowany cyklicznie, aż do znalezienia XAML namescope (ze względu na zachowanie procesora XAML, może być namescope XAML, w katalogu głównym). <xref:System.Windows.FrameworkContentElement> ma analogiczne zachowania, z wyjątkiem tego, który nie <xref:System.Windows.FrameworkContentElement> nigdy nie będą właścicielami XAML namescope. Metody istnieje na <xref:System.Windows.FrameworkContentElement> tak, aby wywołania, które mogą być przekazywane ostatecznie do <xref:System.Windows.FrameworkElement> elementu nadrzędnego.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> Służy do mapowania nowych namescope XAML do istniejącego obiektu. Możesz wywołać <xref:System.Windows.NameScope.SetNameScope%2A> więcej niż jeden raz w celu resetowania lub wyczyść XAML namescope, ale nie jest wspólne użycie. Ponadto <xref:System.Windows.NameScope.GetNameScope%2A> nie jest zazwyczaj używana w kodzie.  
  
### <a name="xaml-namescope-implementations"></a>Implementacje Namescope XAML  
 Następujące klasy implementacji <xref:System.Windows.Markup.INameScope> bezpośrednio:  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> nie korzysta z nazw XAML lub zakresy nazw; korzysta z kluczy zamiast tego, ponieważ jest on implementacji słownika. Tylko przyczyny <xref:System.Windows.ResourceDictionary> implementuje <xref:System.Windows.Markup.INameScope> jest, dzięki czemu można podnieść, wyjątki, aby kod użytkownika, które pomóc w wyjaśnianiu rozróżnienie między true XAML namescope oraz w jaki sposób <xref:System.Windows.ResourceDictionary> obsługuje kluczy, a także po to, aby mieć pewność, że zakresy nazw XAML nie są stosowane do <xref:System.Windows.ResourceDictionary> przez elementy nadrzędne.  
  
 <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> zaimplementować <xref:System.Windows.Markup.INameScope> za pomocą definicji interfejsu jawnego. Jawne implementacje zezwolić na te zakresy nazw XAML, powszechnie zachowanie, gdy są dostępne za pośrednictwem <xref:System.Windows.Markup.INameScope> interfejs, który jest jak zakresy nazw XAML są przekazywane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesów wewnętrznych. Definicje interfejsu jawnego nie są częścią konwencjonalne powierzchni interfejsu API, ale <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style>, ponieważ rzadko występuje konieczność wywołania <xref:System.Windows.Markup.INameScope> metod <xref:System.Windows.FrameworkTemplate> i <xref:System.Windows.Style> bezpośrednio, a zamiast tego użyć innego interfejsu API takie jak <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Poniższe klasy definiują własne namescope XAML przy użyciu <xref:System.Windows.NameScope?displayProperty=nameWithType> klasy pomocnika oraz połączenie z jego implementacja namescope XAML za pośrednictwem <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> dołączona właściwość:  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Zobacz także

- [Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name, dyrektywa](../../xaml-services/x-name-directive.md)
