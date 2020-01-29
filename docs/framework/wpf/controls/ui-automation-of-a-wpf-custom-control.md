---
title: Automatyzacja interfejsu użytkownika kontrolki niestandardowej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: a370ed2c6b1f3273eca93b4865a032e8299f1cfb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738201"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatyzacja interfejsu użytkownika formantu niestandardowego WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] zapewnia jeden uogólniony interfejs, za pomocą którego klienci automatyzacji mogą przeanalizować lub obsługiwać interfejsy użytkownika różnych platform i struktur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] włącza zarówno kod (test), jak i aplikacje ułatwień dostępu, takie jak czytniki zawartości ekranu, umożliwiają przeanalizowanie elementów interfejsu użytkownika i symulowanie interakcji użytkowników z innymi kodem. Aby uzyskać informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na wszystkich platformach, zobacz ułatwienia dostępu.  
  
 W tym temacie opisano sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla kontrolki niestandardowej, która jest uruchamiana w aplikacji WPF. WPF obsługuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pomocą drzewa obiektów automatyzacji równorzędnej, które są równoległe do drzewa elementów interfejsu użytkownika. Kod testowy i aplikacje zapewniające funkcje ułatwień dostępu mogą bezpośrednio korzystać z obiektów równorzędnych automatyzacji (dla kodu w procesie) lub przez uogólniony interfejs dostarczany przez [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Klasy równorzędne automatyzacji  
 Formanty WPF obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem drzewa klas równorzędnych, które pochodzą z <xref:System.Windows.Automation.Peers.AutomationPeer>. Według Konwencji nazwy klas elementów równorzędnych zaczynają się od nazwy klasy kontrolki i kończą się znakiem "AutomationPeer". Na przykład <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> jest klasą równorzędną dla klasy formantów <xref:System.Windows.Controls.Button>. Klasy równorzędne są w przybliżeniu równoważne z typami formantów [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], ale są specyficzne dla elementów WPF. Kod automatyzacji, który uzyskuje dostęp do aplikacji WPF za pomocą interfejsu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] nie korzysta bezpośrednio z elementów równorzędnych usługi Automation, ale kod automatyzacji w tym samym obszarze procesu może bezpośrednio korzystać z elementów równorzędnych usługi Automation.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Wbudowane klasy elementów równorzędnych automatyzacji  
 Elementy implementujące klasę elementu równorzędnego usługi Automation, jeśli akceptują działanie interfejsu od użytkownika lub zawierają informacje, które są niezbędne dla użytkowników aplikacji do odczytywania zawartości ekranu. Nie wszystkie elementy wizualizacji WPF mają obiekty równorzędne automatyzacji. Przykłady klas, które implementują elementy równorzędne automatyzacji, to <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>i <xref:System.Windows.Controls.Label>. Przykłady klas, które nie implementują elementów równorzędnych usługi Automation, są klasy, które pochodzą z <xref:System.Windows.Controls.Decorator>, takich jak <xref:System.Windows.Controls.Border>i klasy oparte na <xref:System.Windows.Controls.Panel>, takie jak <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.Canvas>.  
  
 Klasa bazowa <xref:System.Windows.Controls.Control> nie ma odpowiadającej jej klasy równorzędnej. Jeśli potrzebujesz klasy równorzędnej odpowiadającej formantowi niestandardowemu pochodzącemu z <xref:System.Windows.Controls.Control>, należy utworzyć niestandardową klasę równorzędną z <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Zagadnienia dotyczące zabezpieczeń dla pochodnych elementów równorzędnych  
 Elementy równorzędne automatyzacji muszą działać w środowisku częściowego zaufania. Kod w zestawie UIAutomationClient nie jest skonfigurowany do uruchamiania w środowisku częściowego zaufania, a kod elementu równorzędnego automatyzacji nie powinien odwoływać się do tego zestawu. Zamiast tego należy użyć klas w zestawie UIAutomationTypes. Na przykład należy użyć klasy <xref:System.Windows.Automation.AutomationElementIdentifiers> z zestawu UIAutomationTypes, który odpowiada klasie <xref:System.Windows.Automation.AutomationElement> w zestawie UIAutomationClient. Odwołuje się do zestawu UIAutomationTypes w kodzie równorzędnym usługi Automation.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Nawigacja równorzędna  
 Po znalezieniu elementu równorzędnego usługi Automation kod w procesie może nawigować po drzewie elementów równorzędnych, wywołując metody <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> obiektu. Nawigowanie między elementami WPF w kontrolce jest obsługiwane przez implementację metody <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> przez element równorzędny. System automatyzacji interfejsu użytkownika wywołuje tę metodę w celu skompilowania drzewa podelementów zawartych w kontrolce; na przykład Wyświetl listę elementów w polu listy. Domyślna metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> przejdzie do drzewa wizualnego elementów w celu skompilowania drzewa elementów równorzędnych automatyzacji. Niestandardowe kontrolki przesłonić tę metodę, aby uwidaczniać elementy podrzędne klientom automatyzacji, zwracając elementy równorzędne automatyzacji, które przekazują informacje lub zezwala na interakcję z użytkownikiem.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Dostosowania w pochodnym elemencie równorzędnym  
 Wszystkie klasy pochodne od <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> zawierają <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>chronionej metody wirtualnej. Funkcja WPF wywołuje <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>, aby uzyskać obiekt elementu równorzędnego usługi Automation dla każdej kontrolki. Kod automatyzacji może użyć elementu równorzędnego, aby uzyskać informacje o cechach i funkcjach formantu oraz zasymulować interaktywne użycie. Kontrolka niestandardowa, która obsługuje automatyzację, musi przesłonić <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> i zwrócić wystąpienie klasy, która pochodzi z <xref:System.Windows.Automation.Peers.AutomationPeer>. Na przykład, Jeśli kontrolka niestandardowa dziedziczy z klasy <xref:System.Windows.Controls.Primitives.ButtonBase>, wówczas obiekt zwrócony przez <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> powinien pochodzić od <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Podczas implementowania kontrolki niestandardowej należy zastąpić metody "Core" z klasy równorzędnej usługi Automation, która opisuje zachowanie unikatowe i specyficzne dla kontrolki niestandardowej.  
  
