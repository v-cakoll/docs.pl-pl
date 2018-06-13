---
title: Style dla Fokusu w formantach i FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 6c73c8bbfcf7631094ddf89641de9af38f86f88e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549519"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Style dla Fokusu w formantach i FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia dwa mechanizmy równoległych zmiany wygląd formantu, gdy odbierze fokus klawiatury. Pierwszy mechanizm jest używać metody ustawiające właściwości dla właściwości, takich jak <xref:System.Windows.UIElement.IsKeyboardFocused%2A> w stylu lub szablonie, która jest stosowana do formantu. Drugi mechanizmu jest zapewnienie oddzielne styl jako wartość <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości; "skoncentrowane stylu wizualnego" tworzy oddzielne drzewa wizualnego dla modułu definiowania układu kodu, który rysuje na górze kontrolki, zamiast zmieniać wizualnym drzewie kontrolki lub innych interfejsu użytkownika Element poprzez zastąpienie jej. W tym temacie opisano scenariusze, w których każdy z tych mechanizmów jest właściwe.  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Celem fokus stylu wizualnego.  
 Funkcja stylu wizualnego fokus zapewnia wspólny "model obiektu" wprowadzenie opinie użytkowników visual oparte na nawigacji klawiatury do dowolnego elementu interfejsu użytkownika. Jest to możliwe bez stosowania nowy szablon do formantu lub wiedząc kompozycji określonego szablonu.  
  
 Jednak mówiąc, ponieważ funkcja stylu wizualnego fokus działa bez uprzedniego uzyskania informacji o szablonach formantów, wizualne, które mogą być wyświetlane dla formantu przy użyciu stylu wizualnego fokus jest z konieczności ograniczony. Jej faktycznie działanie jest nakładki innego drzewa wizualnego (moduł definiowania układu) na drzewie wizualnym tworzony przez renderowanie formantu za pomocą szablonu. Zdefiniuj to oddzielne drzewa wizualnego przy użyciu stylu, które wypełnia <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Domyślne zachowanie stylu wizualnego fokus  
 Style wizualne fokus działa tylko wtedy, gdy akcja fokus została zainicjowana za pomocą klawiatury. Dowolną akcję myszy lub zmień fokus programowe wyłącza tryb style wizualne fokus. Aby uzyskać więcej informacji na temat różnice między trybami fokus, zobacz [omówienie fokus](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
 Motywy dla formantów obejmują domyślne zachowanie stylu wizualnego fokus staje się fokus stylu dla wszystkich kontrolek w motywie. Ten styl motywu jest identyfikowany przez wartość klucza statycznych <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Przy deklarowaniu własnego stylu wizualnego fokus na poziomie aplikacji, możesz zastąpić to domyślne zachowanie stylu z kompozycji. Można również w przypadku definiowania motywu całego, następnie należy używać tego samego klucza do zdefiniowania stylu domyślne zachowanie dla całego motywu.  
  
 W kompozycji domyślny styl wizualny fokus jest zazwyczaj bardzo proste. Poniżej przedstawiono nierównej zbliżenia:  
  
```  
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
## <a name="when-to-use-focus-visual-styles"></a>Kiedy należy używać stylów wizualnych fokus  
 Koncepcyjnie wygląd fokus style wizualne stosowana do formantów powinny być spójne z formantami. Zmień styl wizualny tylko wtedy, gdy redagowania całego motywu, gdzie każdego formantu, który jest zdefiniowany w motywie pobiera samego stylu wizualnego fokus lub różnice w stylu które wizualnie jest związany z kontroli Pobi jest jednym ze sposobów zapewnienia spójności Formant Karta. Alternatywnie można użyć tego samego styl (lub podobny style) stylu co focusable klawiatury elementu na stronie lub w interfejsie użytkownika.  
  
 Ustawienie <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> na style poszczególnych kontrolek, które nie są częścią kompozycji jest nie przeznaczenia fokus stylów wizualnych. Jest to spowodowane niespójne zachowanie visual między formantami może prowadzić do mylące czynności użytkownika dotyczących fokus klawiatury. Jeśli są mają zostać zachowania kontroli specyficzne dla fokus klawiatury, które celowo nie są spójne w kompozycji, znacznie lepszym rozwiązaniem jest używać Wyzwalacze w stylach właściwości poszczególnych stanu danych wejściowych, takich jak <xref:System.Windows.UIElement.IsFocused%2A> lub <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Style wizualne fokus działa wyłącznie do fokus klawiatury. Tak fokus style wizualne są typu funkcji ułatwień dostępu. Jeśli chcesz zmiany interfejsu użytkownika dla dowolnego typu fokus, czy za pomocą myszy, klawiatury lub programowo, następnie należy nie należy używać stylów wizualnych fokus i zamiast tego należy użyć metody ustawiające i jest wyzwalane w style lub szablonów, które pracują z wartości właściwości ogólne fokus takie jak `IsFocused` lub `IsFocusWithin`.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Jak utworzyć fokus stylu wizualnego  
 Styl tworzony w stylu wizualnego fokus powinien zawsze mieć <xref:System.Windows.Style.TargetType%2A> z <xref:System.Windows.Controls.Control>. Styl powinien zawierać głównie <xref:System.Windows.Controls.ControlTemplate>. Nie należy określać typ docelowy jako typ, gdy styl wizualny fokus jest przypisany do <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Ponieważ typ docelowy jest zawsze <xref:System.Windows.Controls.Control>, musi być styl za pomocą właściwości, które są wspólne dla wszystkich kontrolek (za pomocą właściwości <xref:System.Windows.Controls.Control> klasy i jej klas podstawowych). Należy utworzyć szablon, który prawidłowo będzie działać jako nakładkę do elementu interfejsu użytkownika, a który nie będzie przesłaniać obszarów funkcjonalnych formantu. Ogólnie rzecz biorąc oznacza to, że wizualny powinien pojawić się poza marginesy kontrolki lub jako efekty tymczasowe lub dyskretnego kodu, które nie powoduje blokowania testowania trafień w formancie których stosowane jest stylu wizualnego fokus. Właściwości używanych w powiązaniu szablonu, które są przydatne do określenia rozmiaru i pozycjonowania szablonu nakładki obejmują <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, i <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternatywy dla przy użyciu stylu wizualnego fokus  
 W sytuacjach, gdzie przy użyciu stylu wizualnego fokus jest nieodpowiedni, ponieważ są tylko style formantów pojedynczego lub ma większą kontrolę nad kontroli szablonu istnieje wiele dostępnych właściwości i techniki, które można utworzyć visual zachowanie w odpowiedzi na zmiany fokusu.  
  
 Wyzwalacze, metody ustawiające i ustawiające zdarzeń są omówiona szczegółowo w [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md). Obsługa zdarzeń trasowane została szczegółowo opisana w [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Jeśli interesuje Cię w szczególności fokus klawiatury <xref:System.Windows.UIElement.IsKeyboardFocused%2A> właściwości zależności można używać właściwości <xref:System.Windows.Trigger>. Wyzwalacz właściwości w stylu lub szablonie jest odpowiedniejsze techniki do definiowania zachowania fokus klawiatury jest bardzo specjalnie z myślą o jeden formant i które mogą być wizualnie niezgodne zachowanie fokus klawiatury dla innych formantów.  
  
 Inny podobny właściwość zależności jest <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, może być odpowiednie do użycia, aby wizualnie wyróżnienia tego fokus klawiatury jest gdzieś w ramach składania lub Obszar funkcjonalny formantu. Na przykład użytkownik może umieścić <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> wyzwalacz tak, aby panelu, który grupuje kilku formantów pojawia się inaczej, nawet jeśli fokus klawiatury może być bardziej precyzyjnie znajdować się na pojedynczego elementu w obrębie tego panelu.  
  
 Można również użyć zdarzenia <xref:System.Windows.UIElement.GotKeyboardFocus> i <xref:System.Windows.UIElement.LostKeyboardFocus> (a także ich odpowiedniki wersja zapoznawcza). Można użyć tych zdarzeń jako podstawę <xref:System.Windows.EventSetter>, lub możesz pisać programy obsługi dla zdarzenia związane z kodem.  
  
### <a name="other-focus-properties"></a>Inne właściwości fokus  
 Jeśli chcesz, aby wszystkie możliwe przyczyny zmiany fokusu do tworzenia wizualnego zachowanie, podstawowa metody ustawiającej lub wyzwalane w <xref:System.Windows.UIElement.IsFocused%2A> właściwości zależności, albo na <xref:System.Windows.UIElement.GotFocus> lub <xref:System.Windows.UIElement.LostFocus> zdarzenia używane na potrzeby <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Przegląd fokusu](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)
