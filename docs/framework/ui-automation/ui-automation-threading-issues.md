---
title: Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: f4820d2db6275e3c1ae9b55754b8cb6fec6fcc56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954064"
---
# <a name="ui-automation-threading-issues"></a>Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ze względu na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sposób korzystania z komunikatów systemu Windows, konflikty mogą wystąpić, gdy aplikacja kliencka próbuje współdziałać z własnym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątkiem. Te konflikty mogą prowadzić do bardzo wolnej wydajności lub nawet spowodować, że aplikacja przestanie odpowiadać.  
  
 Jeśli aplikacja kliencka jest przeznaczona do współdziałania ze wszystkimi elementami na pulpicie, łącznie z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]własnym, należy wykonać wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołania w osobnym wątku. Obejmuje to lokalizowanie elementów (na przykład za pomocą <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metody lub metod) i używanie wzorców kontrolek.  
  
 Wykonywanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wywołań[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w ramach programu obsługi zdarzeń jest bezpieczne, ponieważ program obsługi zdarzeń jest zawsze wywoływany w przypadku braku wątku. Jednak podczas subskrybowania zdarzeń, które mogą pochodzić z aplikacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]klienckiej, należy wykonać <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>wywołanie metody lub metodę powiązaną w przypadku braku[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Usuń programy obsługi zdarzeń w tym samym wątku.
