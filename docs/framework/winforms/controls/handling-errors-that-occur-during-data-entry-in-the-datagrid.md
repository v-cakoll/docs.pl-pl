---
title: 'Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046074"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows

Obsługa błędów z bazowego magazynu danych jest funkcją wymaganą dla aplikacji do wprowadzania danych. Formant Windows Forms <xref:System.Windows.Forms.DataGridView> ułatwia to <xref:System.Windows.Forms.DataGridView.DataError> ujawnienie zdarzenia, które jest zgłaszane, gdy magazyn danych wykryje naruszenie ograniczenia lub naruszoną regułę biznesową.

W tym instruktażu uzyskasz pobieranie wierszy z `Customers` tabeli w przykładowej bazie danych Northwind i wyświetlanie ich <xref:System.Windows.Forms.DataGridView> w kontrolce. W przypadku wykrycia zduplikowanej `CustomerID` wartości w nowym wierszu lub edytowanego istniejącego wiersza <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie zostanie wykonane, które będzie obsługiwane przez wyświetlenie <xref:System.Windows.Forms.MessageBox> opisu wyjątku.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Obsługa błędów występujących podczas wprowadzania danych w kontrolce](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView Windows Forms.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do serwera z przykładową bazą danych Northwind SQL Server.

## <a name="creating-the-form"></a>Tworzenie formularza

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Aby obsłużyć błędy wprowadzania danych w formancie DataGridView

1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.DataGridView> zawiera kontrolkę i <xref:System.Windows.Forms.BindingSource> składnik.

    Poniższy przykład kodu zapewnia inicjalizację podstawową i zawiera `Main` metodę.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Zaimplementuj metodę w definicji klasy formularza do obsługi szczegółów połączenia z bazą danych.

    Ten przykład kodu używa `GetData` metody, która zwraca wypełniony <xref:System.Data.DataTable> obiekt. Upewnij się, że ustawiono `connectionString` zmienną na wartość odpowiednią dla bazy danych.

    > [!IMPORTANT]
    > Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Zaimplementuj procedurę obsługi dla <xref:System.Windows.Forms.Form.Load> zdarzenia formularza, która <xref:System.Windows.Forms.DataGridView> inicjuje i <xref:System.Windows.Forms.BindingSource> konfiguruje powiązanie danych.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Obsłuż <xref:System.Windows.Forms.DataGridView>zdarzenie w. <xref:System.Windows.Forms.DataGridView.DataError>

    Jeśli kontekstem błędu jest operacja zatwierdzania, Wyświetl błąd w <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Naciśnij klawisz F5, aby uruchomić aplikację.

  Zobaczysz <xref:System.Windows.Forms.DataGridView> kontrolkę wypełnioną danymi z tabeli Customers. Jeśli wprowadzisz zduplikowaną wartość dla `CustomerID` i zatwierdzisz edycję, wartość komórki zostanie automatycznie przywrócona, a zobaczysz <xref:System.Windows.Forms.MessageBox> , że zostanie wyświetlony komunikat o błędzie wprowadzania danych.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja zapewnia podstawowe informacje o <xref:System.Windows.Forms.DataGridView> możliwościach formantu. Wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontrolki można dostosować na kilka sposobów:

- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [jak: Zmień style obramowania i linii siatki w kontrolce](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.

- Włącz lub Ogranicz dane wejściowe użytkownika do <xref:System.Windows.Forms.DataGridView> kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce](prevent-row-addition-and-deletion-datagridview.md)DataGridView Windows Forms i [instrukcje: Ustaw kolumny jako tylko do odczytu w kontrolce](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Sprawdź poprawność danych <xref:System.Windows.Forms.DataGridView> wejściowych użytkownika do kontrolki. Aby uzyskać więcej informacji, [zobacz Przewodnik: Sprawdzanie poprawności danych w kontrolce](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, [zobacz Przewodnik: Implementowanie trybu wirtualnego w kontrolce](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.

- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [jak: Dostosuj wygląd komórek w kontrolce](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms i [instrukcje: Ustaw domyślne style komórek dla kontrolki](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
