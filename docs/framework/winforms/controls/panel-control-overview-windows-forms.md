---
title: "Panel — Informacje o formancie (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8855c88a0ec60cd0d44d73046e44c9614347d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="panel-control-overview-windows-forms"></a><span data-ttu-id="14880-102">Panel — Informacje o formancie (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="14880-102">Panel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="14880-103">Formularze systemu Windows <xref:System.Windows.Forms.Panel> formantów służą do zapewniania do zidentyfikowania grupowania dla innych formantów.</span><span class="sxs-lookup"><span data-stu-id="14880-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to provide an identifiable grouping for other controls.</span></span> <span data-ttu-id="14880-104">Zwykle Użyj paneli do podziału formularza przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="14880-104">Typically, you use panels to subdivide a form by function.</span></span> <span data-ttu-id="14880-105">Na przykład może być formularzu zamówienia określający wysyłkowy opcje, takie jak które liczbę operator do użycia.</span><span class="sxs-lookup"><span data-stu-id="14880-105">For example, you may have an order form that specifies mailing options such as which overnight carrier to use.</span></span> <span data-ttu-id="14880-106">Grupowanie wszystkich opcji w panelu daje użytkownikowi logicznej wizualnie.</span><span class="sxs-lookup"><span data-stu-id="14880-106">Grouping all options in a panel gives the user a logical visual cue.</span></span> <span data-ttu-id="14880-107">Na projekt czasu wszystkie formanty, które mogą zostać przeniesione łatwo — po przeniesieniu <xref:System.Windows.Forms.Panel> sterowania wszystkie jego formanty zawarte Przenieś zbyt.</span><span class="sxs-lookup"><span data-stu-id="14880-107">At design time all the controls can be moved easily — when you move the <xref:System.Windows.Forms.Panel> control, all its contained controls move, too.</span></span> <span data-ttu-id="14880-108">Formanty są pogrupowane w panelu jest możliwy za pośrednictwem jego <xref:System.Windows.Forms.Control.Controls%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14880-108">The controls grouped in a panel can be accessed through its <xref:System.Windows.Forms.Control.Controls%2A> property.</span></span> <span data-ttu-id="14880-109">Ta właściwość zwraca kolekcję <xref:System.Windows.Forms.Control> wystąpień, dzięki czemu zwykle trzeba rzutowania formantu pobrać ten sposób jego określonego typu.</span><span class="sxs-lookup"><span data-stu-id="14880-109">This property returns a collection of <xref:System.Windows.Forms.Control> instances, so you will typically need to cast a control retrieved this way to its specific type.</span></span>  
  
## <a name="panel-versus-groupbox"></a><span data-ttu-id="14880-110">Panel i GroupBox</span><span class="sxs-lookup"><span data-stu-id="14880-110">Panel Versus GroupBox</span></span>  
 <span data-ttu-id="14880-111"><xref:System.Windows.Forms.Panel> Formant jest podobny do <xref:System.Windows.Forms.GroupBox> kontrolować; jednak tylko <xref:System.Windows.Forms.Panel> formant może mieć paski przewijania i tylko <xref:System.Windows.Forms.GroupBox> formant zawiera nagłówek.</span><span class="sxs-lookup"><span data-stu-id="14880-111">The <xref:System.Windows.Forms.Panel> control is similar to the <xref:System.Windows.Forms.GroupBox> control; however, only the <xref:System.Windows.Forms.Panel> control can have scroll bars, and only the <xref:System.Windows.Forms.GroupBox> control displays a caption.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="14880-112">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="14880-112">Key Properties</span></span>  
 <span data-ttu-id="14880-113">Wyświetlanie pasków przewijania, należy ustawić <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="14880-113">To display scroll bars, set the <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> property to `true`.</span></span> <span data-ttu-id="14880-114">Można również dostosować wygląd panelu, ustawiając <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, i <xref:System.Windows.Forms.Panel.BorderStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="14880-114">You can also customize the appearance of the panel by setting the <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, and <xref:System.Windows.Forms.Panel.BorderStyle%2A> properties.</span></span> <span data-ttu-id="14880-115">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control.BackColor%2A> i <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości, zobacz [porady: Ustawianie tła panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span><span class="sxs-lookup"><span data-stu-id="14880-115">For more information on the <xref:System.Windows.Forms.Control.BackColor%2A> and <xref:System.Windows.Forms.Control.BackgroundImage%2A> properties, see [How to: Set the Background of a Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span></span> <span data-ttu-id="14880-116"><xref:System.Windows.Forms.Panel.BorderStyle%2A> Właściwość określa, czy panel jest opisane bez widoczna krawędzi (<xref:System.Windows.Forms.BorderStyle.None>), wiersz zwykły (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), lub zasłonięty wiersza (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span><span class="sxs-lookup"><span data-stu-id="14880-116">The <xref:System.Windows.Forms.Panel.BorderStyle%2A> property determines if the panel is outlined with no visible border (<xref:System.Windows.Forms.BorderStyle.None>), a plain line (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), or a shadowed line (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14880-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14880-117">See Also</span></span>  
 <xref:System.Windows.Forms.Panel>  
 [<span data-ttu-id="14880-118">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="14880-118">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [<span data-ttu-id="14880-119">Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="14880-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [<span data-ttu-id="14880-120">Instrukcje: ustawianie tła panelu formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="14880-120">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
