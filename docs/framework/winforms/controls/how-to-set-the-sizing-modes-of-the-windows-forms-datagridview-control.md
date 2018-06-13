---
title: 'Porady: ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 3d2ebb2b42a3e6558d5aedb207bdc4e2607d5270
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536318"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Porady: ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows
W poniższych procedurach pokazano kilka typowych scenariuszy, które dostosować lub połączyć dostępne opcje ustalania rozmiaru <xref:System.Windows.Forms.DataGridView> kontroli i dla określonych kolumn w formancie.  
  
### <a name="to-create-a-fixed-width-column"></a>Aby utworzyć kolumnę o stałej szerokości  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> właściwości <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwości `true`i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwości odpowiednią wartość.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Aby utworzyć kolumnę, które można dostosować jego rozmiaru w celu dopasowania do jego zawartości  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości do trybu na podstawie zawartości zmiany rozmiaru.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Aby utworzyć tryb wypełniania kolumny wartości różnych rozmiarach i ważność  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> ustawiony tryb zmiany rozmiaru dla wszystkich kolumn, które nie zastępują tej wartości. Ustaw <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości kolumn do wartości, które są proporcjonalne do jego średni zawartości szerokości. Ustaw <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości ważnych kolumnach częściowe wyświetlanie zawartości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompletny kod zawiera aplikacji demonstracyjnej, która może ułatwić poznawanie opcje rozmiaru opisanych w tym temacie.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Aby używać tej aplikacji Pokaz:  
  
-   Zmień rozmiar formularza. Sprawdź, jak tryb wypełniania kolumny zmienić ich szerokość podczas zachowywania proporcje wskazywanym przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości. Sprawdź, jak kolumny <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> uniemożliwia zmianę, gdy formularz jest za mały.  
  
-   Zmienianie rozmiarów kolumn sekcjami kolumny za pomocą myszy. Sprawdź, jak niektóre kolumny nie może być po zmianie rozmiaru i jak o zmiennym rozmiarze kolumn nie można dokonać korekty węższe niż ich minimalnej szerokości.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
