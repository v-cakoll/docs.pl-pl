---
title: 'Zadanie 1: Tworzenie nowej aplikacji systemu Windows Presentation Foundation'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bfebf11d66ded668d7c0892d11adde76e0a42c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="d7709-102">Zadanie 1: Tworzenie nowej aplikacji systemu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d7709-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="d7709-103">W tym zadaniu zostanie utworzona pusta [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] aplikacji przy użyciu szablonu z programu Visual Studio aplikacji WPF i dodać odwołanie do odpowiedniego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zestawy przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d7709-103">In this task, you will create an empty [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="d7709-104">Aby utworzyć projekt aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="d7709-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="d7709-105">Otwórz [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] i na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d7709-105">Open [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d7709-106">W **nowy projekt** oknie dialogowym wybierz **Visual C#** lub **Visual Basic** z **zainstalowane szablony** w okienku po lewej stronie pole.</span><span class="sxs-lookup"><span data-stu-id="d7709-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="d7709-107">Jeśli nie ma preferowanego języka, sprawdź w obszarze **inne języki**.</span><span class="sxs-lookup"><span data-stu-id="d7709-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="d7709-108">Wybierz **Windows** w **zainstalowane szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="d7709-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="d7709-109">W górnym okienku, upewnij się, że (wartość domyślna) **.NET Framework 4** zostało wybrane w polu listy rozwijanej, a następnie wybierz **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="d7709-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="d7709-110">Ustaw nazwę projektu, aby **HostingApplication** w dolnej części okna.</span><span class="sxs-lookup"><span data-stu-id="d7709-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="d7709-111">Ustaw nazwę rozwiązania **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="d7709-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="d7709-112">Kliknij przycisk **OK** do utworzenia projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7709-112">Click **OK** to create the application project.</span></span> [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]<span data-ttu-id="d7709-113">tworzy podstawowy interfejs użytkownika WPF aplikacji i zawiera odpowiednią XAML i plików z kodem.</span><span class="sxs-lookup"><span data-stu-id="d7709-113"> creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="d7709-114">Dodaj odwołania do **WorkflowModel** zestawów.</span><span class="sxs-lookup"><span data-stu-id="d7709-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="d7709-115">Aby to zrobić, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HostingApplication** projekt i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d7709-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="d7709-116">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** , naciśnij i przytrzymaj klawisz CTRL, wybierz następujące zestawy, a następnie kliknij **OK**:</span><span class="sxs-lookup"><span data-stu-id="d7709-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="d7709-117">Elementu System.Activities</span><span class="sxs-lookup"><span data-stu-id="d7709-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="d7709-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="d7709-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="d7709-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="d7709-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="d7709-120">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7709-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="d7709-121">Zobacz [zadanie 2: Host projektanta przepływów pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) informacje na temat hosta kanwy projektanta projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d7709-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7709-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7709-122">See Also</span></span>  
 [<span data-ttu-id="d7709-123">Rehosting projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="d7709-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="d7709-124">Zadanie 2: Host projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="d7709-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
