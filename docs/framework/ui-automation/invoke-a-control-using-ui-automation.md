---
title: "Wywoływanie formantu przy użyciu automatyzacji interfejsu użytkownika"
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
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 097c92bf927f211e35b5c55c0fc73c0810338e02
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="invoke-a-control-using-ui-automation"></a>Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób wykonywania następujących zadań:  
  
-   Odnaleźć formantu, który spełnia warunki określoną właściwość przez krótki formantu widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa dla aplikacji docelowej.  
  
-   Utwórz <xref:System.Windows.Automation.AutomationElement> dla każdego formantu.  
  
-   Uzyskaj <xref:System.Windows.Automation.InvokePattern> obiektu za pomocą dowolnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] znaleziony element, który obsługuje <xref:System.Windows.Automation.InvokePattern> — wzorzec formantu.  
  
-   Użyj <xref:System.Windows.Automation.InvokePattern.Invoke%2A> do wywołania formantu z obsługi zdarzeń klienta.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody <xref:System.Windows.Automation.AutomationElement> klasy do wygenerowania <xref:System.Windows.Automation.InvokePattern> obiektu i wywoływanie formantu przy użyciu <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metody.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy InvokePattern i przykładowego elementu Menu klasy ExpandCollapsePattern](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
