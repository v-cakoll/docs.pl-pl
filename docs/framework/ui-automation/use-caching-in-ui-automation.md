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
ms.openlocfilehash: b63d94789d081ce7337b5f9c2abca3f7d9e99eeb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308669"
---
# <a name="use-caching-in-ui-automation"></a>Używanie buforowania w automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tej sekcji przedstawiono sposób implementacji buforowania <xref:System.Windows.Automation.AutomationElement> wzorców właściwości i kontroli.  
  
### <a name="activate-a-cache-request"></a>Aktywuj żądanie pamięci podręcznej  
  
1. Utwórz <xref:System.Windows.Automation.CacheRequest>.  
  
2. Określ właściwości i wzorców do pamięci podręcznej przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3. Określanie zakresu buforowania, ustawiając <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości.  
  
4. Określ widoku poddrzewo, ustawiając <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> właściwości.  
  
5. Ustaw <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> właściwość <xref:System.Windows.Automation.AutomationElementMode.None> Jeśli chcesz zwiększyć wydajność przez nie będą pobierane pełną dokumentację do obiektów. (Umożliwi to niemożliwe, można pobrać bieżących wartości z tych obiektów.)  
  
6. Aktywuj żądanie przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> w ramach `using` bloku (`Using` w Microsoft Visual Basic .NET).  
  
 Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub jeśli zasubskrybujesz zdarzenia, dezaktywowanie żądania za pomocą <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Jeśli <xref:System.Windows.Automation.CacheRequest.Push%2A> użyto) lub usuwając obiekt utworzony przez <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> w `using` bloku (`Using` w Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Właściwości obiektu AutomationElement pamięci podręcznej  
  
1. Podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny, Uzyskaj <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, który został zarejestrowany, kiedy <xref:System.Windows.Automation.CacheRequest> była aktywna. (Można również tworzyć pamięć podręczną, przekazując <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache lub jednego z <xref:System.Windows.Automation.TreeWalker> metody.)  
  
2. Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub pobrać właściwości z <xref:System.Windows.Automation.AutomationElement.Cached%2A> właściwość <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Uzyskaj wzorce pamięci podręcznej i ich właściwości  
  
1. Podczas <xref:System.Windows.Automation.CacheRequest> jest aktywny, Uzyskaj <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, który został zarejestrowany, kiedy <xref:System.Windows.Automation.CacheRequest> była aktywna. (Można również tworzyć pamięć podręczną, przekazując <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache lub jednego z <xref:System.Windows.Automation.TreeWalker> metody.)  
  
2. Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> można pobrać wzorzec pamięci podręcznej.  
  
3. Do pobierania wartości właściwości z `Cached` właściwości wzorca kontrolki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia różne aspekty buforowania, przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> aktywować <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia różne aspekty buforowania, przy użyciu <xref:System.Windows.Automation.CacheRequest.Push%2A> aktywować <xref:System.Windows.Automation.CacheRequest>. Z wyjątkiem po użytkownik chce zagnieździć żądań pamięci podręcznej, to lepiej jest używać <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
