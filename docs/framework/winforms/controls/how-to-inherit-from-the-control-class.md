---
title: 'Instrukcje: dziedziczenie z klasy kontrolek'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02c40e310778bd476742f62ee8b9d8598b084a53
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015853"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="08ea4-102">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="08ea4-102">How to: Inherit from the Control Class</span></span>

<span data-ttu-id="08ea4-103">Jeśli chcesz utworzyć pełną kontrolkę niestandardową do użycia w formularzu systemu Windows, należy dziedziczyć z <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="08ea4-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="08ea4-104">Chociaż dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga wykonania większej liczby zaplanowanych i implementacji, zapewnia również największą gamę opcji.</span><span class="sxs-lookup"><span data-stu-id="08ea4-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="08ea4-105">Podczas dziedziczenia z <xref:System.Windows.Forms.Control>, dziedziczysz bardzo podstawową funkcję, która sprawia, że formanty działają.</span><span class="sxs-lookup"><span data-stu-id="08ea4-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="08ea4-106">Funkcja niezależna od <xref:System.Windows.Forms.Control> klasy obsługuje wprowadzanie danych przez użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar kontrolki, udostępnia uchwyt systemu Windows i zapewnia obsługę komunikatów i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="08ea4-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="08ea4-107">Nie zawiera żadnego malowania, co w tym przypadku jest rzeczywistym renderowaniem interfejsu graficznego formantu lub nie zawiera żadnych określonych funkcji interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="08ea4-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="08ea4-108">Wszystkie te aspekty należy dostarczyć za poorednictwem niestandardowego kodu.</span><span class="sxs-lookup"><span data-stu-id="08ea4-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="08ea4-109">Aby utworzyć kontrolkę niestandardową</span><span class="sxs-lookup"><span data-stu-id="08ea4-109">To create a custom control</span></span>

1. <span data-ttu-id="08ea4-110">W programie Visual Studio Utwórz nową **aplikację systemu Windows** lub projekt **biblioteki formantów systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="08ea4-110">In Visual Studio, create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="08ea4-111">W menu **projekt** wybierz polecenie **Dodaj klasę**.</span><span class="sxs-lookup"><span data-stu-id="08ea4-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="08ea4-112">W oknie dialogowym **Dodaj nowy element** kliknij przycisk **kontrolka**niestandardowa.</span><span class="sxs-lookup"><span data-stu-id="08ea4-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

   <span data-ttu-id="08ea4-113">Do projektu zostanie dodany nowy formant niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="08ea4-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="08ea4-114">Naciśnij klawisz **F7** , aby otworzyć **Edytor kodu** dla kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="08ea4-114">Press **F7** to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="08ea4-115">Znajdź metodę, która będzie pusta, z wyjątkiem wywołania <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="08ea4-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="08ea4-116">Zmodyfikuj kod w celu uwzględnienia dowolnego niestandardowego malowania dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="08ea4-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

   <span data-ttu-id="08ea4-117">Aby uzyskać informacje na temat pisania kodu w celu renderowania grafiki dla kontrolek, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="08ea4-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="08ea4-118">Zaimplementuj wszelkie niestandardowe metody, właściwości lub zdarzenia, które mają być dołączone przez formant.</span><span class="sxs-lookup"><span data-stu-id="08ea4-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="08ea4-119">Zapisz i Przetestuj swój formant.</span><span class="sxs-lookup"><span data-stu-id="08ea4-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="08ea4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08ea4-120">See also</span></span>

- [<span data-ttu-id="08ea4-121">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="08ea4-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="08ea4-122">Instrukcje: Dziedzicz z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="08ea4-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="08ea4-123">Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08ea4-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="08ea4-124">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08ea4-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="08ea4-125">Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08ea4-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="08ea4-126">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="08ea4-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
