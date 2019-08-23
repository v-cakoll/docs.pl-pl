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
ms.openlocfilehash: 38c7742f3e4691f29490e73b05616754415eac58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953904"
---
# <a name="use-caching-in-ui-automation"></a>Używanie buforowania w automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tej sekcji pokazano, jak zaimplementować buforowanie <xref:System.Windows.Automation.AutomationElement> właściwości i wzorców kontrolek.  
  
### <a name="activate-a-cache-request"></a>Aktywuj żądanie pamięci podręcznej  
  
1. Utwórz <xref:System.Windows.Automation.CacheRequest>.  
  
2. Określ właściwości i wzorce do buforowania przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>programu.  
  
3. Określ zakres buforowania przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości.  
  
4. Określ widok poddrzewa przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> właściwości.  
  
5. Ustaw właściwość na <xref:System.Windows.Automation.AutomationElementMode.None> , jeśli chcesz zwiększyć wydajność, nie pobierając pełnych odwołań do obiektów. <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> (Spowoduje to niemożliwe pobranie bieżących wartości z tych obiektów).  
  
6. Aktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku (`Using` w programie Microsoft Visual Basic .NET).  
  
 Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub zasubskrybowaniu zdarzeń, Dezaktywuj żądanie przy <xref:System.Windows.Automation.CacheRequest.Pop%2A> użyciu ( <xref:System.Windows.Automation.CacheRequest.Push%2A> jeśli zostało użyte) lub przez odtworzenie obiektu utworzonego <xref:System.Windows.Automation.CacheRequest.Activate%2A>przez. (Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` w bloku (`Using` w programie Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Właściwości automatyzacji  
  
1. <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.CacheRequest> Gdy jest aktywny, należy uzyskać <xref:System.Windows.Automation.AutomationElement> obiekty za pomocą lub; albo uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane, gdy był aktywny. <xref:System.Windows.Automation.CacheRequest> (Możesz również utworzyć pamięć podręczną, przechodząc <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej <xref:System.Windows.Automation.TreeWalker> z metod).  
  
2. Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz Właściwość <xref:System.Windows.Automation.AutomationElement.Cached%2A> z właściwości <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Uzyskiwanie buforowanych wzorców i ich właściwości  
  
1. <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.CacheRequest> Gdy jest aktywny, należy uzyskać <xref:System.Windows.Automation.AutomationElement> obiekty za pomocą lub; albo uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, które zostało zarejestrowane, gdy był aktywny. <xref:System.Windows.Automation.CacheRequest> (Możesz również utworzyć pamięć podręczną, przechodząc <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache lub jednej <xref:System.Windows.Automation.TreeWalker> z metod).  
  
2. Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub<xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> , aby pobrać buforowany wzorzec.  
  
3. Pobiera wartości właściwości z `Cached` właściwości wzorca kontrolki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu narzędzia <xref:System.Windows.Automation.CacheRequest.Activate%2A> do <xref:System.Windows.Automation.CacheRequest>aktywacji.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia różne aspekty buforowania przy użyciu narzędzia <xref:System.Windows.Automation.CacheRequest.Push%2A> do <xref:System.Windows.Automation.CacheRequest>aktywacji. W przypadku zamiaru zagnieżdżenia żądań pamięci podręcznej najlepiej jest używać <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
