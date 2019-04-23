---
title: Style dla Fokusu w formantach i FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 745c2174c54ed072f91a6d5eb3b43d5385e96b90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172058"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Style dla Fokusu w formantach i FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia dwa mechanizmy równoległe zmieniać wygląd kontrolki, gdy otrzymuje fokus klawiatury. Pierwszy mechanizm jest używać metod ustawiających właściwości dla właściwości, takich jak <xref:System.Windows.UIElement.IsKeyboardFocused%2A> w stylu lub szablonu, która jest stosowana do formantu. Mechanizm drugi ma na celu dostarczenie oddzielne styl jako wartość <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości "skupić stylu wizualnego" tworzy osobne drzewo wizualne dla moduł definiowania układu, który rysuje na górze kontrolki, zamiast zmieniania drzewie wizualnym kontrolki lub innego interfejsu użytkownika element przez zastąpienie. W tym temacie opisano scenariusze, w których każdy z tych mechanizmów jest właściwe.  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Celem styl wizualny fokusu  
 Funkcja styl wizualny fokusu zapewnia typowe "object model" wprowadzenie do visual opinii klientów oparte na nawigacji za pomocą klawiatury do dowolnego elementu interfejsu użytkownika. Jest to możliwe bez zastosowania nowego szablonu do formantu lub wiedząc kompozycji określonego szablonu.  
  
 Mówiąc, ponieważ funkcja styl wizualny fokusu działa bez znajomości szablony kontrolek, wizualną opinię, która może być wyświetlany formantu za pomocą styl wizualny fokusu jest jednak zawsze ograniczony. Faktycznie działania funkcji jest nakładki innego drzewa wizualnego (moduł definiowania układu) na podstawie drzewa wizualnego, utworzonemu renderowania formantu za pomocą szablonu. Zdefiniuj to oddzielne drzewa wizualnego, przy użyciu stylu, który wypełnia <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Domyślne zachowanie styl wizualny fokusu  
 Styl wizualny fokusu działają tylko wtedy, gdy akcja fokus został zainicjowany przez klawiatury. Dowolną akcję myszy lub Zmień zespół programistyczny wyłącza tryb koncentracji uwagi stylów wizualnych. Aby uzyskać więcej informacji na temat różnice między trybami fokus zobacz [Przegląd fokus](focus-overview.md).  
  
 Kompozycje dla kontrolek obejmują domyślne zachowanie styl wizualny fokusu staje się styl wizualny fokusu dla wszystkich kontrolek w motywie. Ten styl motywu jest identyfikowany przez wartość klucza statyczne <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Kiedy Deklarujesz własny styl wizualny fokusu na poziomie aplikacji, można zastąpić domyślne zachowanie styl z tematów. Alternatywnie Jeśli zdefiniujesz całego motywu, użyj tego samego klucza do zdefiniowania stylu domyślnego zachowania dla całej motywu.  
  
 W kompozycji domyślny styl wizualny fokusu jest zazwyczaj bardzo proste. Poniżej przedstawiono zgrubne przybliżenie:  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>Kiedy należy używać stylów wizualnych z fokusem  
 Model wygląd fokus stylów wizualnych zastosować do kontrolek powinna być spójne z formantami. Jednym ze sposobów na zapewnienie spójności jest fokusu stylu wizualnego tylko wtedy, gdy redagowania całego motywu, w którym każdy formant, który jest zdefiniowany w motywie pobiera styl wizualny fokusu tej samej lub różnice w stylu, wizualnie jest powiązane z kontrolki do kontynuacji roli. Alternatywnie można użyć stylu tego samego (lub podobny style) do nadawania stylu każdy element focusable klawiatury, na stronie lub w interfejsie użytkownika.  
  
 Ustawienie <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> na stylów poszczególnych kontrolek, które nie są częścią kompozycji jest nie zamierzonego użycia fokus stylów wizualnych. Jest to spowodowane niespójne zachowanie visual między kontrolkami może prowadzić do mylące czynności użytkownika dotyczących fokus klawiatury. Sygnalizuje pomyślny przebieg operacji specyficznej dla kontroli zachowania fokus klawiatury, które celowo nie są spójne w kompozycji, można znacznie lepszym rozwiązaniem jest Użyj wyzwalaczy w stylach właściwości poszczególnych stanu danych wejściowych, takich jak <xref:System.Windows.UIElement.IsFocused%2A> lub <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Styl wizualny fokusu działają wyłącznie dla fokus klawiatury. W efekcie stylów wizualnych koncentracji uwagi są typem funkcji ułatwień dostępu. Jeśli chcesz, aby zmiany interfejsu użytkownika dla dowolnego typu fokus, czy za pomocą myszy, klawiatury lub programowo, następnie nie należy używać stylów wizualnych fokus i zamiast tego należy używać metod ustawiających i wyzwalaczy w style lub szablony, które pracują z wartości właściwości ogólne fokus takie jak <xref:System.Windows.UIElement.IsFocused%2A> lub <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Jak utworzyć styl wizualny fokusu  
 Styl możesz utworzyć styl wizualny fokusu powinny zawsze występować <xref:System.Windows.Style.TargetType%2A> z <xref:System.Windows.Controls.Control>. Styl powinna składać się głównie z <xref:System.Windows.Controls.ControlTemplate>. Nie określaj typ docelowy jako typ, gdy styl wizualny fokusu jest przypisany do <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Ponieważ typ docelowy jest zawsze <xref:System.Windows.Controls.Control>, musi być stylu za pomocą właściwości, które są wspólne dla wszystkich kontrolek (przy użyciu właściwości <xref:System.Windows.Controls.Control> klasy i jej klasy bazowe). Należy utworzyć szablon, który prawidłowo będzie działać jako nakładkę z elementem interfejsu użytkownika i będzie, nie mogą zasłaniać obszarów funkcjonalnych formantu. Ogólnie rzecz biorąc oznacza to, że wizualną opinię powinien pojawić się poza marginesy kontrolki lub jako tymczasowy lub dyskretny kod efektów, które nie będzie blokować testowania trafień w kontrolce której stosowana jest styl wizualny fokusu. Właściwości, które można użyć w powiązaniu szablonu, które są przydatne do określania rozmiaru i pozycjonowania szablonu nakładki obejmują <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, i <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternatywy dla przy użyciu styl wizualny fokusu  
 W sytuacjach, w którym przy użyciu styl wizualny fokusu jest nieodpowiednia, ponieważ są tylko style kontrolki jednego lub mają większą kontrolę nad szablonu kontrolki istnieje wiele dostępnych właściwości i technik, które można utworzyć wizualizację zachowanie w odpowiedzi na zmiany w trybie koncentracji uwagi.  
  
 Wyzwalacze, metody ustawiające i ustawiające zdarzeń są omówiono szczegółowo w [Tworzenie szablonów i stylów](../controls/styling-and-templating.md). Obsługa zdarzenia trasowane została omówiona w [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Jeśli interesuje Cię specjalnie fokus klawiatury <xref:System.Windows.UIElement.IsKeyboardFocused%2A> właściwości zależności można używać właściwości <xref:System.Windows.Trigger>. Wyzwalacz właściwości w stylu lub szablonu jest techniką bardziej odpowiednie do definiowania zachowania fokus klawiatury jest bardzo specjalnie dla pojedynczego kontrola i który może być wizualnie niezgodny zachowanie fokus klawiatury dla innych kontrolek.  
  
 Jest inna właściwość zależności podobne <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, który może być odpowiednie do użycia, jeśli chcesz wizualnie wyróżnienia że fokus klawiatury jest gdzieś w ramach składania lub obszaru funkcjonalnego formantu. Na przykład może umieścić <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> wyzwalacza w taki sposób, że panel, który grupuje kilka formantów pojawia się inaczej, mimo że fokus klawiatury może być bardziej precyzyjne włączenia pojedynczego elementu poziomu tego panelu.  
  
 Możesz również użyć zdarzenia <xref:System.Windows.UIElement.GotKeyboardFocus> i <xref:System.Windows.UIElement.LostKeyboardFocus> (a także ich odpowiedników w wersji zapoznawczej). Zdarzenia te można użyć jako podstawy dla <xref:System.Windows.EventSetter>, lub można napisać procedury obsługi zdarzeń w związanym z kodem.  
  
### <a name="other-focus-properties"></a>Inne właściwości koncentracji uwagi  
 Jeśli chcesz, aby wszystkie możliwe przyczyny zmieniania fokusu do tworzenia wizualnych zachowanie, podstawowej metody ustawiającej lub Wyzwalaj w momencie <xref:System.Windows.UIElement.IsFocused%2A> właściwość zależności lub alternatywnie w <xref:System.Windows.UIElement.GotFocus> lub <xref:System.Windows.UIElement.LostFocus> zdarzenia używane do <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd fokusu](focus-overview.md)
- [Przegląd danych wejściowych](input-overview.md)
