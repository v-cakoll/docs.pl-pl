---
title: Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
description: Przeczytaj o problemach z wątkiem automatyzacji interfejsu użytkownika. Na przykład mogą wystąpić konflikty, jeśli aplikacja kliencka próbuje korzystać z własnego interfejsu użytkownika w wątku interfejsu użytkownika.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 290c26981d5eb993e2a9ab387f8d106aafa54efb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924542"
---
# <a name="ui-automation-threading-issues"></a>Problemy wielowątkowości dotyczące automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ze względu na sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] korzystania z komunikatów systemu Windows, konflikty mogą wystąpić, gdy aplikacja kliencka próbuje współdziałać z własnym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątkiem. Te konflikty mogą prowadzić do bardzo wolnej wydajności lub nawet spowodować, że aplikacja przestanie odpowiadać.  
  
 Jeśli aplikacja kliencka jest przeznaczona do współdziałania ze wszystkimi elementami na pulpicie, łącznie z własnym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , należy wykonać wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołania w osobnym wątku. Obejmuje to lokalizowanie elementów (na przykład za pomocą <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metody lub metod) i używanie wzorców kontrolek.  
  
 Wykonywanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołań w ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu obsługi zdarzeń jest bezpieczne, ponieważ program obsługi zdarzeń jest zawsze wywoływany w przypadku braku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Jednak podczas subskrybowania zdarzeń, które mogą pochodzić z aplikacji klienckiej [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , należy wykonać wywołanie <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> metody lub metodę powiązaną w przypadku braku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku. Usuń programy obsługi zdarzeń w tym samym wątku.
