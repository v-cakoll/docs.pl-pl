---
title: Dostosuj wygląd wierszy w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744041"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4cb57-102">Porady: dostosowywanie wyglądu wierszy w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4cb57-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4cb57-103">Można kontrolować wygląd wierszy <xref:System.Windows.Forms.DataGridView> przez obsługę jednego lub obu zdarzeń <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4cb57-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="4cb57-104">Te zdarzenia zostały zaprojektowane w taki sposób, aby można było malować tylko to, co chcesz, i aby formant <xref:System.Windows.Forms.DataGridView> maluje resztę.</span><span class="sxs-lookup"><span data-stu-id="4cb57-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="4cb57-105">Na przykład jeśli chcesz malować w niestandardowym tle, możesz obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i umożliwić poszczególnym komórkom malowanie zawartości pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="4cb57-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="4cb57-106">Alternatywnie, można pozwolić, aby komórki sami odmalują i dodawać niestandardowe elementy na pierwszym planie do programu obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4cb57-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="4cb57-107">Możesz również wyłączyć malowanie komórek i malować wszystko w <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4cb57-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="4cb57-108">Poniższy przykład kodu implementuje programy obsługi dla obu zdarzeń w celu zapewnienia tła wyboru gradientu i niestandardową zawartość pierwszego planu, która obejmuje wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="4cb57-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cb57-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4cb57-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4cb57-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4cb57-110">Compiling the Code</span></span>  
 <span data-ttu-id="4cb57-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4cb57-111">This example requires:</span></span>  
  
- <span data-ttu-id="4cb57-112">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="4cb57-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb57-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cb57-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="4cb57-114">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4cb57-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4cb57-115">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="4cb57-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
