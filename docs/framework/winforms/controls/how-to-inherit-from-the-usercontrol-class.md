---
title: 'Instrukcje: dziedziczenie z klasy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 77233517203989f188a2b3ddf436656bc8da82a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966570"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="162b1-102">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="162b1-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="162b1-103">Aby połączyć funkcje co najmniej jednej kontrolki Windows Forms z kodem niestandardowym, można utworzyć *kontrolkę użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="162b1-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="162b1-104">Kontrolki użytkownika łączą programowanie szybkiej kontroli, standardowe funkcje kontroli Windows Forms i uniwersalność niestandardowych właściwości i metod.</span><span class="sxs-lookup"><span data-stu-id="162b1-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="162b1-105">Po rozpoczęciu tworzenia kontrolki użytkownika zostanie wyświetlony widoczny Projektant, na którym można umieścić standardowe kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="162b1-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="162b1-106">Te kontrolki zachowują wszystkie funkcje, a także wygląd i zachowanie (wyglądu i działania) standardowych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="162b1-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="162b1-107">Po wbudowaniu tych kontrolek w kontrolce użytkownika nie są one już dostępne za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="162b1-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="162b1-108">Kontrolka użytkownika wykonuje własne malowanie, a także obsługuje wszystkie podstawowe funkcje związane z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="162b1-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="162b1-109">Aby utworzyć kontrolkę użytkownika</span><span class="sxs-lookup"><span data-stu-id="162b1-109">To create a user control</span></span>

1. <span data-ttu-id="162b1-110">Utwórz nowy projekt **biblioteki formantów systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="162b1-110">Create a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="162b1-111">Tworzony jest nowy projekt z pustą kontrolką użytkownika.</span><span class="sxs-lookup"><span data-stu-id="162b1-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="162b1-112">Przeciągnij kontrolki z karty **Windows Forms** przybornika do projektanta.</span><span class="sxs-lookup"><span data-stu-id="162b1-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="162b1-113">Te kontrolki powinny być rozmieszczone i zaprojektowane tak, aby były wyświetlane w końcowej kontrolce użytkownika.</span><span class="sxs-lookup"><span data-stu-id="162b1-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="162b1-114">Aby umożliwić deweloperom dostęp do kontrolek składnika, należy zadeklarować je jako publiczne lub selektywnie uwidocznić właściwości kontrolki składnik.</span><span class="sxs-lookup"><span data-stu-id="162b1-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="162b1-115">Aby uzyskać szczegółowe informacje [, zobacz How to: Uwidacznia właściwości kontrolek](how-to-expose-properties-of-constituent-controls.md)składnika.</span><span class="sxs-lookup"><span data-stu-id="162b1-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="162b1-116">Zaimplementuj wszelkie niestandardowe metody lub właściwości, które zostaną dołączone do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="162b1-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="162b1-117">Naciśnij klawisz F5, aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="162b1-117">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="162b1-118">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="162b1-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="162b1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="162b1-119">See also</span></span>

- [<span data-ttu-id="162b1-120">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="162b1-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="162b1-121">Instrukcje: Dziedzicz z klasy kontrolki</span><span class="sxs-lookup"><span data-stu-id="162b1-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="162b1-122">Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="162b1-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="162b1-123">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="162b1-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="162b1-124">Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="162b1-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="162b1-125">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="162b1-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
