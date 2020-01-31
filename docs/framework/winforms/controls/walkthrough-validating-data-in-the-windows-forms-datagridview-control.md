---
title: 'Przewodnik: sprawdzanie poprawności danych w formancie DataGridView'
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
ms.openlocfilehash: 45753fb206ad58616c9a727bd81bd2458db6053e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740105"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Wskazówki: sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows

Podczas wyświetlania funkcji wprowadzania danych dla użytkowników często trzeba sprawdzić poprawność danych wprowadzonych w formularzu. Klasa <xref:System.Windows.Forms.DataGridView> zapewnia wygodny sposób wykonywania walidacji przed zatwierdzeniem danych do magazynu danych. Możesz sprawdzić poprawność danych przez obsługę zdarzenia <xref:System.Windows.Forms.DataGridView.CellValidating>, które jest zgłaszane przez <xref:System.Windows.Forms.DataGridView> po zmianie bieżącej komórki.

W tym instruktażu uzyskasz pobieranie wierszy z tabeli `Customers` w przykładowej bazie danych Northwind i wyświetlanie ich w kontrolce <xref:System.Windows.Forms.DataGridView>. Gdy użytkownik edytuje komórkę w kolumnie `CompanyName` i podejmie próbę opuszczenia komórki, program obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellValidating> sprawdzi nowy ciąg nazwy firmy, aby upewnić się, że nie jest pusty. Jeśli nowa wartość jest pustym ciągiem, <xref:System.Windows.Forms.DataGridView> uniemożliwia przechodzenie kursora przez kursor użytkownika do momentu wprowadzenia niepustego ciągu.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [jak: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do serwera z przykładową bazą danych Northwind SQL Server.

## <a name="creating-the-form"></a>Tworzenie formularza

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Aby sprawdzić poprawność danych wprowadzonych w formancie DataGridView

1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera kontrolkę <xref:System.Windows.Forms.DataGridView> i składnik <xref:System.Windows.Forms.BindingSource>.

    Poniższy przykład kodu zapewnia inicjalizację podstawową i zawiera metodę `Main`.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Zaimplementuj metodę w definicji klasy formularza do obsługi szczegółów połączenia z bazą danych.

    Ten przykład kodu używa metody `GetData`, która zwraca wypełniony obiekt <xref:System.Data.DataTable>. Upewnij się, że zmienna `connectionString` jest ustawiona na wartość, która jest odpowiednia dla bazy danych.

    > [!IMPORTANT]
    > Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows, znanego również jako zabezpieczenia zintegrowane, jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.Load> formularza, które inicjuje <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.BindingSource> i konfiguruje powiązanie danych.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Zaimplementuj procedury obsługi dla zdarzeń <xref:System.Windows.Forms.DataGridView.CellValidating> i <xref:System.Windows.Forms.DataGridView.CellEndEdit> formantu <xref:System.Windows.Forms.DataGridView>.

    Program obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellValidating> jest miejscem, w którym można określić, czy wartość komórki w kolumnie `CompanyName` jest pusta. Jeśli sprawdzanie poprawności wartości komórki nie powiedzie się, ustaw właściwość <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> klasy <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> na `true`. Powoduje to, że formant <xref:System.Windows.Forms.DataGridView> uniemożliwia pozostawienie kursora komórki. Ustaw właściwość <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> w wierszu na ciąg objaśniający. Zostanie wyświetlona ikona błędu z etykietką narzędzia zawierającą tekst błędu. W obsłudze zdarzeń <xref:System.Windows.Forms.DataGridView.CellEndEdit> ustaw właściwość <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> w wierszu na pusty ciąg. Zdarzenie <xref:System.Windows.Forms.DataGridView.CellEndEdit> występuje tylko wtedy, gdy komórka kończy tryb edycji, co nie może zrobić, jeśli nie powiedzie się walidacja.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Skompiluj i uruchom aplikację.

  Zobaczysz <xref:System.Windows.Forms.DataGridView> wypełnione danymi z tabeli `Customers`. Po dwukrotnym kliknięciu komórki w kolumnie `CompanyName` można edytować wartość. Jeśli usuniesz wszystkie znaki i naciśniesz klawisz TAB, aby wyjść z komórki, <xref:System.Windows.Forms.DataGridView> uniemożliwia zakończenie pracy. Po wpisaniu niepustego ciągu do komórki, formant <xref:System.Windows.Forms.DataGridView> umożliwia zamknięcie komórki.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja zapewnia podstawowe informacje o możliwościach kontrolki <xref:System.Windows.Forms.DataGridView>. Wygląd i zachowanie kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować na kilka sposobów:

- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [How to: zmiana stylu obramowania i linii siatki w kontrolce DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Włącz lub Ogranicz dane wejściowe użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [How to: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md)i [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Sprawdź dane wejściowe użytkownika dotyczące błędów związanych z bazą danych. Aby uzyskać więcej informacji, zobacz [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).

- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu komórek w kontrolce datagridview Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) i [instrukcje: ustawianie stylów czcionek i kolorów w kontrolce DataGridView Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
