---
title: Tryb wypełniania kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 43b8915efe303b6f56cd4adf5fdbd69f51b0b754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736877"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Tryb wypełniania kolumn w formancie DataGridView formularzy systemu Windows
W trybie wypełniania kolumn formant <xref:System.Windows.Forms.DataGridView> automatycznie zmienia rozmiar swoich kolumn, aby wypełnić szerokość dostępnego obszaru wyświetlania. Kontrolka nie wyświetla poziomego paska przewijania, z wyjątkiem sytuacji, gdy jest to konieczne, aby szerokość każdej kolumny była równa lub większa niż jej wartość właściwości <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
 Zachowanie ustalania wielkości dla każdej kolumny zależy od jego właściwości <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>. Wartość tej właściwości jest dziedziczona z właściwości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> kolumny lub właściwości <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> kontrolki, jeśli wartość kolumny jest <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (wartość domyślna).  
  
 Każda kolumna może mieć inny tryb rozmiaru, ale wszystkie kolumny z trybem rozmiaru <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> będą współużytkować szerokość obszaru wyświetlania, która nie jest używana przez inne kolumny. Ta szerokość jest dzielona między kolumny trybu wypełniania w proporcjach względem ich wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>. Na przykład jeśli dwie kolumny mają <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100 i 200, pierwsza kolumna będzie miała połowę jako druga kolumna.  
  
## <a name="user-resizing-in-fill-mode"></a>Zmienianie rozmiarów użytkownika w trybie wypełniania  
 W przeciwieństwie do trybów ustalania rozmiaru, które są zmieniane na podstawie zawartości komórki, tryb wypełnienia nie uniemożliwia użytkownikom zmiany rozmiaru kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> wartości właściwości `true`. Gdy użytkownik zmienia rozmiar kolumny trybu wypełniania, wszystkie kolumny trybu wypełnienia po zmianie rozmiaru kolumny (z prawej strony, jeśli <xref:System.Windows.Forms.Control.RightToLeft%2A> jest `false`; w przeciwnym razie po lewej stronie) również są zmieniane, aby skompensować zmiany w dostępnej szerokości. Jeśli po kolumnie o zmienionym rozmiarze nie ma kolumn trybu wypełniania, wszystkie inne kolumny trybu wypełniania w kontrolce są zmieniane w celu zrekompensowania. Jeśli w formancie nie ma innych kolumn trybu wypełniania, zmiana rozmiaru jest ignorowana. Jeśli zmieniany jest rozmiar kolumny, która nie jest w trybie Fill, wszystkie kolumny trybu wypełniania w kontrolce zmieniają rozmiary do zrekompensowania.  
  
 Po zmianie rozmiarów kolumny trybu wypełniania wartości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> dla wszystkich zmienionych kolumn są dostosowywane proporcjonalnie. Na przykład, jeśli cztery kolumny trybu wypełniania mają <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, zmianę rozmiarów drugiej kolumny na połowę jej oryginalnej szerokości spowoduje <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, 50, 125 i 125. Zmiana rozmiaru kolumny, która nie jest w trybie Fill, nie spowoduje zmiany wartości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, ponieważ kolumny trybu wypełnienia będą po prostu zmieniane w celu zrekompensowania, zachowując te same proporcje.  
  
## <a name="content-based-fillweight-adjustment"></a>Korekta FillWeight oparta na zawartości  
 Można inicjować wartości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> dla kolumn trybu wypełniania przy użyciu <xref:System.Windows.Forms.DataGridView> automatycznych metod zmieniania rozmiarów, takich jak Metoda <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>. Ta metoda najpierw oblicza szerokości wymagane przez kolumny, aby wyświetlić ich zawartość. Następnie formant dostosowuje wartości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> dla wszystkich kolumn trybu wypełniania, tak aby ich proporcje odpowiadały proporcjom obliczonych szerokości. Na koniec formant zmienia rozmiar kolumn trybu wypełniania przy użyciu nowych <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> proporcji, tak aby wszystkie kolumny w formancie wypełniają dostępne miejsce w poziomie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Korzystając z odpowiednich wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>, można dostosować zachowania ustalania szerokości kolumn dla wielu różnych scenariuszy.  
  
 Poniższy kod demonstracyjny umożliwia eksperymentowanie z różnymi wartościami dla właściwości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>i <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> różnych kolumn. W tym przykładzie formant <xref:System.Windows.Forms.DataGridView> jest powiązany z własną kolekcją <xref:System.Windows.Forms.DataGridView.Columns%2A>, a jedna kolumna jest powiązana z każdą z właściwości <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A>. Każda kolumna jest również reprezentowana przez wiersz w kontrolce, a zmiana wartości w wierszu spowoduje zaktualizowanie właściwości odpowiedniej kolumny, aby zobaczyć, w jaki sposób są one używane.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentarze  
 Aby użyć tej aplikacji demonstracyjnej:  
  
- Zmień rozmiar formularza. Obserwuj, jak kolumny zmieniają swoje szerokości, zachowując proporcje wskazywane przez wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  
  
- Zmień rozmiary kolumn, przeciągając rozdzielacze kolumn za pomocą myszy. Obserwuj, jak zmieniają się wartości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  
  
- Zmień wartość <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> jednej kolumny, a następnie przeciągnij, aby zmienić rozmiar formularza. Obserwuj, w jaki sposób, gdy formularz jest wystarczająco mały, wartości <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> nie są zgodne z wartościami <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
- Zmień wartości <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> dla wszystkich kolumn na duże liczby, tak aby połączone wartości przekroczą szerokość kontrolki. Obserwuj, jak pojawia się poziomy pasek przewijania.  
  
- Zmień wartości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> dla niektórych kolumn. Zwróć uwagę na efekt zmiany rozmiaru kolumn lub formularza.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>
- [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
