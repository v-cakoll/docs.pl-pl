---
title: Style dla Fokusu w formantach i FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 988b084144532df6f7a6073184fcf035b0813bfd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458681"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Style dla Fokusu w formantach i FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia dwa równoległe mechanizmy zmiany wyglądu kontrolki, gdy odbierze fokus klawiatury. Pierwszy mechanizm polega na użyciu metod ustawiających właściwości dla właściwości, takich jak <xref:System.Windows.UIElement.IsKeyboardFocused%2A> w stylu lub szablonie, który jest stosowany do kontrolki. Drugi mechanizm polega na określeniu oddzielnego stylu jako wartości właściwości <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>; "styl wizualizacji ostrości" tworzy osobne drzewo wizualne dla modułu definiowania układu, który jest pobierany na wierzchu formantu, zamiast zmieniać drzewo wizualne formantu lub innego elementu interfejsu użytkownika przez zastąpienie go. W tym temacie omówiono scenariusze, w których każdy z tych mechanizmów jest właściwy.  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Styl wizualizacji fokusu  
 Funkcja stylu wizualizacji fokusu zawiera wspólny "model obiektów" do wprowadzania opinii użytkowników wizualnych na podstawie nawigacji klawiaturowej do dowolnego elementu interfejsu użytkownika. Jest to możliwe bez zastosowania nowego szablonu do kontrolki lub znajomości określonego szablonu.  
  
 Jednak precyzyjne, ponieważ funkcja stylu wizualizacji fokusu działa bez znajomości szablonów kontroli, Wizualizacja wizualna, która może być wyświetlana dla kontrolki korzystającej z stylu wizualizacji, jest niekoniecznie ograniczona. Rzeczywista funkcja jest nakładana na inne drzewo wizualne (moduł definiowania układu) na wierzchu drzewa wizualnego, jak zostało utworzone przez renderowanie kontrolki za pomocą szablonu. Definiujesz to osobne drzewo wizualne przy użyciu stylu, który wypełnia Właściwość <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Domyślne zachowanie stylu wizualnego fokusu  
 Ustaw fokus w stylu wizualizacji tylko wtedy, gdy akcja fokusu została zainicjowana przez klawiaturę. Każda akcja myszy lub zmiana fokusu programistycznego wyłącza tryb dla stylów wizualizacji fokusu. Aby uzyskać więcej informacji o różnicach między trybami koncentracji uwagi, zobacz temat [Omówienie fokusu](focus-overview.md).  
  
 Motywy dla formantów zawierają domyślne zachowanie stylu wizualnego fokusu, które staną się stylem wizualizacji fokusu dla wszystkich kontrolek w motywie. Ten styl motywu jest identyfikowany przez wartość klucza statycznego <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Jeśli zadeklarujesz własny styl wizualizacji fokus na poziomie aplikacji, to domyślne zachowanie stylu zostanie zastąpione przez motywy. Alternatywnie, jeśli zdefiniujesz cały motyw, należy użyć tego samego klucza do zdefiniowania stylu domyślnego zachowania dla całego motywu.  
  
 W motywach domyślny styl wizualny fokus jest ogólnie bardzo prosty. Poniżej przedstawiono przybliżone przybliżenie:  
  
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
## <a name="when-to-use-focus-visual-styles"></a>Kiedy używać stylów wizualnych fokusu  
 Koncepcyjnie wygląd wizualnych stylów fokusu zastosowanych do kontrolek powinien być spójny z kontrolką kontroli. Jednym ze sposobów zapewnienia spójności jest zmiana stylu wizualizacji fokus tylko w przypadku redagowania całego motywu, gdzie każda kontrolka zdefiniowana w motywie pobiera ten sam styl wizualizacji ostrości lub odmianę stylu, który jest wizualnie związany z kontrolką. roli. Alternatywnie, można użyć tego samego stylu (lub podobnych stylów) do stylu każdego elementu klawiatury, który można skupić na stronie lub w interfejsie użytkownika.  
  
 Ustawienie <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> na poszczególnych stylach formantów, które nie są częścią motywu, nie jest zamierzonym użyciem stylów wizualizacji fokusu. Wynika to z faktu, że niespójne zachowanie wizualizacji między kontrolkami może prowadzić do mylącego środowiska użytkownika dotyczącego fokusu klawiatury. Jeśli zamierzasz mieć specjalne zachowania dotyczące kontroli nad fokusem klawiatury, które są świadomie niespójne w motywie, znacznie lepszym rozwiązaniem jest użycie wyzwalaczy w stylach dla poszczególnych właściwości stanu wejściowego, takich jak <xref:System.Windows.UIElement.IsFocused%2A> lub <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Style wizualne Focus działają wyłącznie na potrzeby fokusu klawiatury. W związku z tym style wizualizacji fokusowej są typu funkcji ułatwień dostępu. Jeśli chcesz zmienić interfejs użytkownika dla dowolnego typu fokusu, bez względu na to, czy za pomocą myszy, klawiatury lub programowo, nie należy używać stylów wizualizacji fokusu, a zamiast tego użyć metod ustawiających i wyzwalaczy w stylach lub szablonach, które działają z wartości ogólnych właściwości ostrości takie jak <xref:System.Windows.UIElement.IsFocused%2A> lub <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Jak utworzyć styl wizualizacji fokusu  
 Styl utworzony dla stylu wizualizacji fokus powinien zawsze mieć <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Controls.Control>. Styl powinien obejmować głównie <xref:System.Windows.Controls.ControlTemplate>. Typ docelowy nie jest określany jako typ, do którego zostanie przypisany styl wizualizacji fokusu do <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Ponieważ typ docelowy jest zawsze <xref:System.Windows.Controls.Control>, należy użyć właściwości, które są wspólne dla wszystkich kontrolek (przy użyciu właściwości klasy <xref:System.Windows.Controls.Control> i jej klas bazowych). Należy utworzyć szablon, który będzie prawidłowo działać jako nakładka dla elementu interfejsu użytkownika i który nie będzie zasłaniał obszarów funkcjonalnych formantu. Zazwyczaj oznacza to, że opinia wizualna powinna być wyświetlana poza marginesami kontrolnymi lub jako niezależne lub niezauważalne efekty, które nie blokują testowania trafień na kontrolce, w której zastosowano styl wizualizacji fokusu. Właściwości, których można użyć w powiązaniu szablonu, które są przydatne do określania rozmiarów i pozycjonowania szablonu nakładki, obejmują <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>i <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternatywy do użycia stylu wizualizacji fokusu  
 W przypadku sytuacji, gdy użycie stylu wizualizacji fokusowej nie jest odpowiednie, ponieważ są tylko style pojedynczych kontrolek lub że chcesz mieć większą kontrolę nad szablonem kontrolki, istnieje wiele innych dostępnych właściwości i technik, które mogą tworzyć wizualizacje zachowanie w odpowiedzi na zmiany fokusu.  
  
 Wyzwalacze, metody ustawiające i metody ustawiające zdarzenia są szczegółowo omówione w [stylu i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md). Obsługa zdarzeń kierowanych została omówiona w [omówieniu zdarzeń kierowanych](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Jeśli interesuje Cię szczególny nacisk na klawiaturę, właściwość zależności <xref:System.Windows.UIElement.IsKeyboardFocused%2A> może być używana dla właściwości <xref:System.Windows.Trigger>. Wyzwalacz właściwości w stylu lub szablonie jest bardziej odpowiednią techniką służącą do definiowania zachowania fokusu klawiatury, który jest bardzo specyficzny dla jednej kontrolki i który może być niezgodny z zachowaniem fokusu klawiatury dla innych formantów.  
  
 Inna podobna właściwość zależności jest <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, co może być odpowiednie do użycia, jeśli chcesz wizualnie wywołać ten fokus klawiatury w obrębie złożenia lub w obszarze funkcjonalnym formantu. Na przykład można umieścić wyzwalacz <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, aby panel, który grupuje kilka kontrolek wygląda inaczej, nawet jeśli fokus klawiatury może precyzyjnie znajdować się na pojedynczym elemencie w tym panelu.  
  
 Można również użyć zdarzeń <xref:System.Windows.UIElement.GotKeyboardFocus> i <xref:System.Windows.UIElement.LostKeyboardFocus> (a także ich odpowiedników w wersji zapoznawczej). Tych zdarzeń można użyć jako podstawy dla <xref:System.Windows.EventSetter>lub można pisać procedury obsługi zdarzeń w kodzie.  
  
### <a name="other-focus-properties"></a>Inne właściwości fokusu  
 Jeśli chcesz, aby wszystkie możliwe przyczyny zmiany fokusu powodowały tworzenie zachowań wizualizacji, należy oprzeć metodę ustawiającą lub wyzwalaczem we właściwości zależności <xref:System.Windows.UIElement.IsFocused%2A> lub na zdarzeniach <xref:System.Windows.UIElement.GotFocus> lub <xref:System.Windows.UIElement.LostFocus> używanych dla <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Przegląd fokusu](focus-overview.md)
- [Przegląd danych wejściowych](input-overview.md)
