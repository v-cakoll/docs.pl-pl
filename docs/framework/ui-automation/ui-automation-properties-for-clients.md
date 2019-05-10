---
title: Właściwości automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
ms.openlocfilehash: 5fe988ab94584f79bf3a27257e521ee3a11babc5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624268"
---
# <a name="ui-automation-properties-for-clients"></a>Właściwości automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu przedstawiono podstawowe informacje dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, ponieważ są one udostępniane aplikacjom klienckim automatyzacji interfejsu użytkownika.  
  
 Właściwości <xref:System.Windows.Automation.AutomationElement> obiekty zawierają informacje dotyczące [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów, zwykle kontrolki. Właściwości <xref:System.Windows.Automation.AutomationElement> są ogólny; będącego, nie odnoszą się do typu formantu. Wiele z tych właściwości są widoczne w <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> struktury.  
  
 Wzorce kontrolki mają również właściwości. Właściwości wzorce kontrolki są specyficzne dla wzorca. Na przykład <xref:System.Windows.Automation.ScrollPattern> ma właściwości, które umożliwiają aplikacji klienckiej dowiedzieć się, czy okno jest w pionie lub poziomie przewijany i jakie bieżący widok rozmiary i położenie przewijania. Wzorce kontrolki udostępnianie ich właściwości przez strukturę; na przykład <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości są tylko do odczytu. Aby ustawić właściwości formantu, należy użyć metody wzorca właściwej opcji kontroli. Na przykład użyć <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> w celu zmiany wartości położenie okna przewijania.  
  
 Aby poprawić wydajność, wartości właściwości kontrolek i wzorce kontrolki mogą być buforowane podczas <xref:System.Windows.Automation.AutomationElement> pobierane są obiekty. Aby uzyskać więcej informacji, zobacz [buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
<a name="Property_IDs"></a>   
## <a name="property-ids"></a>Identyfikatory właściwości  
 Właściwość [!INCLUDE[TLA#tla_id#plural](../../../includes/tlasharptla-idsharpplural-md.md)] są unikatowe, stałe wartości, które są hermetyzowane w <xref:System.Windows.Automation.AutomationProperty> obiektów. Aplikacje klienckie automatyzacji interfejsu użytkownika, Pobierz te [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] z <xref:System.Windows.Automation.AutomationElement> klasy lub z odpowiedniej kontroli klasy wzorca, takich jak <xref:System.Windows.Automation.ScrollPattern>. Dostawcy automatyzacji interfejsu użytkownika, Uzyskaj je z <xref:System.Windows.Automation.AutomationElementIdentifiers> lub z jednego formantu do wzorca identyfikatory klas, takich jak <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Wartość numeryczna <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> z <xref:System.Windows.Automation.AutomationProperty> jest używana przez dostawców w celu zidentyfikowania właściwości, które są odpytywane dla w <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> metody. Ogólnie rzecz biorąc, aplikacji klienckich nie trzeba sprawdzić <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> Służy tylko do celów debugowania i diagnostyki.  
  
<a name="Property_Conditions"></a>   
## <a name="property-conditions"></a>Warunków właściwości  
 Właściwość [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] są używane podczas tworzenia <xref:System.Windows.Automation.PropertyCondition> używana do znajdowania obiektów <xref:System.Windows.Automation.AutomationElement> obiektów. Na przykład użytkownik może chcieć znaleźć <xref:System.Windows.Automation.AutomationElement> nazwę niektórych lub wszystkich kontrolek, które są włączone. Każdy <xref:System.Windows.Automation.PropertyCondition> Określa <xref:System.Windows.Automation.AutomationProperty> identyfikatora i wartość właściwości muszą być zgodne.  
  
 Aby uzyskać więcej informacji zobacz następujące tematy odniesienia:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
<a name="Retrieving_Properties"></a>   
## <a name="retrieving-properties"></a>Pobieranie właściwości  
 Niektóre właściwości <xref:System.Windows.Automation.AutomationElement> i wszystkie właściwości klasy wzorca kontrolki są widoczne jako właściwości zagnieżdżone `Current` lub `Cached` właściwość <xref:System.Windows.Automation.AutomationElement> lub obiekt wzorzec formantu.  
  
 Ponadto wszelkie <xref:System.Windows.Automation.AutomationElement> lub kontroli właściwości wzorzec, łącznie z właściwością, która nie jest dostępna w <xref:System.Windows.Automation.AutomationElement.Cached%2A> lub <xref:System.Windows.Automation.AutomationElement.Current%2A> struktury, można pobrać przy użyciu jednej z następujących metod:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Te metody oferują nieznacznie wyższa wydajność, a także dostęp do pełnego zakresu właściwości.  
  
 Poniższy przykład kodu pokazuje dwa sposoby pobierania właściwości na <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Można pobrać właściwości wzorców kontrolek obsługiwanych przez <xref:System.Windows.Automation.AutomationElement>, nie trzeba pobrać obiekt wzorzec formantu. Po prostu przekazać jeden z identyfikatorów właściwości wzorca do metody.  
  
 Poniższy przykład kodu pokazuje dwa sposoby pobierania właściwości przy użyciu wzorca kontrolki.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Metody zwracają <xref:System.Object>. Aplikację należy zrzutować zwracany obiekt na właściwy typ. przed rozpoczęciem korzystania z wartości.  
  
<a name="_Default_Property_Values"></a>   
## <a name="default-property-values"></a>Domyślne wartości właściwości  
 Jeśli dostawcy automatyzacji interfejsu użytkownika nie implementuje właściwość [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] system jest w stanie dostarczyć wartość domyślną. Na przykład, jeśli dostawca dla formantu nie obsługuje właściwości identyfikowane przez <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zwraca pusty ciąg. Podobnie jeśli dostawca nie obsługuje właściwości identyfikowane przez <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zwraca `false`.  
  
 To zachowanie można zmienić za pomocą <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> przeciążenia metody. Po określeniu `true` jako drugi parametr [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie zwraca wartości domyślne, ale zamiast tego zwraca specjalna wartość <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Poniższy przykład kodu próbuje pobrać właściwość z elementu, a jeśli właściwość nie jest obsługiwany, zdefiniowanych przez aplikację zamian jest używana wartość.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Aby dowiedzieć się, jakie właściwości są obsługiwane przez element, należy użyć <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. To zwraca tablicę <xref:System.Windows.Automation.AutomationProperty> identyfikatorów.  
  
<a name="Property_changed_Events"></a>   
## <a name="property-changed-events"></a>Zdarzenia zmiany właściwości  
 Gdy wartość właściwości na <xref:System.Windows.Automation.AutomationElement> lub zmiany wzorca formantów, zdarzenie jest wywoływane. Aplikacja może subskrybować takie zdarzenia przez wywołanie metody <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, dostarczenie tablicę <xref:System.Windows.Automation.AutomationProperty> identyfikatorów jako ostatni parametr, aby określić właściwości zainteresowania.  
  
 W <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, można zidentyfikować właściwości, które uległy zmianie, sprawdzając <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> członkiem argumenty zdarzeń. Argumenty również zawierają stare i nowe wartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, które uległy zmianie. Te wartości są typu <xref:System.Object> i należy zrzutować do poprawnego typu przed ich użyciem.  
  
<a name="Additional_AutomationElement_Properties"></a>   
## <a name="additional-automationelement-properties"></a>Właściwości obiektu AutomationElement dodatkowe  
 Oprócz <xref:System.Windows.Automation.AutomationElement.Current%2A> i <xref:System.Windows.Automation.AutomationElement.Cached%2A> struktury właściwość <xref:System.Windows.Automation.AutomationElement> ma następujące właściwości, które są pobierane w drodze prostą właściwość metody dostępu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekcja podrzędnych <xref:System.Windows.Automation.AutomationElement> obiekty, które znajdują się w pamięci podręcznej.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement> Obiektu nadrzędnego, który znajduje się w pamięci podręcznej.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Właściwość statyczna) <xref:System.Windows.Automation.AutomationElement> , Który ma fokus wprowadzania.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Właściwość statyczna) Katalog główny <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
