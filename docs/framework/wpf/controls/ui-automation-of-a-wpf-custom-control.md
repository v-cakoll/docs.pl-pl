---
title: Automatyzacja interfejsu użytkownika formantu niestandardowego
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
ms.openlocfilehash: 9c33d0e5da70820041ba2a2881082d9f7d179fc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187507"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatyzacja interfejsu użytkownika formantu niestandardowego WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]zapewnia jeden, uogólniony interfejs, który klienci automatyzacji można użyć do badania lub obsługi interfejsów użytkownika różnych platform i struktur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia zarówno kod zapewnienia jakości (test) i aplikacje ułatwień dostępu, takie jak czytniki ekranu, aby zbadać elementy interfejsu użytkownika i symulować interakcję użytkownika z nimi z innego kodu. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] informacje na temat wszystkich platform, zobacz ułatwienia dostępu.  
  
 W tym temacie opisano sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla niestandardowego formantu, który działa w aplikacji WPF. WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] WPF obsługuje za pośrednictwem drzewa obiektów automatyzacji elementów równorzędnych, które paralele drzewa elementów interfejsu użytkownika. Kod testowy i aplikacje zapewniające funkcje ułatwień dostępu mogą używać obiektów równorzędnych automatyzacji bezpośrednio (w przypadku kodu w trakcie procesu) lub za pośrednictwem uogólnionego interfejsu udostępnianego przez [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]program .  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>Klasy elementów równorzędnych automatyzacji  
 WPF WPF kontroluje obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem <xref:System.Windows.Automation.Peers.AutomationPeer>drzewa klas elementów równorzędnych, które wynikają z . Zgodnie z konwencją nazwy klas równorzędnych zaczynają się od nazwy klasy kontrolnej i kończą się na "AutomationPeer". Na przykład <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> jest klasą <xref:System.Windows.Controls.Button> równorzędową dla klasy kontrolnej. Klasy elementów równorzędnych są w przybliżeniu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] równoważne typów kontroli, ale są specyficzne dla elementów WPF. Kod automatyzacji, który uzyskuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] dostęp do aplikacji WPF za pośrednictwem interfejsu nie używa łajdakami automatyzacji bezpośrednio, ale kod automatyzacji w tej samej przestrzeni procesowej można użyć automatyzacji równorzędnych bezpośrednio.  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>Wbudowane klasy elementów elementów automatyzacji  
 Elementy implementują klasy peer automatyzacji, jeśli akceptują działania interfejsu od użytkownika lub jeśli zawierają informacje potrzebne przez użytkowników aplikacji czytnika ekranu. Nie wszystkie elementy wizualne WPF mają elementy równorzędne automatyzacji. Przykładami klas implementujnych <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox>przez <xref:System.Windows.Controls.Label>elementy równorzędne automatyzacji są , i . Przykładami klas, które nie implementują kamicy <xref:System.Windows.Controls.Decorator>równorzędnych automatyzacji, są klasy, które wynikają z , takie <xref:System.Windows.Controls.Border>jak , i klasy oparte na <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.Canvas>.  
  
 Klasa <xref:System.Windows.Controls.Control> podstawowa nie ma odpowiedniej klasy równorzędnej. Jeśli klasa równorzędna musi odpowiadać formancie niestandardowemu, które wywodzi się z <xref:System.Windows.Controls.Control>, należy wyprowadzić niestandardową klasę równorzędną z . <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>Zagadnienia dotyczące zabezpieczeń dla rysów pochodnych  
 Elementy równorzędne automatyzacji muszą działać w środowisku częściowego zaufania. Kod w UIAutomationClient zestawu nie jest skonfigurowany do uruchamiania w środowisku częściowego zaufania i kodu równorzędnego automatyzacji nie należy odwoływać się do tego zestawu. Zamiast tego należy użyć klas w UIAutomationTypes zestawu. Na przykład należy użyć <xref:System.Windows.Automation.AutomationElementIdentifiers> klasy z UIAutomationTypes zestawu, który <xref:System.Windows.Automation.AutomationElement> odpowiada klasy w UIAutomationClient zestawu. Jest to bezpieczne do odwołania UIAutomationTypes zestawu w kodzie równorzędnym automatyzacji.  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>Nawigacja równorzędna  
 Po zlokalizowaniu elementu równorzędnego automatyzacji, kod w trakcie <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> można <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> poruszać się po drzewie równorzędnym, wywołując obiektu i metody. Nawigacja między elementami WPF w formancie jest <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> obsługiwana przez implementację metody równorzędnej. System automatyzacji interfejsu użytkownika wywołuje tę metodę do tworzenia drzewa podelementów zawartych w formancie; na przykład lista elementów w polu listy. Metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> domyślna przechodzi przez drzewo wizualne elementów do tworzenia drzewa elementów równorzędnych automatyzacji. Formanty niestandardowe zastępują tę metodę, aby udostępnić elementy podrzędne klientom automatyzacji, zwracając elementy równorzędne automatyzacji elementów, które przekazują informacje lub umożliwiają interakcję z użytkownikiem.  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>Dostosowania w elementach elementów pochodnych  
 Wszystkie klasy, które <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> wywodzą się <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>z chronionej metody wirtualnej i zawierają je. WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> wywołania, aby uzyskać obiekt równorzędny automatyzacji dla każdego formantu. Kod automatyzacji można użyć elementu równorzędnego, aby uzyskać informacje o właściwościach i funkcjach formantu oraz symulować użycie interaktywne. Niestandardowy formant obsługujący automatyzację musi zastąpić i zwrócić wystąpienie <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> klasy, która wywodzi się z <xref:System.Windows.Automation.Peers.AutomationPeer>. Na przykład jeśli formant niestandardowy <xref:System.Windows.Controls.Primitives.ButtonBase> pochodzi z klasy, <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> obiekt zwracany przez powinien pochodzić od <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Podczas implementowania formantu niestandardowego, należy zastąpić "Core" metody z klasy równorzędnej automatyzacji podstawowej, które opisują zachowanie unikatowe i specyficzne dla formantu niestandardowego.  
  
