---
title: "Porady: ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8a120d1d80f40353eb7e0c3feb26c224175cc72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="afd7d-102">Porady: ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="afd7d-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="afd7d-103">Można przypisać formantów, które istnieją w formularzu nowego formantu kontenera.</span><span class="sxs-lookup"><span data-stu-id="afd7d-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afd7d-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="afd7d-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="afd7d-105">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="afd7d-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="afd7d-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="afd7d-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="afd7d-107">Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="afd7d-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="afd7d-108">Przeciągnij trzy <xref:System.Windows.Forms.Button> formantów **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="afd7d-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="afd7d-109">Umieść je się w pobliżu siebie, ale pozostaw je niewyrównany.</span><span class="sxs-lookup"><span data-stu-id="afd7d-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="afd7d-110">W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikona formantu.</span><span class="sxs-lookup"><span data-stu-id="afd7d-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="afd7d-111">Nie przeciągnij ikonę na formularzu.</span><span class="sxs-lookup"><span data-stu-id="afd7d-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="afd7d-112">Przenieś wskaźnik myszy w pobliżu trzech <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="afd7d-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="afd7d-113">Wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikona kontroli dołączony.</span><span class="sxs-lookup"><span data-stu-id="afd7d-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="afd7d-114">Kliknij i przytrzymaj przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="afd7d-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="afd7d-115">Przeciągnij wskaźnik myszy Rysowanie konturu <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="afd7d-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="afd7d-116">Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="afd7d-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="afd7d-117">Zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="afd7d-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="afd7d-118">Trzy <xref:System.Windows.Forms.Button> formanty zostaną wstawione do <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="afd7d-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd7d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afd7d-119">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="afd7d-120">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="afd7d-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="afd7d-121">Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="afd7d-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="afd7d-122">Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="afd7d-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
