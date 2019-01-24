---
title: 'Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 39cd901c0129124bece8e8d3a573fd45209cfb00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679412"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="f5c67-102">Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="f5c67-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="f5c67-103">W tym zadaniu utworzysz pustą aplikację Windows Presentation Foundation (WPF) za pomocą szablonu programu Visual Studio w aplikacji WPF i dodać odwołania do odpowiednich [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zestawy przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f5c67-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="f5c67-104">Aby utworzyć projekt aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="f5c67-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="f5c67-105">Otwórz program Visual Studio i **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f5c67-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f5c67-106">W **nowy projekt** okna dialogowego wybierz opcję **Visual C#**  lub **języka Visual Basic** z **zainstalowane szablony** w okienku po lewej stronie strony pola.</span><span class="sxs-lookup"><span data-stu-id="f5c67-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="f5c67-107">Jeśli nie ma preferowanego języka, sprawdź w obszarze **inne języki**.</span><span class="sxs-lookup"><span data-stu-id="f5c67-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="f5c67-108">Wybierz **Windows** w **zainstalowane szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="f5c67-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="f5c67-109">W górnym okienku upewnij się, że (wartość domyślna) **.NET Framework 4** zostało wybrane w polu listy rozwijanej, a następnie wybierz **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="f5c67-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="f5c67-110">Ustaw nazwę projektu, aby **HostingApplication** w dolnej części okna.</span><span class="sxs-lookup"><span data-stu-id="f5c67-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="f5c67-111">Ustaw nazwę rozwiązania na **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="f5c67-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="f5c67-112">Kliknij przycisk **OK** utworzenie projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5c67-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="f5c67-113">Visual Studio tworzy podstawowe WPF UI dla aplikacji i obejmuje odpowiednie XAML i plikami CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="f5c67-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="f5c67-114">Dodaj odwołania do **WorkflowModel** zestawów.</span><span class="sxs-lookup"><span data-stu-id="f5c67-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="f5c67-115">Aby to zrobić, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HostingApplication** projektu, a następnie wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f5c67-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="f5c67-116">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** kartę, naciśnij i przytrzymaj klawisz CTRL, wybierz następujące zestawy, a następnie kliknij **OK**:</span><span class="sxs-lookup"><span data-stu-id="f5c67-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="f5c67-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="f5c67-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="f5c67-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="f5c67-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="f5c67-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="f5c67-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="f5c67-120">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5c67-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f5c67-121">Zobacz [zadanie 2: Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) Aby dowiedzieć się, jak hostować na kanwie projektanta projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f5c67-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c67-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5c67-122">See also</span></span>
- [<span data-ttu-id="f5c67-123">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f5c67-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)
- [<span data-ttu-id="f5c67-124">Zadanie 2. Hostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f5c67-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
