---
title: "Porady: dziedziczenie z klasy formantów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7cbca79cd3541df1db7ace3a7d5f67bf3f2b2ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="81a8d-102">Porady: dziedziczenie z klasy formantów</span><span class="sxs-lookup"><span data-stu-id="81a8d-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="81a8d-103">Jeśli chcesz utworzyć całkowicie niestandardowego formantu do użycia na formularzu systemu Windows, należy dziedziczyć z <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="81a8d-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="81a8d-104">Podczas dziedziczenia z <xref:System.Windows.Forms.Control> klasy wymaga wykonania więcej planowania i wdrażania, również zapewnia ona największą gamę opcji.</span><span class="sxs-lookup"><span data-stu-id="81a8d-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="81a8d-105">Podczas dziedziczenia z <xref:System.Windows.Forms.Control>, dziedziczą bardzo podstawowe funkcje, dzięki formanty pracy.</span><span class="sxs-lookup"><span data-stu-id="81a8d-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="81a8d-106">Funkcje związane z <xref:System.Windows.Forms.Control> klasy obsługi danych wejściowych użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar formantu zapewnia obsługi systemu windows i zapewnia obsługi wiadomości i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="81a8d-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="81a8d-107">Nie obejmuje żadnych rysowania, czyli w tym przypadku rzeczywistych renderowania formantu interfejsu graficznego, nie jest ona zawierać żadnych funkcji interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="81a8d-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="81a8d-108">Należy podać wszystkie te aspekty za pomocą kodu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="81a8d-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81a8d-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="81a8d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="81a8d-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="81a8d-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="81a8d-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="81a8d-112">Można utworzyć niestandardowego formantu</span><span class="sxs-lookup"><span data-stu-id="81a8d-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="81a8d-113">Utwórz nową **aplikacji systemu Windows** lub **Biblioteka formantów systemu Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="81a8d-114">Z **projektu** menu, wybierz **Dodaj klasę**.</span><span class="sxs-lookup"><span data-stu-id="81a8d-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="81a8d-115">W **Dodaj nowy element** okno dialogowe, kliknij przycisk **formant niestandardowy**.</span><span class="sxs-lookup"><span data-stu-id="81a8d-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="81a8d-116">Formant niestandardowy jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="81a8d-117">Naciśnij klawisz F7, aby otworzyć **edytora kodu** dla formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="81a8d-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="81a8d-118">Zlokalizuj <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, która będzie pusty, z wyjątkiem wywołanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="81a8d-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="81a8d-119">Zmodyfikuj kod, aby uwzględnić wszystkie niestandardowe rysowania dla formantu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="81a8d-120">Aby uzyskać informacje dotyczące pisania kodu do renderowania grafiki dla formantów, zobacz [niestandardowe malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="81a8d-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="81a8d-121">Implementuje żadnych niestandardowych metod, właściwości lub zdarzeń, zawierające formantu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="81a8d-122">Zapisz i przetestować formantu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a8d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81a8d-123">See Also</span></span>  
 [<span data-ttu-id="81a8d-124">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="81a8d-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="81a8d-125">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="81a8d-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="81a8d-126">Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81a8d-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="81a8d-127">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81a8d-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="81a8d-128">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81a8d-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="81a8d-129">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="81a8d-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
