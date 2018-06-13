---
title: Pobierz właściwości elementu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 73678433692f5532f712f0d2c7a3c5bf138a87b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405580"
---
# <a name="get-ui-automation-element-properties"></a>Pobierz właściwości elementu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie pokazano, jak można pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.  
  
### <a name="get-a-current-property-value"></a>Pobierz bieżącą wartość właściwości  
  
1.  Uzyskaj <xref:System.Windows.Automation.AutomationElement> właściwości, których chcesz uzyskać.  
  
2.  Wywołanie <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, lub pobrać <xref:System.Windows.Automation.AutomationElement.Current%2A> strukturę właściwości i get wartość jednego z jego elementów członkowskich.  
  
### <a name="get-a-cached-property-value"></a>Pobieranie wartości właściwości pamięci podręcznej  
  
1.  Uzyskaj <xref:System.Windows.Automation.AutomationElement> właściwości, których chcesz uzyskać. Właściwość muszą podano w <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Wywołanie <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, lub pobrać <xref:System.Windows.Automation.AutomationElement.Cached%2A> strukturę właściwości i get wartość jednego z jego elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
