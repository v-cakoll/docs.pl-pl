---
title: 'Porady: dziedziczenie z klasy formantów'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458381"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="8ec71-102">Porady: dziedziczenie z klasy formantów</span><span class="sxs-lookup"><span data-stu-id="8ec71-102">How to: Inherit from the Control Class</span></span>

<span data-ttu-id="8ec71-103">Jeśli chcesz utworzyć pełną kontrolkę niestandardową do użycia w formularzu systemu Windows, należy dziedziczyć z klasy <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="8ec71-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="8ec71-104">Chociaż dziedziczenie z klasy <xref:System.Windows.Forms.Control> wymaga wykonania większej liczby planowania i implementacji, zapewnia również największy zakres opcji.</span><span class="sxs-lookup"><span data-stu-id="8ec71-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="8ec71-105">Podczas dziedziczenia z <xref:System.Windows.Forms.Control>dziedziczyć bardzo podstawowe funkcje, które ułatwiają działanie kontrolek.</span><span class="sxs-lookup"><span data-stu-id="8ec71-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="8ec71-106">Funkcja niezależna od klasy <xref:System.Windows.Forms.Control> obsługuje wprowadzanie danych przez użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar kontrolki, udostępnia uchwyt systemu Windows i zapewnia obsługę komunikatów i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="8ec71-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="8ec71-107">Nie zawiera żadnego malowania, co w tym przypadku jest rzeczywistym renderowaniem interfejsu graficznego formantu lub nie zawiera żadnych określonych funkcji interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ec71-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="8ec71-108">Wszystkie te aspekty należy dostarczyć za poorednictwem niestandardowego kodu.</span><span class="sxs-lookup"><span data-stu-id="8ec71-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="8ec71-109">Aby utworzyć kontrolkę niestandardową</span><span class="sxs-lookup"><span data-stu-id="8ec71-109">To create a custom control</span></span>

1. <span data-ttu-id="8ec71-110">W programie Visual Studio Utwórz nową **aplikację systemu Windows** lub projekt **biblioteki formantów systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="8ec71-110">In Visual Studio, create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="8ec71-111">W menu **projekt** wybierz polecenie **Dodaj klasę**.</span><span class="sxs-lookup"><span data-stu-id="8ec71-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="8ec71-112">W oknie dialogowym **Dodaj nowy element** kliknij przycisk **kontrolka niestandardowa**.</span><span class="sxs-lookup"><span data-stu-id="8ec71-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

   <span data-ttu-id="8ec71-113">Do projektu zostanie dodany nowy formant niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="8ec71-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="8ec71-114">Naciśnij klawisz **F7** , aby otworzyć **Edytor kodu** dla kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="8ec71-114">Press **F7** to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="8ec71-115">Znajdź metodę <xref:System.Windows.Forms.Control.OnPaint%2A>, która będzie pusta, z wyjątkiem wywołania metody <xref:System.Windows.Forms.Control.OnPaint%2A> klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="8ec71-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="8ec71-116">Zmodyfikuj kod w celu uwzględnienia dowolnego niestandardowego malowania dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8ec71-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

   <span data-ttu-id="8ec71-117">Aby uzyskać informacje na temat pisania kodu w celu renderowania grafiki dla kontrolek, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="8ec71-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="8ec71-118">Zaimplementuj wszelkie niestandardowe metody, właściwości lub zdarzenia, które mają być dołączone przez formant.</span><span class="sxs-lookup"><span data-stu-id="8ec71-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="8ec71-119">Zapisz i Przetestuj swój formant.</span><span class="sxs-lookup"><span data-stu-id="8ec71-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec71-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ec71-120">See also</span></span>

- [<span data-ttu-id="8ec71-121">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="8ec71-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="8ec71-122">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="8ec71-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="8ec71-123">Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ec71-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="8ec71-124">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ec71-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="8ec71-125">Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ec71-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="8ec71-126">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8ec71-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
