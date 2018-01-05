---
title: "TrackBar — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="05918-102">TrackBar — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="05918-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="05918-103">Formularze systemu Windows <xref:System.Windows.Forms.TrackBar> formantu (nazywanych także "suwaka") jest używany na potrzeby nawigowaniu po dużej ilości informacji lub wizualnie dostosowywania liczbowych ustawienie.</span><span class="sxs-lookup"><span data-stu-id="05918-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="05918-104"><xref:System.Windows.Forms.TrackBar> Formantu ma dwie części: thumb, znanej także jako suwaka i znaczniki osi.</span><span class="sxs-lookup"><span data-stu-id="05918-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="05918-105">Stronie przycisku suwaka wchodzi w skład, którą można dostosować.</span><span class="sxs-lookup"><span data-stu-id="05918-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="05918-106">Odpowiada jego położenie <xref:System.Windows.Forms.TrackBar.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="05918-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="05918-107">Znaczniki są wskaźniki wizualne, które są rozmieszczone w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="05918-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="05918-108">Trackbar jest przesuwany w przyrostach, które określają i można wyrównać poziomo czy pionowo.</span><span class="sxs-lookup"><span data-stu-id="05918-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="05918-109">Na przykład można użyć do kontrolowania szybkość lub mysz migania kursora dla systemu pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05918-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="05918-110">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="05918-110">Key Properties</span></span>  
 <span data-ttu-id="05918-111">Właściwości klucza obiektu <xref:System.Windows.Forms.TrackBar> sterowania stanowią <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, i <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span><span class="sxs-lookup"><span data-stu-id="05918-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="05918-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A>jest odstępy to znaczniki osi.</span><span class="sxs-lookup"><span data-stu-id="05918-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="05918-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A>i <xref:System.Windows.Forms.TrackBar.Maximum%2A> to najmniejsza i największa wartości, które mogą być przedstawiane na pasek śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05918-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="05918-114">Są dwa inne ważne właściwości <xref:System.Windows.Forms.TrackBar.SmallChange%2A> i <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span><span class="sxs-lookup"><span data-stu-id="05918-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="05918-115">Wartość <xref:System.Windows.Forms.TrackBar.SmallChange%2A> właściwość jest liczba pozycji przycisku przewijania przenosi w odpowiedzi na potrzeby naciśnięto klawisz Strzałka w lewo lub w.</span><span class="sxs-lookup"><span data-stu-id="05918-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="05918-116">Wartość <xref:System.Windows.Forms.TrackBar.LargeChange%2A> właściwość jest liczba pozycji stronie przycisku suwaka przejdzie w odpowiedzi na potrzeby naciśnięto klawisz PAGE UP lub PAGE DOWN, lub w odpowiedzi na myszy kliknie pasek śledzenia na każdej stronie przycisku suwaka.</span><span class="sxs-lookup"><span data-stu-id="05918-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05918-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05918-117">See Also</span></span>  
 <xref:System.Windows.Forms.TrackBar>  
 [<span data-ttu-id="05918-118">TrackBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="05918-118">TrackBar Control</span></span>](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
