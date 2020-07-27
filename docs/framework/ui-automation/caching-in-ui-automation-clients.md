---
title: Buforowanie w klientach automatyzacji interfejsu użytkownika
description: Uzyskaj szczegółowe informacje o buforowaniu w klientach automatyzacji interfejsu użytkownika w programie .NET. Buforowanie jest zdefiniowane jako wstępne pobieranie danych.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 4fbb4acabebea54015b11cefdf8a37c7e2dc93f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168250"
---
# <a name="caching-in-ui-automation-clients"></a>Buforowanie w klientach automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono buforowanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości i wzorców kontrolek.  
  
 W programie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] buforowanie oznacza wstępne pobranie danych. Następnie można uzyskać dostęp do danych bez dalszej komunikacji między procesami. Buforowanie jest zwykle używane przez aplikacje klienckie automatyzacji interfejsu użytkownika do pobierania zbiorczych właściwości i wzorców kontrolek. Informacje są następnie pobierane z pamięci podręcznej w razie konieczności. Aplikacja okresowo aktualizuje pamięć podręczną, zazwyczaj w odpowiedzi na zdarzenia oznaczające, że coś w programie [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] uległo zmianie.  
  
 Zalety buforowania są najbardziej zauważalne w przypadku formantów Windows Presentation Foundation (WPF) i kontrolek niestandardowych z dostawcami automatyzacji interfejsu użytkownika po stronie serwera. Dostęp do dostawców po stronie klienta, takich jak domyślny dostawcy dla formantów Win32, ma mniejsze korzyści.  
  
 Buforowanie występuje, gdy aplikacja aktywuje a <xref:System.Windows.Automation.CacheRequest> , a następnie używa dowolnej metody lub właściwości, która zwraca, <xref:System.Windows.Automation.AutomationElement> na przykład, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> , <xref:System.Windows.Automation.AutomationElement.FindAll%2A> . Metody <xref:System.Windows.Automation.TreeWalker> klasy są wyjątkiem; buforowanie jest wykonywane tylko wtedy <xref:System.Windows.Automation.CacheRequest> , gdy parametr jest określony jako parametru (na przykład <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType> .  
  
 Buforowanie występuje również w przypadku zasubskrybowania zdarzenia, gdy <xref:System.Windows.Automation.CacheRequest> jest ono aktywne. <xref:System.Windows.Automation.AutomationElement>Przekazanie do programu obsługi zdarzeń jako źródło zdarzenia zawiera buforowane właściwości i wzorce określone przez oryginalny <xref:System.Windows.Automation.CacheRequest> . Wszelkie zmiany wprowadzone w ramach <xref:System.Windows.Automation.CacheRequest> subskrypcji zdarzenia nie mają żadnego skutku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwości i wzorce kontrolek elementu mogą być buforowane.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Opcje buforowania  
 <xref:System.Windows.Automation.CacheRequest>Określa następujące opcje buforowania.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Właściwości do buforowania  
 Można określić właściwości pamięci podręcznej, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> dla każdej właściwości przed aktywowaniem żądania.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Wzorce kontroli do pamięci podręcznej  
 Możesz określić wzorce kontroli do buforowania, wywołując <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> dla każdego wzorca przed aktywowaniem żądania. Gdy wzorzec jest buforowany, jego właściwości nie są automatycznie buforowane; należy określić właściwości, które mają być buforowane przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType> .  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Zakres i filtrowanie pamięci podręcznej  
 Można określić elementy, których właściwości i wzorce mają być buforowane przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> Właściwości przed aktywowaniem żądania. Zakres jest względny dla elementów, które są pobierane, gdy żądanie jest aktywne. Jeśli na przykład ustawisz tylko, <xref:System.Windows.Automation.TreeScope.Children> a następnie pobierzesz <xref:System.Windows.Automation.AutomationElement> , właściwości i wzorce elementów podrzędnych tego elementu są buforowane, ale nie są to elementy samego elementu. Aby zapewnić, że buforowanie zostanie wykonane dla pobranego elementu, musisz uwzględnić <xref:System.Windows.Automation.TreeScope.Element> we <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości. Nie można ustawić zakresu na <xref:System.Windows.Automation.TreeScope.Parent> lub <xref:System.Windows.Automation.TreeScope.Ancestors> . Jednak element nadrzędny może być buforowany, gdy element podrzędny jest buforowany; Zobacz Pobieranie buforowanych elementów podrzędnych i elementów nadrzędnych w tym temacie.  
  
 Właściwość ma wpływ na zakres buforowania <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> . Domyślnie buforowanie jest wykonywane tylko dla elementów, które są wyświetlane w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Można jednak zmienić tę właściwość, aby zastosować buforowanie do wszystkich elementów lub tylko do elementów, które są wyświetlane w widoku zawartości.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Siła odwołań do elementów  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement> , domyślnie masz dostęp do wszystkich właściwości i wzorców tego elementu, w tym tych, które nie zostały w pamięci podręcznej. Jednak w celu zwiększenia wydajności można określić, że odwołanie do elementu odnosi się tylko do danych w pamięci podręcznej, ustawiając <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> Właściwość <xref:System.Windows.Automation.CacheRequest> na <xref:System.Windows.Automation.AutomationElementMode.None> . W takim przypadku nie masz dostępu do żadnych niebuforowanych właściwości i wzorców pobranych elementów. Oznacza to, że nie można uzyskać dostępu do żadnych właściwości za pośrednictwem <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> `Current` właściwości lub <xref:System.Windows.Automation.AutomationElement> któregokolwiek wzorca kontrolki ani nie można pobrać wzorca przy użyciu <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> . W przypadku wzorców w pamięci podręcznej można wywoływać metody, które pobierają właściwości tablicy, takie jak <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType> , ale nie wszystkie operacje wykonywane na formancie, takie jak <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType> .  
  
 Przykładem aplikacji, która może nie wymagać pełnych odwołań do obiektów, jest czytnik ekranu, który umożliwia pobieranie z wyprzedzeniem <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> właściwości i elementów w oknie, ale nie wymaga <xref:System.Windows.Automation.AutomationElement> samych obiektów.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Aktywowanie CacheRequest  
 Buforowanie jest wykonywane tylko wtedy <xref:System.Windows.Automation.AutomationElement> , gdy obiekty są pobierane <xref:System.Windows.Automation.CacheRequest> , gdy jest aktywny dla bieżącego wątku. Istnieją dwa sposoby aktywowania programu <xref:System.Windows.Automation.CacheRequest> .  
  
 Typowym sposobem jest wywołanie <xref:System.Windows.Automation.CacheRequest.Activate%2A> . Ta metoda zwraca obiekt, który implementuje <xref:System.IDisposable> . Żądanie pozostaje aktywne, dopóki <xref:System.IDisposable> obiekt już istnieje. Najprostszym sposobem na sterowanie okresem istnienia obiektu jest ujęcie wywołania w `using` bloku (C#) lub `Using` (Visual Basic). Dzięki temu żądanie zostanie zdjęte ze stosu, nawet jeśli zostanie zgłoszony wyjątek.  
  
 Inny sposób, który jest przydatny w przypadku zagnieżdżania żądań pamięci podręcznej, jest wywoływany <xref:System.Windows.Automation.CacheRequest.Push%2A> . Spowoduje to umieszczenie żądania na stosie i jego aktywowanie. Żądanie pozostaje aktywne, dopóki nie zostanie usunięte ze stosu przez <xref:System.Windows.Automation.CacheRequest.Pop%2A> . Żądanie stanie się tymczasowo nieaktywne, jeśli na stosie zostanie wypchnięte inne żądanie. aktywne jest tylko żądanie najwyższego poziomu na stosie.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Pobieranie właściwości pamięci podręcznej  
 Można pobrać zbuforowane właściwości elementu za pomocą następujących metod i właściwości.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Wyjątek jest zgłaszany, jeśli żądana właściwość nie znajduje się w pamięci podręcznej.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, podobnie jak <xref:System.Windows.Automation.AutomationElement.Current%2A> , uwidacznia poszczególne właściwości jako elementy członkowskie struktury. Nie trzeba jednak pobierać tej struktury; dostęp do poszczególnych właściwości można uzyskać bezpośrednio. Na przykład <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> Właściwość można uzyskać z `element.Cached.Name` , gdzie `element` jest <xref:System.Windows.Automation.AutomationElement> .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Pobieranie wzorców formantów w pamięci podręcznej  
 Można pobrać zbuforowane Wzorce formantów elementu przy użyciu poniższych metod.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Jeśli wzorzec nie znajduje się w pamięci podręcznej, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> zgłasza wyjątek i <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> zwraca `false` .  
  
 Można pobrać zbuforowane właściwości wzorca kontrolki za pomocą `Cached` właściwości obiektu wzorca. Możesz również pobrać bieżące wartości za pomocą `Current` właściwości, ale tylko wtedy, gdy <xref:System.Windows.Automation.AutomationElementMode.None> nie została określona podczas <xref:System.Windows.Automation.AutomationElement> pobierania. ( <xref:System.Windows.Automation.AutomationElementMode.Full> jest wartością domyślną i umożliwia dostęp do bieżących wartości).  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Pobieranie buforowanych elementów podrzędnych i elementów nadrzędnych  
 Po pobraniu <xref:System.Windows.Automation.AutomationElement> i przeprowadzeniu buforowania żądania dla elementów podrzędnych tego elementu za pośrednictwem <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości żądania można pobrać elementy podrzędne z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> właściwości elementu, który został pobrany.  
  
 Jeśli <xref:System.Windows.Automation.TreeScope.Element> został uwzględniony w zakresie żądania pamięci podręcznej, element główny żądania jest następnie dostępny z <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> właściwości dowolnego elementu podrzędnego.  
  
> [!NOTE]
> Nie można buforować obiektów nadrzędnych ani elementów nadrzędnych elementu głównego żądania.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Aktualizowanie pamięci podręcznej  
 Pamięć podręczna jest prawidłowa tylko pod warunkiem, że nie ma żadnych zmian w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Aplikacja jest odpowiedzialna za aktualizowanie pamięci podręcznej, zazwyczaj w odpowiedzi na zdarzenia.  
  
 Jeśli zasubskrybujesz zdarzenie <xref:System.Windows.Automation.CacheRequest> , gdy jest aktywny, otrzymujesz <xref:System.Windows.Automation.AutomationElement> zaktualizowaną pamięć podręczną jako źródło zdarzenia za każdym razem, gdy obiekt delegowany obsługi zdarzeń jest wywoływany. Możesz również zaktualizować informacje w pamięci podręcznej dla elementu przez wywołanie <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A> . Można przekazać oryginalny, <xref:System.Windows.Automation.CacheRequest> Aby zaktualizować wszystkie informacje, które były wcześniej buforowane.  
  
 Aktualizacja pamięci podręcznej nie zmienia właściwości żadnych istniejących <xref:System.Windows.Automation.AutomationElement> odwołań.  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Przykład FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
