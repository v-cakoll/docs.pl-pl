---
title: Wzorce formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: f62631a15dd348b6f6ea27a82d7b45aab92ceed2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179950"
---
# <a name="ui-automation-control-patterns-overview"></a>Wzorce formantów automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przeglądzie wprowadzono wzorce kontroli. Wzorce kontroli umożliwiają kategoryzowanie i udostępnianie funkcji formantu niezależnie od typu formantu lub wyglądu formantu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]używa wzorców kontroli do reprezentowania typowych zachowań kontroli. Na przykład używasz invoke wzorzec formantu dla formantów, które mogą być wywoływane (takie jak przyciski) i wzorzec kontroli przewijania dla formantów, które mają paski przewijania (takie jak pola listy, widoki listy lub pola kombi). Ponieważ każdy wzorzec formantu reprezentuje oddzielne funkcje, można je połączyć, aby opisać pełny zestaw funkcji obsługiwanych przez określony formant.  
  
> [!NOTE]
> Agreguj formanty — [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] zbudowane za pomocą formantów podrzędnych, które zapewniają funkcje udostępniane przez rodzica — powinny implementować wszystkie wzorce kontroli zwykle skojarzone z każdym formantem podrzędnym. Z kolei te same wzorce kontroli nie muszą być implementowane przez formanty podrzędne.  
  
<a name="uiautomation_control_pattern_includes"></a>
## <a name="ui-automation-control-pattern-components"></a>Składniki wzorca automatyzacji interfejsu użytkownika  
 Wzorce kontroli obsługują metody, właściwości, zdarzenia i relacje potrzebne do zdefiniowania dyskretnego elementu funkcjonalności dostępnego w formancie.  
  
- Relacja między elementem automatyzacji interfejsu użytkownika i jego element nadrzędny, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy podrzędne i rodzeństwo opisuje strukturę elementu w drzewie.  
  
- Metody umożliwiają klientom automatyzacji interfejsu użytkownika manipulowanie formantem.  
  
- Właściwości i zdarzenia zawierają informacje o funkcji wzorca formantu, a także informacje o stanie formantu.  
  
 Wzorce sterowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] odnoszą się do interfejsów odnoszą się do modelu obiektu komponentu (COM) obiektów. W programie COM można zbadać obiekt, aby zapytać, jakie interfejsy obsługuje, a następnie użyć tych interfejsów, aby uzyskać dostęp do funkcji. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]automatyzacji interfejsu użytkownika klienci mogą poprosić formant, który kontroluje wzorce, które obsługuje, a następnie wchodzić w interakcje z formantem za pośrednictwem właściwości, metod, zdarzeń i struktur udostępniane przez obsługiwane wzorce kontroli. Na przykład dla pola edycji wielowierszowej <xref:System.Windows.Automation.Provider.IScrollProvider>dostawcy automatyzacji interfejsu użytkownika implementują . Gdy klient wie, <xref:System.Windows.Automation.AutomationElement> że <xref:System.Windows.Automation.ScrollPattern> obsługuje wzorzec formantu, można użyć właściwości, metody i zdarzenia udostępniane przez ten wzorzec formantu do manipulowania formantu lub uzyskać dostęp do informacji o formancie.  
  
<a name="uiautomation_control_pattern_client_provider"></a>
## <a name="ui-automation-providers-and-clients"></a>Dostawcy automatyzacji interfejsu użytkownika i klienci  
 Dostawcy automatyzacji interfejsu użytkownika implementują wzorce kontroli, aby udostępnić odpowiednie zachowanie dla określonego elementu funkcji obsługiwanych przez formant.  
  
 Automatyzacja interfejsu użytkownika klienci dostęp [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do metod i właściwości klas [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]wzorców kontroli i [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]używać ich do uzyskania informacji o , lub manipulować . Te klasy wzorców kontroli <xref:System.Windows.Automation> znajdują się w <xref:System.Windows.Automation.InvokePattern> obszarze <xref:System.Windows.Automation.SelectionPattern>nazw (na przykład i ).  
  
 Klienci <xref:System.Windows.Automation.AutomationElement> używają metod <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> (takich jak lub <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) lub akcesorów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] środowiska wykonawczego języka wspólnego (CLR), aby uzyskać dostęp do właściwości wzorca. Każda klasa wzorca formantu ma <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>element pola (na przykład lub ), który <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> identyfikuje <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ten wzorzec <xref:System.Windows.Automation.AutomationElement>formantu i może być przekazywany jako parametr do lub do pobrania tego wzorca dla .  
  
