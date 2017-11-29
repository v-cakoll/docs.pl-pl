---
title: "Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
caps.latest.revision: "9"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: a1eaed2a7876c6e6981e7cc4172442b19800586b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-threading-issues"></a>Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ze względu na sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] używa komunikatów systemu Windows, konflikty może wystąpić, gdy aplikacja kliencka próbuje interakcji z własną [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Te konflikty może prowadzić do bardzo niską wydajność lub nawet spowodować, że aplikacja przestanie odpowiadać.  
  
 Jeśli aplikacja kliencka jest przeznaczony do interakcji z wszystkich elementów na pulpicie, łącznie z własną [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], należy się upewnić, wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w oddzielnym wątku. Dotyczy to również lokalizowanie elementów (na przykład za pomocą <xref:System.Windows.Automation.TreeWalker> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> — metoda) i przy użyciu wzorców formantu.  
  
 Bezpiecznie dokonanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] program obsługi zdarzeń, ponieważ program obsługi zdarzeń jest zawsze wywoływane dla innej[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Jednak gdy subskrybowanie zdarzeń, które mogą pochodzić od aplikacji klienta [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], należy wywołać <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, lub powiązanej metody, na innej[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Usuń obsługę zdarzeń w tym samym wątku.
