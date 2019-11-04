---
title: 'Porady: ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459197"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="34e83-102">Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="34e83-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="34e83-103">Kontrolki, które istnieją w formularzu, można przypisać do nowej kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="34e83-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="34e83-104">W programie Visual Studio przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="34e83-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="34e83-105">Umieść je blisko siebie, ale pozostaw nie wyrównane.</span><span class="sxs-lookup"><span data-stu-id="34e83-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="34e83-106">W **przyborniku**kliknij ikonę kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="34e83-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="34e83-107">(Nie przeciągaj ikony na formularz).</span><span class="sxs-lookup"><span data-stu-id="34e83-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="34e83-108">Przesuń wskaźnik myszy blisko trzech formantów <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="34e83-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="34e83-109">Wskaźnik zmieni się na krzyżyk z dołączoną ikoną kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="34e83-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="34e83-110">Kliknij i przytrzymaj przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="34e83-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="34e83-111">Przeciągnij wskaźnik myszy, aby narysować kontur kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="34e83-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="34e83-112">Narysuj kontur wokół trzech formantów <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="34e83-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="34e83-113">Zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="34e83-113">Release the mouse button.</span></span>

   <span data-ttu-id="34e83-114">Trzy kontrolki <xref:System.Windows.Forms.Button> są teraz wstawiane do kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="34e83-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="34e83-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34e83-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="34e83-116">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="34e83-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="34e83-117">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="34e83-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
