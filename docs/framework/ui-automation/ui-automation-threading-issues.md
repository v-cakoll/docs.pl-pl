---
title: Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7d8df325d18c3657d4955fa534d29bb7fdbc595c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176584"
---
# <a name="ui-automation-threading-issues"></a>Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ze względu na sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] używa Windows wiadomości, konflikty mogą wystąpić, gdy aplikacja kliencka próbuje korzystać z własnej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Te konflikty mogą prowadzić do bardzo niska wydajność lub nawet spowodować, że aplikacja przestanie odpowiadać.  
  
 Jeśli Twoja aplikacja kliencka jest przeznaczony do interakcji z wszystkich elementów na pulpicie, łącznie z własną [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], należy wprowadzić wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w oddzielnym wątku. Obejmuje to znajdowanie elementów (na przykład za pomocą <xref:System.Windows.Automation.TreeWalker> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metoda) i przy użyciu wzorców kontrolek.  
  
 Jest bezpieczne robić [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] procedura obsługi zdarzeń, ponieważ program obsługi zdarzeń zawsze jest wywoływana w innej niż[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Jednak podczas subskrybowania zdarzenia, które mogą pochodzić od aplikacji klienckiej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], musi wykonać wywołanie do <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, lub powiązanej metody, na innej niż[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Usuń programy obsługi zdarzeń w tym samym wątku.
