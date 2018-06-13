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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cf01a695de4078df1f59b68742bc19fd4b8b9024
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401333"
---
# <a name="use-caching-in-ui-automation"></a>Używanie buforowania w automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tej sekcji przedstawiono sposób wykonania buforowanie <xref:System.Windows.Automation.AutomationElement> wzorce właściwości i kontroli.  
  
### <a name="activate-a-cache-request"></a>Aktywuj żądania pamięci podręcznej  
  
1.  Utwórz <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Określ właściwości i wzorce do pamięci podręcznej przy użyciu <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3.  Określ zakres buforowania przez ustawienie <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> właściwości.  
  
4.  Określ widok poddrzewo, ustawiając <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> właściwości.  
  
5.  Ustaw <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> właściwości <xref:System.Windows.Automation.AutomationElementMode.None> Jeśli chcesz zwiększyć wydajność nie przywracając pełną odwołania do obiektów. (Będzie go można pobrać bieżących wartości z tych obiektów.)  
  
6.  Aktywuj żądania przy użyciu <xref:System.Windows.Automation.CacheRequest.Activate%2A> w `using` bloku (`Using` w programie Microsoft Visual Basic .NET).  
  
 Po uzyskaniu <xref:System.Windows.Automation.AutomationElement> obiektów lub subskrybowanie zdarzeń, Dezaktywuj żądania przy użyciu <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Jeśli <xref:System.Windows.Automation.CacheRequest.Push%2A> użyto) lub usuwanie obiektu utworzonego przez <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Użyj <xref:System.Windows.Automation.CacheRequest.Activate%2A> w `using` bloku (`Using` w programie Microsoft Visual Basic .NET).  
  
### <a name="cache-automationelement-properties"></a>Właściwości Obiekt AutomationElement pamięci podręcznej  
  
1.  Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskać <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, który został zarejestrowany program <xref:System.Windows.Automation.CacheRequest> był aktywny. (Można również utworzyć pamięci podręcznej przez przekazanie <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache lub jedną z <xref:System.Windows.Automation.TreeWalker> metody.)  
  
2.  Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub pobrać właściwości z <xref:System.Windows.Automation.AutomationElement.Cached%2A> właściwość <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Uzyskaj wzorce pamięci podręcznej i ich właściwości  
  
1.  Gdy <xref:System.Windows.Automation.CacheRequest> jest aktywny, uzyskać <xref:System.Windows.Automation.AutomationElement> obiektów przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; lub uzyskać <xref:System.Windows.Automation.AutomationElement> jako źródło zdarzenia, który został zarejestrowany program <xref:System.Windows.Automation.CacheRequest> był aktywny. (Można również utworzyć pamięci podręcznej przez przekazanie <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache lub jedną z <xref:System.Windows.Automation.TreeWalker> metody.)  
  
2.  Użyj <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> można pobrać wzorzec pamięci podręcznej.  
  
3.  Pobiera się wartości właściwości z `Cached` właściwości wzorca formantu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia różne aspekty buforowania, za pomocą <xref:System.Windows.Automation.CacheRequest.Activate%2A> aktywować <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia różne aspekty buforowania, za pomocą <xref:System.Windows.Automation.CacheRequest.Push%2A> aktywować <xref:System.Windows.Automation.CacheRequest>. Z wyjątkiem, gdy chcesz zagnieździć żądań pamięci podręcznej, zaleca się używania <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Zobacz też  
 [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
