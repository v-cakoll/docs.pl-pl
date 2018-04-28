---
title: 'Porady: rozróżnianie między kliknięciami a dwukrotnymi kliknięciami'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f6f92c225e7b3c745c5cf439c9094d72fa0cde0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a><span data-ttu-id="40cd7-102">Porady: rozróżnianie między kliknięciami a dwukrotnymi kliknięciami</span><span class="sxs-lookup"><span data-stu-id="40cd7-102">How to: Distinguish Between Clicks and Double-Clicks</span></span>
<span data-ttu-id="40cd7-103">Zazwyczaj pojedynczy *kliknij* inicjuje akcji interfejsu użytkownika a *kliknij dwukrotnie* rozszerza akcji.</span><span class="sxs-lookup"><span data-stu-id="40cd7-103">Typically, a single *click* initiates a user interface (UI) action and a *double-click* extends the action.</span></span> <span data-ttu-id="40cd7-104">Na przykład jednego kliknięcia zazwyczaj wybiera element, a następnie dwukrotne Edytuje wybrany element.</span><span class="sxs-lookup"><span data-stu-id="40cd7-104">For example, one click usually selects an item, and a double-click edits the selected item.</span></span> <span data-ttu-id="40cd7-105">Jednak zdarzenia kliknięcia formularze systemu Windows nie łatwo zmiany scenariusz, w którym przez kliknięcie i dwukrotne akcje niezgodne, ponieważ powiązane akcji <xref:System.Windows.Forms.Control.Click> lub <xref:System.Windows.Forms.Control.MouseClick> zdarzeń jest wykonywane przed akcją powiązane <xref:System.Windows.Forms.Control.DoubleClick>lub <xref:System.Windows.Forms.Control.MouseDoubleClick> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="40cd7-105">However, the Windows Forms click events do not easily accommodate a scenario where a click and a double-click perform incompatible actions, because an action tied to the <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> event is performed before the action tied to the <xref:System.Windows.Forms.Control.DoubleClick> or <xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span> <span data-ttu-id="40cd7-106">W tym temacie przedstawiono dwa rozwiązania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="40cd7-106">This topic demonstrates two solutions to this problem.</span></span> <span data-ttu-id="40cd7-107">Rozwiązanie polega na kliknij dwukrotnie zdarzenie i wycofać akcje obsługi zdarzenia kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="40cd7-107">One solution is to handle the double-click event and roll back the actions in the handling of the click event.</span></span> <span data-ttu-id="40cd7-108">W rzadkich przypadkach może być konieczne symulować kliknij i dwukrotnie kliknij zachowanie obsługa <xref:System.Windows.Forms.Control.MouseDown> zdarzeń i za pomocą <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> i <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> właściwości <xref:System.Windows.Forms.SystemInformation> klasy.</span><span class="sxs-lookup"><span data-stu-id="40cd7-108">In rare situations you may need to simulate click and double-click behavior by handling the <xref:System.Windows.Forms.Control.MouseDown> event and by using the <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> and <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> properties of the <xref:System.Windows.Forms.SystemInformation> class.</span></span> <span data-ttu-id="40cd7-109">Pomiar czasu między kliknięciami a jeśli drugie kliknięcie występuje przed wartością <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> osiągnięciu i kliknięcie mieści się w prostokącie zdefiniowane przez <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, wykonania akcji kliknij dwukrotnie; w przeciwnym razie wykonaj akcję kliknij.</span><span class="sxs-lookup"><span data-stu-id="40cd7-109">You measure the time between clicks and if a second click occurs before the value of <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> is reached and the click is within a rectangle defined by <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, perform the double-click action; otherwise, perform the click action.</span></span>  
  
### <a name="to-roll-back-a-click-action"></a><span data-ttu-id="40cd7-110">Aby wycofać akcji kliknij pozycję</span><span class="sxs-lookup"><span data-stu-id="40cd7-110">To roll back a click action</span></span>  
  
-   <span data-ttu-id="40cd7-111">Sprawdź, czy użytkownik pracuje z formantu ma standard kliknij dwukrotnie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="40cd7-111">Ensure that the control you are working with has standard double-click behavior.</span></span> <span data-ttu-id="40cd7-112">Jeśli nie, Włącz kontrolki z <xref:System.Windows.Forms.Control.SetStyle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="40cd7-112">If not, enable the control with the <xref:System.Windows.Forms.Control.SetStyle%2A> method.</span></span> <span data-ttu-id="40cd7-113">Kliknij dwukrotnie zdarzenie i wycofać kliknij akcję, a także akcji kliknij dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="40cd7-113">Handle the double-click event and roll back the click action as well as the double-click action.</span></span> <span data-ttu-id="40cd7-114">Poniższy przykład kodu pokazuje, jak utworzyć niestandardowe przycisk z włączone, a także wycofywaniu akcji kliknij kod obsługi zdarzenia kliknij dwukrotnie kliknij dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="40cd7-114">The following code example demonstrates a how to create a custom button with double-click enabled, as well as how to roll back the click action in the double-click event handling code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a><span data-ttu-id="40cd7-115">Aby odróżnić kliknięć w MouseDown — zdarzenie</span><span class="sxs-lookup"><span data-stu-id="40cd7-115">To distinguish between clicks in the MouseDown event</span></span>  
  
-   <span data-ttu-id="40cd7-116">Obsługa <xref:System.Windows.Forms.Control.MouseDown> zdarzeń i określenie miejsca i czasu span między kliknięciami za pomocą odpowiedniej <xref:System.Windows.Forms.SystemInformation> właściwości i <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="40cd7-116">Handle the <xref:System.Windows.Forms.Control.MouseDown> event and determine the location and time span between clicks using the appropriate <xref:System.Windows.Forms.SystemInformation> properties and a <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="40cd7-117">Wykonaj odpowiednią akcję w zależności od tego, czy odbywa się kliknij lub kliknij dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="40cd7-117">Perform the appropriate action depending on whether a click or double-click takes place.</span></span> <span data-ttu-id="40cd7-118">W poniższym przykładzie kodu pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="40cd7-118">The following code example demonstrates how this can be done.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40cd7-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="40cd7-119">Compiling the Code</span></span>  
 <span data-ttu-id="40cd7-120">Wymagaj te przykłady:</span><span class="sxs-lookup"><span data-stu-id="40cd7-120">These examples require:</span></span>  
  
-   <span data-ttu-id="40cd7-121">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="40cd7-121">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="40cd7-122">Dla informacji o tworzeniu tych przykładów z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="40cd7-122">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="40cd7-123">Wklejając kod w nowych projektach, można także utworzyć tych przykładów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40cd7-123">You can also build these examples in Visual Studio by pasting the code into new projects.</span></span>  <span data-ttu-id="40cd7-124">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="40cd7-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40cd7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40cd7-125">See Also</span></span>  
 [<span data-ttu-id="40cd7-126">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40cd7-126">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
