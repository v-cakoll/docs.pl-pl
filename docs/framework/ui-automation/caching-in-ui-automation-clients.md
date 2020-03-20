---
title: Buforowanie w klientach automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 186ed77594aadab9e3f49ef30e559e159aee1b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180286"
---
# <a name="caching-in-ui-automation-clients"></a>Buforowanie w klientach automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] buforowanie właściwości i wzorców kontroli.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], buforowanie oznacza wstępne pobieranie danych. Dostęp do danych można następnie uzyskać bez dalszej komunikacji między procesami. Buforowanie jest zwykle używany przez aplikacje klienckie automatyzacji interfejsu użytkownika do pobierania właściwości i wzorców kontroli zbiorczo. Informacje są następnie pobierane z pamięci podręcznej w razie potrzeby. Aplikacja aktualizuje pamięć podręczną okresowo, zwykle w odpowiedzi [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] na zdarzenia oznaczające, że coś w zmienił.  
  
 Korzyści z buforowania są najbardziej zauważalne za pomocą formantów Windows Presentation Foundation (WPF) i formantów niestandardowych, które mają dostawców automatyzacji interfejsu użytkownika po stronie serwera. Jest mniej korzyści podczas uzyskiwania dostępu do dostawców po stronie klienta, takich jak domyślni dostawcy formanty Win32.  
  
 Buforowanie występuje, gdy aplikacja <xref:System.Windows.Automation.CacheRequest> aktywuje a, a następnie używa <xref:System.Windows.Automation.AutomationElement>dowolnej metody lub właściwości, która zwraca ; na przykład <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, . Metody <xref:System.Windows.Automation.TreeWalker> klasy są wyjątkiem; buforowanie odbywa się tylko <xref:System.Windows.Automation.CacheRequest> wtedy, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>gdy parametr jest określony jako parametr (na przykład .  
  
 Buforowanie występuje również podczas subskrybowania zdarzenia, gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny. Przekazany <xref:System.Windows.Automation.AutomationElement> do programu obsługi zdarzeń jako źródło zdarzenia zawiera buforowane właściwości i <xref:System.Windows.Automation.CacheRequest>wzorce określone przez oryginalny . Wszelkie zmiany wprowadzone <xref:System.Windows.Automation.CacheRequest> po subskrybowaniu zdarzenia nie mają wpływu.  
  
 Właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i wzorce kontroli elementu mogą być buforowane.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Opcje buforowania  
 Określa <xref:System.Windows.Automation.CacheRequest> następujące opcje buforowania.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Właściwości do pamięci podręcznej  
 Można określić właściwości do <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> pamięci podręcznej, wywołując dla każdej właściwości przed aktywacją żądania.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Steruj wzorcami do pamięci podręcznej  
 Można określić wzorce kontroli <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> do pamięci podręcznej, wywołując dla każdego wzorca przed aktywacją żądania. Gdy wzorzec jest buforowany, jego właściwości nie są automatycznie buforowane; należy określić właściwości, które mają <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>być buforowane za pomocą programu .  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Zakres i filtrowanie buforowania  
 Można określić elementy, których właściwości i wzorce chcesz <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> buforować, ustawiając właściwość przed aktywacją żądania. Zakres jest względem elementów, które są pobierane, gdy żądanie jest aktywne. Na przykład jeśli ustawisz tylko <xref:System.Windows.Automation.TreeScope.Children>, <xref:System.Windows.Automation.AutomationElement>a następnie pobrać , właściwości i wzorce elementów podrzędnych tego elementu są buforowane, ale nie te samego elementu. Aby upewnić się, że buforowanie odbywa się dla <xref:System.Windows.Automation.TreeScope.Element> samego <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> pobranego elementu, należy uwzględnić we właściwości. Nie jest możliwe ustawienie zakresu <xref:System.Windows.Automation.TreeScope.Parent> <xref:System.Windows.Automation.TreeScope.Ancestors>na lub . Jednak element nadrzędny może być buforowany, gdy element podrzędny jest buforowany; zobacz Pobieranie buforowanych dzieci i rodziców w tym temacie.  
  
 Na zakres buforowania ma również wpływ <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> nieruchomość. Domyślnie buforowanie jest wykonywane tylko dla elementów, które [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pojawiają się w widoku kontrolnym drzewa. Można jednak zmienić tę właściwość, aby zastosować buforowanie do wszystkich elementów lub tylko do elementów, które pojawiają się w widoku zawartości.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Siła odniesień do elementów  
 Podczas pobierania programu <xref:System.Windows.Automation.AutomationElement>, domyślnie masz dostęp do wszystkich właściwości i wzorców tego elementu, w tym tych, które nie zostały zapisane w pamięci podręcznej. Jednak dla większej wydajności można określić, że odwołanie do elementu odnosi się <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> tylko do <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElementMode.None>danych buforowanych, ustawiając właściwość do . W takim przypadku nie masz dostępu do żadnych właściwości nie buforowane i wzorce pobranych elementów. Oznacza to, że nie można <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> uzyskać `Current` dostępu <xref:System.Windows.Automation.AutomationElement> do żadnych właściwości za pośrednictwem lub właściwości lub wzorca kontroli; ani nie można pobrać wzorzec za pomocą <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. W przypadku wzorców buforowanych można wywoływać metody pobierające <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>właściwości tablicy, takie jak , ale <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>nie wszystkie, które wykonują akcje na formancie, takie jak .  
  
 Przykładem aplikacji, która może nie wymagać pełnych odwołań do obiektów, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> jest <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> czytnik ekranu, który wstępnie wciągałby i właściwości elementów w oknie, ale nie potrzebowałby <xref:System.Windows.Automation.AutomationElement> samych obiektów.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Aktywowanie cacherequest  
 Buforowanie jest wykonywane <xref:System.Windows.Automation.AutomationElement> tylko wtedy, gdy <xref:System.Windows.Automation.CacheRequest> obiekty są pobierane, gdy jest aktywny dla bieżącego wątku. Istnieją dwa sposoby <xref:System.Windows.Automation.CacheRequest>aktywowania pliku .  
  
 Typowym sposobem jest <xref:System.Windows.Automation.CacheRequest.Activate%2A>wywołanie . Ta metoda zwraca obiekt, <xref:System.IDisposable>który implementuje . Żądanie pozostaje aktywne tak długo, <xref:System.IDisposable> jak obiekt istnieje. Najprostszym sposobem kontrolowania okresu istnienia obiektu jest ująć `using` wywołanie w `Using` bloku (C#) lub (Visual Basic). Gwarantuje to, że żądanie zostanie wyświetlenie z stosu, nawet jeśli wyjątek jest wywoływany.  
  
 Innym sposobem, który jest przydatny, gdy chcesz zagnieżdżać żądania pamięci podręcznej, jest wywołanie <xref:System.Windows.Automation.CacheRequest.Push%2A>. Spowoduje to, że żądanie na stosie i aktywuje go. Żądanie pozostaje aktywne, dopóki nie zostanie <xref:System.Windows.Automation.CacheRequest.Pop%2A>usunięte ze stosu przez . Żądanie staje się tymczasowo nieaktywne, jeśli inne żądanie jest wypychane na stosie; tylko górne żądanie na stosie jest aktywne.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Pobieranie właściwości buforowanych  
 Można pobrać buforowane właściwości elementu za pomocą następujących metod i właściwości.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Wyjątek jest wywoływany, jeśli żądana właściwość nie znajduje się w pamięci podręcznej.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, <xref:System.Windows.Automation.AutomationElement.Current%2A>na przykład, udostępnia poszczególne właściwości jako elementy członkowskie konstrukcji. Jednak nie trzeba pobierać tej struktury; można uzyskać dostęp do poszczególnych właściwości bezpośrednio. Na przykład <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> właściwość można `element.Cached.Name`uzyskać `element` z <xref:System.Windows.Automation.AutomationElement>, gdzie jest .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Pobieranie wzorców kontroli w pamięci podręcznej  
 Można pobrać wzorce kontroli buforowane elementu za pomocą następujących metod.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Jeśli wzorzec nie znajduje <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> się w pamięci <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> `false`podręcznej, zgłasza wyjątek i zwraca .  
  
 Można pobrać buforowane właściwości wzorca formantu `Cached` przy użyciu właściwości obiektu wzorca. Można również pobrać bieżące wartości `Current` za pośrednictwem <xref:System.Windows.Automation.AutomationElementMode.None> właściwości, ale <xref:System.Windows.Automation.AutomationElement> tylko wtedy, gdy nie został określony, gdy został pobrany. (<xref:System.Windows.Automation.AutomationElementMode.Full> jest wartością domyślną, która umożliwia dostęp do bieżących wartości.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Pobieranie buforowanych dzieci i rodziców  
 Podczas pobierania <xref:System.Windows.Automation.AutomationElement> i żądania buforowania dla elementów podrzędnych tego elementu za pośrednictwem <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości żądania, jest <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> następnie możliwe, aby uzyskać elementy podrzędne z właściwości pobranego elementu.  
  
 Jeśli <xref:System.Windows.Automation.TreeScope.Element> został uwzględniony w zakresie żądania pamięci podręcznej, główny element żądania <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> jest następnie dostępny z właściwości dowolnego elementu podrzędnego.  
  
> [!NOTE]
> Nie można buforować elementów nadrzędnych lub elementów nadrzędnych elementu głównego żądania.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Aktualizowanie pamięci podręcznej  
 Pamięć podręczna jest prawidłowa tylko [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]tak długo, jak nic się nie zmieni w pliku . Aplikacja jest odpowiedzialna za aktualizowanie pamięci podręcznej, zazwyczaj w odpowiedzi na zdarzenia.  
  
 Jeśli subskrybujesz zdarzenie, <xref:System.Windows.Automation.CacheRequest> gdy a jest <xref:System.Windows.Automation.AutomationElement> aktywny, można uzyskać z zaktualizowaną pamięcią podręczną jako źródło zdarzenia, gdy jest wywoływana delegat obsługi zdarzeń. Można również zaktualizować buforowane informacje dla <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>elementu, wywołując . Można przekazać w <xref:System.Windows.Automation.CacheRequest> oryginale, aby zaktualizować wszystkie informacje, które wcześniej były buforowane.  
  
 Aktualizowanie pamięci podręcznej nie zmienia właściwości <xref:System.Windows.Automation.AutomationElement> żadnych istniejących odwołań.  
  
## <a name="see-also"></a>Zobacz też

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Próbka ściągacza](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
