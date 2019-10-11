---
title: Zadanie 1. Tworzenie nowej aplikacji Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031897"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="6dff8-102">Zadanie 1. Tworzenie nowej aplikacji Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="6dff8-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="6dff8-103">W tym zadaniu utworzysz pustą aplikację Windows Presentation Foundation (WPF) za pomocą szablonu aplikacji WPF programu Visual Studio i dodasz odwołania do odpowiednich zestawów przepływów pracy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6dff8-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="6dff8-104">Aby utworzyć projekt aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="6dff8-104">To create the WPF Application project</span></span>

1. <span data-ttu-id="6dff8-105">Otwórz program Visual Studio i w menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="6dff8-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="6dff8-106">W oknie dialogowym **Nowy projekt** wybierz pozycję **Wizualizacja C#**  lub **Visual Basic** w okienku **zainstalowane szablony** po lewej stronie pola.</span><span class="sxs-lookup"><span data-stu-id="6dff8-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="6dff8-107">Jeśli wybrany język nie jest wyświetlany, zapoznaj się z **innymi językami**.</span><span class="sxs-lookup"><span data-stu-id="6dff8-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="6dff8-108">W okienku **zainstalowane szablony** wybierz pozycję **Windows** .</span><span class="sxs-lookup"><span data-stu-id="6dff8-108">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="6dff8-109">W górnym okienku upewnij się, że (wartość domyślna) **.NET Framework 4** została wybrana w polu listy rozwijanej, a następnie wybierz pozycję **Aplikacja WPF**.</span><span class="sxs-lookup"><span data-stu-id="6dff8-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="6dff8-110">Ustaw nazwę projektu na **HostingApplication** w dolnej części okna.</span><span class="sxs-lookup"><span data-stu-id="6dff8-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="6dff8-111">Ustaw nazwę rozwiązania na **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="6dff8-111">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="6dff8-112">Kliknij przycisk **OK** , aby utworzyć projekt aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dff8-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="6dff8-113">Program Visual Studio tworzy podstawowy interfejs użytkownika WPF dla aplikacji i zawiera odpowiednie pliki XAML i powiązane z kodem.</span><span class="sxs-lookup"><span data-stu-id="6dff8-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="6dff8-114">Dodaj odwołania do zestawów **WorkflowModel** .</span><span class="sxs-lookup"><span data-stu-id="6dff8-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="6dff8-115">W tym celu w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **HostingApplication** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="6dff8-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="6dff8-116">W oknie dialogowym **Dodaj odwołanie** kliknij kartę **.NET** , przytrzymaj wciśnięty klawisz CTRL, wybierz następujące zestawy, a następnie kliknij przycisk **OK**:</span><span class="sxs-lookup"><span data-stu-id="6dff8-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="6dff8-117">System. Activities</span><span class="sxs-lookup"><span data-stu-id="6dff8-117">System.Activities</span></span>
    - <span data-ttu-id="6dff8-118">System. Activities. Presentation</span><span class="sxs-lookup"><span data-stu-id="6dff8-118">System.Activities.Presentation</span></span>
    - <span data-ttu-id="6dff8-119">System. Activities. Core. Presentation</span><span class="sxs-lookup"><span data-stu-id="6dff8-119">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="6dff8-120">Zobacz [zadanie 2: hostowanie Projektant przepływu pracy,](task-2-host-the-workflow-designer.md) aby dowiedzieć się, jak hostować kanwę projektu projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6dff8-120">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="6dff8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dff8-121">See also</span></span>

- [<span data-ttu-id="6dff8-122">Hostowanie Projektant przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6dff8-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="6dff8-123">Zadanie 2. hostowanie Projektant przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6dff8-123">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
