---
title: 'Przewodnik: utworzenie niezwiązanej kontrolki DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 99561490786f3f3569f272138001ea5ad8937410
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343472"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Przewodnik: utworzenie niezwiązanej kontrolki DataGridView formularzy systemu Windows
Można często wyświetlić dane tabelaryczne, która nie pochodzi z bazy danych. Na przykład można wyświetlić zawartości dwuwymiarową tablicę ciągów. <xref:System.Windows.Forms.DataGridView> Klasy umożliwia łatwe i dużym stopniu dostosowywane do wyświetlania danych bez powiązania ze źródłem danych. W tym instruktażu pokazano, jak wypełnić <xref:System.Windows.Forms.DataGridView> sterowania i zarządzania nimi dodawania i usuwania wierszy w trybie "niepowiązanych". Domyślnie użytkownik może dodawać nowe wiersze. Aby zapobiec wierszy, ustawianie <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwość `false`.  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Tworzenie formantu DataGridView formularzy Windows niepowiązanych](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Aby użyć niezwiązanego formantu DataGridView  
  
1. Utwórz klasę, która pochodzi od klasy <xref:System.Windows.Forms.Form> i zawiera następujące deklaracje zmiennych i `Main` metody.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Implementowanie `SetupLayout` metody w definicji klasy formularza, aby zdefiniować układ formularza.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Tworzenie `SetupDataGridView` metodę, aby skonfigurować <xref:System.Windows.Forms.DataGridView> kolumny i właściwości.  
  
     Metoda ta najpierw umożliwia dodanie <xref:System.Windows.Forms.DataGridView> kontrolki formularza <xref:System.Windows.Forms.Control.Controls%2A> kolekcji. Następnie liczbę kolumn do wyświetlenia można ustawić przy użyciu <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> właściwości. Domyślny styl w nagłówkach kolumn została ustawiona przez ustawienie <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, i <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> zwrócone przez <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> właściwości.  
  
     Układ i wygląd właściwości są ustawione, a następnie przypisywania nazw kolumn. Gdy ta metoda kończy działanie, <xref:System.Windows.Forms.DataGridView> kontrolka będzie gotowa do wypełnienia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Tworzenie `PopulateDataGridView` metodę, aby dodać wiersze do <xref:System.Windows.Forms.DataGridView> kontroli.  
  
     Każdy wiersz reprezentuje utworu i związane z nim informacje.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Za pomocą metody narzędziowe w miejscu można dołączyć procedury obsługi zdarzeń.  
  
     Będzie obsługiwać **Dodaj** i **Usuń** przycisków <xref:System.Windows.Forms.Control.Click> zdarzenia, formularz <xref:System.Windows.Forms.Form.Load> zdarzenia i <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.  
  
     Gdy **Dodaj** przycisku <xref:System.Windows.Forms.Control.Click> zdarzenie jest zgłaszane, dodawany jest nowy, pusty wiersz do <xref:System.Windows.Forms.DataGridView>.  
  
     Gdy **Usuń** przycisku <xref:System.Windows.Forms.Control.Click> zdarzenie jest zgłaszane w zaznaczonym wierszu zostanie usunięty, chyba że jest to wiersz dla nowych rekordów, który umożliwia użytkownikowi dodawanie nowych wierszy. Ten wiersz jest zawsze ostatni wiersz w <xref:System.Windows.Forms.DataGridView> kontroli.  
  
     Gdy formularz <xref:System.Windows.Forms.Form.Load> zdarzenie jest zgłaszane, `SetupLayout`, `SetupDataGridView`, i `PopulateDataGridView` są wywoływane metody narzędziowe.  
  
     Gdy <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie jest zgłaszane, każdej komórki w `Date` kolumny jest w formacie daty długiej, chyba że nie można przeanalizować wartości komórki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Zostanie wyświetlony <xref:System.Windows.Forms.DataGridView> kontrolkę wyświetlającą utworów muzycznych na liście `PopulateDataGridView`. Można dodawać nowe wiersze z **Dodaj wiersz** przycisku, na które można usunąć wybranych wierszy z **Usuń wiersz** przycisku. Niezwiązane <xref:System.Windows.Forms.DataGridView> kontroli jest magazynem danych i jego dane są niezależne od dowolnego źródła zewnętrznego, takie jak <xref:System.Data.DataSet> lub tablicy.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zapewnia podstawową wiedzę na temat <xref:System.Windows.Forms.DataGridView> funkcje formantu. Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontroli na kilka sposobów:  
  
-   Zmienianie stylów obramowania i nagłówek. Aby uzyskać więcej informacji, zobacz [jak: Zmiana obramowania i formantu DataGridView formularzy style linii siatki w Windows](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Włączać lub ograniczać danych wprowadzonych przez użytkownika <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać więcej informacji, zobacz [jak: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy](prevent-row-addition-and-deletion-datagridview.md), i [jak: Określanie kolumn jako tylko do odczytu w Windows formantu DataGridView formularzy](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Sprawdź dane wejściowe użytkownika błędy związane z bazy danych. Aby uzyskać więcej informacji, zobacz [instruktażu: Obsługa błędów występujących podczas wprowadzania danych w Windows formantu DataGridView formularzy](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [instruktażu: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Dostosowywanie wyglądu komórek. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy Windows](customize-the-appearance-of-cells-in-the-datagrid.md) i [jak: Ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy Windows](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Wyświetlanie danych w formancie DataGridView formularzy systemu Windows](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: utworzenie niezwiązanej kontrolki DataGridView formularzy systemu Windows](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows](data-display-modes-in-the-windows-forms-datagridview-control.md)
