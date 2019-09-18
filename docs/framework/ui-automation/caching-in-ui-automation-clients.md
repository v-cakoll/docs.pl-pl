---
title: Buforowanie w klientach automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: bf617279b16f53164209f5ae7605830dabda4c2e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043929"
---
# <a name="caching-in-ui-automation-clients"></a>Buforowanie w klientach automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tym temacie przedstawiono buforowanie właściwości i wzorców kontrolek.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie buforowanie oznacza wstępne pobranie danych. Następnie można uzyskać dostęp do danych bez dalszej komunikacji między procesami. Buforowanie jest zwykle używane przez aplikacje klienckie automatyzacji interfejsu użytkownika do pobierania zbiorczych właściwości i wzorców kontrolek. Informacje są następnie pobierane z pamięci podręcznej w razie konieczności. Aplikacja okresowo aktualizuje pamięć podręczną, zazwyczaj w odpowiedzi na zdarzenia oznaczające, że coś [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] w programie uległo zmianie.  
  
 Zalety buforowania są najbardziej zauważalne w przypadku formantów Windows Presentation Foundation (WPF) i kontrolek niestandardowych z dostawcami automatyzacji interfejsu użytkownika po stronie serwera. Podczas uzyskiwania dostępu do dostawców po stronie klienta, takich jak domyślny dostawcy dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolek, jest mniej korzyści.  
  
 Buforowanie występuje, <xref:System.Windows.Automation.CacheRequest> gdy aplikacja aktywuje a, a następnie używa dowolnej metody lub właściwości, która <xref:System.Windows.Automation.AutomationElement>zwraca, na przykład <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>,, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Metody <xref:System.Windows.Automation.TreeWalker> klasy są wyjątkiem; buforowanie jest wykonywane tylko <xref:System.Windows.Automation.CacheRequest> wtedy, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>gdy parametr jest określony jako parametru (na przykład.  
  
 Buforowanie występuje również w przypadku zasubskrybowania zdarzenia, gdy <xref:System.Windows.Automation.CacheRequest> jest ono aktywne. Przekazanie do programu obsługi zdarzeń jako źródło zdarzenia zawiera buforowane właściwości i wzorce określone przez oryginalny <xref:System.Windows.Automation.CacheRequest>. <xref:System.Windows.Automation.AutomationElement> Wszelkie zmiany wprowadzone w ramach <xref:System.Windows.Automation.CacheRequest> subskrypcji zdarzenia nie mają żadnego skutku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwości i wzorce kontrolek elementu mogą być buforowane.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Opcje buforowania  
 <xref:System.Windows.Automation.CacheRequest> Określa następujące opcje buforowania.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Właściwości do buforowania  
 Można określić właściwości pamięci podręcznej, <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> wywołując dla każdej właściwości przed aktywowaniem żądania.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Wzorce kontroli do pamięci podręcznej  
 Możesz określić wzorce kontroli do buforowania, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> dla każdego wzorca przed aktywowaniem żądania. Gdy wzorzec jest buforowany, jego właściwości nie są automatycznie buforowane; należy określić właściwości, które mają być buforowane przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Zakres i filtrowanie pamięci podręcznej  
 Można określić elementy, których właściwości i wzorce mają być buforowane przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> właściwości przed aktywowaniem żądania. Zakres jest względny dla elementów, które są pobierane, gdy żądanie jest aktywne. Jeśli na przykład ustawisz tylko <xref:System.Windows.Automation.TreeScope.Children>, a następnie <xref:System.Windows.Automation.AutomationElement>pobierzesz, właściwości i wzorce elementów podrzędnych tego elementu są buforowane, ale nie są to elementy samego elementu. Aby zapewnić, że buforowanie zostanie wykonane dla pobranego elementu, musisz uwzględnić <xref:System.Windows.Automation.TreeScope.Element> <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> we właściwości. Nie można ustawić zakresu na <xref:System.Windows.Automation.TreeScope.Parent> lub. <xref:System.Windows.Automation.TreeScope.Ancestors> Jednak element nadrzędny może być buforowany, gdy element podrzędny jest buforowany; Zobacz Pobieranie buforowanych elementów podrzędnych i elementów nadrzędnych w tym temacie.  
  
 <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> Właściwość ma wpływ na zakres buforowania. Domyślnie buforowanie jest wykonywane tylko dla elementów, które są wyświetlane w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa. Można jednak zmienić tę właściwość, aby zastosować buforowanie do wszystkich elementów lub tylko do elementów, które są wyświetlane w widoku zawartości.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Siła odwołań do elementów  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement>, domyślnie masz dostęp do wszystkich właściwości i wzorców tego elementu, w tym tych, które nie zostały w pamięci podręcznej. Jednak w celu zwiększenia wydajności można określić, że odwołanie do elementu odnosi się tylko do danych w pamięci podręcznej <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> , ustawiając właściwość <xref:System.Windows.Automation.CacheRequest> na <xref:System.Windows.Automation.AutomationElementMode.None>. W takim przypadku nie masz dostępu do żadnych niebuforowanych właściwości i wzorców pobranych elementów. Oznacza to, że nie można uzyskać dostępu do <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> żadnych właściwości `Current` za pośrednictwem właściwości <xref:System.Windows.Automation.AutomationElement> lub któregokolwiek wzorca kontrolki ani nie można pobrać wzorca przy <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> użyciu <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>lub. W przypadku wzorców w pamięci podręcznej można wywoływać metody, które pobierają właściwości tablicy, takie jak <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ale nie wszystkie operacje wykonywane na formancie, takie jak. <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>  
  
 Przykładem aplikacji, która może nie wymagać pełnych odwołań do obiektów, jest czytnik ekranu, który umożliwia pobieranie z <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> wyprzedzeniem właściwości i <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> elementów w oknie, <xref:System.Windows.Automation.AutomationElement> ale nie wymaga samych obiektów.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Aktywowanie CacheRequest  
 Buforowanie jest wykonywane tylko wtedy <xref:System.Windows.Automation.AutomationElement> , <xref:System.Windows.Automation.CacheRequest> gdy obiekty są pobierane, gdy jest aktywny dla bieżącego wątku. Istnieją dwa sposoby aktywowania programu <xref:System.Windows.Automation.CacheRequest>.  
  
 Typowym sposobem jest wywołanie <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Ta metoda zwraca obiekt, który implementuje <xref:System.IDisposable>. Żądanie pozostaje aktywne, <xref:System.IDisposable> dopóki obiekt już istnieje. Najprostszym sposobem na sterowanie okresem istnienia obiektu jest ujęcie wywołania w `using` bloku (C#) lub `Using` (Visual Basic). Dzięki temu żądanie zostanie zdjęte ze stosu, nawet jeśli zostanie zgłoszony wyjątek.  
  
 Inny sposób, który jest przydatny w przypadku zagnieżdżania żądań pamięci podręcznej, <xref:System.Windows.Automation.CacheRequest.Push%2A>jest wywoływany. Spowoduje to umieszczenie żądania na stosie i jego aktywowanie. Żądanie pozostaje aktywne, dopóki nie zostanie usunięte ze stosu przez <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Żądanie stanie się tymczasowo nieaktywne, jeśli na stosie zostanie wypchnięte inne żądanie. aktywne jest tylko żądanie najwyższego poziomu na stosie.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Pobieranie właściwości pamięci podręcznej  
 Można pobrać zbuforowane właściwości elementu za pomocą następujących metod i właściwości.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Wyjątek jest zgłaszany, jeśli żądana właściwość nie znajduje się w pamięci podręcznej.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, podobnie <xref:System.Windows.Automation.AutomationElement.Current%2A>jak, uwidacznia poszczególne właściwości jako elementy członkowskie struktury. Nie trzeba jednak pobierać tej struktury; dostęp do poszczególnych właściwości można uzyskać bezpośrednio. Na przykład <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> Właściwość można uzyskać z `element.Cached.Name`, gdzie `element` jest <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Pobieranie wzorców formantów w pamięci podręcznej  
 Można pobrać zbuforowane Wzorce formantów elementu przy użyciu poniższych metod.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Jeśli wzorzec nie znajduje się w pamięci podręcznej, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> zgłasza wyjątek i <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> zwraca. `false`  
  
 Można pobrać zbuforowane właściwości wzorca kontrolki za pomocą `Cached` właściwości obiektu wzorca. Możesz również pobrać bieżące wartości za pomocą `Current` właściwości, ale <xref:System.Windows.Automation.AutomationElementMode.None> tylko wtedy, gdy nie <xref:System.Windows.Automation.AutomationElement> została określona podczas pobierania. (<xref:System.Windows.Automation.AutomationElementMode.Full> jest wartością domyślną i umożliwia dostęp do bieżących wartości).  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Pobieranie buforowanych elementów podrzędnych i elementów nadrzędnych  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement> i przeprowadzeniu buforowania żądania dla elementów podrzędnych tego elementu <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> za pośrednictwem właściwości żądania można pobrać elementy podrzędne z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> właściwości elementu, który został pobrany.  
  
 Jeśli <xref:System.Windows.Automation.TreeScope.Element> został uwzględniony w zakresie żądania pamięci podręcznej, element główny żądania jest następnie dostępny <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> z właściwości dowolnego elementu podrzędnego.  
  
> [!NOTE]
> Nie można buforować obiektów nadrzędnych ani elementów nadrzędnych elementu głównego żądania.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Aktualizowanie pamięci podręcznej  
 Pamięć podręczna jest prawidłowa tylko pod warunkiem, że nie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ma żadnych zmian w. Aplikacja jest odpowiedzialna za aktualizowanie pamięci podręcznej, zazwyczaj w odpowiedzi na zdarzenia.  
  
 Jeśli zasubskrybujesz zdarzenie, gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, otrzymujesz zaktualizowaną pamięć podręczną jako źródło zdarzenia za każdym razem, <xref:System.Windows.Automation.AutomationElement> gdy obiekt delegowany obsługi zdarzeń jest wywoływany. Możesz również zaktualizować informacje w pamięci podręcznej dla elementu <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>przez wywołanie. Można przekazać oryginalny <xref:System.Windows.Automation.CacheRequest> , aby zaktualizować wszystkie informacje, które były wcześniej buforowane.  
  
 Aktualizacja pamięci podręcznej nie zmienia właściwości żadnych istniejących <xref:System.Windows.Automation.AutomationElement> odwołań.  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Przykład FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
