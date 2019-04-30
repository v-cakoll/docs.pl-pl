---
title: Tworzenie działań przepływu pracy przy użyciu klasy działań
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 1bec10b6ae9fb43319cfb6acbf59133e1acca09c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755509"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="5b26c-102">Tworzenie działań przepływu pracy przy użyciu klasy działań</span><span class="sxs-lookup"><span data-stu-id="5b26c-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="5b26c-103">Najprostszy sposób tworzenia działania przy użyciu Windows Workflow Foundation (WF) w [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] polega na utworzeniu klasy, która dziedziczy <xref:System.Activities.Activity> tworząca funkcji przez łączenie niestandardowych działań lub czynności z [wbudowane Biblioteka działań](net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="5b26c-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="5b26c-104">W tym temacie pokazano, jak utworzyć działanie, które zapisuje dwa komunikaty do konsoli.</span><span class="sxs-lookup"><span data-stu-id="5b26c-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="5b26c-105">Aby utworzyć niestandardowe działanie za pomocą projektanta działań</span><span class="sxs-lookup"><span data-stu-id="5b26c-105">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="5b26c-106">Open Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5b26c-106">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="5b26c-107">Wybierz plik, nowy, projektu.</span><span class="sxs-lookup"><span data-stu-id="5b26c-107">Select File, New, Project.</span></span> <span data-ttu-id="5b26c-108">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="5b26c-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="5b26c-109">Wybierz **Biblioteka działań** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="5b26c-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="5b26c-110">Nazwa nowego projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="5b26c-110">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="5b26c-111">Otwórz nowe działanie.</span><span class="sxs-lookup"><span data-stu-id="5b26c-111">Open the new activity.</span></span>  <span data-ttu-id="5b26c-112">Przeciągnij <xref:System.Activities.Statements.Sequence> działania z przybornika na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="5b26c-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="5b26c-113">Przeciągnij <xref:System.Activities.Statements.WriteLine> działanie do <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="5b26c-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="5b26c-114">Wprowadź `"Hello World"` (z cudzysłowami) do **tekstu** pola.</span><span class="sxs-lookup"><span data-stu-id="5b26c-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="5b26c-115">Przeciągnij sekundy <xref:System.Activities.Statements.WriteLine> działanie do <xref:System.Activities.Statements.Sequence> działania poniżej pierwszy z nich.</span><span class="sxs-lookup"><span data-stu-id="5b26c-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="5b26c-116">Wprowadź `"Goodbye"` (z cudzysłowami) do **tekstu** pola.</span><span class="sxs-lookup"><span data-stu-id="5b26c-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