<a name="uiautomation_control_patterns_dynamic"></a>
## <a name="dynamic-control-patterns"></a>Dynamiczne wzorce sterowania  
 Niektóre formanty nie zawsze obsługują ten sam zestaw wzorców kontroli. Wzorce kontroli są uważane za obsługiwane, gdy są dostępne dla klienta automatyzacji interfejsu użytkownika. Na przykład wielowierszowe pole edycji umożliwia przewijanie w pionie tylko wtedy, gdy zawiera więcej wierszy tekstu niż może być wyświetlanych w widocznym obszarze. Przewijanie jest wyłączone po usunięciu wystarczającej ilości tekstu, aby przewijanie nie było już wymagane. W tym przykładzie wzorzec formantu ScrollPattern jest dynamicznie obsługiwany w zależności od bieżącego stanu formantu (ile tekstu jest w polu edycji).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>
## <a name="control-pattern-classes-and-interfaces"></a>Klasy wzorca sterowania i interfejsy  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli opisano wzorce kontroli. W tabeli wymieniono również klasy używane przez klientów automatyzacji interfejsu użytkownika w celu uzyskania dostępu do wzorców kontroli, a także interfejsy używane przez dostawców automatyzacji interfejsu użytkownika do ich zaimplementowania.  
  
|Klasa wzorca sterowania|Interfejs dostawcy|Opis|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Służy do formantów, które mogą być zadokowane w kontenerze dokowania. Na przykład paski narzędzi lub palety narzędzi.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Służy do formantów, które mogą być rozwinięte lub zwinięte. Na przykład elementy menu w aplikacji, takie jak **menu Plik.**|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Używane dla formantów obsługujących funkcje siatki, takie jak zmiana rozmiaru i przenoszenie do określonej komórki. Na przykład duży widok ikony w Eksploratorze Windows lub proste tabele bez nagłówków w programie Microsoft Word.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Służy do formantów, które mają komórki w siatce. Poszczególne komórki powinny obsługiwać wzorzec GridItem. Na przykład każda komórka w widoku szczegółów Eksploratora Microsoft Windows.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Używane dla formantów, które mogą być wywoływane, takie jak przycisk.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Służy do formantów, które mogą przełączać się między wieloma reprezentacjami tego samego zestawu informacji, danych lub elementów podrzędnych. Na przykład formant widoku listy, w którym dane są dostępne w widokach miniatur, kafelek, ikon, listy lub szczegółów.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Używane dla formantów, które mają zakres wartości, które mogą być stosowane do formantu. Na przykład formant pokrętła zawierający lata może mieć zakres od 1900 do 2010, podczas gdy inny formant pokrętła prezentujący miesiące będzie miał zakres od 1 do 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Służy do formantów, które można przewijać. Na przykład formant, który ma paski przewijania, które są aktywne, gdy istnieje więcej informacji niż można wyświetlić w widocznym obszarze formantu.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Używane dla formantów, które mają poszczególne elementy na liście, która jest przewijana. Na przykład formant listy, który ma poszczególne elementy na liście przewijania, takich jak kontrolka pola kombi.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Służy do formantów kontenera wyboru. Na przykład pola listy i pola kombi.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Używane dla poszczególnych elementów w formantach kontenera wyboru, takich jak pola listy i pola kombi.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Używane dla formantów, które mają siatkę, a także informacje nagłówka. Na przykład arkusze programu Microsoft Excel.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Używany dla elementów w tabeli.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Służy do edycji formantów i dokumentów, które ujawniają informacje tekstowe.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Służy do formantów, gdzie można przełączać stan. Na przykład pola wyboru i elementów menu wyboru.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Służy do formantów, które można zmieniać, przenosić i obracać. Typowe zastosowania wzorca formantu Przekształcania są w projektantach, formularzach, edytorach graficznych i aplikacjach do rysowania.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Umożliwia klientom uzyskanie lub ustawienie wartości formanty, które nie obsługują zakresu wartości. Na przykład selektor daty.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Udostępnia informacje specyficzne dla systemu Windows, podstawowe pojęcie do systemu operacyjnego Microsoft Windows. Przykładami formantów, które są oknami aplikacji najwyższego poziomu (Microsoft Word, Microsoft Windows Explorer itd.), oknami podrzędnymi interfejsu wielu dokumentów (MDI) i oknami dialogowymi.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
- [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md)
- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
