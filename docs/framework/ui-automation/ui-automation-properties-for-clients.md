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
ms.openlocfilehash: 3ef1e7c6e21f30c5bdea096003f192c38059ab2e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441364"
---
# <a name="ui-automation-properties-for-clients"></a>Właściwości automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym omówieniu przedstawiono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, które są widoczne dla aplikacji klienckich automatyzacji interfejsu użytkownika.  
  
 Właściwości obiektów <xref:System.Windows.Automation.AutomationElement> zawierają informacje dotyczące [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów, zazwyczaj kontrolek. Właściwości <xref:System.Windows.Automation.AutomationElement> są ogólne; to nie jest specyficzne dla typu formantu. Wiele z tych właściwości jest dostępnych w strukturze <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation>.  
  
 Wzorce formantów mają również właściwości. Właściwości wzorców kontrolek są specyficzne dla wzorca. Na przykład <xref:System.Windows.Automation.ScrollPattern> ma właściwości, które umożliwiają aplikacji klienckiej wykrywanie, czy okno jest przewijane w poziomie, czy w pionie, a także aktualne rozmiary widoku i położenia przewijania. Wzorce formantów uwidaczniają wszystkie właściwości za pomocą struktury; na przykład <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 Właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] są tylko do odczytu. Aby ustawić właściwości kontrolki, należy użyć metod odpowiedniego wzorca kontrolki. Na przykład użyj <xref:System.Windows.Automation.ScrollPattern.Scroll%2A>, aby zmienić wartości pozycji okna przewijania.  
  
 Aby zwiększyć wydajność, wartości właściwości formantów i wzorców formantów mogą być buforowane podczas pobierania obiektów <xref:System.Windows.Automation.AutomationElement>. Aby uzyskać więcej informacji, zobacz [buforowanie w klientach automatyzacji interfejsu użytkownika](caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>Identyfikatory właściwości  
 Identyfikatory właściwości (identyfikatory) są unikatowe, stałe wartości, które są hermetyzowane w obiektach <xref:System.Windows.Automation.AutomationProperty>. Aplikacje klienckie automatyzacji interfejsu użytkownika uzyskują te identyfikatory z klasy <xref:System.Windows.Automation.AutomationElement> lub z odpowiedniej klasy wzorca kontroli, takiej jak <xref:System.Windows.Automation.ScrollPattern>. Dostawcy automatyzacji interfejsu użytkownika pobierają je z <xref:System.Windows.Automation.AutomationElementIdentifiers> lub z jednej z klas identyfikatorów wzorca kontroli, takich jak <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> liczbowa <xref:System.Windows.Automation.AutomationProperty> jest używana przez dostawców do identyfikowania właściwości, które są badane w metodzie <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType>. Ogólnie rzecz biorąc aplikacje klienckie nie muszą przeanalizować <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> jest używany tylko do celów debugowania i diagnostyki.  
  
## <a name="property-conditions"></a>Warunki właściwości  
 Identyfikatory właściwości są używane w konstruowaniu <xref:System.Windows.Automation.PropertyCondition> obiektów używanych do znajdowania obiektów <xref:System.Windows.Automation.AutomationElement>. Na przykład możesz chcieć znaleźć <xref:System.Windows.Automation.AutomationElement>, który ma określoną nazwę, lub wszystkie kontrolki, które są włączone. Każda <xref:System.Windows.Automation.PropertyCondition> określa identyfikator <xref:System.Windows.Automation.AutomationProperty> i wartość, która musi być zgodna z właściwością.  
  
 Aby uzyskać więcej informacji, zobacz następujące tematy dotyczące odwołań:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Pobieranie właściwości  
 Niektóre właściwości <xref:System.Windows.Automation.AutomationElement> i wszystkie właściwości klasy wzorca kontrolki są uwidaczniane jako właściwości zagnieżdżone właściwości `Current` lub `Cached` obiektu wzorca <xref:System.Windows.Automation.AutomationElement> lub formantu.  
  
 Ponadto wszelkie <xref:System.Windows.Automation.AutomationElement> lub właściwości wzorca kontrolki, w tym właściwość, która nie jest dostępna w strukturze <xref:System.Windows.Automation.AutomationElement.Cached%2A> lub <xref:System.Windows.Automation.AutomationElement.Current%2A>, można pobrać przy użyciu jednej z następujących metod:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Te metody oferują nieco lepszą wydajność, a także dostęp do pełnego zakresu właściwości.  
  
 Poniższy przykład kodu przedstawia dwa sposoby pobierania właściwości na <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Aby można było pobrać właściwości wzorców formantów obsługiwanych przez <xref:System.Windows.Automation.AutomationElement>, nie trzeba pobierać obiektu wzorca kontrolki. Po prostu Przekaż jeden z identyfikatorów właściwości wzorca do metody.  
  
 Poniższy przykład kodu przedstawia dwa sposoby pobierania właściwości we wzorcu kontrolki.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 Metody `Get` zwracają <xref:System.Object>. Aplikacja musi rzutować zwracany obiekt na właściwy typ przed użyciem wartości.  
  
## <a name="default-property-values"></a>Domyślne wartości właściwości  
 Jeśli dostawca automatyzacji interfejsu użytkownika nie implementuje właściwości, system [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] może podać wartość domyślną. Na przykład jeśli dostawca kontrolki nie obsługuje właściwości identyfikowanej przez <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zwraca pusty ciąg. Analogicznie, jeśli dostawca nie obsługuje właściwości identyfikowanej przez <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zwraca `false`.  
  
 To zachowanie można zmienić, korzystając z przeciążeń metody <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType>. Jeśli określisz `true` jako drugi parametr, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie zwróci wartości domyślnej, ale zamiast tego zwraca wartość specjalną <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Poniższy przykładowy kod próbuje pobrać właściwość z elementu, a jeśli właściwość nie jest obsługiwana, używana jest wartość zdefiniowana przez aplikację.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Aby poznać, jakie właściwości są obsługiwane przez element, użyj <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Zwraca tablicę identyfikatorów <xref:System.Windows.Automation.AutomationProperty>.  
  
## <a name="property-changed-events"></a>Zdarzenia ze zmienionymi właściwościami  
 Gdy wartość właściwości w <xref:System.Windows.Automation.AutomationElement> lub wzorzec kontrolki zmienia się, zostanie zgłoszone zdarzenie. Aplikacja może subskrybować takie zdarzenia, wywołując <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, dostarczając tablicę identyfikatorów <xref:System.Windows.Automation.AutomationProperty> jako ostatni parametr, aby określić właściwości zainteresowania.  
  
 W <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>można zidentyfikować właściwość, która została zmieniona przez sprawdzenie, czy <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> Członkowskie argumenty zdarzenia. Argumenty zawierają również stare i nowe wartości właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które uległy zmianie. Te wartości są typu <xref:System.Object> i muszą być rzutowane na poprawny typ przed użyciem.  
  
## <a name="additional-automationelement-properties"></a>Dodatkowe właściwości usługi AutomationElement  
 Oprócz struktur właściwości <xref:System.Windows.Automation.AutomationElement.Current%2A> i <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement> ma następujące właściwości, które są pobierane za pomocą prostych metod dostępu do właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekcja obiektów podrzędnych <xref:System.Windows.Automation.AutomationElement>, które znajdują się w pamięci podręcznej.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement> obiekt nadrzędny, który znajduje się w pamięci podręcznej.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Właściwość statyczna) <xref:System.Windows.Automation.AutomationElement>, który ma fokus wprowadzania.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Właściwość statyczna) Główny <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](caching-in-ui-automation-clients.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
- [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md)
