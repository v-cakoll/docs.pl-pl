---
title: Automatyzacja interfejsu użytkownika formantu niestandardowego WPF
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
ms.openlocfilehash: ef045ffaac47c6cb196d821c25d96c4d2cd7bf88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254250"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatyzacja interfejsu użytkownika formantu niestandardowego WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]zapewnia jeden uogólniony interfejs, za pomocą którego klienci automatyzacji mogą testować lub obsługiwać interfejsy użytkownika różnych platform i struktur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]Włącza zarówno kod (test), jak i aplikacje ułatwień dostępu, takie jak czytniki zawartości ekranu, umożliwiają przeanalizowanie elementów interfejsu użytkownika i symulowanie interakcji użytkownika z innymi kodem. Aby uzyskać informacje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na temat wszystkich platform, zobacz ułatwienia dostępu.  
  
 W tym temacie opisano sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla kontrolki niestandardowej, która jest uruchamiana w aplikacji WPF. WPF obsługuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] drzewo obiektów automatyzacji równorzędnej, które są równoległe w drzewie elementów interfejsu użytkownika. Kod testowy i aplikacje zapewniające funkcje ułatwień dostępu mogą bezpośrednio korzystać z obiektów równorzędnych automatyzacji (dla kodu w procesie) lub przez uogólniony Interfejs [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]zapewniany przez program.  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Klasy równorzędne automatyzacji  
 Formanty WPF obsługują [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] w drzewie klasy równorzędnej, które pochodzą od <xref:System.Windows.Automation.Peers.AutomationPeer>. Według Konwencji nazwy klas elementów równorzędnych zaczynają się od nazwy klasy kontrolki i kończą się znakiem "AutomationPeer". Na przykład <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> jest klasą równorzędną <xref:System.Windows.Controls.Button> dla klasy Control. Klasy równorzędne są w przybliżeniu równoważne [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] z typami formantów, ale są [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] specyficzne dla elementów. Kod automatyzacji, który uzyskuje dostęp do aplikacji [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] WPF za pomocą interfejsu, nie korzysta bezpośrednio z elementów równorzędnych usługi Automation, ale kod automatyzacji w tym samym obszarze procesu może bezpośrednio korzystać z elementów równorzędnych usługi Automation.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Wbudowane klasy elementów równorzędnych automatyzacji  
 Elementy implementujące klasę elementu równorzędnego usługi Automation, jeśli akceptują działanie interfejsu od użytkownika lub zawierają informacje, które są niezbędne dla użytkowników aplikacji do odczytywania zawartości ekranu. Nie wszystkie elementy wizualizacji WPF mają obiekty równorzędne automatyzacji. Przykłady klas, które implementują elementy równorzędne <xref:System.Windows.Controls.Button>automatyzacji <xref:System.Windows.Controls.TextBox>, to <xref:System.Windows.Controls.Label>, i. Przykłady klas, które nie implementują elementów równorzędnych automatyzacji, to klasy, <xref:System.Windows.Controls.Decorator>które pochodzą z <xref:System.Windows.Controls.Border>, takie jak i klasy <xref:System.Windows.Controls.Panel>oparte na, <xref:System.Windows.Controls.Grid> takie <xref:System.Windows.Controls.Canvas>jak i.  
  
 Klasa bazowa <xref:System.Windows.Controls.Control> nie ma odpowiadającej jej klasy równorzędnej. Jeśli potrzebujesz klasy równorzędnej, aby odpowiadała formantowi niestandardowemu pochodzącemu <xref:System.Windows.Controls.Control>z, należy utworzyć niestandardową klasę elementu <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>równorzędnego z.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Zagadnienia dotyczące zabezpieczeń dla pochodnych elementów równorzędnych  
 Elementy równorzędne automatyzacji muszą działać w środowisku częściowego zaufania. Kod w zestawie UIAutomationClient nie jest skonfigurowany do uruchamiania w środowisku częściowego zaufania, a kod elementu równorzędnego automatyzacji nie powinien odwoływać się do tego zestawu. Zamiast tego należy użyć klas w zestawie UIAutomationTypes. Na przykład należy użyć <xref:System.Windows.Automation.AutomationElementIdentifiers> klasy z zestawu UIAutomationTypes, która odnosi <xref:System.Windows.Automation.AutomationElement> się do klasy w zestawie UIAutomationClient. Odwołuje się do zestawu UIAutomationTypes w kodzie równorzędnym usługi Automation.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Nawigacja równorzędna  
 Po znalezieniu elementu równorzędnego usługi Automation kod w procesie może nawigować po drzewie elementów równorzędnych, wywołując metody <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> obiektu <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> i. Nawigacja między [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementami w kontrolce jest obsługiwana przez implementację <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> metody przez element równorzędny. System automatyzacji interfejsu użytkownika wywołuje tę metodę w celu skompilowania drzewa podelementów zawartych w kontrolce; na przykład Wyświetl listę elementów w polu listy. Metoda Domyślna <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> przejdzie do drzewa wizualnego elementów w celu skompilowania drzewa elementów równorzędnych automatyzacji. Niestandardowe kontrolki przesłonić tę metodę, aby uwidaczniać elementy podrzędne klientom automatyzacji, zwracając elementy równorzędne automatyzacji, które przekazują informacje lub zezwala na interakcję z użytkownikiem.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Dostosowania w pochodnym elemencie równorzędnym  
 Wszystkie klasy, które pochodzą <xref:System.Windows.UIElement> z <xref:System.Windows.ContentElement> i zawierają chronioną metodę <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>wirtualną. Wywołanie <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> WPF do pobrania obiektu elementu równorzędnego usługi Automation dla każdej kontrolki. Kod automatyzacji może użyć elementu równorzędnego, aby uzyskać informacje o cechach i funkcjach formantu oraz zasymulować interaktywne użycie. Kontrolka niestandardowa, która obsługuje <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> automatyzację, musi przesłonić i zwrócić wystąpienie <xref:System.Windows.Automation.Peers.AutomationPeer>klasy, która pochodzi od. Na przykład, Jeśli kontrolka niestandardowa dziedziczy <xref:System.Windows.Controls.Primitives.ButtonBase> z klasy, obiekt zwrócony przez <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> element powinien pochodzić od <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Podczas implementowania kontrolki niestandardowej należy zastąpić metody "Core" z klasy równorzędnej usługi Automation, która opisuje zachowanie unikatowe i specyficzne dla kontrolki niestandardowej.  
  
### <a name="override-oncreateautomationpeer"></a>Zastąp OnCreateAutomationPeer  
 Zastąp <xref:System.Windows.Automation.Peers.AutomationPeer>metodę dla kontrolki niestandardowej, aby zwracała obiekt dostawcy, który musi być pochodny bezpośrednio lub pośrednio z. <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>  
  
### <a name="override-getpattern"></a>Przesłoń GetPattern  
 Elementy równorzędne automatyzacji upraszczają pewne aspekty implementacji dostawców po [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] stronie serwera, ale elementy równorzędne automatyzacji kontroli muszą nadal obsługiwać interfejsy wzorców. Podobnie jak w przypadku dostawców spoza platformy WPF, elementy równorzędne obsługują wzorce kontroli przez dostarczanie implementacji <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> interfejsów w przestrzeni nazw <xref:System.Windows.Automation.Provider.IInvokeProvider>, takich jak. Interfejsy wzorca kontroli mogą być implementowane przez element równorzędny lub przez inny obiekt. Implementacja elementu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> zwraca obiekt obsługujący określony wzorzec. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]kod wywołuje <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metodę i <xref:System.Windows.Automation.Peers.PatternInterface> określa wartość wyliczenia. Przesłonięcie <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> powinien zwrócić obiekt implementujący określony wzorzec. Jeśli kontrolka nie ma niestandardowej implementacji wzorca, można wywołać implementację <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> typu podstawowego, aby pobrać jej implementację lub wartość null, Jeśli wzorzec nie jest obsługiwany dla tego typu formantu. Na przykład niestandardowa kontrolka NumericUpDown może być ustawiona na wartość w zakresie, więc jej [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] element równorzędny <xref:System.Windows.Automation.Provider.IRangeValueProvider> implementuje interfejs. Poniższy przykład pokazuje, jak <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> Metoda elementu równorzędnego została przesłonięta w celu reagowania <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> na wartość.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> Metoda może również określać podelement jako dostawcę wzorca. Poniższy kod pokazuje, jak <xref:System.Windows.Controls.ItemsControl> transfery obsługują wzorzec przewijania do elementu równorzędnego jego <xref:System.Windows.Controls.ScrollViewer> wewnętrznej kontroli.  
  
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
  
 Aby określić podelement dla obsługi wzorca, ten kod pobiera obiekt podelementu, tworzy element równorzędny przy użyciu <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> metody, <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> ustawia właściwość nowego elementu równorzędnego na bieżącą końcówkę i zwraca nowy element równorzędny. Ustawienie <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> dla elementu podrzędnego zapobiega pojawianiu się elementu podrzędnego w drzewie elementów równorzędnych usługi Automation i wyznacza wszystkie zdarzenia wywoływane przez podelement, który pochodzi z formantu określonego w <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. Formant nie jest wyświetlany w drzewie automatyzacji, a zdarzenia przewijania, które generuje, pojawiają się jako pochodzące <xref:System.Windows.Controls.ItemsControl> z obiektu. <xref:System.Windows.Controls.ScrollViewer>  
  
