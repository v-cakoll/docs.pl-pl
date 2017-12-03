---
title: "Przy użyciu klasy Activity tworzenia działania przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94433d398f662a96bf046603574ad881128a2081
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Przy użyciu klasy Activity tworzenia działania przepływu pracy
Najprostszym sposobem tworzenia działania przy użyciu [!INCLUDE[wf](../../../includes/wf-md.md)] w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] polega na utworzeniu klasy, która dziedziczy <xref:System.Activities.Activity> tworzącą funkcji przez łączenie niestandardowe działania lub działania z [Biblioteka działań wbudowanych ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). W tym temacie przedstawiono sposób tworzenia działania, która zapisuje dwa komunikaty do konsoli.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Aby utworzyć niestandardowe działanie przy użyciu narzędzia Projektant działań  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Wybierz plik, nowe, projektu. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Biblioteka działań** w **szablony** okna. Nazwa nowego projektu HelloActivity.  
  
3.  Otwórz nowe działanie.  Przeciągnij <xref:System.Activities.Statements.Sequence> działania z przybornika na powierzchnię projektanta.  
  
4.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działania do <xref:System.Activities.Statements.Sequence> działania. Wprowadź `"Hello World"` (z cudzysłowami) do **tekst** pola.  
  
5.  Przeciągnij drugi <xref:System.Activities.Statements.WriteLine> działania do <xref:System.Activities.Statements.Sequence> działania poniżej pierwsza z nich. Wprowadź `"Goodbye"` (z cudzysłowami) do **tekst** pola.
