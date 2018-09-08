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
ms.openlocfilehash: 1a0eea1930699ed85fcf0eaf184ba0aabe398d73
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137658"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="c7654-102">Porady: dziedziczenie z klasy formantów</span><span class="sxs-lookup"><span data-stu-id="c7654-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="c7654-103">Jeśli chcesz utworzyć formant całkowicie niestandardowy do użycia w formularzu Windows, możesz powinien dziedziczyć <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7654-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="c7654-104">Podczas dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga wykonania więcej planowania i wdrażania go oferuje także funkcje największej gamy opcji.</span><span class="sxs-lookup"><span data-stu-id="c7654-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="c7654-105">Gdy dziedziczenie z <xref:System.Windows.Forms.Control>, dziedziczą bardzo podstawowe funkcje, który sprawia, że formanty, które działają.</span><span class="sxs-lookup"><span data-stu-id="c7654-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="c7654-106">Funkcje związane z <xref:System.Windows.Forms.Control> klasy obsługuje danych wejściowych użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar formantu, zapewnia uchwytów okien i zapewnia Obsługa komunikatów i bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="c7654-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="c7654-107">Zawierają wszelkie rysowania, czyli w tym przypadku rzeczywistego renderowania interfejsu graficznego kontrolki, nie jest włączyć wszystkie funkcje interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c7654-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="c7654-108">Należy podać wszystkie te aspekty poprzez kod niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="c7654-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7654-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c7654-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c7654-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c7654-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c7654-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c7654-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="c7654-112">Aby utworzyć formant niestandardowy</span><span class="sxs-lookup"><span data-stu-id="c7654-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="c7654-113">Utwórz nową **aplikacji Windows** lub **Biblioteka formantów Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="c7654-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="c7654-114">Z **projektu** menu, wybierz **Dodaj klasę**.</span><span class="sxs-lookup"><span data-stu-id="c7654-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="c7654-115">W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolkę niestandardową**.</span><span class="sxs-lookup"><span data-stu-id="c7654-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="c7654-116">Nowy formant niestandardowy zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="c7654-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="c7654-117">Naciśnij klawisz F7, aby otworzyć **Edytor kodu** kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="c7654-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="c7654-118">Znajdź <xref:System.Windows.Forms.Control.OnPaint%2A> metody, która będzie pusta, z wyjątkiem wywołanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c7654-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="c7654-119">Zmodyfikuj kod, aby zastosować niestandardowe rysowania, które kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c7654-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="c7654-120">Informacje na temat pisania kodu w celu renderowania grafiki dla formantów, zobacz [niestandardowe malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="c7654-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="c7654-121">Implementuje żadnych niestandardowych metod, właściwości lub zdarzeń, zawierające Twoją kontrolą.</span><span class="sxs-lookup"><span data-stu-id="c7654-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="c7654-122">Zapisz i przetestuj formantu.</span><span class="sxs-lookup"><span data-stu-id="c7654-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7654-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7654-123">See Also</span></span>  
 [<span data-ttu-id="c7654-124">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c7654-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="c7654-125">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="c7654-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="c7654-126">Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7654-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="c7654-127">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7654-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="c7654-128">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7654-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="c7654-129">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c7654-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
