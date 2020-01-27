---
title: Ustawianie trybów ustalania rozmiarów kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738390"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Porady: ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows
W poniższych procedurach przedstawiono niektóre typowe scenariusze, które dostosowują lub łączą opcje ustalania rozmiarów dostępne dla kontrolki <xref:System.Windows.Forms.DataGridView> i dla konkretnych kolumn w kontrolce.  
  
### <a name="to-create-a-fixed-width-column"></a>Aby utworzyć kolumnę o stałej szerokości  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, właściwość <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.False>, właściwość <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na `true`i Właściwość <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> na odpowiednią wartość.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Aby utworzyć kolumnę, która dostosowuje jej rozmiar w celu dopasowania jej do zawartości  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na tryb ustalania wielkości na podstawie zawartości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Aby utworzyć kolumny trybu wypełniania dla wartości o różnej wielkości i ważności  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>, aby ustawić tryb ustalania szerokości dla wszystkich kolumn, które nie przesłaniają tej wartości. Ustaw właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kolumn na wartości proporcjonalnie do ich średnich szerokości zawartości. Ustaw właściwości <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> ważnych kolumn, aby zapewnić wyświetlanie częściowej zawartości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Przykład  
 Poniższy kompletny przykład kodu zawiera aplikację demonstracyjną, która może pomóc w zrozumieniu opcji zmiany wielkości opisanej w tym temacie.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Aby użyć tej aplikacji demonstracyjnej:  
  
- Zmień rozmiar formularza. Obserwuj, jak kolumny trybu wypełniania zmieniają ich szerokości, zachowując proporcje wskazywane przez wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>. Obserwuj, jak <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> kolumny uniemożliwiają jej zmianę, gdy formularz jest zbyt mały.  
  
- Zmień rozmiary kolumn, przeciągając rozdzielacze kolumn za pomocą myszy. Zwróć uwagę na to, jak nie można zmienić rozmiaru niektórych kolumn i jak kolumny o zmiennym rozmiarze nie mogą być węższe niż ich minimalne szerokości.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
