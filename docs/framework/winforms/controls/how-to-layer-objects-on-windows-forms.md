---
title: 'Porady: tworzenie warstw obiektów na formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: d67d9b204c316dce5f3818496d791ed4c1b352f2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561185"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="bb901-102">Porady: tworzenie warstw obiektów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb901-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="bb901-103">Podczas tworzenia interfejsu użytkownika złożonych lub praca wielu dokumentów (MDI) interfejsu często warto warstwy kontroli i formularze podrzędne, aby utworzyć bardziej złożone interfejsy użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="bb901-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="bb901-104">Aby przenieść i śledzenie kontrolek i systemu windows w ramach grupy, manipulować ich porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="bb901-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="bb901-105">*Porządek* jest warstwy visual kontrolek w formularzu wzdłuż osi z formularza (na głębokości).</span><span class="sxs-lookup"><span data-stu-id="bb901-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="bb901-106">Okno w górnej części porządek nakłada się na inne okna.</span><span class="sxs-lookup"><span data-stu-id="bb901-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="bb901-107">Inne okna nakładać się na okna w dolnej części porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="bb901-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb901-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="bb901-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bb901-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="bb901-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bb901-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="bb901-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="bb901-111">Warstwa kontrolek w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="bb901-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="bb901-112">Zaznacz kontrolkę, którą chcesz warstwy.</span><span class="sxs-lookup"><span data-stu-id="bb901-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="bb901-113">Na **Format** menu wskaż **kolejności**, a następnie kliknij przycisk **Przesuń na wierzch** lub **Przesuń na spód**.</span><span class="sxs-lookup"><span data-stu-id="bb901-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="bb901-114">Aby programowo warstwy formantów</span><span class="sxs-lookup"><span data-stu-id="bb901-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="bb901-115">Użyj <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> metody do manipulowania porządek kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bb901-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="bb901-116">Na przykład jeśli <xref:System.Windows.Forms.TextBox> kontroli `txtFirstName`, jest poniżej innej kontrolki, a chcesz ma go na początku, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb901-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="bb901-117">Formularze Windows obsługuje *zawieranie kontrolek*.</span><span class="sxs-lookup"><span data-stu-id="bb901-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="bb901-118">Zawieranie kontrolek obejmuje umieszczenie kontrolki w ramach zawierający kontrolki, takie jak liczba <xref:System.Windows.Forms.RadioButton> kontrolki w ramach <xref:System.Windows.Forms.GroupBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="bb901-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="bb901-119">Można następnie warstwy kontrolek w kontrolce zawierającego.</span><span class="sxs-lookup"><span data-stu-id="bb901-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="bb901-120">Przesunięcie pole grupy przenosi, formanty, ponieważ są zawarte wewnątrz niego.</span><span class="sxs-lookup"><span data-stu-id="bb901-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb901-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb901-121">See Also</span></span>  
 [<span data-ttu-id="bb901-122">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb901-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="bb901-123">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb901-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="bb901-124">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="bb901-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="bb901-125">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb901-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="bb901-126">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="bb901-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
