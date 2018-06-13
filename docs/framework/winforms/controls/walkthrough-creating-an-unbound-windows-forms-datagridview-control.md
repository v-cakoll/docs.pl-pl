---
title: 'Wskazówki: utworzenie niezwiązanego formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: 26c2241f4b0a3b23255de15b3d0c9f8bdd15de02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541157"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Wskazówki: utworzenie niezwiązanego formantu DataGridView formularzy systemu Windows
Często można wyświetlić danych tabelarycznych, który nie pochodzi z bazy danych. Na przykład można wyświetlić zawartości jest tablicą dwuwymiarową ciągów. <xref:System.Windows.Forms.DataGridView> Klasa umożliwia łatwe i dużym stopniu dostosowywane do wyświetlania danych bez powiązania ze źródłem danych. W tym przewodniku przedstawiono sposób wypełnienia <xref:System.Windows.Forms.DataGridView> sterowania i zarządzania dodawania i usuwania wierszy w trybie "niezwiązanego". Domyślnie użytkownik może dodawać nowych wierszy. Aby zapobiec dodawaniu, ustaw <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> jest właściwość `false`.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [jak: utworzyć niezwiązanego formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Aby użyć niezwiązanego formantu DataGridView  
  
1.  Utwórz klasę pochodną <xref:System.Windows.Forms.Form> i zawiera następujące deklaracje zmiennych i `Main` metody.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  Implementowanie `SetupLayout` metody w definicji klasy formularza, aby skonfigurować układu formularza.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  Utwórz `SetupDataGridView` metodę, aby skonfigurować <xref:System.Windows.Forms.DataGridView> kolumny i właściwości.  
  
     Ta metoda najpierw dodaje <xref:System.Windows.Forms.DataGridView> sterowania do formularza <xref:System.Windows.Forms.Control.Controls%2A> kolekcji. Następnie liczbę kolumn, który będzie wyświetlany jest ustawiony za pomocą <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> właściwości. Domyślny styl nagłówków kolumn jest ustawiana przez ustawienie <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, i <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> zwrócony przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> właściwości.  
  
     Układ i wyglądu właściwości są ustawione, a następnie nazwy kolumn są przypisane. Gdy ta metoda jest kończona, <xref:System.Windows.Forms.DataGridView> kontrolka będzie gotowa do wypełnienia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  Utwórz `PopulateDataGridView` metody w celu dodania wierszy do <xref:System.Windows.Forms.DataGridView> formantu.  
  
     Każdy wiersz reprezentuje utworu i związane z nim informacje.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  Z metody narzędziowe w miejscu można dołączyć procedury obsługi zdarzeń.  
  
     Będzie obsługiwać **Dodaj** i **usunąć** przycisków <xref:System.Windows.Forms.Control.Click> zdarzenia, formularz <xref:System.Windows.Forms.Form.Load> zdarzenia i <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.  
  
     Gdy **Dodaj** przycisku <xref:System.Windows.Forms.Control.Click> zdarzenie jest zgłaszane, dodawany jest nowy, pusty wiersz do <xref:System.Windows.Forms.DataGridView>.  
  
     Gdy **usunąć** przycisku <xref:System.Windows.Forms.Control.Click> zdarzenie jest zgłaszane, wybrany wiersz został usunięty, chyba że jest wiersza dla nowych rekordów, który umożliwia użytkownikowi dodawanie nowych wierszy. Ten wiersz jest zawsze ostatni wiersz w <xref:System.Windows.Forms.DataGridView> formantu.  
  
     Gdy formularz <xref:System.Windows.Forms.Form.Load> zdarzenie jest zgłaszane, `SetupLayout`, `SetupDataGridView`, i `PopulateDataGridView` są wywoływane metody narzędziowe.  
  
     Gdy <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie jest zgłaszane, każda komórka w `Date` kolumny jest w formacie daty długiej, chyba że nie można przeanalizować wartości komórki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Zobaczysz <xref:System.Windows.Forms.DataGridView> kontrolkę wyświetlającą utworów muzycznych na liście `PopulateDataGridView`. Można dodawać nowe wiersze z **Dodaj wiersz** przycisk, a można usunąć zaznaczone wiersze z **Usuń wiersz** przycisku. Niezwiązane <xref:System.Windows.Forms.DataGridView> kontroli jest magazynem danych i jego danych jest niezależna od wszelkich zewnętrznych źródeł, takich jak <xref:System.Data.DataSet> lub tablicy.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera podstawowe <xref:System.Windows.Forms.DataGridView> funkcje formantu. Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> sterowania na kilka sposobów:  
  
-   Zmienianie stylów obramowania i nagłówek. Aby uzyskać więcej informacji, zobacz [porady: Zmiana obramowania i style linii siatki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Włącz lub ograniczanie danych wejściowych użytkownika na <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [porady: Zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), i [jak: utworzyć tylko do odczytu w kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Sprawdź dane wejściowe użytkownika błędy związane z bazy danych. Aby uzyskać więcej informacji, zobacz [wskazówki: obsługa błędów tego Occur podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Dostosowywanie wyglądu komórek. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) i [porady: Ustaw domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: tworzenie niepowiązanej kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
