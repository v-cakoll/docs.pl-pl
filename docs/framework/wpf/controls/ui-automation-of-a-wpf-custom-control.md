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
ms.openlocfilehash: fbd19591c260b0ad160339b45fd762e7a87bbc74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatyzacja interfejsu użytkownika formantu niestandardowego WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] udostępnia interfejs jednej, uogólniony tego automatyzacji, którego klienci mogą używać do zbadania lub nie działać z różnych platform i struktur interfejsów użytkownika. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] umożliwia aplikacji ułatwień dostępu, takich jak czytniki poznać elementy interfejsu użytkownika i symulowanie interakcji z nimi z innego kodu i kody jakości (test). Aby uzyskać informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na wszystkich platformach, zobacz ułatwień dostępu.  
  
 W tym temacie opisano sposób implementowania dostawcy automatyzacji interfejsu użytkownika po stronie serwera dla kontrolki niestandardowej, która działa w aplikacji WPF. WPF obsługuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem drzewa obiektów równorzędnych automatyzacji równoleżnikami drzewa elementów interfejsu użytkownika. Testowanie kodu i aplikacje, które zapewniają funkcje ułatwień dostępu, można użyć obiektów równorzędnych automatyzacji bezpośrednio (dla kodu w procesie) lub za pośrednictwem uogólniony interfejs dostarczony przez [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Klasy automatyzacji elementów równorzędnych  
 Obsługa formanty WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] za pośrednictwem drzewa klas elementów równorzędnych, które pochodzą z <xref:System.Windows.Automation.Peers.AutomationPeer>. Konwencja nazwy klasy elementów równorzędnych rozpoczynać się nazwą klasy formantu i kończyć "AutomationPeer". Na przykład <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> jest klasa elementu równorzędnego dla <xref:System.Windows.Controls.Button> kontrolować klasy. Klasy elementu równorzędnego są w przybliżeniu równy [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kontrolowanie typów, ale są specyficzne dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów. Kod automatyzacji, który uzyskuje dostęp do aplikacji WPF za pośrednictwem [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] interfejs używa automatyzacji elementów równorzędnych bezpośrednio, ale kodu automatyzacji przestrzeni procesu można korzystać bezpośrednio automatyzacji elementów równorzędnych.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Klasy elementu równorzędnego automatyzacji wbudowane  
 Elementy implementuje klasy elementu równorzędnego automatyzacji po ich zaakceptowaniu działania interfejsu użytkownika, czy zawierają one informacje wymagane przez użytkowników aplikacji odczytywania zawartości ekranu. Nie wszystkie elementy wizualne WPF ma automatyzacji elementów równorzędnych. Przykłady klas implementujących automatyzacji elementów równorzędnych <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, i <xref:System.Windows.Controls.Label>. Klasy, które nie implementują automatyzacji elementów równorzędnych przykłady klas, które pochodzą z <xref:System.Windows.Controls.Decorator>, takich jak <xref:System.Windows.Controls.Border>i na podstawie klasy <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.Canvas>.  
  
 Podstawowym <xref:System.Windows.Controls.Control> klasa nie ma odpowiedniej klasy elementu równorzędnego. Jeśli potrzebujesz odpowiadają kontrolki niestandardowej, która jest pochodną klasy elementu równorzędnego <xref:System.Windows.Controls.Control>, powinien pochodzić równorzędnej niestandardowej klasy z <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Zagadnienia dotyczące zabezpieczeń dla pochodnego elementów równorzędnych  
 Elementy równorzędne automatyzacji muszą działać w środowisku częściowego zaufania. Kod w zestawie UIAutomationClient nie jest skonfigurowana do uruchamiania w środowisku częściowego zaufania, a kod elementu równorzędnego automatyzacji nie powinny odwoływać tego zestawu. Zamiast tego należy użyć klasy w zestawie UIAutomationTypes. Na przykład należy używać <xref:System.Windows.Automation.AutomationElementIdentifiers> klasy z zestawu UIAutomationTypes, która odpowiada <xref:System.Windows.Automation.AutomationElement> klasy w zestawie UIAutomationClient. Jest to bezpieczne odwoływać się do zestawu UIAutomationTypes w kodzie elementu równorzędnego automatyzacji.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Nawigacji elementu równorzędnego  
 Po zlokalizowaniu elementu równorzędnego automatyzacji, kodu w procesie można przechodzić drzewa elementów równorzędnych przez wywołanie obiektu <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> metody. Nawigacji między [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów w formancie jest obsługiwana przez implementację obiektu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> metody. Automatyzacja interfejsu użytkownika systemu wywołuje tę metodę w celu zbudowania drzewa podelementy zawartych w kontrolce; na przykład listę elementów w polu listy. Wartość domyślna <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> metody są przesyłane za pośrednictwem elementów do tworzenia drzewa automatyzacji elementów równorzędnych w drzewie wizualnym. Niestandardowe formanty przesłonić tę metodę do udostępnienia elementów podrzędnych dla klientów automatyzacji, zwracając elementów równorzędnych automatyzacji elementów, które mogą służyć do przekazywania informacji lub zezwolić na interakcję użytkownika.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Dostosowywanie w pochodnej elementu równorzędnego  
 Wszystkie klasy, które pochodzą z <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> zawierają chronione metody wirtualnej <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. Wywołania WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> można pobrać obiektu równorzędnego automatyzacji dla każdego formantu. Kodu automatyzacji można użyć elementu równorzędnego, aby uzyskać informacje dotyczące formantu cechy i funkcje i symulowanie interakcyjnej. Przesłonięcie kontrolki niestandardowej, która obsługuje automatyzacji <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> i zwrócić wystąpienia klasy, która jest pochodną <xref:System.Windows.Automation.Peers.AutomationPeer>. Na przykład, jeśli formant niestandardowy jest pochodną <xref:System.Windows.Controls.Primitives.ButtonBase> klasy, a następnie zwrócona przez obiekt <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> powinien pochodzić od <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Podczas implementowania kontrolkę niestandardową, konieczne jest przesłonięcie metody "Core" z klasy podstawowej automatyzacji elementów równorzędnych, które opisują zachowanie unikatowe i specyficzne dla formantu niestandardowego.  
  
### <a name="override-oncreateautomationpeer"></a>Zastąpienie OnCreateAutomationPeer  
 Zastąpienie <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> metodę dla kontrolki niestandardowej, którego nie zwraca obiekt dostawcy, w którym musi dziedziczyć pośrednio lub bezpośrednio <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Zastąpienie GetPattern  
 Elementy równorzędne automatyzacji uprościć niektóre aspekty implementacja po stronie serwera [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] dostawców, ale elementy równorzędne automatyzacji formantu niestandardowego nadal musi obsługiwać interfejsy wzorca. Podobnie jak dostawców innych niż WPF elementów równorzędnych Obsługa wzorców formantów zapewniając implementacje interfejsów w <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> przestrzeni nazw, takich jak <xref:System.Windows.Automation.Provider.IInvokeProvider>. Można zaimplementować interfejsów wzorzec kontroli przez węzeł równorzędny samego lub innego obiektu. Implementacja obiektu równorzędnego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> zwraca obiekt, który obsługuje określony wzorzec. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kod wywoła <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> — metoda i określa <xref:System.Windows.Automation.Peers.PatternInterface> wartości wyliczenia. Zastąpienia z <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> powinna zwracać obiekt, który implementuje określony wzorzec. Jeśli formant nie ma niestandardowych implementacji wzorca, należy wywołać implementacja typu podstawowego <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> można pobrać jej implementacja lub wartość null, jeśli wzorzec nie jest obsługiwana dla tego typu formantu. Na przykład niestandardowego formantu NumericUpDown można ustawić na wartość w zakresie, więc jego [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] może implementować elementu równorzędnego <xref:System.Windows.Automation.Provider.IRangeValueProvider> interfejsu. W poniższym przykładzie przedstawiono sposób węzła równorzędnego <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metoda zostanie przesłonięta odpowiedzieć na <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> wartość.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metody można również określić podelement jako dostawca wzorca. Poniższy kod przedstawia sposób <xref:System.Windows.Controls.ItemsControl> transferów przewiń wzorzec obsługi dla elementu równorzędnego z wewnętrznymi <xref:System.Windows.Controls.ScrollViewer> formantu.  
  
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
  
 Aby określić podelement obsługi wzorzec, ten kod pobiera obiekt podelement, tworzy elementu równorzędnego za pomocą <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> metoda, ustawia <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> właściwość nowego elementu równorzędnego dla bieżącego elementu równorzędnego i zwraca nowy element równorzędny. Ustawienie <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> na podelementem zapobiega podelement znajdujących się w drzewie elementu równorzędnego automatyzacji i wyznacza wszystkie zdarzenia wygenerowane przez element podrzędny jako pochodzący z kontrolą określonych w <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> Formant nie jest wyświetlany w drzewie automatyzacji i przewijania zdarzenia, które generuje wydają się pochodzić z <xref:System.Windows.Controls.ItemsControl> obiektu.  
  
### <a name="override-core-methods"></a>Przesłaniaj metody "Core"  
 Automatyzacja kod pobiera informacje o formantu wywoływania metod publicznych klasy elementu równorzędnego. Aby podać informacje dotyczące formantu, należy zastąpić każdej metody, której nazwa kończy się wyrazem "Core" podczas implementacji sterowania różni się od zapewnianej przez klasę podstawową automatyzacji elementów równorzędnych. Co najmniej musi implementować formantu <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> metody, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Implementacji <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> opisuje formantu zwracając <xref:System.Windows.Automation.ControlType> wartość. Mimo że można zwrócić <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, należy przywrócić jedną z bardziej szczegółowe typy formantów Jeśli opisuje on dokładnie formantu. Zwracana wartość <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> wymaga dodatkowej pracy dla dostawcy zaimplementować [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], i [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produkty klienta są do przewidzenia Struktura kontroli, klawiatury i wzorce kontrolę.  
  
 Implementowanie <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> i <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metod, aby określić, czy formantu danych zawartość lub spełnia interakcyjne roli w interfejsie użytkownika (lub obie). Domyślnie obie metody zwracają `true`. Te ustawienia zwiększają jego użyteczność automatyzacji narzędzi, takich jak czytniki ekranu, które mogą używać tych metod do filtrowania Automatyzacja drzewa. Jeśli Twoje <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> wzorzec transferów — metoda obsługi podelement węzła równorzędnego, peer podelement <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metoda może zwracać wartość false, aby ukryć element równorzędny podelement z drzewa automatyzacji. Na przykład przewijanie w <xref:System.Windows.Controls.ListBox> jest obsługiwany przez <xref:System.Windows.Controls.ScrollViewer>i węzła równorzędnego automatyzacji dla <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> zwróconego przez <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metody <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> skojarzony z <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. W związku z tym <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metody <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> zwraca `false`, dzięki czemu <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> nie pojawia się w drzewie automatyzacji.  
  
 Z elementu równorzędnego automatyzacji należy podać wartości domyślne odpowiednie dla formantu. Uwaga XAML, który odwołuje się do formantu można zastąpić z elementu równorzędnego implementacje metody podstawowej przez dołączenie <xref:System.Windows.Automation.AutomationProperties> atrybutów. Na przykład następujące XAML tworzy przycisk zawiera dwa dostosowane [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementuje wzorzec dostawców  
 Interfejsy implementowane przez niestandardowego dostawcy są jawnie deklarować, jeśli element będący właścicielem pochodzi bezpośrednio z <xref:System.Windows.Controls.Control>. Na przykład następujący kod deklaruje element równorzędny dla <xref:System.Windows.Controls.Control> , który zawiera wartość zakresu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Jeśli formant będący właścicielem pochodzi z określonego typu formantu, takich jak <xref:System.Windows.Controls.Primitives.RangeBase>, element równorzędny mogą pochodzić z klasy równoważne pochodnej elementu równorzędnego. W takim przypadku elementu równorzędnego będzie dziedziczyć <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, który udostępnia podstawową implementację <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Poniższy kod przedstawia deklarację elementu równorzędnego.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Zapoznać się z przykładem implementacji, [numericupdown — formant niestandardowy motyw i przykładowe Obsługa automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Wywoływanie zdarzeń  
 Klienci automatyzacji możliwe subskrybowanie zdarzeń automatyzacji. Niestandardowe formanty muszą zgłosić zmiany do kontrolowania stanu przez wywołanie metody <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> metody. Podobnie, gdy wartość właściwości zostanie zmieniona, wywołaj <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> metody. Poniższy kod przedstawia sposób pobierania obiektu równorzędnego z kodem kontroli i wywołać metodę, aby wywołać zdarzenie. Do optymalizacji kodu Określa, czy wszystkie obiekty nasłuchujące dla tego typu zdarzenia. Wywoływanie zdarzeń tylko wtedy, gdy istnieją odbiorników pozwala uniknąć niepotrzebnego obciążenia i ułatwia kontrolowanie pozostają reakcji.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika](../../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Formant niestandardowy NumericUpDown motywu i przykładowe Obsługa automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=160025)  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
