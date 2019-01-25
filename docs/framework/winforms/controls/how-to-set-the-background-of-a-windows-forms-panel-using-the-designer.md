---
title: 'Instrukcje: Ustawianie tła panelu formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: be0359e13bcab868374189c6b42df392327b8eb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645075"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="16612-102">Instrukcje: Ustawianie tła panelu formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="16612-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="16612-103">Formularze Windows <xref:System.Windows.Forms.Panel> formant może wyświetlić kolor tła i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="16612-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="16612-104"><xref:System.Windows.Forms.Control.BackColor%2A> Właściwość ustawia kolor tła kontrolki, które są zawarte w panelu, takich jak etykiety i przycisków radiowych.</span><span class="sxs-lookup"><span data-stu-id="16612-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="16612-105">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wypełni wszystkie panelu wyboru.</span><span class="sxs-lookup"><span data-stu-id="16612-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="16612-106">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz, który pojawi się za zaporą formantów, które są zawarte w panelu.</span><span class="sxs-lookup"><span data-stu-id="16612-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="16612-107">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą formularza, który zawiera <xref:System.Windows.Forms.Panel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="16612-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="16612-108">Aby dowiedzieć się, jak skonfigurować taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="16612-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16612-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="16612-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="16612-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="16612-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="16612-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="16612-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="16612-112">Aby ustawić tło w programie Windows Forms Designer</span><span class="sxs-lookup"><span data-stu-id="16612-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="16612-113">Wybierz <xref:System.Windows.Forms.Panel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="16612-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="16612-114">W **właściwości** , kliknij strzałkę znajdujący się obok <xref:System.Windows.Forms.Control.BackColor%2A> właściwość, aby wyświetlić okno z trzema kartami.</span><span class="sxs-lookup"><span data-stu-id="16612-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="16612-115">Wybierz **niestandardowe** kartę, aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="16612-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="16612-116">Wybierz **Web** lub **systemu** kartę, aby wyświetlić listę nazw wstępnie zdefiniowanych kolorów, a następnie wybierz kolor.</span><span class="sxs-lookup"><span data-stu-id="16612-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="16612-117">W **właściwości** , kliknij strzałkę znajdujący się obok <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="16612-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="16612-118">W **Otwórz** oknie dialogowym Wybierz plik który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="16612-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16612-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16612-119">See also</span></span>
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="16612-120">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="16612-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [<span data-ttu-id="16612-121">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="16612-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [<span data-ttu-id="16612-122">Instrukcje: Grupowanie formantów z formantem panelu formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="16612-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
