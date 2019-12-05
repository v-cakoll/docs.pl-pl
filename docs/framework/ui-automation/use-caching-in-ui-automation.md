---
title: Używanie buforowania w automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 679192b611a423e095ee9acc956d247364940edf
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800794"
---
# <a name="use-caching-in-ui-automation"></a>Używanie buforowania w automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tej sekcji pokazano, jak zaimplementować buforowanie właściwości <xref:System.Windows.Automation.AutomationElement> i wzorców kontrolek.  
  
### <a name="activate-a-cache-request"></a>Aktywuj żądanie pamięci podręcznej  
  
1. Utwórz <xref:System.Windows.Automation.CacheRequest>.  
  
2. Określ właściwości i wzorce do buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3. Określ zakres buforowania, ustawiając właściwość <xref:System.Windows.Automation.CacheRequest.TreeScope%2A>.  
  
4. Określ widok poddrzewa, ustawiając właściwość <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A>.  
  
5. Ustaw właściwość <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> na <xref:System.Windows.Automation.AutomationElementMode.None>, jeśli chcesz zwiększyć wydajność, nie pobierając pełnych odwołań do obiektów. (Spowoduje to niemożliwe pobranie bieżących wartości z tych obiektów).  
  
6. Aktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> w bloku `using` (`Using` w programie Microsoft Visual Basic .NET).  
  
 Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub zasubskrybowaniu zdarzeń należy dezaktywować żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Pop%2A> (jeśli <xref:System.Windows.Automation.CacheRequest.Push%2A> była użyta) lub przez pozbywanie obiektu utworzonego przez <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> w bloku `using` (`Using` w Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Właściwości automatyzacji  
  
1. Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskaj <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskaj <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane dla momentu, gdy <xref:System.Windows.Automation.CacheRequest> był aktywny. (Możesz również utworzyć pamięć podręczną, przekazując <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej z metod <xref:System.Windows.Automation.TreeWalker>).  
  
2. Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz właściwość z właściwości <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Uzyskiwanie buforowanych wzorców i ich właściwości  
  
1. Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskaj <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskaj <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane dla momentu, gdy <xref:System.Windows.Automation.CacheRequest> był aktywny. (Możesz również utworzyć pamięć podręczną, przekazując <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej z metod <xref:System.Windows.Automation.TreeWalker>).  
  
2. Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> do pobrania buforowanego wzorca.  
  
3. Pobiera wartości właściwości z właściwości `Cached` wzorca kontrolki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> do uaktywnienia <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Push%2A> do uaktywnienia <xref:System.Windows.Automation.CacheRequest>. W przypadku zamiaru zagnieżdżenia żądań pamięci podręcznej warto używać <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](caching-in-ui-automation-clients.md)
