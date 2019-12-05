---
title: Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 8dc21a680a19933e9db8d52a0e6b7e6ffdd333f8
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800828"
---
# <a name="ui-automation-threading-issues"></a>Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ze względu na sposób, w jaki [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] korzysta z komunikatów systemu Windows, konflikty mogą wystąpić, gdy aplikacja kliencka próbuje współdziałać z własnym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w wątku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Te konflikty mogą prowadzić do bardzo wolnej wydajności lub nawet spowodować, że aplikacja przestanie odpowiadać.  
  
 Jeśli aplikacja kliencka jest przeznaczona do współdziałania z wszystkimi elementami na pulpicie, w tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], należy wykonać wszystkie wywołania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w oddzielnym wątku. Obejmuje to lokalizowanie elementów (na przykład przy użyciu <xref:System.Windows.Automation.TreeWalker> lub metody <xref:System.Windows.Automation.AutomationElement.FindAll%2A>) i używanie wzorców kontrolek.  
  
 Wykonywanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołań w ramach programu obsługi zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jest bezpieczne, ponieważ program obsługi zdarzeń jest zawsze wywoływany w wątku nie[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Jednak podczas subskrybowania zdarzeń, które mogą pochodzić z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]aplikacji klienckiej, należy wykonać wywołanie <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>lub powiązanej metody w wątku nie[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Usuń programy obsługi zdarzeń w tym samym wątku.
