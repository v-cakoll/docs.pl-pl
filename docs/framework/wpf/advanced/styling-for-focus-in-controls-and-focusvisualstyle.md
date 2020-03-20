---
title: Style dla Fokusu w formantach i FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: fda7ed12d232af5a7cfb8eb43cbb09eb793da171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141202"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Style dla Fokusu w formantach i FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia dwa równoległe mechanizmy zmiany wyglądu formantu po odebraniu fokusu klawiatury. Pierwszy mechanizm jest użycie ustawiaczy właściwości dla <xref:System.Windows.UIElement.IsKeyboardFocused%2A> właściwości, takich jak w stylu lub szablonie, który jest stosowany do formantu. Drugi mechanizm jest zapewnienie oddzielnego stylu jako <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> wartość właściwości; "Focus visual style" tworzy oddzielne drzewo wizualne dla adorner, który rysuje się na górze formantu, zamiast zmieniać drzewa wizualnego formantu lub innego elementu interfejsu użytkownika, zastępując go. W tym temacie omówiono scenariusze, w których każdy z tych mechanizmów jest odpowiedni.  

<a name="Purpose"></a>
## <a name="the-purpose-of-focus-visual-style"></a>Cel skupienia styl wizualny  
 Funkcja stylu wizualnego fokusu zapewnia wspólny "model obiektu" do wprowadzania wizualnych opinii użytkowników na podstawie nawigacji klawiatury do dowolnego elementu interfejsu użytkownika. Jest to możliwe bez stosowania nowego szablonu do formantu lub znajomości kompozycji określonego szablonu.  
  
 Jednak właśnie dlatego, że funkcja stylu wizualnego fokusu działa bez znajomości szablonów formantu, wizualne sprzężenie zwrotne, które mogą być wyświetlane dla formantu przy użyciu stylu wizualnego fokusu, jest koniecznie ograniczone. Co funkcja faktycznie nie jest nakładanie innego drzewa wizualnego (adorner) na górze drzewa wizualnego, jak utworzone przez renderowania formantu za pośrednictwem jego szablonu. Definiujesz to oddzielne drzewo wizualne przy <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> użyciu stylu, który wypełnia właściwość.  
  
<a name="Default"></a>
## <a name="default-focus-visual-style-behavior"></a>Domyślne zachowanie w stylu wizualnym fokusu  
 Style wizualne fokusu działają tylko wtedy, gdy akcja fokusu została zainicjowana przez klawiaturę. Każda akcja myszy lub zmiana fokusu programowego wyłącza tryb stylów wizualnych ostrości. Aby uzyskać więcej informacji na temat różnic między trybami fokusu, zobacz [Omówienie fokusu](focus-overview.md).  
  
 Motywy formanty obejmują domyślne zachowanie stylu wizualnego fokusu, które staje się stylem wizualnym fokusu dla wszystkich formantów w motywie. Ten styl motywu jest identyfikowany przez <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>wartość klucza statycznego . Podczas deklarowania własnego stylu wizualnego fokusu na poziomie aplikacji, należy zastąpić to domyślne zachowanie stylu z motywów. Alternatywnie, jeśli zdefiniujesz cały motyw, należy użyć tego samego klawisza do zdefiniowania stylu domyślnego zachowania dla całego motywu.  
  
 W motywach domyślny styl wizualny fokusu jest na ogół bardzo prosty. Poniżej przedstawiono przybliżenie przybliżone:  
  
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
## <a name="when-to-use-focus-visual-styles"></a>Kiedy używać stylów wizualnych focus  
 Koncepcyjnie wygląd stylów wizualnych fokusu stosowane do formantów powinny być spójne od kontroli do kontroli. Jednym ze sposobów zapewnienia spójności jest zmiana stylu wizualnego ostrości tylko wtedy, gdy komponujesz cały motyw, gdzie każda formant zdefiniowany w motywie otrzymuje ten sam styl wizualny fokusu lub pewną odmianę stylu, która jest wizualnie związana od sterowania do Kontroli. Alternatywnie można użyć tego samego stylu (lub podobnych stylów) do stylu każdy element fokusujna na stronie lub w interfejsie użytkownika.  
  
 Ustawienie <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> poszczególnych stylów sterowania, które nie są częścią motywu, nie jest zamierzonym użyciem stylów wizualnych fokusu. Jest tak, ponieważ niespójne zachowanie wizualne między formantami może prowadzić do mylące środowisko użytkownika dotyczące fokusu klawiatury. Jeśli zamierzasz zachowania specyficzne dla kontroli dla fokusu klawiatury, które celowo nie są spójne w całym temacie, znacznie <xref:System.Windows.UIElement.IsFocused%2A> <xref:System.Windows.UIElement.IsKeyboardFocused%2A>lepszym podejściem jest użycie wyzwalaczy w stylach dla poszczególnych właściwości stanu wejściowego, takich jak lub .  
  
 Style wizualne focus działają wyłącznie na potrzeby ustawiania ostrości na klawiaturze. W związku z tym style wizualne fokusu są rodzajem funkcji ułatwień dostępu. Jeśli chcesz, aby zmiany interfejsu użytkownika dla dowolnego typu fokusu, czy to za pomocą myszy, klawiatury, lub programowo, to nie należy używać stylów wizualnych fokus, a zamiast tego należy używać ustawiaczy i wyzwalaczy w stylach lub szablonach, które działają od wartości ogólnych właściwości ostrości, takich jak <xref:System.Windows.UIElement.IsFocused%2A> lub <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>
