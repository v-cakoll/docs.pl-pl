---
title: "Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 39275c38e4a7d28248b46f1116990c5bbe21a15f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="subscribe-to-ui-automation-events"></a>Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób subskrybowania zdarzenia generowane przez dostawców automatyzacji interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu rejestruje program obsługi zdarzeń dla zdarzenia, które jest wywoływane, gdy formant takie jak przycisk jest wywoływany i usuwa go podczas zamykania aplikacji. Zdarzenie jest identyfikowane przez <xref:System.Windows.Automation.AutomationEvent> przekazany jako parametr <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] subskrybować zdarzenie jest zgłaszane, gdy fokus się zmieni. Program obsługi zdarzeń jest wyrejestrowany w metodzie, który można wywołać podczas zamykania aplikacji lub gdy powiadomienia o zdarzeniach interfejsu użytkownika nie jest już wymagane.  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>  
 [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