### <a name="override-oncreateautomationpeer"></a>Zastąp oncreateautomationpeer  
 Zastąpić <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> metodę formantu niestandardowego, tak aby zwracał obiekt dostawcy, <xref:System.Windows.Automation.Peers.AutomationPeer>który musi pochodzić bezpośrednio lub pośrednio z programu .  
  
### <a name="override-getpattern"></a>Zastępowanie GetPattern  
 Elementy równorzędne automatyzacji [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] upraszczają niektóre aspekty implementacji dostawców po stronie serwera, ale niestandardowe elementy równorzędne automatyzacji sterowania muszą nadal obsługiwać interfejsy wzorców. Podobnie jak dostawcy innych niż WPF, elementy równorzędne <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> obsługują wzorce <xref:System.Windows.Automation.Provider.IInvokeProvider>kontroli, udostępniając implementacje interfejsów w obszarze nazw, takich jak . Interfejsy wzorca kontroli mogą być implementowane przez sam element równorzędny lub przez inny obiekt. Implementacja peer <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> zwraca obiekt, który obsługuje określony wzorzec. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]kod wywołuje <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metodę i <xref:System.Windows.Automation.Peers.PatternInterface> określa wartość wyliczenia. Zastąpienie <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> należy zwrócić obiekt, który implementuje określony wzorzec. Jeśli formant nie ma niestandardowej implementacji wzorca, można wywołać <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> implementację typu podstawowego, aby pobrać jego implementację lub wartość null, jeśli wzorzec nie jest obsługiwany dla tego typu formantu. Na przykład niestandardowy formant NumericUpDown można ustawić na wartość [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] w zakresie, więc jego element równorzędny zaimplementuje <xref:System.Windows.Automation.Provider.IRangeValueProvider> interfejs. Poniższy przykład pokazuje, jak <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metoda elementu równorzędnego jest zastępowana, aby odpowiedzieć na <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> wartość.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> może również określić podelement jako dostawcy wzorca. Poniższy kod <xref:System.Windows.Controls.ItemsControl> pokazuje, jak przenosi obsługi wzorca przewijania do elementu równorzędnego jego kontroli wewnętrznej. <xref:System.Windows.Controls.ScrollViewer>  
  
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
  
 Aby określić podelement do obsługi wzorców, ten kod pobiera obiekt podsezaku, tworzy element równorzędny przy użyciu <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> metody, ustawia <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> właściwość nowego elementu równorzędnego do bieżącego elementu równorzędnego i zwraca nowy element równorzędny. Ustawienie <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> podelement zapobiega pojawianiu się podelementu w drzewie elementów równorzędnych automatyzacji i oznacza <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>wszystkie zdarzenia wywoływane przez podelement jako pochodzące z formantu określonego w programie . Formant <xref:System.Windows.Controls.ScrollViewer> nie pojawia się w drzewie automatyzacji i przewijania zdarzeń, które generuje wydają się pochodzić z <xref:System.Windows.Controls.ItemsControl> obiektu.  
  
