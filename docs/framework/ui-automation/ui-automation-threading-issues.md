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
# <a name="ui-automation-threading-issues"></a><span data-ttu-id="0099a-102">Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0099a-102">UI Automation Threading Issues</span></span>
> [!NOTE]
>  <span data-ttu-id="0099a-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0099a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0099a-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="0099a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0099a-105">Ze względu na sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] używa komunikatów systemu Windows, konflikty może wystąpić, gdy aplikacja kliencka próbuje interakcji z własną [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku.</span><span class="sxs-lookup"><span data-stu-id="0099a-105">Because of the way [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uses Windows messages, conflicts can occur when a client application attempts to interact with its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] on the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="0099a-106">Te konflikty może prowadzić do bardzo niską wydajność lub nawet spowodować, że aplikacja przestanie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="0099a-106">These conflicts can lead to very slow performance or even cause the application to stop responding.</span></span>  
  
 <span data-ttu-id="0099a-107">Jeśli aplikacja kliencka jest przeznaczony do interakcji z wszystkich elementów na pulpicie, łącznie z własną [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], należy się upewnić, wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="0099a-107">If your client application is intended to interact with all elements on the desktop, including its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you should make all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls on a separate thread.</span></span> <span data-ttu-id="0099a-108">Dotyczy to również lokalizowanie elementów (na przykład za pomocą <xref:System.Windows.Automation.TreeWalker> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> — metoda) i przy użyciu wzorców formantu.</span><span class="sxs-lookup"><span data-stu-id="0099a-108">This includes locating elements (for example, by using <xref:System.Windows.Automation.TreeWalker> or the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method) and using control patterns.</span></span>  
  
 <span data-ttu-id="0099a-109">Bezpiecznie dokonanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] program obsługi zdarzeń, ponieważ program obsługi zdarzeń jest zawsze wywoływane dla innej[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku.</span><span class="sxs-lookup"><span data-stu-id="0099a-109">It is safe to make [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event handler, because the event handler is always called on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="0099a-110">Jednak gdy subskrybowanie zdarzeń, które mogą pochodzić od aplikacji klienta [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], należy wywołać <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, lub powiązanej metody, na innej[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku.</span><span class="sxs-lookup"><span data-stu-id="0099a-110">However, when subscribing to events that may originate from your client application's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you must make the call to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, or a related method, on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="0099a-111">Usuń obsługę zdarzeń w tym samym wątku.</span><span class="sxs-lookup"><span data-stu-id="0099a-111">Remove event handlers on the same thread.</span></span>
