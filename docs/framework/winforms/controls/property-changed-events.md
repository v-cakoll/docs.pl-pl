---
title: "Zdarzenia zmiany właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7685891e99f1dcb2ca9e515c7dc6d7730ff0b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-changed-events"></a><span data-ttu-id="806fd-102">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="806fd-102">Property-Changed Events</span></span>
<span data-ttu-id="806fd-103">Jeśli chcesz, aby formantu można wysłać powiadomienia, gdy właściwość o nazwie *PropertyName* zmiany, zdefiniuj zdarzenia o nazwie *PropertyName* `Changed` i metodę o nazwie `On` *PropertyName* `Changed` który wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="806fd-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="806fd-104">Konwencja nazewnictwa w formularzach systemu Windows są dołączane słowo *zmienione* do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="806fd-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="806fd-105">Typ delegata skojarzonego zdarzenia dla zdarzenia zmiany właściwości jest <xref:System.EventHandler>, a typ danych zdarzenia jest <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="806fd-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="806fd-106">Klasa podstawowa <xref:System.Windows.Forms.Control> definiuje wiele zdarzeń zmiany właściwości, takie jak <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>i inne.</span><span class="sxs-lookup"><span data-stu-id="806fd-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="806fd-107">Aby uzyskać ogólne informacje o zdarzeniach, zobacz [zdarzenia](../../../../docs/standard/events/index.md) i [zdarzenia w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="806fd-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="806fd-108">Zdarzenia zmiany właściwości są przydatne, ponieważ umożliwiają one konsumentów formantu można dołączyć procedury obsługi zdarzeń, które odpowiadają na zmiany.</span><span class="sxs-lookup"><span data-stu-id="806fd-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="806fd-109">Jeśli formantu musi odpowiadać na zdarzenie zmiany właściwości, która zgłasza, Zastąp odpowiadającą jej `On` *PropertyName* `Changed` metody zamiast dołączanie delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="806fd-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="806fd-110">Formant zazwyczaj odpowiada na zdarzenie zmiany właściwości, aktualizując inne właściwości lub ponownego narysowania niektórych lub wszystkich powierzchni do rysowania.</span><span class="sxs-lookup"><span data-stu-id="806fd-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="806fd-111">W poniższym przykładzie przedstawiono sposób `FlashTrackBar` kontrolki niestandardowej reaguje na niektóre zdarzenia zmiany właściwości, które dziedziczy on z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="806fd-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="806fd-112">Pełny przykład, zobacz [jak: utworzyć Windows formularze kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="806fd-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="806fd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="806fd-113">See Also</span></span>  
 [<span data-ttu-id="806fd-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="806fd-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="806fd-115">Zdarzenia w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="806fd-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="806fd-116">Właściwości formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="806fd-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
