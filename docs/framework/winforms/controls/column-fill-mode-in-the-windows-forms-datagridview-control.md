---
title: Tryb wypełniania kolumn w formancie DataGridView
description: Dowiedz się, w jaki sposób formant DataGridView Windows Forms w trybie wypełniania kolumn zmienia rozmiar swoich kolumn automatycznie, dzięki czemu wypełniają szerokość dostępnego obszaru wyświetlania.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 766a58954250d78ce6e44404730332b3158e1fad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622825"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Tryb wypełniania kolumn w formancie DataGridView formularzy systemu Windows
W trybie wypełniania kolumn <xref:System.Windows.Forms.DataGridView> kontrolka automatycznie zmienia rozmiar swoich kolumn, aby wypełnić szerokość dostępnego obszaru wyświetlania. Kontrolka nie wyświetla poziomego paska przewijania, z wyjątkiem sytuacji, gdy jest to konieczne, aby szerokość każdej kolumny była równa lub większa niż jej <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartość właściwości.  
  
 Zachowanie ustalania wielkości dla każdej kolumny zależy od jej <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> właściwości. Wartość tej właściwości jest dziedziczona z <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> Właściwości kolumny lub właściwości kontrolki, <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> Jeśli wartość kolumny to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (wartość domyślna).  
  
 Każda kolumna może mieć inny tryb rozmiaru, ale każda kolumna z trybem rozmiaru <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> będzie współużytkować szerokość obszaru wyświetlania, która nie jest używana przez inne kolumny. Ta szerokość jest dzielona między kolumny trybu wypełniania w proporcjach względem ich <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości. Na przykład jeśli dwie kolumny mają <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100 i 200, pierwsza kolumna będzie miała połowę jako druga kolumna.  
  
## <a name="user-resizing-in-fill-mode"></a>Zmienianie rozmiarów użytkownika w trybie wypełniania  
 W przeciwieństwie do trybów ustalania rozmiaru, które są zmieniane na podstawie zawartości komórki, tryb wypełnienia nie uniemożliwia użytkownikom zmiany rozmiaru kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> wartości właściwości `true` . Gdy użytkownik zmienia rozmiar kolumny trybu wypełniania, wszystkie kolumny trybu wypełnienia po zmianie rozmiaru kolumny (z prawej strony <xref:System.Windows.Forms.Control.RightToLeft%2A> , jeśli jest `false` ; w przeciwnym razie po lewej) również są zmieniane, aby zrekompensować zmianę w dostępnej szerokości. Jeśli po kolumnie o zmienionym rozmiarze nie ma kolumn trybu wypełniania, wszystkie inne kolumny trybu wypełniania w kontrolce są zmieniane w celu zrekompensowania. Jeśli w formancie nie ma innych kolumn trybu wypełniania, zmiana rozmiaru jest ignorowana. Jeśli zmieniany jest rozmiar kolumny, która nie jest w trybie Fill, wszystkie kolumny trybu wypełniania w kontrolce zmieniają rozmiary do zrekompensowania.  
  
 Po zmianie wielkości kolumny trybu wypełniania <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości wszystkich kolumn, które zostały zmienione, są dostosowywane proporcjonalnie. Na przykład jeśli cztery kolumny trybu wypełniania mają <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, zmieni rozmiar drugiej kolumny na połowę jej pierwotnej szerokości, spowoduje to <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, 50, 125 i 125. Zmiana rozmiaru kolumny, która nie jest w trybie Fill, nie spowoduje zmiany żadnych <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości, ponieważ kolumny trybu wypełniania będą po prostu zmieniane w celu zrekompensowania, zachowując te same proporcje.  
  
## <a name="content-based-fillweight-adjustment"></a>Korekta FillWeight oparta na zawartości  
 Możesz inicjować <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości kolumn trybu wypełniania przy użyciu <xref:System.Windows.Forms.DataGridView> metod automatycznego zmieniania rozmiarów, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> Metoda. Ta metoda najpierw oblicza szerokości wymagane przez kolumny, aby wyświetlić ich zawartość. Następnie formant dostosowuje <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości dla wszystkich kolumn trybu wypełniania, tak aby ich proporcje były zgodne z proporcjami obliczonych szerokości. Na koniec formant zmienia rozmiar kolumn trybu wypełniania przy użyciu nowych <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> proporcji, dzięki czemu wszystkie kolumny w formancie wypełniają dostępne miejsce w poziomie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Za pomocą odpowiednich wartości <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości,, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> , można dostosować zachowania ustalania szerokości kolumn dla wielu różnych scenariuszy.  
  
 Poniższy kod demonstracyjny umożliwia eksperymentowanie z różnymi wartościami dla <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości, i <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> różnych kolumn. W tym przykładzie <xref:System.Windows.Forms.DataGridView> formant jest powiązany z własną <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcją, a jedna kolumna jest powiązana z każdą z <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A> <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości,, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> , <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> . Każda kolumna jest również reprezentowana przez wiersz w kontrolce, a zmiana wartości w wierszu spowoduje zaktualizowanie właściwości odpowiedniej kolumny, aby zobaczyć, w jaki sposób są one używane.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentarze  
 Aby użyć tej aplikacji demonstracyjnej:  
  
- Zmień rozmiar formularza. Obserwuj, jak kolumny zmieniają swoje szerokości, zachowując proporcje wskazywane przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości.  
  
- Zmień rozmiary kolumn, przeciągając rozdzielacze kolumn za pomocą myszy. Obserwuj, jak <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> zmieniają się wartości.  
  
- Zmień <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartość dla jednej kolumny, a następnie przeciągnij, aby zmienić rozmiar formularza. Obserwuj, w jaki sposób, gdy formularz jest wystarczająco mały, <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> wartości nie przechodzą poniżej <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości.  
  
- Zmień <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości dla wszystkich kolumn na duże liczby, tak aby połączone wartości przekroczą szerokość kontrolki. Obserwuj, jak pojawia się poziomy pasek przewijania.  
  
- Zmień <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> wartości niektórych kolumn. Zwróć uwagę na efekt zmiany rozmiaru kolumn lub formularza.  
  
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
