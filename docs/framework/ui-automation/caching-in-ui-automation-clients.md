---
title: Buforowanie w klientach automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 5c0c92f40ae60785f780cb573bb7faa77a31f273
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741778"
---
# <a name="caching-in-ui-automation-clients"></a>Buforowanie w klientach automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono buforowanie właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wzorców kontrolek.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]buforowanie oznacza wstępne pobranie danych. Następnie można uzyskać dostęp do danych bez dalszej komunikacji między procesami. Buforowanie jest zwykle używane przez aplikacje klienckie automatyzacji interfejsu użytkownika do pobierania zbiorczych właściwości i wzorców kontrolek. Informacje są następnie pobierane z pamięci podręcznej w razie konieczności. Aplikacja okresowo aktualizuje pamięć podręczną, zazwyczaj w odpowiedzi na zdarzenia, co oznacza, że coś w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] uległo zmianie.  
  
 Zalety buforowania są najbardziej zauważalne w przypadku formantów Windows Presentation Foundation (WPF) i kontrolek niestandardowych z dostawcami automatyzacji interfejsu użytkownika po stronie serwera. Dostęp do dostawców po stronie klienta, takich jak domyślny dostawcy dla formantów Win32, ma mniejsze korzyści.  
  
 Buforowanie występuje, gdy aplikacja aktywuje <xref:System.Windows.Automation.CacheRequest> a następnie używa dowolnej metody lub właściwości, która zwraca <xref:System.Windows.Automation.AutomationElement>; na przykład <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Metody klasy <xref:System.Windows.Automation.TreeWalker> są wyjątkiem; buforowanie jest wykonywane tylko wtedy, gdy <xref:System.Windows.Automation.CacheRequest> jest określony jako parametr (na przykład <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Buforowanie występuje również w przypadku zasubskrybowania zdarzenia, gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny. <xref:System.Windows.Automation.AutomationElement> przeszedł do programu obsługi zdarzeń, ponieważ Źródło zdarzenia zawiera buforowane właściwości i wzorce określone przez oryginalny <xref:System.Windows.Automation.CacheRequest>. Wszelkie zmiany wprowadzone w <xref:System.Windows.Automation.CacheRequest> po zasubskrybowaniu zdarzenia nie mają żadnego skutku.  
  
 Właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wzorce kontrolek elementu mogą być buforowane.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Opcje buforowania  
 <xref:System.Windows.Automation.CacheRequest> określa następujące opcje buforowania.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Właściwości do buforowania  
 Możesz określić właściwości do buforowania, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> dla każdej właściwości przed aktywowaniem żądania.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Wzorce kontroli do pamięci podręcznej  
 Możesz określić wzorce kontroli do buforowania, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> dla każdego wzorca przed aktywowaniem żądania. Gdy wzorzec jest buforowany, jego właściwości nie są automatycznie buforowane; należy określić właściwości, które mają być buforowane przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Zakres i filtrowanie pamięci podręcznej  
 Można określić elementy, których właściwości i wzorce mają być buforowane przez ustawienie właściwości <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> przed aktywowaniem żądania. Zakres jest względny dla elementów, które są pobierane, gdy żądanie jest aktywne. Na przykład jeśli ustawisz tylko <xref:System.Windows.Automation.TreeScope.Children>, a następnie pobierzesz <xref:System.Windows.Automation.AutomationElement>, właściwości i wzorce elementów podrzędnych tego elementu są buforowane, ale nie są to elementy samego elementu. Aby upewnić się, że buforowanie jest wykonywane dla pobranego elementu, należy uwzględnić <xref:System.Windows.Automation.TreeScope.Element> we właściwości <xref:System.Windows.Automation.CacheRequest.TreeScope%2A>. Nie można ustawić zakresu <xref:System.Windows.Automation.TreeScope.Parent> ani <xref:System.Windows.Automation.TreeScope.Ancestors>. Jednak element nadrzędny może być buforowany, gdy element podrzędny jest buforowany; Zobacz Pobieranie buforowanych elementów podrzędnych i elementów nadrzędnych w tym temacie.  
  
 Właściwość <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> ma także wpływ na zakres buforowania. Domyślnie buforowanie jest wykonywane tylko dla elementów, które są wyświetlane w widoku kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Można jednak zmienić tę właściwość, aby zastosować buforowanie do wszystkich elementów lub tylko do elementów, które są wyświetlane w widoku zawartości.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Siła odwołań do elementów  
 Gdy pobierasz <xref:System.Windows.Automation.AutomationElement>, domyślnie masz dostęp do wszystkich właściwości i wzorców tego elementu, w tym tych, które nie zostały w pamięci podręcznej. Jednak w celu zapewnienia większej wydajności można określić, że odwołanie do elementu odnosi się tylko do danych w pamięci podręcznej, ustawiając właściwość <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> <xref:System.Windows.Automation.CacheRequest> do <xref:System.Windows.Automation.AutomationElementMode.None>. W takim przypadku nie masz dostępu do żadnych niebuforowanych właściwości i wzorców pobranych elementów. Oznacza to, że nie można uzyskać dostępu do żadnych właściwości za pośrednictwem <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub właściwości `Current` <xref:System.Windows.Automation.AutomationElement> lub żadnego wzorca kontrolki; nie można też pobrać wzorca przy użyciu <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. W przypadku wzorców w pamięci podręcznej można wywoływać metody, które pobierają właściwości tablicy, takie jak <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ale nie wszystkie te, które wykonują działania w formancie, takie jak <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Przykładem aplikacji, która może nie wymagać pełnych odwołań do obiektów, jest czytnik ekranu, który pobiera <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> i <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> właściwości elementów w oknie, ale nie potrzebuje <xref:System.Windows.Automation.AutomationElement> obiektów.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Aktywowanie CacheRequest  
 Buforowanie jest wykonywane tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElement> obiekty są pobierane, gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny dla bieżącego wątku. Istnieją dwa sposoby aktywowania <xref:System.Windows.Automation.CacheRequest>.  
  
 Typowym sposobem jest wywołanie <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Ta metoda zwraca obiekt, który implementuje <xref:System.IDisposable>. Żądanie pozostaje aktywne, o ile istnieje obiekt <xref:System.IDisposable>. Najprostszym sposobem na sterowanie okresem istnienia obiektu jest ujęcie wywołania w bloku `using` (C#) lub `Using` (Visual Basic). Dzięki temu żądanie zostanie zdjęte ze stosu, nawet jeśli zostanie zgłoszony wyjątek.  
  
 Inny sposób, który jest przydatny w przypadku zagnieżdżania żądań pamięci podręcznej, to wywołanie <xref:System.Windows.Automation.CacheRequest.Push%2A>. Spowoduje to umieszczenie żądania na stosie i jego aktywowanie. Żądanie pozostanie aktywne, dopóki nie zostanie usunięte ze stosu przez <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Żądanie stanie się tymczasowo nieaktywne, jeśli na stosie zostanie wypchnięte inne żądanie. aktywne jest tylko żądanie najwyższego poziomu na stosie.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Pobieranie właściwości pamięci podręcznej  
 Można pobrać zbuforowane właściwości elementu za pomocą następujących metod i właściwości.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Wyjątek jest zgłaszany, jeśli żądana właściwość nie znajduje się w pamięci podręcznej.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, jak <xref:System.Windows.Automation.AutomationElement.Current%2A>, uwidacznia poszczególne właściwości jako elementy członkowskie struktury. Nie trzeba jednak pobierać tej struktury; dostęp do poszczególnych właściwości można uzyskać bezpośrednio. Na przykład właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> można uzyskać z `element.Cached.Name`, gdzie `element` jest <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Pobieranie wzorców formantów w pamięci podręcznej  
 Można pobrać zbuforowane Wzorce formantów elementu przy użyciu poniższych metod.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Jeśli wzorzec nie znajduje się w pamięci podręcznej, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> zgłasza wyjątek, a <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> zwraca `false`.  
  
 Można pobrać zbuforowane właściwości wzorca kontrolki za pomocą właściwości `Cached` obiektu wzorca. Możesz również pobrać bieżące wartości za pomocą właściwości `Current`, ale tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElementMode.None> nie została określona podczas pobierania <xref:System.Windows.Automation.AutomationElement>. (<xref:System.Windows.Automation.AutomationElementMode.Full> jest wartością domyślną i umożliwia dostęp do bieżących wartości).  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Pobieranie buforowanych elementów podrzędnych i elementów nadrzędnych  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement> i buforowania żądań dla elementów podrzędnych tego elementu za pośrednictwem właściwości <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> żądania można pobrać elementy podrzędne z właściwości <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> elementu, który został pobrany.  
  
 Jeśli <xref:System.Windows.Automation.TreeScope.Element> został uwzględniony w zakresie żądania pamięci podręcznej, element główny żądania jest następnie dostępny z właściwości <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> dowolnego elementu podrzędnego.  
  
> [!NOTE]
> Nie można buforować obiektów nadrzędnych ani elementów nadrzędnych elementu głównego żądania.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Aktualizowanie pamięci podręcznej  
 Pamięć podręczna jest prawidłowa tylko pod warunkiem, że nie ma żadnych zmian w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Aplikacja jest odpowiedzialna za aktualizowanie pamięci podręcznej, zazwyczaj w odpowiedzi na zdarzenia.  
  
 Jeśli subskrybujesz zdarzenie, gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskujesz <xref:System.Windows.Automation.AutomationElement> ze zaktualizowaną pamięcią podręczną jako źródłem zdarzenia za każdym razem, gdy obiekt delegowany obsługi zdarzeń zostanie wywołany. Możesz również zaktualizować informacje w pamięci podręcznej dla elementu, wywołując <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Możesz przekazać oryginalny <xref:System.Windows.Automation.CacheRequest>, aby zaktualizować wszystkie informacje, które były wcześniej buforowane.  
  
 Aktualizacja pamięci podręcznej nie powoduje zmiany właściwości istniejących odwołań <xref:System.Windows.Automation.AutomationElement>.  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Przykład FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
