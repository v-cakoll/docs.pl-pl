---
title: 'Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987043"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="be648-102">Instrukcje: Przypisz ponownie istniejące kontrolki do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="be648-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="be648-103">Kontrolki, które istnieją w formularzu, można przypisać do nowej kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="be648-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="be648-104">W programie Visual Studio przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="be648-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="be648-105">Umieść je blisko siebie, ale pozostaw nie wyrównane.</span><span class="sxs-lookup"><span data-stu-id="be648-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="be648-106">W **przyborniku**kliknij <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be648-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="be648-107">(Nie przeciągaj ikony na formularz).</span><span class="sxs-lookup"><span data-stu-id="be648-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="be648-108">Przesuń wskaźnik myszy blisko trzech <xref:System.Windows.Forms.Button> kontrolek.</span><span class="sxs-lookup"><span data-stu-id="be648-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="be648-109">Wskaźnik zmieni się w krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> dołączoną ikoną kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be648-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="be648-110">Kliknij i przytrzymaj przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="be648-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="be648-111">Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="be648-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="be648-112">Narysuj kontur wokół trzech <xref:System.Windows.Forms.Button> kontrolek.</span><span class="sxs-lookup"><span data-stu-id="be648-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="be648-113">Zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="be648-113">Release the mouse button.</span></span>

   <span data-ttu-id="be648-114">Trzy <xref:System.Windows.Forms.Button> kontrolki są teraz wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be648-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="be648-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be648-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="be648-116">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="be648-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="be648-117">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania</span><span class="sxs-lookup"><span data-stu-id="be648-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
