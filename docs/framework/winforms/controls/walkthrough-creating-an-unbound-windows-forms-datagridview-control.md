---
title: Tworzenie niepowiązanej kontrolki DataGridView
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
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740175"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Wskazówki: utworzenie niezwiązanego formantu DataGridView formularzy systemu Windows
Możesz często wyświetlać dane tabelaryczne, które nie pochodzą z bazy danych. Na przykład możesz chcieć pokazać zawartość dwuwymiarowej tablicy ciągów. Klasa <xref:System.Windows.Forms.DataGridView> zapewnia łatwy i wysoce dostosowywalny sposób wyświetlania danych bez powiązania ze źródłem danych. W tym instruktażu pokazano, jak wypełnić formant <xref:System.Windows.Forms.DataGridView> i zarządzać dodawaniem i usuwaniem wierszy w trybie "niepowiązane". Domyślnie użytkownik może dodawać nowe wiersze. Aby zapobiec dodawaniu wierszy, ustaw właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> na `false`.  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Create a unboundd Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Aby użyć niepowiązanej kontrolki DataGridView  
  
1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera następujące deklaracje zmiennych i metodę `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Zaimplementuj metodę `SetupLayout` w definicji klasy formularza, aby skonfigurować układ formularza.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Utwórz metodę `SetupDataGridView`, aby skonfigurować <xref:System.Windows.Forms.DataGridView> kolumny i właściwości.  
  
     Ta metoda najpierw dodaje formant <xref:System.Windows.Forms.DataGridView> do kolekcji <xref:System.Windows.Forms.Control.Controls%2A> formularza. Następnie liczba kolumn do wyświetlenia jest ustawiana za pomocą właściwości <xref:System.Windows.Forms.DataGridView.ColumnCount%2A>. Styl domyślny dla nagłówków kolumn jest ustawiany przez ustawienie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>i <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> zwrócone przez właściwość <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>.  
  
     Właściwości układu i wyglądu są ustawiane, a następnie nazwy kolumn są przypisane. Po zakończeniu tej metody formant <xref:System.Windows.Forms.DataGridView> jest gotowy do wypełnienia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Utwórz metodę `PopulateDataGridView`, aby dodać wiersze do kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
     Każdy wiersz reprezentuje utwór i powiązane z nim informacje.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Przy użyciu metod narzędziowych można dołączać programy obsługi zdarzeń.  
  
     Będą obsługiwane <xref:System.Windows.Forms.Control.Click> zdarzenia **dodawania** i **usuwania** przycisków, zdarzenie <xref:System.Windows.Forms.Form.Load> formularza oraz zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting> kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
     Po wywołaniu zdarzenia <xref:System.Windows.Forms.Control.Click> przycisku **Dodaj** do <xref:System.Windows.Forms.DataGridView>zostanie dodany nowy pusty wiersz.  
  
     Gdy zostanie wywołane zdarzenie <xref:System.Windows.Forms.Control.Click> przycisku **Usuń** , wybrany wiersz zostanie usunięty, chyba że jest to wiersz dla nowych rekordów, co umożliwia użytkownikowi dodawanie nowych wierszy. Ten wiersz jest zawsze ostatnim wierszem w kontrolce <xref:System.Windows.Forms.DataGridView>.  
  
     Gdy zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.Form.Load> formularza, metody narzędzi `SetupLayout`, `SetupDataGridView`i `PopulateDataGridView` są wywoływane.  
  
     Po wywołaniu zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting> każda komórka w kolumnie `Date` jest formatowana jako data długa, chyba że nie można przeanalizować wartości komórki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
- Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Zobaczysz kontrolkę <xref:System.Windows.Forms.DataGridView>, która wyświetla utwory muzyczne wymienione w `PopulateDataGridView`. Możesz dodać nowe wiersze za pomocą przycisku **Dodaj wiersz** i usunąć zaznaczone wiersze, używając przycisku **Usuń wiersz** . Niepowiązany Formant <xref:System.Windows.Forms.DataGridView> jest magazynem danych i jego dane są niezależne od dowolnego źródła zewnętrznego, takiego jak <xref:System.Data.DataSet> lub tablica.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zapewnia podstawowe informacje o możliwościach kontrolki <xref:System.Windows.Forms.DataGridView>. Wygląd i zachowanie kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować na kilka sposobów:  
  
- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [How to: zmiana stylu obramowania i linii siatki w kontrolce DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Włącz lub Ogranicz dane wejściowe użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [How to: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md)i [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Sprawdź dane wejściowe użytkownika dotyczące błędów związanych z bazą danych. Aby uzyskać więcej informacji, zobacz [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu komórek w kontrolce datagridview Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) i [instrukcje: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: tworzenie niepowiązanej kontrolki DataGridView formularzy Windows Forms](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
