---
title: 'Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: f7dcb3d949182efee3538174909b0f856dceedee
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589488"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="48bfb-102">Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="48bfb-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="48bfb-103">Można sterować wyglądem <xref:System.Windows.Forms.DataGridView> wierszy dzięki obsłudze jedną lub obie <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="48bfb-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="48bfb-104">Te zdarzenia są zaprojektowane tak, aby można malować tylko co chcesz while, dzięki czemu <xref:System.Windows.Forms.DataGridView> kontroli malowanie pozostałe.</span><span class="sxs-lookup"><span data-stu-id="48bfb-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="48bfb-105">Na przykład, jeśli chcesz malować tło niestandardowe mogą obsługiwać <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> zdarzeń, dzięki czemu pojedyncze komórki malowanie własne zawartość pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="48bfb-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="48bfb-106">Alternatywnie można pozwolić komórek malowanie samodzielnie i Dodaj zawartość niestandardowego narzędzia w obsłudze dla <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="48bfb-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="48bfb-107">Można również wyłączyć malowania komórki i malowanie wszystko samodzielnie w <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="48bfb-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="48bfb-108">Poniższy przykładowy kod implementuje programy obsługi dla obu zdarzeń w celu zaznaczenia gradientu tła i część zawartości niestandardowych pierwszego planu, obejmującej wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="48bfb-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48bfb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="48bfb-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48bfb-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="48bfb-110">Compiling the Code</span></span>  
 <span data-ttu-id="48bfb-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="48bfb-111">This example requires:</span></span>  
  
- <span data-ttu-id="48bfb-112">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="48bfb-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48bfb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48bfb-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="48bfb-114">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="48bfb-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="48bfb-115">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="48bfb-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
