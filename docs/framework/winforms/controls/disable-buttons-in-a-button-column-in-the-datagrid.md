---
title: 'Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 0687b4e4c3896e7663c5c093a43a2db72e0053f8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082055"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Zawiera kontrolki <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlania komórki za pomocą interfejsu użytkownika (UI), jak przycisk. Jednak <xref:System.Windows.Forms.DataGridViewButtonCell> nie zapewnia możliwość wyłączenia wyglądu przycisku wyświetlane w komórce.  
  
 Poniższy przykład kodu demonstruje sposób dostosowywania <xref:System.Windows.Forms.DataGridViewButtonCell> klasy, aby wyświetlić przyciski, który może znajdować się wyłączone. W przykładzie zdefiniowano nowy typ komórki `DataGridViewDisableButtonCell`, która jest pochodną <xref:System.Windows.Forms.DataGridViewButtonCell>. Ten typ komórki zawiera nową `Enabled` właściwość, która może być równa `false` do rysowania przycisk wyłączone w komórce. W przykładzie zdefiniowano też nowy typ kolumny, `DataGridViewDisableButtonColumn`, który wyświetla `DataGridViewDisableButtonCell` obiektów. Aby zademonstrować tego nową komórkę i kolumny typu, bieżąca wartość <xref:System.Windows.Forms.DataGridViewCheckBoxCell> w obiekcie nadrzędnym <xref:System.Windows.Forms.DataGridView> Określa, czy `Enabled` właściwość `DataGridViewDisableButtonCell` w tym samym wierszu jest `true` lub `false`.  
  
> [!NOTE]
>  Po utworzeniu klasy pochodnej z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, pamiętaj zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania. Należy także wywołać klasy bazowej `Clone` metody, aby właściwości klasy bazowej są kopiowane do nowej komórce lub kolumnie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing, przestrzeń nazw System.Windows.Forms i System.Windows.Forms.VisualStyles.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
