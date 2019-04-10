---
title: 'Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 2639322707c1c7e378f6d389a1dec80fd619841c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328221"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="c1eb7-102">Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="c1eb7-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="c1eb7-103">Możesz przypisać formantów, które istnieją w formularzu do nowej kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1eb7-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c1eb7-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c1eb7-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c1eb7-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="c1eb7-107">Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="c1eb7-107">To reassign existing controls to a different parent</span></span>  
  
1. <span data-ttu-id="c1eb7-108">Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="c1eb7-109">Umieść je blisko siebie, ale pozostawić je niewyrównanych.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2. <span data-ttu-id="c1eb7-110">W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="c1eb7-111">Nie przeciągnij ikony na formularzu.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-111">Do not drag the icon onto the form.</span></span>  
  
3. <span data-ttu-id="c1eb7-112">Przesuń wskaźnik myszy w pobliżu trzy <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="c1eb7-113">Wskaźnik zmienia się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki dołączone.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4. <span data-ttu-id="c1eb7-114">Kliknij i przytrzymaj przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-114">Click and hold the mouse button.</span></span>  
  
5. <span data-ttu-id="c1eb7-115">Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="c1eb7-116">Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7. <span data-ttu-id="c1eb7-117">Zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="c1eb7-118">Trzy <xref:System.Windows.Forms.Button> formanty są wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1eb7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1eb7-119">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="c1eb7-120">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c1eb7-120">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="c1eb7-121">Przewodnik: rozmieszczanie kontrolek w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1eb7-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="c1eb7-122">Przewodnik: rozmieszczanie kontrolek w formularzach systemu Windows za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="c1eb7-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
