---
title: 'Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039785"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d1e65-102">Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="d1e65-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="d1e65-103">Kontrolki, które istnieją w formularzu, można przypisać do nowej kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="d1e65-103">You can assign controls that exist on your form to a new container control.</span></span>

## <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d1e65-104">Aby ponownie przypisać istniejące kontrolki do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="d1e65-104">To reassign existing controls to a different parent</span></span>

1. <span data-ttu-id="d1e65-105">Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="d1e65-105">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>

     <span data-ttu-id="d1e65-106">Umieść je blisko siebie, ale pozostaw nie wyrównane.</span><span class="sxs-lookup"><span data-stu-id="d1e65-106">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="d1e65-107">W **przyborniku**kliknij <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d1e65-107">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>

     <span data-ttu-id="d1e65-108">Nie przeciągaj ikony na formularz.</span><span class="sxs-lookup"><span data-stu-id="d1e65-108">Do not drag the icon onto the form.</span></span>

3. <span data-ttu-id="d1e65-109">Przesuń wskaźnik myszy blisko trzech <xref:System.Windows.Forms.Button> kontrolek.</span><span class="sxs-lookup"><span data-stu-id="d1e65-109">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

     <span data-ttu-id="d1e65-110">Wskaźnik zmieni się w krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> dołączoną ikoną kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d1e65-110">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="d1e65-111">Kliknij i przytrzymaj przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="d1e65-111">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="d1e65-112">Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="d1e65-112">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="d1e65-113">Narysuj kontur wokół trzech <xref:System.Windows.Forms.Button> kontrolek.</span><span class="sxs-lookup"><span data-stu-id="d1e65-113">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="d1e65-114">Zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="d1e65-114">Release the mouse button.</span></span>

     <span data-ttu-id="d1e65-115">Trzy <xref:System.Windows.Forms.Button> kontrolki są teraz wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d1e65-115">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1e65-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1e65-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="d1e65-117">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1e65-117">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d1e65-118">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d1e65-118">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="d1e65-119">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania</span><span class="sxs-lookup"><span data-stu-id="d1e65-119">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
