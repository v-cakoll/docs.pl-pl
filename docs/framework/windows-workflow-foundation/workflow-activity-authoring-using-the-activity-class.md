---
title: Przy użyciu klasy Activity tworzenia działania przepływu pracy
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 040fe777e332efdfb296e6fb6565935f466ded71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Przy użyciu klasy Activity tworzenia działania przepływu pracy
Najprostszym sposobem Utwórz działanie przy użyciu systemu Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] polega na utworzeniu klasy, która dziedziczy <xref:System.Activities.Activity> tworzącą funkcji przez łączenie niestandardowe działania lub działania z [wbudowane Biblioteka działań](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). W tym temacie przedstawiono sposób tworzenia działania, która zapisuje dwa komunikaty do konsoli.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Aby utworzyć niestandardowe działanie przy użyciu narzędzia Projektant działań  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Wybierz plik, nowe, projektu. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Biblioteka działań** w **szablony** okna. Nazwa nowego projektu HelloActivity.  
  
3.  Otwórz nowe działanie.  Przeciągnij <xref:System.Activities.Statements.Sequence> działania z przybornika na powierzchnię projektanta.  
  
4.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działania do <xref:System.Activities.Statements.Sequence> działania. Wprowadź `"Hello World"` (z cudzysłowami) do **tekst** pola.  
  
5.  Przeciągnij drugi <xref:System.Activities.Statements.WriteLine> działania do <xref:System.Activities.Statements.Sequence> działania poniżej pierwsza z nich. Wprowadź `"Goodbye"` (z cudzysłowami) do **tekst** pola.
