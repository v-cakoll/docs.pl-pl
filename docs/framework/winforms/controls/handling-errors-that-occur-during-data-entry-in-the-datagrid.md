---
title: 'Przewodnik: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView'
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
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738740"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Wskazówki: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows

Obsługa błędów z bazowego magazynu danych jest funkcją wymaganą dla aplikacji do wprowadzania danych. Formant Windows Forms <xref:System.Windows.Forms.DataGridView> ułatwia to poprzez ujawnienie zdarzenia <xref:System.Windows.Forms.DataGridView.DataError>, które jest zgłaszane, gdy magazyn danych wykryje naruszenie ograniczenia lub naruszoną regułę biznesową.

W tym instruktażu uzyskasz pobieranie wierszy z tabeli `Customers` w przykładowej bazie danych Northwind i wyświetlanie ich w kontrolce <xref:System.Windows.Forms.DataGridView>. W przypadku wykrycia zduplikowanej wartości `CustomerID` w nowym wierszu lub zmodyfikowanym wierszu <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie zostanie wykonane, które zostanie obsłużone przez wyświetlenie <xref:System.Windows.Forms.MessageBox> opisującego wyjątek.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do serwera z przykładową bazą danych Northwind SQL Server.

## <a name="creating-the-form"></a>Tworzenie formularza

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Aby obsłużyć błędy wprowadzania danych w formancie DataGridView

1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera kontrolkę <xref:System.Windows.Forms.DataGridView> i składnik <xref:System.Windows.Forms.BindingSource>.

    Poniższy przykład kodu zapewnia inicjalizację podstawową i zawiera metodę `Main`.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Zaimplementuj metodę w definicji klasy formularza do obsługi szczegółów połączenia z bazą danych.

    Ten przykład kodu używa metody `GetData`, która zwraca wypełniony obiekt <xref:System.Data.DataTable>. Upewnij się, że zmienna `connectionString` jest ustawiona na wartość, która jest odpowiednia dla bazy danych.

    > [!IMPORTANT]
    > Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.Load> formularza, które inicjuje <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.BindingSource> i konfiguruje powiązanie danych.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Obsłuż zdarzenie <xref:System.Windows.Forms.DataGridView.DataError> w <xref:System.Windows.Forms.DataGridView>.

    Jeśli kontekstem błędu jest operacja zatwierdzania, Wyświetl błąd w <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Naciśnij klawisz F5, aby uruchomić aplikację.

  Zobaczysz, że formant <xref:System.Windows.Forms.DataGridView> wypełniony danymi z tabeli Customers. Jeśli wprowadzisz zduplikowaną wartość `CustomerID` i zatwierdzisz edycję, wartość komórki zostanie automatycznie przywrócona, a zobaczysz <xref:System.Windows.Forms.MessageBox>, który wyświetla błąd wprowadzania danych.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja zapewnia podstawowe informacje o możliwościach kontrolki <xref:System.Windows.Forms.DataGridView>. Wygląd i zachowanie kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować na kilka sposobów:

- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [How to: zmiana stylu obramowania i linii siatki w kontrolce DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Włącz lub Ogranicz dane wejściowe użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [How to: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md)i [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Sprawdź poprawność danych wejściowych użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu komórek w kontrolce datagridview Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) i [instrukcje: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
