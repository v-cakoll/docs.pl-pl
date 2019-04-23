---
title: Buforowanie w klientach automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 4c403fa6f0de34e970eb0c74df13d807e92f8a05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175828"
---
# <a name="caching-in-ui-automation-clients"></a>Buforowanie w klientach automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono buforowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorców właściwości i kontroli.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], pamięć podręczna oznacza, że wstępnego pobierania danych. Następnie są dostępne dane bez dalszej komunikacji między procesami. Buforowanie zazwyczaj służy przez aplikacje klienckie automatyzacji interfejsu użytkownika można pobrać właściwości i wzorców kontrolki w trybie zbiorczym. Informacje są następnie pobierane z pamięci podręcznej, zgodnie z potrzebami. Aplikacja aktualizuje pamięć podręczną okresowo, zwykle w odpowiedzi na zdarzenia oznaczający, że coś w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] został zmieniony.  
  
 Korzyści wynikające z pamięci podręcznej są najbardziej zauważalne w przypadku kontrolek Windows Presentation Foundation (WPF) i niestandardowe formanty, które mają dostawców automatyzacji interfejsu użytkownika po stronie serwera. Istnieje mniej korzyść podczas uzyskiwania dostępu do dostawców po stronie klienta, takich jak domyślnych dostawców dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki.  
  
 Buforowanie występuje, gdy aplikacja aktywuje <xref:System.Windows.Automation.CacheRequest> , a następnie używa wszelkie metody lub właściwości, która zwraca <xref:System.Windows.Automation.AutomationElement>, na przykład <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Metody <xref:System.Windows.Automation.TreeWalker> klasy są wyjątek; buforowanie tylko jest wykonywane, jeśli <xref:System.Windows.Automation.CacheRequest> jest określony jako parametr (na przykład <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Buforowanie również występuje, gdy zasubskrybujesz zdarzenia podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny. <xref:System.Windows.Automation.AutomationElement> Przekazany do obsługi zdarzenia, źródło zdarzenia zawiera właściwości pamięci podręcznej i wzorce określone, oryginalnym <xref:System.Windows.Automation.CacheRequest>. Wszelkie zmiany wprowadzone do <xref:System.Windows.Automation.CacheRequest> po zasubskrybowaniu zdarzenie nie mają wpływu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wzorców właściwości oraz kontrolki elementu mogą być buforowane.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Opcje pamięci podręcznej  
 <xref:System.Windows.Automation.CacheRequest> Określa następujące opcje do buforowania.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Właściwości do pamięci podręcznej  
 Można określić właściwości do pamięci podręcznej, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> dla każdej właściwości przed aktywowaniem żądania.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Wzorce kontrolki do pamięci podręcznej  
 Wzorce kontrolki do pamięci podręcznej można określić, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> dla każdego wzorca przed aktywowaniem żądania. Gdy wzorzec są buforowane, jego właściwości nie są automatycznie buforowane; należy określić żądane właściwości pamięci podręcznej przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Zakres i filtrowanie buforowania  
 Można określić elementy, których właściwości i wzorce, które mają być buforowane, ustawiając <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> właściwości przed aktywowaniem żądania. Zakres jest określana względem elementów, które są pobierane, gdy żądanie jest aktywne. Na przykład jeśli ustawisz tylko <xref:System.Windows.Automation.TreeScope.Children>, a następnie pobrać <xref:System.Windows.Automation.AutomationElement>, właściwości i wzorce elementy podrzędne tego elementu są buforowane, ale wyklucza te samego elementu. Aby upewnić się, że buforowanie jest wykonywane dla samego elementu pobrane, należy dołączyć <xref:System.Windows.Automation.TreeScope.Element> w <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości. Nie jest możliwe ustawić zakres <xref:System.Windows.Automation.TreeScope.Parent> lub <xref:System.Windows.Automation.TreeScope.Ancestors>. Jednak element nadrzędny mogą być buforowane podczas buforowania nie zawiera elementu podrzędnego; Zobacz Pobieranie pamięci podręcznej elementów podrzędnych i nadrzędnych, w tym temacie.  
  
 Zakres buforowania wpływa także <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> właściwości. Domyślnie, buforowanie odbywa się tylko dla elementów, które są wyświetlane w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Można jednak zmienić tę właściwość, aby zastosować buforowania, aby wszystkie elementy lub tylko do elementów, które są wyświetlane w widoku zawartości.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Siła odwołania do elementu  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement>, domyślnie mają dostęp do wszystkich właściwości i wzorce tego elementu, w tym te, które nie zostały zapisane. Jednak aby uzyskać większą wydajność można określić czy odwołanie do elementu dotyczy tylko dane w pamięci podręcznej, ustawiając <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> właściwość <xref:System.Windows.Automation.CacheRequest> do <xref:System.Windows.Automation.AutomationElementMode.None>. W tym przypadku nie masz dostępu do żadnych właściwości niebuforowanym i wzorce pobrane elementy. Oznacza to, że nie masz dostępu do żadnych właściwości, za pośrednictwem <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub `Current` właściwość <xref:System.Windows.Automation.AutomationElement> lub wszelkie wzorzec kontroli; nie można pobrać wzorca za pomocą <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Wzorce pamięci podręcznej, można wywołać metody pobierające właściwości tablicy, takich jak <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ale nie wszystkie, wykonywać akcje na kontrolki, takie jak <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Przykład aplikacji, która nie może być konieczne pełne odwołań do obiektów jest czytnika ekranu, który będzie pobrana z wyprzedzeniem <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> i <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> właściwości elementów w oknie, ale nie są wymagane <xref:System.Windows.Automation.AutomationElement> same obiekty.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Aktywowanie klasy CacheRequest  
 Buforowanie jest wykonywane tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElement> obiekty są pobierane podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny dla bieżącego wątku. Istnieją dwa sposoby aktywacji <xref:System.Windows.Automation.CacheRequest>.  
  
 Zwykle jest wywołanie <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Ta metoda zwraca obiekt, który implementuje <xref:System.IDisposable>. Żądanie pozostaje aktywne tak długo, jak <xref:System.IDisposable> obiekt istnieje. Najprostszym sposobem, aby kontrolować okres istnienia obiektu jest ujęcie wywołania w ramach `using` (C#) lub `Using` bloku (Visual Basic). Daje to gwarancję, że żądanie będzie zostać zdjęte ze stosu ze stosu nawet wtedy, gdy wyjątek jest zgłaszany.  
  
 Inny sposób, co jest przydatne, gdy chcesz zagnieździć żądań pamięci podręcznej, jest wywołanie <xref:System.Windows.Automation.CacheRequest.Push%2A>. Umieszcza żądanie ze stosu i aktywuje go. Żądanie pozostaje aktywne, dopóki zostanie usunięta ze stosu przez <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Żądanie staje się tymczasowo nieaktywny, jeśli kolejne żądanie są wypychane na stosie; żądanie najważniejsze na stosie jest aktywny.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Trwa pobieranie pamięci podręcznej właściwości  
 Właściwości pamięci podręcznej elementu można pobrać za pomocą następujących metod i właściwości.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Wyjątek jest zgłaszany, jeśli Żądana właściwość nie znajduje się w pamięci podręcznej.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, takich jak <xref:System.Windows.Automation.AutomationElement.Current%2A>, udostępnia poszczególne właściwości jako elementy członkowskie struktury. Jednakże nie trzeba pobrać tę strukturę; można uzyskać dostęp do poszczególnych właściwości bezpośrednio. Na przykład <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> właściwości, które można otrzymać od `element.Cached.Name`, gdzie `element` jest <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Trwa pobieranie pamięci podręcznej wzorce kontrolki  
 Wzorce kontroli pamięci podręcznej elementu można pobrać za pomocą następujących metod.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Jeśli wzorzec nie znajduje się w pamięci podręcznej, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> zgłasza wyjątek, i <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> zwraca `false`.  
  
 Można pobrać właściwości pamięci podręcznej — wzorzec kontrolki za pomocą `Cached` właściwości obiektu wzorca. Możesz również pobrać bieżące wartości za pomocą `Current` właściwości, ale tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElementMode.None> nie została określona podczas <xref:System.Windows.Automation.AutomationElement> została pobrana. (<xref:System.Windows.Automation.AutomationElementMode.Full> jest wartością domyślną, a to pozwala na dostęp do bieżących wartości.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Trwa pobieranie pamięci podręcznej elementy podrzędne i elementy nadrzędne  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement> i buforowania na obiekty podrzędne danego elementu za pomocą żądania <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości żądania, jest odwoływanie można pobrać elementu podrzędnego elementy z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> właściwość elementu można pobrać.  
  
 Jeśli <xref:System.Windows.Automation.TreeScope.Element> został uwzględniony w zakresie żądanie pamięci podręcznej, element główny żądania jest następnie dostępne <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> właściwości elementów podrzędnych.  
  
> [!NOTE]
>  Nie można buforować rodziców lub elementów nadrzędnych elementu głównego żądania.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Aktualizowanie pamięci podręcznej  
 Pamięć podręczna jest prawidłowy tylko tak długo, jak nic się nie zmienia w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Aplikacja jest odpowiedzialny za aktualizowanie pamięci podręcznej, zwykle w odpowiedzi na zdarzenia.  
  
 Jeśli zasubskrybujesz zdarzenia podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskaniu <xref:System.Windows.Automation.AutomationElement> przy użyciu zaktualizowanych pamięci podręcznej jako źródło zdarzenia w każdym przypadku, gdy jest wywoływana w swoim delegacie programu obsługi zdarzeń. Możesz także zaktualizować buforowanych informacji dla elementu, wywołując <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Można przekazać w oryginalnym <xref:System.Windows.Automation.CacheRequest> Aby zaktualizować wszystkie informacje, który wcześniej był buforowany.  
  
 Aktualizowanie pamięci podręcznej nie zmienia żadnych istniejących właściwości <xref:System.Windows.Automation.AutomationElement> odwołania.  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Przykładowe FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
