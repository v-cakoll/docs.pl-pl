---
title: Tworzenie działań przepływu pracy przy użyciu klasy działań
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: abdabc46aa54e19d5a04c5b34d6d2b9be07488d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711866"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Tworzenie działań przepływu pracy przy użyciu klasy działań
Najprostszy sposób tworzenia działania przy użyciu Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] polega na utworzeniu klasy, która dziedziczy <xref:System.Activities.Activity> tworząca funkcji przez łączenie niestandardowych działań lub czynności z [wbudowane Biblioteka działań](net-framework-4-5-built-in-activity-library.md). W tym temacie pokazano, jak utworzyć działanie, które zapisuje dwa komunikaty do konsoli.

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Aby utworzyć niestandardowe działanie za pomocą projektanta działań

1.  Open Visual Studio 2012.

2.  Wybierz plik, nowy, projektu. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Biblioteka działań** w **szablony** okna. Nazwa nowego projektu HelloActivity.

3.  Otwórz nowe działanie.  Przeciągnij <xref:System.Activities.Statements.Sequence> działania z przybornika na powierzchni projektowej.

4.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działanie do <xref:System.Activities.Statements.Sequence> działania. Wprowadź `"Hello World"` (z cudzysłowami) do **tekstu** pola.

5.  Przeciągnij sekundy <xref:System.Activities.Statements.WriteLine> działanie do <xref:System.Activities.Statements.Sequence> działania poniżej pierwszy z nich. Wprowadź `"Goodbye"` (z cudzysłowami) do **tekstu** pola.
