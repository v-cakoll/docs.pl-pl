---
title: 'Instrukcje: Ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 85322afcaae96b07d085d2b44d923542ecbf9bf6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708889"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Instrukcje: Ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms
Poniższe procedury przedstawiają kilka typowych scenariuszy, dostosować można też połączyć dostępne opcje zmiany rozmiaru, które <xref:System.Windows.Forms.DataGridView> kontroli i określonych kolumn w formancie.  
  
### <a name="to-create-a-fixed-width-column"></a>Aby utworzyć kolumnę o stałej szerokości  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> właściwości <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwości `true`i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwość do odpowiedniej wartości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Aby utworzyć kolumnę, który dostosowuje jego rozmiar w celu dopasowania do jego zawartości  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwość trybu ustalania rozmiaru na podstawie zawartości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Aby utworzyć tryb wypełniania kolumny wartości różnych rozmiarach i ich znaczenie  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> można ustawić tryb zmiany rozmiaru dla wszystkich kolumn, które nie zastąpić tę wartość. Ustaw <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości kolumn do wartości, które są proporcjonalne do ich średniej zawartości szerokości. Ustaw <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości ważnych kolumnach, aby zapewnić wyświetlanie zawartości częściowej.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompletny kod zapewnia aplikacji demonstracyjnych, która może pomóc Ci zrozumieć opcje zmiany rozmiaru, opisane w tym temacie.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Aby użyć tej aplikacji demonstracyjnych:  
  
-   Zmień rozmiar formularza. Sprawdź, jak tryb wypełniania kolumn zmienić ich szerokości, gdy zachowanie proporcji wskazywanym przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości. Sprawdź, jak w kolumnie <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> uniemożliwia zmianę, gdy formularz jest za mały.  
  
-   Zmień rozmiary kolumn, przeciągając separator kolumn za pomocą myszy. Sprawdź, jak niektóre kolumny nie może być o zmienionym rozmiarze i jak o zmiennym rozmiarze kolumn nie może zostać wykonana węższe niż ich minimalne szerokości.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
