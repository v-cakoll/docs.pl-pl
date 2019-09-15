---
title: 'Instrukcje: Tworzenie niestandardowego szablonu działań'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 4ec84658dbe3039a4d7d714f8da183e6a5eb6ca4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989712"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="a7f45-102">Instrukcje: Tworzenie niestandardowego szablonu działań</span><span class="sxs-lookup"><span data-stu-id="a7f45-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="a7f45-103">Niestandardowe szablony działań służą do dostosowywania konfiguracji działań, w tym niestandardowych działań złożonych, dzięki czemu użytkownicy nie muszą tworzyć poszczególnych działań osobno i konfigurować ich właściwości oraz inne ustawienia ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a7f45-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="a7f45-104">Te szablony niestandardowe można udostępnić w **przyborniku** w [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] programie lub z poziomu projektanta, z którego użytkownicy mogą przeciągać je na wstępnie skonfigurowaną powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="a7f45-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="a7f45-105">są dostarczane z dobrymi przykładami takich szablonów: [Projektant szablonów SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) oraz [Projektant szablonów ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) w kategorii [Projektant działań związanych z obsługą wiadomości](/visualstudio/workflow-designer/messaging-activity-designers) .</span><span class="sxs-lookup"><span data-stu-id="a7f45-105">ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="a7f45-106">W pierwszej procedurze w tym temacie opisano sposób tworzenia niestandardowego szablonu działania dla działania **opóźnienia** i drugiej procedury opisano krótko, jak udostępnić go w programie, [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] aby sprawdzić, czy szablon niestandardowy działa.</span><span class="sxs-lookup"><span data-stu-id="a7f45-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>

 <span data-ttu-id="a7f45-107">Niestandardowe szablony działań muszą implementować <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="a7f45-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="a7f45-108">Interfejs ma pojedynczą <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodę, za pomocą której można tworzyć i konfigurować wystąpienia działań używane w szablonie.</span><span class="sxs-lookup"><span data-stu-id="a7f45-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="a7f45-109">Aby utworzyć szablon dla działania opóźnionego</span><span class="sxs-lookup"><span data-stu-id="a7f45-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="a7f45-110">Uruchom program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="a7f45-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="a7f45-111">W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="a7f45-112">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a7f45-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="a7f45-113">W okienku **typy projektów** wybierz **przepływ pracy** z projektów **wizualnych C#**  lub grup **Visual Basic** w zależności od preferencji językowych.</span><span class="sxs-lookup"><span data-stu-id="a7f45-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="a7f45-114">W okienku **Szablony** wybierz pozycję **Biblioteka działań**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="a7f45-115">W polu **Nazwa** wprowadź `DelayActivityTemplate`wartość.</span><span class="sxs-lookup"><span data-stu-id="a7f45-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="a7f45-116">Zaakceptuj wartości domyślne w polach tekstowych **Lokalizacja** i **Nazwa rozwiązania** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="a7f45-117">Kliknij prawym przyciskiem myszy katalog odwołania projektu DelayActivityTemplate w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="a7f45-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="a7f45-118">Przejdź do karty **.NET** i wybierz pozycję **platformie docelowej** w kolumnie **Nazwa składnika** po lewej stronie, a następnie kliknij przycisk **OK** , aby dodać odwołanie do pliku platformie docelowej. dll.</span><span class="sxs-lookup"><span data-stu-id="a7f45-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="a7f45-119">Powtórz tę procedurę, aby dodać odwołania do plików system. Activities. Presentation. dll i 'Windowsbase. dll.</span><span class="sxs-lookup"><span data-stu-id="a7f45-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="a7f45-120">Kliknij prawym przyciskiem myszy projekt DelayActivityTemplate w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** , a następnie pozycję **nowy element** , aby otworzyć okno dialogowe **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="a7f45-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="a7f45-121">Wybierz szablon **klasy** , nadaj mu nazwę MyDelayTemplate, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="a7f45-122">Otwórz plik MyDelayTemplate.cs i Dodaj następujące instrukcje.</span><span class="sxs-lookup"><span data-stu-id="a7f45-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="a7f45-123">Zaimplementuj <xref:System.Activities.Presentation.IActivityTemplateFactory> `MyDelayActivity` z klasą przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="a7f45-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="a7f45-124">Spowoduje to skonfigurowanie opóźnienia o długości 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="a7f45-124">This configures the delay to have a duration of 10 seconds.</span></span>

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

14. <span data-ttu-id="a7f45-125">Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** , aby wygenerować plik DelayActivityTemplate. dll.</span><span class="sxs-lookup"><span data-stu-id="a7f45-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="a7f45-126">Aby udostępnić szablon w Projektant przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a7f45-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="a7f45-127">Kliknij prawym przyciskiem myszy rozwiązanie DelayActivityTemplate w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** , a następnie **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="a7f45-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="a7f45-128">Wybierz szablon **aplikacja konsoli przepływu pracy** , nadaj mu `CustomActivityTemplateApp`nazwę, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="a7f45-129">Kliknij prawym przyciskiem myszy katalog odwołania projektu CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="a7f45-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="a7f45-130">Przejdź do karty **projekty** i wybierz pozycję **DelayActivityTemplate** z kolumny **Nazwa projektu** po lewej stronie, a następnie kliknij przycisk **OK** , aby dodać odwołanie do pliku DelayActivityTemplate. dll, który został utworzony w pierwszej procedurze.</span><span class="sxs-lookup"><span data-stu-id="a7f45-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="a7f45-131">Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz polecenie **Kompiluj** , aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7f45-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="a7f45-132">Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="a7f45-133">Wybierz opcję **Uruchom bez debugowania** z menu **Debuguj** i naciśnij dowolny klawisz, aby kontynuować po wyświetleniu monitu z okna cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="a7f45-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="a7f45-134">Otwórz plik Workflow1. XAML i Otwórz **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="a7f45-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="a7f45-135">Znajdź szablon " **Opóźnij** " w kategorii **DelayActivityTemplate** .</span><span class="sxs-lookup"><span data-stu-id="a7f45-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="a7f45-136">Przeciągnij go na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="a7f45-136">Drag it onto the design surface.</span></span> <span data-ttu-id="a7f45-137">Upewnij się, że `Duration` w oknie właściwości ustawiono wartość 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="a7f45-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="a7f45-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7f45-138">Example</span></span>
 <span data-ttu-id="a7f45-139">Plik MyDelayActivity.cs powinien zawierać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a7f45-139">The MyDelayActivity.cs file should contain the following code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a7f45-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7f45-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="a7f45-141">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a7f45-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
