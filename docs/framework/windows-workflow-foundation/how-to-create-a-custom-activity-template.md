---
title: 'Instrukcje: Tworzenie niestandardowego szablonu działania'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f910d1367c941dbc319421d402cae8f4194872e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715253"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="d8b49-102">Instrukcje: Tworzenie niestandardowego szablonu działania</span><span class="sxs-lookup"><span data-stu-id="d8b49-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="d8b49-103">Niestandardowe szablony działań służą do dostosowywania konfiguracji działań, w tym niestandardowych działań złożonych, dzięki czemu użytkownicy nie muszą tworzyć poszczególnych działań osobno i konfigurować ich właściwości oraz inne ustawienia ręcznie.</span><span class="sxs-lookup"><span data-stu-id="d8b49-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="d8b49-104">Te szablony niestandardowe można udostępnić w **przyborniku** w Projektant przepływu pracy systemu Windows lub z poziomu projektanta, z którego użytkownicy mogą je przeciągać do wstępnie skonfigurowanej powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="d8b49-104">These custom templates can be made available in the **Toolbox** on the Windows Workflow Designer or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> <span data-ttu-id="d8b49-105">Projektant przepływu pracy są dostarczane z dobrymi przykładami takich szablonów: [Projektant szablonów SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) oraz [Projektant szablonów ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) w kategorii [projektantów działań związanych z obsługą wiadomości](/visualstudio/workflow-designer/messaging-activity-designers) .</span><span class="sxs-lookup"><span data-stu-id="d8b49-105">Workflow Designer ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="d8b49-106">W pierwszej procedurze w tym temacie opisano sposób tworzenia niestandardowego szablonu działania dla działania **opóźnienia** i drugiej procedury opisano krótko, jak udostępnić go w Projektant przepływu pracy, aby sprawdzić, czy szablon niestandardowy działa.</span><span class="sxs-lookup"><span data-stu-id="d8b49-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a Workflow Designer to verify that the custom template works.</span></span>

 <span data-ttu-id="d8b49-107">Niestandardowe szablony działań muszą implementować <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="d8b49-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="d8b49-108">Interfejs ma jedną metodę <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A>, za pomocą której można tworzyć i konfigurować wystąpienia działań używane w szablonie.</span><span class="sxs-lookup"><span data-stu-id="d8b49-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="d8b49-109">Aby utworzyć szablon dla działania opóźnionego</span><span class="sxs-lookup"><span data-stu-id="d8b49-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="d8b49-110">Uruchom program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="d8b49-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="d8b49-111">W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="d8b49-112">Zostanie otwarte okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="d8b49-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="d8b49-113">W okienku **typy projektów** wybierz **przepływ pracy** z projektów **wizualnych C#**  lub grup **Visual Basic** w zależności od preferencji językowych.</span><span class="sxs-lookup"><span data-stu-id="d8b49-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="d8b49-114">W okienku **Szablony** wybierz pozycję **Biblioteka działań**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="d8b49-115">W polu **Nazwa** wprowadź `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="d8b49-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="d8b49-116">Zaakceptuj wartości domyślne w polach tekstowych **Lokalizacja** i **Nazwa rozwiązania** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="d8b49-117">Kliknij prawym przyciskiem myszy katalog odwołania projektu DelayActivityTemplate w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="d8b49-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="d8b49-118">Przejdź do karty **.NET** i wybierz pozycję **platformie docelowej** w kolumnie **Nazwa składnika** po lewej stronie, a następnie kliknij przycisk **OK** , aby dodać odwołanie do pliku platformie docelowej. dll.</span><span class="sxs-lookup"><span data-stu-id="d8b49-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="d8b49-119">Powtórz tę procedurę, aby dodać odwołania do plików system. Activities. Presentation. dll i 'Windowsbase. dll.</span><span class="sxs-lookup"><span data-stu-id="d8b49-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="d8b49-120">Kliknij prawym przyciskiem myszy projekt DelayActivityTemplate w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** , a następnie pozycję **nowy element** , aby otworzyć okno dialogowe **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="d8b49-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="d8b49-121">Wybierz szablon **klasy** , nadaj mu nazwę MyDelayTemplate, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="d8b49-122">Otwórz plik MyDelayTemplate.cs i Dodaj następujące instrukcje.</span><span class="sxs-lookup"><span data-stu-id="d8b49-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="d8b49-123">Zaimplementuj <xref:System.Activities.Presentation.IActivityTemplateFactory> z klasą `MyDelayActivity` z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="d8b49-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="d8b49-124">Spowoduje to skonfigurowanie opóźnienia o długości 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="d8b49-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="d8b49-125">Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** , aby wygenerować plik DelayActivityTemplate. dll.</span><span class="sxs-lookup"><span data-stu-id="d8b49-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="d8b49-126">Aby udostępnić szablon w Projektant przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d8b49-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="d8b49-127">Kliknij prawym przyciskiem myszy rozwiązanie DelayActivityTemplate w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** , a następnie **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="d8b49-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="d8b49-128">Wybierz szablon **aplikacja konsoli przepływu pracy** , nadaj mu nazwę `CustomActivityTemplateApp`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="d8b49-129">Kliknij prawym przyciskiem myszy katalog odwołania projektu CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="d8b49-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="d8b49-130">Przejdź do karty **projekty** i wybierz pozycję **DelayActivityTemplate** z kolumny **Nazwa projektu** po lewej stronie, a następnie kliknij przycisk **OK** , aby dodać odwołanie do pliku DelayActivityTemplate. dll, który został utworzony w pierwszej procedurze.</span><span class="sxs-lookup"><span data-stu-id="d8b49-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="d8b49-131">Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz polecenie **Kompiluj** , aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8b49-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="d8b49-132">Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="d8b49-133">Wybierz opcję **Uruchom bez debugowania** z menu **Debuguj** i naciśnij dowolny klawisz, aby kontynuować po wyświetleniu monitu z okna cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="d8b49-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="d8b49-134">Otwórz plik Workflow1. XAML i Otwórz **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="d8b49-135">Znajdź szablon " **Opóźnij** " w kategorii **DelayActivityTemplate** .</span><span class="sxs-lookup"><span data-stu-id="d8b49-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="d8b49-136">Przeciągnij go na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="d8b49-136">Drag it onto the design surface.</span></span> <span data-ttu-id="d8b49-137">Upewnij się, że w oknie **Właściwości** ustawiono właściwość `Duration` na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="d8b49-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="d8b49-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8b49-138">Example</span></span>
 <span data-ttu-id="d8b49-139">Plik MyDelayActivity.cs powinien zawierać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="d8b49-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d8b49-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8b49-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="d8b49-141">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d8b49-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