### <a name="override-core-methods"></a>Zastępowanie metod "Core"  
 Kod automatyzacji pobiera informacje o formancie, wywołując metody publiczne klasy równorzędnej. Aby podać informacje o formancie, należy zastąpić każdą metodę, której nazwa kończy się na "Core", gdy implementacja formantu różni się od tej dostarczonej przez klasę równorzędną automatyzacji podstawowej. Co najmniej formant musi <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> implementować metody i, <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Implementacja <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> opisuje formant, zwracając <xref:System.Windows.Automation.ControlType> wartość. Chociaż można <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>zwrócić, należy zwrócić jeden z bardziej szczegółowych typów formantów, jeśli dokładnie opisuje formant. Wartość zwracana <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> wymaga dodatkowej pracy [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]dla [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy do zaimplementowania , a produkty klienckie nie są w stanie przewidzieć struktury kontroli, interakcji z klawiaturą i możliwych wzorców kontroli.  
  
 Zaimplementuj <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> metody i <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metody, aby wskazać, czy formant zawiera zawartość danych lub spełnia rolę interaktywną w interfejsie użytkownika (lub obu). Domyślnie obie metody `true`zwracają . Te ustawienia zwiększają użyteczność narzędzi automatyzacji, takich jak czytniki ekranu, które mogą używać tych metod do filtrowania drzewa automatyzacji. Jeśli <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metoda przenosi obsługi wzorca do elementu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> podelementu, podelement peer metoda może zwrócić false, aby ukryć element równorzędny podelement z drzewa automatyzacji. Na przykład <xref:System.Windows.Controls.ListBox> przewijanie w a <xref:System.Windows.Controls.ScrollViewer>jest obsługiwane przez <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> program , <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> a element równorzędny automatyzacji jest zwracany przez metodę <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> skojarzoną z . <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer> W związku <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> z tym <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> `false`metoda zwraca <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> , tak, że nie pojawia się w drzewie automatyzacji.  
  
 Element równorzędny automatyzacji powinien podać odpowiednie wartości domyślne dla formantu. Należy zauważyć, że XAML, który odwołuje się do formantu <xref:System.Windows.Automation.AutomationProperties> można zastąpić implementacje elementów równorzędnych podstawowych metod, w tym atrybuty. Na przykład następujący kod XAML tworzy przycisk, [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] który ma dwie niestandardowe właściwości.  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementowanie dostawców wzorców  
 Interfejsy zaimplementowane przez niestandardowego dostawcę są jawnie zadeklarowane, jeśli element własny pochodzi bezpośrednio z <xref:System.Windows.Controls.Control>. Na przykład poniższy kod deklaruje element <xref:System.Windows.Controls.Control> równorzędny dla, który implementuje wartość zakresu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Jeśli formant posiadania pochodzi z określonego typu <xref:System.Windows.Controls.Primitives.RangeBase>formantu, takiego jak , element równorzędny może pochodzić z równoważnej pochodnej klasy równorzędnej. W takim przypadku element równorzędny będzie pochodzić z <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, który dostarcza podstawową implementację <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Poniższy kod przedstawia deklarację takiego elementu równorzędnego.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Na przykład implementacji zobacz kod źródłowy [języka C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) lub [Visual Basic,](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) który implementuje i zużywa formant niestandardowy NumericUpDown.  
  
### <a name="raise-events"></a>Podnieść wydarzenia  
 Klienci automatyzacji mogą subskrybować zdarzenia automatyzacji. Formanty niestandardowe muszą zgłaszać <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> zmiany w celu kontrolowania stanu, wywołując metodę. Podobnie, gdy zmienia się wartość <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> właściwości, wywołaj metodę. Poniższy kod pokazuje, jak uzyskać obiekt równorzędny z wewnątrz kodu kontrolnego i wywołać metodę, aby podnieść zdarzenie. Jako optymalizacja kod określa, czy istnieją detektory dla tego typu zdarzenia. Wywoływanie zdarzenia tylko wtedy, gdy istnieją detektory unika niepotrzebnych narzutów i pomaga kontroli pozostają elastyczne.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd automatyzacji interfejsu użytkownika](../../ui-automation/ui-automation-overview.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Kontrola niestandardowa NumericUpDown (C#) w usłudze GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Kontrola niestandardowa NumericUpDown (Visual Basic) w usłudze GitHub](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
