---
title: 'Instrukcje: Dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: ba76f10bc3b33f268f28565f6174bc81ce8edcc5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220286"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Instrukcje: Dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms
Można sterować wyglądem <xref:System.Windows.Forms.DataGridView> wierszy dzięki obsłudze jedną lub obie <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> zdarzenia. Te zdarzenia są zaprojektowane tak, aby można malować tylko co chcesz while, dzięki czemu <xref:System.Windows.Forms.DataGridView> kontroli malowanie pozostałe. Na przykład, jeśli chcesz malować tło niestandardowe mogą obsługiwać <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> zdarzeń, dzięki czemu pojedyncze komórki malowanie własne zawartość pierwszego planu. Alternatywnie można pozwolić komórek malowanie samodzielnie i Dodaj zawartość niestandardowego narzędzia w obsłudze dla <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> zdarzeń. Można również wyłączyć malowania komórki i malowanie wszystko samodzielnie w <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> programu obsługi zdarzeń.  
  
 Poniższy przykładowy kod implementuje programy obsługi dla obu zdarzeń w celu zaznaczenia gradientu tła i część zawartości niestandardowych pierwszego planu, obejmującej wiele kolumn.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  

## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
