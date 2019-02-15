---
title: Tryb wypełniania kolumn w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 823d3c06648ed37003176eab9df538d95f1ced69
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304313"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Tryb wypełniania kolumn w formancie DataGridView formularzy systemu Windows
W tryb wypełniania kolumny <xref:System.Windows.Forms.DataGridView> kontroli zmienia rozmiar kolumn automatycznie, tak aby zajmowały szerokość obszaru dostępny ekran. Kontrolka nie wyświetla poziomy pasek przewijania z wyjątkiem sytuacji, gdy jest konieczne zapewnienie szerokość każdej kolumny równa lub większa niż jego <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości właściwości.  
  
 Zachowanie zmiany rozmiaru kolumn zależy od jego <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> właściwości. Wartość tej właściwości jest dziedziczony z kolumny <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości lub jej kontrolkę <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> właściwość, jeśli wartość kolumny jest <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (wartość domyślna).  
  
 Każda kolumna może mieć tryb użycia innego rozmiaru, ale żadnych kolumn z trybem rozmiar <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> współużytkują szerokości obszaru wyświetlania, która nie jest używany przez inne kolumny. Szerokość ta jest podzielony między tryb wypełniania kolumn w proporcjach względem ich <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości. Na przykład, jeśli dwie kolumny mają <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości od 100 do 200, pierwszej kolumny będą połowę jako szerokość całego drugiej kolumny.  
  
## <a name="user-resizing-in-fill-mode"></a>Zmiana rozmiaru w trybie do wypełnienia użytkownika  
 W przeciwieństwie do ustalania rozmiaru tryby, które zmiany rozmiaru na podstawie zawartości komórki, tryb wypełniania nie uniemożliwia użytkownikom zmiana rozmiaru kolumn, które mają <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> wartości właściwości `true`. Gdy użytkownik zmienia rozmiar tryb wypełniania kolumny, tryb wypełniania kolumn po zmianie rozmiaru kolumny (do prawej strony, jeśli <xref:System.Windows.Forms.Control.RightToLeft%2A> jest `false`; w przeciwnym razie po lewej stronie) również rozmiar kompensuje zmianę szerokości dostępne. W przypadku żadne tryb wypełniania kolumny po kolumnie o zmienionym rozmiarze, następnie wszystkie pozostałe kolumny trybu wypełnienia w kontrolce zmieniany jest rozmiar do wyrównania. W przypadku nie tryb wypełniania kolumn w formancie, zmianę rozmiaru jest ignorowany. Zmiany rozmiaru kolumny, która nie jest w trybie do wypełnienia dnia wszystkich tryb wypełniania kolumn w formancie zmiana rozmiaru w celu kompensacji.  
  
 Po zmianie rozmiaru kolumny tryb wypełniania <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości dla wszystkich kolumn, które zmieniane są dostosowywane proporcjonalnie. Na przykład, jeśli ma cztery kolumny tryb wypełniania <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, druga kolumna w wysokości równej połowie oryginalną szerokość rozmiaru spowoduje <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości 100, 50, 125 i 125. Zmiana rozmiaru kolumny, która nie jest w trybie do wypełnienia nie zmieni się dowolne <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości, ponieważ tryb wypełniania kolumn wystarczy zmienić rozmiar celu kompensacji przy zachowaniu tych samych proporcji.  
  
## <a name="content-based-fillweight-adjustment"></a>Dostosowanie FillWeight na podstawie zawartości  
 Można zainicjować <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości dla tryb wypełniania kolumn przy użyciu <xref:System.Windows.Forms.DataGridView> automatycznej zmiany rozmiaru metod, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> metody. Metoda ta najpierw oblicza szerokości wymagane według kolumn, aby wyświetlić ich zawartość. Następnie dopasowuje kontrolki <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości dla wszystkich tryb wypełniania kolumn, aby ich proporcje odpowiadały proporcji szerokości obliczeniowych. Na koniec kontrolki zmienia rozmiar tryb wypełniania kolumn za pomocą nowego <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> proporcjach tak, aby wszystkie kolumny w kontrolce wypełnienia dostępnego miejsca na poziomie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Korzystając z odpowiednimi wartościami dla <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, i <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> właściwości, można dostosować zachowania ustawianie rozmiaru kolumn w wielu różnych scenariuszach.  
  
 Poniższy kod pokaz pozwala na eksperymentowanie z różnymi wartościami dla <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, i <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości różnych kolumn. W tym przykładzie <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z własną <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji i jedną kolumnę jest powiązana ze wszystkimi <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwości. Każdej z kolumn jest również jest reprezentowanych przez wiersz w kontrolce, a zmiana wartości w wierszu spowoduje zaktualizowanie właściwości odpowiadającej jej kolumny, dzięki czemu można zobaczyć, jak wartości wchodzić w interakcje.  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Komentarze  
 Aby użyć tej aplikacji demonstracyjnych:  
  
-   Zmień rozmiar formularza. Sprawdź, jak kolumny zmienić ich szerokości, gdy zachowanie proporcji wskazywanym przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości.  
  
-   Zmień rozmiary kolumn, przeciągając separator kolumn za pomocą myszy. Sprawdź sposób, w jaki <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> zmiany wartości.  
  
-   Zmiana <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości dla jednej kolumny, a następnie przeciągnij, aby zmienić rozmiar formularza. Sprawdź jak to zrobić, po dokonaniu małym, formularz <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> wartości nie odbywają się poniżej <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości.  
  
-   Zmiana <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> wartości dla wszystkich kolumn dużą, tak, aby wartości połączone przekracza szerokość formantu. Sprawdź sposób wyświetlania poziomego paska przewijania.  
  
-   Zmiana <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> wartości dla niektórych kolumn. Obserwuj wpływ podczas zmiany rozmiaru kolumn lub w formularzu.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
-   Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
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
- [Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
