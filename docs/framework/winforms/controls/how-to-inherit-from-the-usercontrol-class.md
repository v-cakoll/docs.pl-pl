---
title: 'Porady: dziedziczenie z klasy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10bb807d012a130ad633b7ce06f99c5abf2cdda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458373"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="b1594-102">Porady: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="b1594-102">How to: Inherit from the UserControl Class</span></span>

<span data-ttu-id="b1594-103">Aby połączyć funkcje co najmniej jednej kontrolki Windows Forms z kodem niestandardowym, można utworzyć *kontrolkę użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="b1594-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="b1594-104">Kontrolki użytkownika łączą programowanie szybkiej kontroli, standardowe funkcje kontroli Windows Forms i uniwersalność niestandardowych właściwości i metod.</span><span class="sxs-lookup"><span data-stu-id="b1594-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="b1594-105">Po rozpoczęciu tworzenia kontrolki użytkownika zostanie wyświetlony widoczny Projektant, na którym można umieścić standardowe kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b1594-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="b1594-106">Te kontrolki zachowują wszystkie funkcje, a także wygląd i zachowanie (wyglądu i działania) standardowych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="b1594-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="b1594-107">Po wbudowaniu tych kontrolek w kontrolce użytkownika nie są one już dostępne za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="b1594-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="b1594-108">Kontrolka użytkownika wykonuje własne malowanie, a także obsługuje wszystkie podstawowe funkcje związane z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="b1594-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="b1594-109">Aby utworzyć kontrolkę użytkownika</span><span class="sxs-lookup"><span data-stu-id="b1594-109">To create a user control</span></span>

1. <span data-ttu-id="b1594-110">Utwórz nowy projekt **biblioteki formantów systemu Windows** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1594-110">Create a new **Windows Control Library** project in Visual Studio.</span></span>

   <span data-ttu-id="b1594-111">Tworzony jest nowy projekt z pustą kontrolką użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1594-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="b1594-112">Przeciągnij kontrolki z karty **Windows Forms** **przybornika** do projektanta.</span><span class="sxs-lookup"><span data-stu-id="b1594-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="b1594-113">Te kontrolki powinny być rozmieszczone i zaprojektowane tak, aby były wyświetlane w końcowej kontrolce użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1594-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="b1594-114">Aby umożliwić deweloperom dostęp do kontrolek składnika, należy zadeklarować je jako publiczne lub selektywnie uwidocznić właściwości kontrolki składnik.</span><span class="sxs-lookup"><span data-stu-id="b1594-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="b1594-115">Aby uzyskać szczegółowe informacje, zobacz [How to: Uwidacznianie właściwości kontrolek składnika](how-to-expose-properties-of-constituent-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b1594-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="b1594-116">Zaimplementuj wszelkie niestandardowe metody lub właściwości, które zostaną dołączone do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b1594-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="b1594-117">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="b1594-117">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="b1594-118">Aby uzyskać więcej informacji, zobacz [jak: testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="b1594-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1594-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1594-119">See also</span></span>

- [<span data-ttu-id="b1594-120">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b1594-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="b1594-121">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="b1594-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="b1594-122">Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1594-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="b1594-123">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1594-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="b1594-124">Rozwiązywanie problemów dziedziczonych programów obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1594-124">Troubleshoot Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="b1594-125">Instrukcje: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="b1594-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
