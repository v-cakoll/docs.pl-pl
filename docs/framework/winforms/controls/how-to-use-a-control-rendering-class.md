---
title: 'Instrukcje: używanie klasy renderowania kontrolki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: a0f450ff5f169026007002a0d2907ee35e79b29d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630556"
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="ea51a-102">Instrukcje: używanie klasy renderowania kontrolki</span><span class="sxs-lookup"><span data-stu-id="ea51a-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="ea51a-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Forms.ComboBoxRenderer> klasy do renderowania kontrolki pola kombi strzałkę listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="ea51a-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="ea51a-104">Przykład zawiera <xref:System.Windows.Forms.Control.OnPaint%2A> metoda prostego formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="ea51a-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="ea51a-105"><xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Właściwość jest używana do określenia, czy style wizualne są włączone w obszarze klienta w aplikacji systemu windows.</span><span class="sxs-lookup"><span data-stu-id="ea51a-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="ea51a-106">Jeśli style wizualne są aktywne, a następnie <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> metody będą renderowane strzałki listy rozwijanej przy użyciu stylów wizualnych; w przeciwnym razie <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> metody będą renderowane strzałki listy rozwijanej w stylu klasycznym Windows.</span><span class="sxs-lookup"><span data-stu-id="ea51a-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea51a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea51a-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea51a-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ea51a-108">Compiling the Code</span></span>  
 <span data-ttu-id="ea51a-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ea51a-109">This example requires:</span></span>  
  
- <span data-ttu-id="ea51a-110">Niestandardowy formant pochodzące z <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="ea51a-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
- <span data-ttu-id="ea51a-111">A <xref:System.Windows.Forms.Form> obsługujący kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="ea51a-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
- <span data-ttu-id="ea51a-112">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ea51a-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea51a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea51a-113">See also</span></span>

- [<span data-ttu-id="ea51a-114">Renderowanie kontrolek przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="ea51a-114">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)
