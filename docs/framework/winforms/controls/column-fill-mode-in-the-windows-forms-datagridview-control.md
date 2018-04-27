---
title: Tryb wypełniania kolumn w formancie DataGridView formularzy systemu Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b3f43929db5a7cbd340f3c570b278f1e1b0687d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Tryb wypełniania kolumn w formancie DataGridView formularzy systemu Windows
W tryb wypełniania kolumny <xref:System.Windows.Forms.DataGridView> kontroli zmienia rozmiar kolumn automatycznie, tak aby zajmowały szerokości obszaru wyświetlania dostępne. Formant nie są wyświetlane na pasku przewijania w poziomie, z wyjątkiem przypadków, gdy jest muszą być szerokość każdej kolumny jest równa lub większa niż jego <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości właściwości.  
  
 Zachowanie ustalania rozmiaru kolumn zależy od jego <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> właściwości. Wartość tej właściwości jest odziedziczone kolumny <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości lub formantu <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwości, jeśli wartość kolumny jest <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (wartość domyślna).  
  
 Każda kolumna może mieć inny rozmiar tryb, ale kolumn zawierających tryb rozmiar <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> udostępni szerokości obszaru wyświetlania, który nie jest używany przez innych kolumn. Szerokość ta jest podzielony tryb wypełniania kolumny w proporcjach względem ich <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości. Na przykład, jeśli dwie kolumny mają <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości od 100 do 200, pierwsza kolumna będzie połowy jako szerokie, jak druga kolumna.  
  
## <a name="user-resizing-in-fill-mode"></a>Zmiana rozmiaru w trybie wypełnienia użytkownika  
 W przeciwieństwie do zmiany rozmiaru tryby, które zmiany rozmiaru na podstawie zawartości komórki, tryb wypełniania nie uniemożliwia użytkownikom zmiana rozmiaru kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> wartości właściwości `true`. Gdy użytkownik zmieni tryb wypełniania kolumny, tryb wypełniania kolumny po zmianie rozmiaru kolumn (do prawej strony, jeśli <xref:System.Windows.Forms.Control.RightToLeft%2A> jest `false`; w przeciwnym razie po lewej stronie) również zmienić rozmiar kompensacji zmiany dostępne szerokości. Jeśli po zmianie rozmiaru kolumny nie ma kolumn tryb wypełniania, innych kolumn tryb wypełniania w formancie jest zmieniany na kompensacji. Jeśli nie istnieją żadne tryb wypełniania kolumny w formancie, rozmiar jest ignorowana. Zmieniono rozmiar kolumny, która nie jest w trybie wypełnienia wszystkie tryb wypełniania kolumny w formancie zmiana rozmiarów kompensacji.  
  
 Po zmianie rozmiaru tryb wypełniania kolumny, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości dla wszystkich kolumn, które zmienione zostaną skorygowane proporcjonalnie. Na przykład, jeśli ma cztery tryb wypełniania kolumny <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> spowoduje wartości od 100, zmiana rozmiaru w drugiej kolumnie połowa oryginalną szerokość <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, 50, 125 i 125. Zmiana rozmiaru kolumny, która nie jest w trybie wypełnienia nie zmieni się dowolne <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości, ponieważ tryb wypełniania kolumny po prostu zmieni się rozmiar odpowiednio przy zachowaniu tej samej proporcji.  
  
## <a name="content-based-fillweight-adjustment"></a>Dostosowanie FillWeight na podstawie zawartości  
 Można zainicjować <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości tryb wypełniania kolumny za pomocą <xref:System.Windows.Forms.DataGridView> automatycznej zmiany rozmiaru metod, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metody. Ta metoda najpierw oblicza szerokości wymagane według kolumn, aby wyświetlić ich zawartość. Następnie można dostosować formantu <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości dla wszystkich kolumn tryb wypełniania, aby ich proporcje odpowiadały proporcji szerokości obliczeniowej. Na koniec formantu zmienia rozmiar tryb wypełniania kolumny za pomocą nowej <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> proporcjach tak, aby wypełnił dostępne miejsce poziomie, wszystkie kolumny w formancie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Przy użyciu wartości odpowiednich dla <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> właściwości, można dostosować zachowania ustawianie rozmiaru kolumn dla wielu różnych scenariuszach.  
  
 Poniższy kod pokaz Umożliwia wypróbowanie różnych wartości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, i <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości różnych kolumn. W tym przykładzie <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z własną <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji i jedną kolumnę jest powiązana ze wszystkimi <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwości. Każdej kolumny również jest reprezentowany przez wierszy w formancie i zmianę wartości w wierszu spowoduje zaktualizowanie właściwości odpowiadającej mu kolumny, tak aby były widoczne interakcje wartości.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentarze  
 Aby używać tej aplikacji Pokaz:  
  
-   Zmień rozmiar formularza. Obserwować, jak kolumny zmienić ich szerokość podczas zachowywania proporcje wskazywanym przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości.  
  
-   Zmienianie rozmiarów kolumn sekcjami kolumny za pomocą myszy. Obserwować jak <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> zmiany wartości.  
  
-   Zmień <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości dla jednej kolumny, a następnie przeciągnij, aby zmienić rozmiar formularza. Obserwować, jak to zrobić, po dokonaniu formularza duże, <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> wartości nie zejść poniżej <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości.  
  
-   Zmień <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości dla wszystkich kolumn dużą liczbą tak, aby wartości połączone przekracza szerokość formantu. Obserwować sposób wyświetlania poziomego paska przewijania.  
  
-   Zmień <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> wartości dla niektórych kolumn. Obserwować wpływ podczas zmiany rozmiaru kolumn lub w formularzu.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
-   Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>  
 [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
