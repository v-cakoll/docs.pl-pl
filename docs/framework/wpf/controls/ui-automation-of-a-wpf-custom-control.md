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
ms.openlocfilehash: 0e77b26bdc7eaa038c69a6fb706ee066aa223a2e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211956"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatyzacja interfejsu użytkownika formantu niestandardowego WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] udostępnia interfejs pojedynczego, uogólnionego tej usługi automation, w których klienci mogą używać do sprawdzania lub działanie interfejsów użytkownika różnych platform i struktur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] umożliwia aplikacji ułatwień dostępu, takich jak czytniki zawartości ekranu do badania elementy interfejsu użytkownika i symulacji interakcji użytkownika z nimi z innym kodem i kody jakości (test). Aby uzyskać informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na wszystkich platformach, zobacz funkcje ułatwień dostępu.  
  
 W tym temacie opisano, jak do implementowania dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla formantu niestandardowego, który jest uruchamiany w aplikacji WPF. WPF obsługuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem drzewa obiektów automatyzacji elementów równorzędnych, które równoleżnikami drzewa elementów interfejsu użytkownika. Testowanie kodu i aplikacje, które udostępniają funkcje ułatwień dostępu, można użyć obiektów równorzędnych automatyzacji bezpośrednio (dla kodu w procesie) lub za pomocą uogólnionej interfejs dostarczony przez [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Klasy elementu równorzędnego automatyzacji  
 WPF kontroluje pomocy technicznej [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem drzewa klas elementów równorzędnych, które wynikają z <xref:System.Windows.Automation.Peers.AutomationPeer>. Zgodnie z konwencją nazw klas elementów równorzędnych zaczynają się od Nazwa klasy kontrolki i kończyć się znakiem "AutomationPeer". Na przykład <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> jest klasą elementu równorzędnego dla <xref:System.Windows.Controls.Button> kontrolować klasy. Klasy elementu równorzędnego są w przybliżeniu do [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować typów, ale są specyficzne dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów. Kod automatyzacji, który uzyskuje dostęp do aplikacji WPF przy użyciu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] interfejsu nie korzysta z elementy równorzędne automatyzacji bezpośrednio, ale kodu automatyzacji w tej samej przestrzeni procesu może bezpośrednio korzystać elementy równorzędne automatyzacji.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Klasy elementu równorzędnego wbudowanych automatyzacji  
 Elementy implementacji klasy elementu równorzędnego automatyzacji, po ich zaakceptowaniu działania interfejsu użytkownika, czy zawierają one informacje wymagane przez użytkowników aplikacji czytnika zawartości ekranu. Nie wszystkie elementy wizualne WPF ma elementy równorzędne automatyzacji. Przykłady klas, które implementują elementy równorzędne automatyzacji <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, i <xref:System.Windows.Controls.Label>. Klasy, które nie implementują elementy równorzędne automatyzacji przykłady klas, które wynikają z <xref:System.Windows.Controls.Decorator>, takich jak <xref:System.Windows.Controls.Border>i klas na podstawie <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.Canvas>.  
  
 Podstawa <xref:System.Windows.Controls.Control> klasa nie ma odpowiedniej klasy elementu równorzędnego. Jeśli potrzebujesz odpowiadają kontrolkę niestandardową, która pochodzi z klasy elementu równorzędnego <xref:System.Windows.Controls.Control>, powinien pochodzić klasy równorzędnej niestandardowej z <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Zagadnienia dotyczące zabezpieczeń dla elementów równorzędnych pochodne  
 Elementy równorzędne automatyzacji należy uruchomić w środowisku częściowego zaufania. Kod w zestawie UIAutomationClient nie jest skonfigurowany do uruchamiania w środowisku częściowego zaufania, a kod elementu równorzędnego automatyzacji nie powinny odwoływać się tego zestawu. Zamiast tego należy użyć klasy w zestawie UIAutomationTypes. Na przykład, należy użyć <xref:System.Windows.Automation.AutomationElementIdentifiers> klasy z zestawu UIAutomationTypes, która odnosi się do <xref:System.Windows.Automation.AutomationElement> klasy w zestawie UIAutomationClient. Jest bezpieczne odwołać się do zestawu UIAutomationTypes w kodzie równorzędnej automatyzacji.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Nawigacji elementu równorzędnego  
 Po zlokalizowaniu partnera usługi automation, kod w trakcie przejść drzewa elementów równorzędnych przez wywołanie obiektu <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> metody. Nawigacja wśród [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów wewnątrz kontrolki jest obsługiwana przez implementację równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> metody. System automatyzacji interfejsu użytkownika wywołuje tę metodę w celu zbudowania drzewa podelementy zawartych w kontroli. na przykład elementy listy w polu listy. Wartość domyślna <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> metoda przechodzi przez wizualnego drzewa elementów do tworzenia drzewa elementy równorzędne automatyzacji. Kontrolki niestandardowe przesłonić tę metodę, aby uwidocznić elementy podrzędne dla klientów automatyzacji, zwracając elementy równorzędne automatyzacji elementów, które przekazują informacje lub zezwalają na interakcję użytkownika.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Dostosowania w pochodnej elementu równorzędnego  
 Wszystkie klasy, które wynikają z <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> zawierają metody wirtualnej chronionej <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. Wywołania WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> można pobrać obiektu równorzędnego automatyzacji dla każdego formantu. Kod automatyzacji można użyć elementu równorzędnego, aby uzyskać informacje na temat funkcji i właściwości kontrolki i do interakcyjnej symulacji. Przesłonięcie kontrolek niestandardowych, które obsługuje automatyzację <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> i zwrócić wystąpienia klasy, która pochodzi od klasy <xref:System.Windows.Automation.Peers.AutomationPeer>. Na przykład, jeśli formant niestandardowy jest pochodną <xref:System.Windows.Controls.Primitives.ButtonBase> klasy, a następnie obiektu zwróconego przez <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> powinien pochodzić od <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Podczas implementowania formant niestandardowy, konieczne jest przesłonięcie metody "Podstawowy" z klasy elementu równorzędnego podstawowej usługi automation, które opisują zachowanie unikatowe i specyficzne dla formantu niestandardowego.  
  
### <a name="override-oncreateautomationpeer"></a>Zastąp OnCreateAutomationPeer  
 Zastąp <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> metodę niestandardową kontrolkę tak że zwraca obiekt dostawcy, która musi dziedziczyć pośrednio lub bezpośrednio <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Zastąp GetPattern  
 Elementy równorzędne automatyzacji, Uprość niektóre aspekty wdrażania po stronie serwera [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy, ale elementy równorzędne automatyzacji formantu niestandardowego muszą nadal obsługiwać interfejsy wzorca. Takich jak WPF innych dostawców, elementami równorzędnymi Obsługa wzorców kontrolek, dostarczając implementacje interfejsów w <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> przestrzeni nazw, takich jak <xref:System.Windows.Automation.Provider.IInvokeProvider>. Interfejsy wzorzec kontroli może być implementowany przez węzeł równorzędny, samego lub innego obiektu. Implementacja elementu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> zwraca obiekt, który obsługuje określony wzorzec. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kod wywołuje metodę <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metody i określa <xref:System.Windows.Automation.Peers.PatternInterface> wartość wyliczenia. Zastąpienie metody <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> powinna zwracać obiekt, który implementuje określony wzorzec. Jeśli formant nie ma niestandardową implementację wzorca, można wywołać implementację typu podstawowego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> można pobrać jego implementacja lub wartość null, jeśli wzorzec nie jest obsługiwana dla tego typu kontrolki. Na przykład niestandardowy formant NumericUpDown, można ustawić wartość należącą do zakresu, dzięki czemu jego [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] zaimplementować elementu równorzędnego <xref:System.Windows.Automation.Provider.IRangeValueProvider> interfejsu. W poniższym przykładzie przedstawiono sposób równorzędnego <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metoda zostanie przesłonięta odpowiedzieć na <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> wartość.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metodę można również określić podelementem jako dostawca wzorca. Poniższy kod przedstawia sposób <xref:System.Windows.Controls.ItemsControl> transfery przewiń wzorca obsługi na węźle równorzędnym jego wewnętrznych <xref:System.Windows.Controls.ScrollViewer> kontroli.  
  
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
  
 Aby określić podelement obsługi wzorzec, ten kod pobiera obiekt podelement, tworzy elementu równorzędnego przy użyciu <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> metody ustawia <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> właściwości nowego elementu równorzędnego dla bieżącego elementu równorzędnego i zwraca nowy element równorzędny. Ustawienie <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> na podelementem uniemożliwia element podrzędny znajdujących się w drzewie elementów równorzędnych usługi automation i wszystkie zdarzenia wygenerowane przez element podrzędny określa jako pochodzący z kontrolą określonych w <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> Formant nie jest wyświetlany w drzewie automatyzacji i przewijania zdarzenia, które generuje wyglądają, jakby pochodziły z <xref:System.Windows.Controls.ItemsControl> obiektu.  
  
### <a name="override-core-methods"></a>Przesłaniaj metody "Podstawowy"  
 Kod automatyzacji pobiera informacje o kontroli nad przez wywołanie metody publiczne klas elementów równorzędnych. Aby podać informacje o kontroli nad, Zastąp każdą metodę, której nazwa kończy się ciągiem "Podstawowy" podczas implementacji kontroli różni się od podanym przez klasę automatyzacji podstawowego elementu równorzędnego. Jako minimum, należy zaimplementować kontroli nad <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> metody, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Implementacja <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> opisuje Twoją kontrolą, zwracając <xref:System.Windows.Automation.ControlType> wartość. Mimo że może zwrócić <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, powinna zwrócić jeden z typów kontroli dokładniejsze Jeśli dokładnie opisuje Twoją kontrolą. Zwracana wartość wynosząca <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> wymaga dodatkowej pracy dla dostawcy zaimplementować [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], i [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produkty klienckie nie są w stanie przewidzieć struktura kontrolki interakcji klawiatury i wzorców kontrolek możliwe.  
  
 Implementowanie <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metod, aby określić, czy kontroli nad zawartością danych lub spełnia interaktywne roli w interfejsie użytkownika (lub obie). Domyślnie, obie metody zwracają `true`. Te ustawienia zwiększyć użyteczność narzędzi automatyzacji, takich jak czytniki zawartości ekranu, których może używać tych metod w celu filtrowania drzewa automatyzacji. Jeśli Twoje <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> wzorzec transfery metody obsługi element podrzędny elementu równorzędnego, element podrzędny elementu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metoda może zwracać wartość false, aby ukryć element podrzędny elementu równorzędnego z drzewa automatyzacji. Na przykład przewijanie w <xref:System.Windows.Controls.ListBox> jest obsługiwany przez <xref:System.Windows.Controls.ScrollViewer>i węzłem równorzędnym automatyzacji dla <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> jest zwracany przez <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metody <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> skojarzony z <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. W związku z tym <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metody <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> zwraca `false`, dzięki czemu <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> nie jest wyświetlana w drzewie usługi automation.  
  
 Sieci równorzędnej automatyzacji podać wartości domyślne odpowiednie dla kontrolki. Należy pamiętać, XAML, który odwołuje się do kontrolki można zastąpić swoje implementacji elementu równorzędnego z podstawowych metod umieszczając <xref:System.Windows.Automation.AutomationProperties> atrybutów. Na przykład następujące XAML tworzy przycisk, który ma dwa dostosowane [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementacja wzorca dostawców  
 Interfejsy implementowane przez niestandardowego dostawcy są jawnie zadeklarowane, jeśli element będący właścicielem pochodzi bezpośrednio z <xref:System.Windows.Controls.Control>. Na przykład, poniższy kod deklaruje elementu równorzędnego dla <xref:System.Windows.Controls.Control> , który zawiera wartość zakresu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Jeśli kontrolka będąca właścicielem pochodzi z określonego typu formantu, takie jak <xref:System.Windows.Controls.Primitives.RangeBase>, element równorzędny mogą pochodzić z klasy równoważnych pochodna elementów równorzędnych. W tym przypadku będzie dziedziczyć elementu równorzędnego <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, która dostarcza implementację podstawową <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Poniższy kod przedstawia deklaracji elementu równorzędnego.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Aby przykładem implementacji, zobacz [NumericUpDown kontrolkę niestandardową przy użyciu przykładowych Obsługa automatyzacji interfejsu użytkownika i motyw](https://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Wywoływanie zdarzeń  
 Klienci automatyzacji można subskrybowanie zdarzeń automatyzacji. Niestandardowe formanty, należy zgłosić zmiany do kontrolowania stanu przez wywołanie metody <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> metody. Podobnie po zmianie wartości właściwości, wywołaj <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> metody. Poniższy kod przedstawia sposób pobierania obiektu równorzędnego z kodem kontroli i wywołać metodę, aby wywołać zdarzenie. Optymalizacji kod określa, czy wszystkie obiekty nasłuchujące dla tego typu zdarzenia. Wywoływanie zdarzeń tylko wtedy, gdy istnieją odbiorników pozwala uniknąć niepotrzebnych nakładów pracy i ułatwia kontrolowanie, czas reakcji.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika](../../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Formant NumericUpDown niestandardowe z motywu i przykładowe Obsługa automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=160025)  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