## <a name="how-to-create-a-focus-visual-style"></a>Jak utworzyć styl wizualny fokusu  
 Styl, który tworzysz dla stylu wizualnego <xref:System.Windows.Controls.Control>ostrości, powinien zawsze mieć <xref:System.Windows.Style.TargetType%2A> Styl powinien składać się <xref:System.Windows.Controls.ControlTemplate>głównie z . Nie określono typu docelowego jako typu, w którym styl wizualny fokusu jest przypisany do pliku <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Ponieważ typ docelowy <xref:System.Windows.Controls.Control>jest zawsze, należy styl przy użyciu właściwości, które są <xref:System.Windows.Controls.Control> wspólne dla wszystkich formantów (przy użyciu właściwości klasy i jej klas podstawowych). Należy utworzyć szablon, który będzie poprawnie działać jako nakładka do elementu interfejsu użytkownika i który nie będzie zasłaniać obszarów funkcjonalnych formantu. Ogólnie rzecz biorąc oznacza to, że wizualne sprzężenie zwrotne powinny pojawić się poza marginesami formantu lub jako efekty tymczasowe lub dyskretne, które nie zablokują testowania trafień w formancie, w którym zastosowano styl wizualny fokusu. Właściwości, których można użyć w wiązaniu szablonu, które są przydatne do <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>określania rozmiaru i pozycjonowania szablonu nakładki, obejmują , , <xref:System.Windows.FrameworkElement.Margin%2A>i <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternatywy dla korzystania ze stylu wizualnego focus  
 W sytuacjach, w których użycie stylu wizualnego fokusu nie jest odpowiednie, ponieważ stylizujesz tylko pojedyncze formanty lub chcesz uzyskać większą kontrolę nad szablonem formantu, istnieje wiele innych dostępnych właściwości i technik, które mogą tworzyć wizualizacje zachowania w odpowiedzi na zmiany ostrości.  
  
 Wyzwalacze, ustawiacze i ustawiacze zdarzeń są szczegółowo omówione w [artykule Stylowanie i Tworzenie szablonów.](../../../desktop-wpf/fundamentals/styles-templates-overview.md) Obsługa kierowanych zdarzeń została omówiona w [omówienie zdarzeń trasowanych](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused (Klawiatura Zpowłoką)  
 Jeśli jesteś szczególnie zainteresowany fokus <xref:System.Windows.UIElement.IsKeyboardFocused%2A> klawiatury, właściwość zależności <xref:System.Windows.Trigger>może służyć do właściwości . Wyzwalacz właściwości w stylu lub szablonie jest bardziej odpowiednią techniką definiowania zachowania fokusu klawiatury, które jest bardzo specjalnie dla pojedynczego formantu i które może nie być wizualnie zgodne z zachowaniem fokusu klawiatury dla innych formantów.  
  
 Inną podobną właściwością zależności jest <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, który może być odpowiedni do użycia, jeśli chcesz wizualnie wywołać, że fokus klawiatury znajduje się gdzieś w obrębie kompozycji lub w obszarze funkcjonalnym formantu. Na przykład można umieścić <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> wyzwalacz w taki sposób, że panel, który grupuje kilka formantów, wygląda inaczej, nawet jeśli fokus klawiatury może być dokładniej na pojedynczym elemencie w tym panelu.  
  
 Można również użyć <xref:System.Windows.UIElement.GotKeyboardFocus> zdarzeń <xref:System.Windows.UIElement.LostKeyboardFocus> i (a także ich odpowiedników podglądu). Można użyć tych zdarzeń jako <xref:System.Windows.EventSetter>podstawy dla , lub można napisać programy obsługi zdarzeń w kodzie.  
  
### <a name="other-focus-properties"></a>Inne właściwości ostrości  
 Jeśli chcesz, aby wszystkie możliwe przyczyny zmiany fokusu wywołały zachowanie <xref:System.Windows.UIElement.IsFocused%2A> wizualne, należy oprzeć <xref:System.Windows.UIElement.GotFocus> ustawiacz lub wyzwalacz na właściwości zależności lub alternatywnie na zdarzeniach lub <xref:System.Windows.UIElement.LostFocus> zdarzeniach używanych dla programu <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Przegląd fokusu](focus-overview.md)
- [Przegląd Dane wejściowe](input-overview.md)