### <a name="override-oncreateautomationpeer"></a>Zastąp OnCreateAutomationPeer  
 Zastąp metodę <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> niestandardowej kontrolki, aby zwracała obiekt dostawcy, który musi być pochodny bezpośrednio lub pośrednio z <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Przesłoń GetPattern  
 Elementy równorzędne automatyzacji upraszczają pewne aspekty implementacji dostawców [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] po stronie serwera, ale elementy równorzędne automatyzacji kontroli muszą nadal obsługiwać interfejsy wzorców. Podobnie jak w przypadku dostawców spoza platformy WPF, elementy równorzędne obsługują wzorce kontroli, dostarczając implementacje interfejsów w przestrzeni nazw <xref:System.Windows.Automation.Provider?displayProperty=nameWithType>, takich jak <xref:System.Windows.Automation.Provider.IInvokeProvider>. Interfejsy wzorca kontroli mogą być implementowane przez element równorzędny lub przez inny obiekt. Implementacja elementu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> zwraca obiekt obsługujący określony wzorzec. kod [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje metodę <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> i określa <xref:System.Windows.Automation.Peers.PatternInterface> wartość wyliczenia. Przesłonięcie <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> powinno zwrócić obiekt implementujący określony wzorzec. Jeśli kontrolka nie ma niestandardowej implementacji wzorca, można wywołać implementację typu podstawowego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>, aby pobrać jej implementację lub wartość null, Jeśli wzorzec nie jest obsługiwany dla tego typu formantu. Na przykład niestandardowa kontrolka NumericUpDown może być ustawiona na wartość w zakresie, więc jej element równorzędny [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] implementuje interfejs <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Poniższy przykład pokazuje, jak Metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> elementu równorzędnego została przesłonięta, aby odpowiedzieć na wartość <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> może również określać podelement jako dostawcę wzorca. Poniższy kod przedstawia sposób, w jaki <xref:System.Windows.Controls.ItemsControl> przenosi obsługę wzorca przewijania do elementu równorzędnego wewnętrznej kontroli <xref:System.Windows.Controls.ScrollViewer>.  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Aby określić podelement dla obsługi wzorca, ten kod pobiera obiekt podelementu, tworzy element równorzędny za pomocą metody <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>, ustawia właściwość <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> nowego elementu równorzędnego na bieżącą komunikację równorzędną i zwraca nowy element równorzędny. Ustawienie <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> w podelemencie uniemożliwia wyświetlenie elementu w drzewie elementów równorzędnych usługi Automation i oznacza wszystkie zdarzenia wywoływane przez podelement pochodzący z formantu określonego w <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. Formant <xref:System.Windows.Controls.ScrollViewer> nie jest wyświetlany w drzewie automatyzacji, a zdarzenia przewijania, które generuje, pochodzą z obiektu <xref:System.Windows.Controls.ItemsControl>.  
  
### <a name="override-core-methods"></a>Przesłoń metody "Core"  
 Kod automatyzacji pobiera informacje o kontrolce przez wywoływanie metod publicznych klasy równorzędnej. Aby podać informacje o kontrolce, Zastąp każdą metodę o nazwie "Core", gdy implementacja formantu różni się od tego, który jest określony przez podstawową klasę elementu równorzędnego usługi Automation. Co najmniej formant musi implementować <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> metod, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Twoja implementacja <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> opisuje swój formant, zwracając wartość <xref:System.Windows.Automation.ControlType>. Chociaż można zwrócić <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, należy zwrócić jeden z bardziej specyficznych typów kontroli, jeśli dokładnie opisuje formant. Wartość zwracana przez <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> wymaga dodatkowej pracy dla dostawcy w celu zaimplementowania [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produkty klienckie nie mogą przewidzieć struktury kontroli, interakcji z klawiaturą i możliwych wzorców kontrolek.  
  
 Zaimplementuj metody <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>, aby wskazać, czy kontrolka zawiera zawartość danych, czy też pełni rolę interaktywną w interfejsie użytkownika (lub obu). Domyślnie obie metody zwracają `true`. Te ustawienia zwiększają użyteczność narzędzi automatyzacji, takich jak czytniki ekranu, które mogą używać tych metod do filtrowania drzewa automatyzacji. Jeśli metoda <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> przeniesie obsługę wzorca do elementu równorzędnego, Metoda <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> elementu równorzędnego węzła może zwrócić wartość false, aby ukryć element równorzędny elementu podrzędnego w drzewie automatyzacji. Na przykład przewijanie w <xref:System.Windows.Controls.ListBox> jest obsługiwane przez <xref:System.Windows.Controls.ScrollViewer>, a element równorzędny usługi Automation dla <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> jest zwracany przez <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metodę <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>, która jest skojarzona z <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. W związku z tym Metoda <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> zwraca `false`, tak aby <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> nie była wyświetlana w drzewie automatyzacji.  
  
 Element równorzędny usługi Automation powinien zapewnić odpowiednie wartości domyślne dla kontrolki. Należy zauważyć, że kod XAML, który odwołuje się do formantu, może zastąpić implementacje równorzędne metod podstawowych przez uwzględnienie atrybutów <xref:System.Windows.Automation.AutomationProperties>. Na przykład poniższy kod XAML tworzy przycisk, który ma dwie niestandardowe właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementowanie dostawców wzorców  
 Interfejsy zaimplementowane przez niestandardowego dostawcę są zadeklarowane w sposób jawny, jeśli element będący właścicielem dziedziczy bezpośrednio z <xref:System.Windows.Controls.Control>. Na przykład poniższy kod deklaruje element równorzędny dla <xref:System.Windows.Controls.Control>, który implementuje wartość zakresu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Jeśli kontrolka będąca właścicielem pochodzi z określonego typu formantu, takiego jak <xref:System.Windows.Controls.Primitives.RangeBase>, element równorzędny może pochodzić od równoważnej pochodnej klasy równorzędnej. W takim przypadku element równorzędny pochodzi od <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, który dostarcza podstawową implementację <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Poniższy kod przedstawia deklarację takiego elementu równorzędnego.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Aby zapoznać się z przykładową implementacją, zobacz [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) lub [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) kod źródłowy, który implementuje i zużywa kontrolkę niestandardową NumericUpDown.  
  
### <a name="raise-events"></a>Zgłoś zdarzenia  
 Klienci usługi Automation mogą subskrybować zdarzenia automatyzacji. Kontrolki niestandardowe muszą raportować zmiany w stanie kontroli, wywołując metodę <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>. Podobnie, gdy wartość właściwości ulega zmianie, wywołaj metodę <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>. Poniższy kod pokazuje, jak uzyskać obiekt elementu równorzędnego z kodu sterującego i wywołać metodę w celu podniesienia zdarzenia. Jako Optymalizacja kod określa, czy istnieją detektory dla tego typu zdarzenia. Podnoszenie zdarzenia tylko wtedy, gdy istnieją detektory zapobiegają niepotrzebnemu obciążeniu i pomagają formantowi pozostały czas odpowiedzi.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika](../../ui-automation/ui-automation-overview.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Kontrolka niestandardowa NumericUpDown (C#) w witrynie GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Kontrolka niestandardowa NumericUpDown (Visual Basic) w witrynie GitHub](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
