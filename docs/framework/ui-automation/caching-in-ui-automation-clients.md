---
title: "Buforowanie w klientach automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: be07dc3ec6aac48382fab12285ee08bcb5fe7d49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="caching-in-ui-automation-clients"></a>Buforowanie w klientach automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono buforowanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorce właściwości i kontroli.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], buforowanie oznacza pobierania danych. Dane mają dostęp bez dalszej komunikacji między procesami. Buforowanie zazwyczaj jest używany przez aplikacje klienckie automatyzacji interfejsu użytkownika można pobrać właściwości i wzorców formantu w partii. Informacje następnie są pobierane z pamięci podręcznej, zgodnie z potrzebami. Aplikacja aktualizacji pamięci podręcznej okresowo, zazwyczaj w odpowiedzi na zdarzenia oznaczający, że coś w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] została zmieniona.  
  
 Korzyści wynikające z buforowania są najbardziej zauważalne z [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] kontrolek i kontrolek niestandardowych, które mają dostawców automatyzacji interfejsu użytkownika po stronie serwera. Brak mniej korzyści podczas uzyskiwania dostępu do dostawcy po stronie klienta takich jak domyślnych dostawców dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki.  
  
 Buforowanie występuje, gdy aplikacja aktywuje <xref:System.Windows.Automation.CacheRequest> , a następnie używa dowolnej metody lub właściwości, która zwraca <xref:System.Windows.Automation.AutomationElement>, na przykład <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Metody <xref:System.Windows.Automation.TreeWalker> klasy są wyjątkiem; buforowanie jest wykonywane tylko jeśli <xref:System.Windows.Automation.CacheRequest> jest określony jako parametr (na przykład <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Buforowanie również występuje, gdy subskrybować zdarzenia podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny. <xref:System.Windows.Automation.AutomationElement> Przekazany do obsługi zdarzenia jako źródło zdarzenia zawiera właściwości pamięci podręcznej i wzorce określony przez oryginalny <xref:System.Windows.Automation.CacheRequest>. Wszelkie zmiany wprowadzone do <xref:System.Windows.Automation.CacheRequest> po zasubskrybowaniu zdarzenie nie mają żadnego skutku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwości i kontroli wzorce elementu mogą być buforowane.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Opcje do buforowania  
 <xref:System.Windows.Automation.CacheRequest> Określa następujące opcje buforowania.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Właściwości do pamięci podręcznej  
 Możesz określić właściwości do pamięci podręcznej przez wywołanie metody <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> dla każdej właściwości przed uaktywnieniem żądania.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Wzorce kontrolki do pamięci podręcznej  
 Wzorce kontrolki do pamięci podręcznej można określić przez wywołanie metody <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> dla każdego wzorca przed uaktywnieniem żądania. Jeśli wzorzec jest pamięci podręcznej, jego właściwości nie są automatycznie buforowane; należy określić właściwości mają być buforowane przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Zakres i filtrowanie buforowania  
 Można określić elementów, których właściwości i wzorce, które mają być buforowane, ustawiając <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> właściwości przed uaktywnieniem żądania. Zakres jest określana względem elementów, które są pobierane, gdy żądanie jest aktywny. Na przykład jeśli ustawisz tylko <xref:System.Windows.Automation.TreeScope.Children>, a następnie pobrać <xref:System.Windows.Automation.AutomationElement>, właściwości i wzorce elementów podrzędnych tego elementu są buforowane, ale nie tych samego elementu. Aby upewnić się, że buforowanie jest wykonywane na potrzeby elementu pobrane, musi zawierać <xref:System.Windows.Automation.TreeScope.Element> w <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości. Nie jest możliwe ustawić zakres <xref:System.Windows.Automation.TreeScope.Parent> lub <xref:System.Windows.Automation.TreeScope.Ancestors>. Jednak element nadrzędny mogą być buforowane podczas elementu podrzędnego jest buforowana; Zobacz Pobieranie elementów podrzędnych w pamięci podręcznej i elementów nadrzędnych w tym temacie.  
  
 Zakres buforowanie wpływa także <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> właściwości. Domyślnie buforowanie jest wykonywane tylko dla elementów, które są wyświetlane w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Można jednak zmienić tę właściwość, aby zastosować buforowanie, aby wszystkie elementy lub tylko dla elementów, które są wyświetlane w widoku zawartości.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Siła odwołania do elementu  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement>, domyślnie mają dostęp do wszystkich właściwości i wzorce tego elementu, łącznie z tymi, które nie zostały zapisane. Jednak w przypadku większej wydajności można określić czy odwołanie do elementu odwołuje się do pamięci podręcznej danych, ustawiając <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> właściwość <xref:System.Windows.Automation.CacheRequest> do <xref:System.Windows.Automation.AutomationElementMode.None>. W takim przypadku nie masz dostępu do żadnych właściwości niebuforowanym i wzorce pobrane elementów. Oznacza to, że nie masz dostępu do żadnych właściwości za pośrednictwem <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub `Current` właściwość <xref:System.Windows.Automation.AutomationElement> lub dowolnego — wzorzec formantu; nie można pobrać wzorca za pomocą <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Buforowane wzorce, można wywołać metody pobierające właściwości tablicy, takich jak <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ale nie wszystkie że akcje w formancie, takich jak <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Przykładem aplikacji, która nie może być konieczne pełne odwołania do obiektów jest czytnika ekranu, który będzie pobrana z wyprzedzeniem <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> i <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> właściwości elementów w oknie, ale nie jest wymagane <xref:System.Windows.Automation.AutomationElement> same obiekty.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Aktywowanie obiektu CacheRequest  
 Buforowanie jest wykonywane tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElement> obiekty są pobierane podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny dla bieżącego wątku. Istnieją dwa sposoby aktywacji <xref:System.Windows.Automation.CacheRequest>.  
  
 Zwykle jest wywołanie <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Ta metoda zwraca obiekt, który implementuje <xref:System.IDisposable>. Żądanie pozostaje aktywne tak długo, jak <xref:System.IDisposable> obiekt istnieje. Najprostszym sposobem zarządzają okresem istnienia obiektu jest należy ująć w wywołaniu `using` ([!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]) lub `Using` ([!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) bloku. Daje to pewność, że żądanie będzie zostać zdjęte ze stosu ze stosu, nawet jeśli zgłoszony wyjątek.  
  
 Inny sposób, co jest przydatne, gdy chcesz zagnieździć żądań pamięci podręcznej, jest wywołanie <xref:System.Windows.Automation.CacheRequest.Push%2A>. Umieszcza żądania na stosie i aktywuje go. Żądanie pozostaje aktywne, dopóki zostanie usunięta ze stosu przez <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Żądanie staje się tymczasowo nieaktywny, jeśli inne żądanie spoczywa na stosie; żądanie top w stosie jest aktywna.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Podczas pobierania właściwości w pamięci podręcznej  
 Za pomocą następujących metod i właściwości można pobrać właściwości pamięci podręcznej elementu.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Zgłoszony wyjątek, jeśli Żądana właściwość nie jest w pamięci podręcznej.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, takich jak <xref:System.Windows.Automation.AutomationElement.Current%2A>, udostępnia poszczególnych właściwości jako członkowie struktury. Jednak nie należy do pobierania tej struktury; można uzyskać dostęp do poszczególnych właściwości bezpośrednio. Na przykład <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> można uzyskać właściwości `element.Cached.Name`, gdzie `element` jest <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Pobieranie wzorców formantu w pamięci podręcznej  
 Wzorce formantu pamięci podręcznej elementu można pobrać za pomocą następujących metod.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Jeśli wzorzec nie znajduje się w pamięci podręcznej, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> zgłasza wyjątek, i <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> zwraca `false`.  
  
 Buforowane właściwości wzorca formantu można pobrać za pomocą `Cached` właściwości obiektu wzorca. Można również pobrać bieżące wartości za pośrednictwem `Current` właściwości, ale tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElementMode.None> nie została określona podczas <xref:System.Windows.Automation.AutomationElement> został pobrany. (<xref:System.Windows.Automation.AutomationElementMode.Full> jest to wartość domyślna i umożliwia dostęp do bieżącej wartości.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Pobieranie w pamięci podręcznej elementów podrzędnych i elementów nadrzędnych  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement> i buforowania dla elementów podrzędnych tego elementu za pomocą żądania <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości żądania, jest następnie można uzyskać podrzędne elementy z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> właściwości elementu można pobrać.  
  
 Jeśli <xref:System.Windows.Automation.TreeScope.Element> został uwzględniony w zakresie żądań pamięci podręcznej jest następnie dostępnym dla elementu głównego żądania <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> właściwości elementów podrzędnych.  
  
> [!NOTE]
>  Nie można buforować nadrzędnych ani elementów nadrzędnych elementu głównego żądania.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Aktualizacja pamięci podręcznej  
 Pamięć podręczna jest prawidłowy tylko tak długo, jak żadne zmiany w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Aplikacja jest odpowiedzialny za Aktualizacja pamięci podręcznej, zazwyczaj w odpowiedzi na zdarzenia.  
  
 Jeśli subskrybować zdarzenia podczas <xref:System.Windows.Automation.CacheRequest> jest uzyskać aktywny, <xref:System.Windows.Automation.AutomationElement> z zaktualizowano pamięci podręcznej jako źródła zdarzeń, gdy jest wywoływana z obiektu delegowanego obsługi zdarzeń. Można także zaktualizować buforowanych informacji dla elementu przez wywołanie metody <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Można przekazać w oryginalnym <xref:System.Windows.Automation.CacheRequest> Aby zaktualizować wszystkie informacje, który wcześniej był buforowany.  
  
 Aktualizacja pamięci podręcznej nie zmienia żadnych istniejących właściwości <xref:System.Windows.Automation.AutomationElement> odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Przykładowe FetchTimer](http://msdn.microsoft.com/en-us/5b7d3294-de22-4f24-b2d6-d4785a304b90)
