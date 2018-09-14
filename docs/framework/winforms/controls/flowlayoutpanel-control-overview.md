---
title: FlowLayoutPanel — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 73767114da1c04222fb8ceaf812153421c4597aa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517765"
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="4cebd-102">FlowLayoutPanel — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="4cebd-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="4cebd-103"><xref:System.Windows.Forms.FlowLayoutPanel> Kontroli rozmieszcza jego zawartość w kierunku przepływu poziomej lub pionowej.</span><span class="sxs-lookup"><span data-stu-id="4cebd-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="4cebd-104">Może zawijać się zawartość formantu z jeden wiersz do następnego lub z jednej kolumny do następnego.</span><span class="sxs-lookup"><span data-stu-id="4cebd-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="4cebd-105">Alternatywnie można przyciąć zamiast zawijania jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="4cebd-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="4cebd-106">Można określić kierunek przepływu, ustawiając wartość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4cebd-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="4cebd-107"><xref:System.Windows.Forms.FlowLayoutPanel> Kontroli poprawnie odwraca kierunku przepływu w układy od prawej do lewej (RTL).</span><span class="sxs-lookup"><span data-stu-id="4cebd-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="4cebd-108">Można również określić, czy <xref:System.Windows.Forms.FlowLayoutPanel> zawartość kontrolki jest opakowana lub przycięty, ustawiając wartość <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4cebd-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="4cebd-109"><xref:System.Windows.Forms.FlowLayoutPanel> Automatycznie kontrolowania rozmiarów do jego zawartości, po ustawieniu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="4cebd-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="4cebd-110">Zapewnia także **FlowBreak** właściwości do jego formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4cebd-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="4cebd-111">Ustawienie wartości właściwości FlowBreak `true` powoduje, że <xref:System.Windows.Forms.FlowLayoutPanel> formantu, aby zatrzymać układu kontrolek w bieżącym kierunek przepływu i zawijania do następnego wiersza lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="4cebd-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="4cebd-112">Wszystkie kontrolki Windows Forms może być elementem podrzędnym <xref:System.Windows.Forms.FlowLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="4cebd-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="4cebd-113">Dzięki tej możliwości można skonstruować układy zaawansowane dostosowania do formularza wymiarów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4cebd-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="4cebd-114">Zobacz też [wskazówki: rozmieszczanie formantów Windows Forms za pomocą FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="4cebd-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cebd-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cebd-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="4cebd-116">FlowLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4cebd-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