### <a name="override-core-methods"></a>Przesłoń metody "Core"  
 Kod automatyzacji pobiera informacje o kontrolce przez wywoływanie metod publicznych klasy równorzędnej. Aby podać informacje o kontrolce, Zastąp każdą metodę o nazwie "Core", gdy implementacja formantu różni się od tego, który jest określony przez podstawową klasę elementu równorzędnego usługi Automation. Co najmniej formant musi implementować <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> metody i <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> , jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Twoja implementacja <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> zawiera opis kontrolki przez <xref:System.Windows.Automation.ControlType> zwrócenie wartości. Chociaż można zwrócić <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, należy zwrócić jeden z bardziej specyficznych typów kontroli, jeśli dokładnie opisuje formant. Wartość <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> zwracana przez dostawcę wymaga dodatkowej pracy dla dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produkty klienckie nie mogą przewidywać struktury kontroli, interakcji z klawiaturą i możliwych wzorców kontrolek.  
  
 Zaimplementuj metody <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>i, aby wskazać, czy formant zawiera zawartość danych, czy też pełni rolę interaktywną w interfejsie użytkownika (lub obu). <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> Domyślnie obie metody zwracają `true`. Te ustawienia zwiększają użyteczność narzędzi automatyzacji, takich jak czytniki ekranu, które mogą używać tych metod do filtrowania drzewa automatyzacji. Jeśli metoda przenosi obsługę wzorca do elementu równorzędnego elementów podrzędnych, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> Metoda elementu równorzędnego elementu podrzędnego może zwrócić wartość false, aby ukryć element równorzędny elementu podrzędnego w drzewie automatyzacji. <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> Na przykład, przewijanie w <xref:System.Windows.Controls.ListBox> a jest obsługiwane <xref:System.Windows.Controls.ScrollViewer>przez, a element równorzędny automatyzacji <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> dla jest zwracany przez metodę <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> , która jest skojarzona z <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. W związku z tym <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> `false`Metoda zwraca, tak abyniebyławyświetlanawdrzewieautomatyzacji.<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>  
  
 Element równorzędny usługi Automation powinien zapewnić odpowiednie wartości domyślne dla kontrolki. Należy zauważyć, że kod XAML odwołujący się do formantu może zastąpić implementacje równorzędne metod podstawowych przez dołączenie <xref:System.Windows.Automation.AutomationProperties> atrybutów. Na przykład poniższy kod XAML tworzy przycisk, który ma dwie niestandardowe [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementowanie dostawców wzorców  
 Interfejsy implementowane przez niestandardowego dostawcę są zadeklarowane w sposób jawny, jeśli element będący właścicielem dziedziczy bezpośrednio z <xref:System.Windows.Controls.Control>. Na przykład poniższy kod deklaruje element równorzędny dla <xref:System.Windows.Controls.Control> , który implementuje wartość zakresu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Jeśli kontrolka będąca właścicielem pochodzi z określonego typu formantu, takiego <xref:System.Windows.Controls.Primitives.RangeBase>jak, element równorzędny może pochodzić od równoważnej pochodnej klasy równorzędnej. W takim przypadku element równorzędny pochodzi od <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, który dostarcza podstawową implementację programu. <xref:System.Windows.Automation.Provider.IRangeValueProvider> Poniższy kod przedstawia deklarację takiego elementu równorzędnego.  
  
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
 Klienci usługi Automation mogą subskrybować zdarzenia automatyzacji. Kontrolki niestandardowe muszą raportować zmiany w stanie kontroli, wywołując <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> metodę. Podobnie, gdy wartość właściwości ulega zmianie, wywołaj <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> metodę. Poniższy kod pokazuje, jak uzyskać obiekt elementu równorzędnego z kodu sterującego i wywołać metodę w celu podniesienia zdarzenia. Jako Optymalizacja kod określa, czy istnieją detektory dla tego typu zdarzenia. Podnoszenie zdarzenia tylko wtedy, gdy istnieją detektory zapobiegają niepotrzebnemu obciążeniu i pomagają formantowi pozostały czas odpowiedzi.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika](../../ui-automation/ui-automation-overview.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Kontrolka niestandardowa NumericUpDown (C#) w witrynie GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Kontrolka niestandardowa NumericUpDown (Visual Basic) w witrynie GitHub](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
