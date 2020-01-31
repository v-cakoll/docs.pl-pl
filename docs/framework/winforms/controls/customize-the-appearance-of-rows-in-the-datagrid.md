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
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Porady: dostosowywanie wyglądu wierszy w formancie DataGridView formularzy systemu Windows
Można kontrolować wygląd wierszy <xref:System.Windows.Forms.DataGridView> przez obsługę jednego lub obu zdarzeń <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>. Te zdarzenia zostały zaprojektowane w taki sposób, aby można było malować tylko to, co chcesz, i aby formant <xref:System.Windows.Forms.DataGridView> maluje resztę. Na przykład jeśli chcesz malować w niestandardowym tle, możesz obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i umożliwić poszczególnym komórkom malowanie zawartości pierwszego planu. Alternatywnie, można pozwolić, aby komórki sami odmalują i dodawać niestandardowe elementy na pierwszym planie do programu obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>. Możesz również wyłączyć malowanie komórek i malować wszystko w <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> obsłudze zdarzeń.  
  
 Poniższy przykład kodu implementuje programy obsługi dla obu zdarzeń w celu zapewnienia tła wyboru gradientu i niestandardową zawartość pierwszego planu, która obejmuje wiele kolumn.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
