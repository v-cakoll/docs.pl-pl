---
title: 'Instrukcje: Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: fa1bd6c0274fdf702072e062e6eeab7078375491
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600287"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d45d1-102">Instrukcje: Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="d45d1-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="d45d1-103">Możesz przypisać formantów, które istnieją w formularzu do nowej kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="d45d1-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d45d1-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d45d1-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d45d1-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d45d1-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d45d1-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d45d1-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d45d1-107">Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="d45d1-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="d45d1-108">Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="d45d1-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="d45d1-109">Umieść je blisko siebie, ale pozostawić je niewyrównanych.</span><span class="sxs-lookup"><span data-stu-id="d45d1-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="d45d1-110">W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d45d1-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="d45d1-111">Nie przeciągnij ikony na formularzu.</span><span class="sxs-lookup"><span data-stu-id="d45d1-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="d45d1-112">Przesuń wskaźnik myszy w pobliżu trzy <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d45d1-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="d45d1-113">Wskaźnik zmienia się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki dołączone.</span><span class="sxs-lookup"><span data-stu-id="d45d1-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="d45d1-114">Kliknij i przytrzymaj przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="d45d1-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="d45d1-115">Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d45d1-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="d45d1-116">Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d45d1-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="d45d1-117">Zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="d45d1-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="d45d1-118">Trzy <xref:System.Windows.Forms.Button> formanty są wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d45d1-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45d1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d45d1-119">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="d45d1-120">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d45d1-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d45d1-121">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d45d1-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="d45d1-122">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="d45d1-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
