---
title: 'Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046376"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy systemu Windows

Podczas wyświetlania funkcji wprowadzania danych dla użytkowników często trzeba sprawdzić poprawność danych wprowadzonych w formularzu. <xref:System.Windows.Forms.DataGridView> Klasa zapewnia wygodny sposób wykonywania walidacji przed zatwierdzeniem danych do magazynu danych. Możesz sprawdzić poprawność danych, <xref:System.Windows.Forms.DataGridView.CellValidating> obsługując zdarzenie, które jest zgłaszane <xref:System.Windows.Forms.DataGridView> przez chwilę zmiany bieżącej komórki.

W tym instruktażu uzyskasz pobieranie wierszy z `Customers` tabeli w przykładowej bazie danych Northwind i wyświetlanie ich <xref:System.Windows.Forms.DataGridView> w kontrolce. Gdy użytkownik edytuje komórkę w `CompanyName` kolumnie i próbuje opuścić komórkę <xref:System.Windows.Forms.DataGridView.CellValidating> , program obsługi zdarzeń sprawdzi nowy ciąg nazwy firmy, aby upewnić się, że nie jest pusty. Jeśli nowa wartość jest pustym ciągiem, <xref:System.Windows.Forms.DataGridView> uniemożliwi to przeprowadzenie kursora użytkownika od opuszczenia komórki do momentu wprowadzenia niepustego ciągu.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Sprawdź poprawność danych w kontrolce](how-to-validate-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do serwera z przykładową bazą danych Northwind SQL Server.

## <a name="creating-the-form"></a>Tworzenie formularza

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Aby sprawdzić poprawność danych wprowadzonych w formancie DataGridView

1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.DataGridView> zawiera kontrolkę i <xref:System.Windows.Forms.BindingSource> składnik.

    Poniższy przykład kodu zapewnia inicjalizację podstawową i zawiera `Main` metodę.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Zaimplementuj metodę w definicji klasy formularza do obsługi szczegółów połączenia z bazą danych.

    Ten przykład kodu używa `GetData` metody, która zwraca wypełniony <xref:System.Data.DataTable> obiekt. Upewnij się, że ustawiono `connectionString` zmienną na wartość odpowiednią dla bazy danych.

    > [!IMPORTANT]
    > Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows, znanego również jako zabezpieczenia zintegrowane, jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Zaimplementuj procedurę obsługi dla <xref:System.Windows.Forms.Form.Load> zdarzenia formularza, która <xref:System.Windows.Forms.DataGridView> inicjuje i <xref:System.Windows.Forms.BindingSource> konfiguruje powiązanie danych.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Zaimplementuj procedury obsługi dla <xref:System.Windows.Forms.DataGridView> zdarzeń <xref:System.Windows.Forms.DataGridView.CellValidating> kontrolki <xref:System.Windows.Forms.DataGridView.CellEndEdit> i.

    Procedura obsługi `CompanyName` zdarzeń pozwala określić, czy wartość komórki w kolumnie jest pusta. <xref:System.Windows.Forms.DataGridView.CellValidating> Jeśli wartość komórki nie powiedzie się, ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Właściwość <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> klasy na `true`. Powoduje to, <xref:System.Windows.Forms.DataGridView> że formant uniemożliwia pozostawienie kursora od komórki. <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> Ustaw właściwość w wierszu na ciąg objaśniający. Zostanie wyświetlona ikona błędu z etykietką narzędzia zawierającą tekst błędu. W programie obsługi <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>zdarzeńUstaw właściwość w wierszu na pusty ciąg. <xref:System.Windows.Forms.DataGridView.CellEndEdit> <xref:System.Windows.Forms.DataGridView.CellEndEdit> Zdarzenie występuje tylko wtedy, gdy komórka kończy tryb edycji, którego nie można zrobić, jeśli nie powiedzie się walidacja.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Skompiluj i uruchom aplikację.

  Zobaczysz dane `Customers` wypełnioneztabeli.<xref:System.Windows.Forms.DataGridView> Po dwukrotnym kliknięciu komórki w `CompanyName` kolumnie można edytować wartość. Jeśli usuniesz wszystkie znaki i naciśniesz klawisz Tab, aby wyjść z komórki, <xref:System.Windows.Forms.DataGridView> zapobiega to zamknięciu. Po wpisaniu niepustego ciągu do komórki, <xref:System.Windows.Forms.DataGridView> kontrolka umożliwia zamknięcie komórki.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja zapewnia podstawowe informacje o <xref:System.Windows.Forms.DataGridView> możliwościach formantu. Wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontrolki można dostosować na kilka sposobów:

- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [jak: Zmień style obramowania i linii siatki w kontrolce](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.

- Włącz lub Ogranicz dane wejściowe użytkownika do <xref:System.Windows.Forms.DataGridView> kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce](prevent-row-addition-and-deletion-datagridview.md)DataGridView Windows Forms i [instrukcje: Ustaw kolumny jako tylko do odczytu w kontrolce](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Sprawdź dane wejściowe użytkownika dotyczące błędów związanych z bazą danych. Aby uzyskać więcej informacji, [zobacz Przewodnik: Obsługa błędów występujących podczas wprowadzania danych w kontrolce](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView Windows Forms.

- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, [zobacz Przewodnik: Implementowanie trybu wirtualnego w kontrolce](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.

- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [jak: Dostosuj wygląd komórek w kontrolce](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms i [instrukcje: Ustawianie stylów czcionek i kolorów w kontrolce](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: Obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
