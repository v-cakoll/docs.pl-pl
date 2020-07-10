---
title: Dodawanie przycisków Załaduj, Zapisz i Anuluj do kontrolki BindingNavigator
description: Dowiedz się, jak dodać przyciski Załaduj, Zapisz i Anuluj do kontrolki Windows Forms BindingNavigator.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173422"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows

<xref:System.Windows.Forms.BindingNavigator>Formant jest <xref:System.Windows.Forms.ToolStrip> formantem specjalnego przeznaczenia, który jest przeznaczony do nawigowania i manipulowania kontrolkami w formularzu, które są powiązane z danymi.

Ponieważ jest to <xref:System.Windows.Forms.ToolStrip> formant, <xref:System.Windows.Forms.BindingNavigator> składnik można łatwo zmodyfikować w taki sposób, aby obejmował dodatkowe lub alternatywne polecenia dla użytkownika.

W poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany z danymi, a <xref:System.Windows.Forms.ToolStrip> kontrolka dodana do formularza zostanie zmodyfikowana w celu uwzględnienia przycisków ładowania, zapisywania i anulowania.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Dodawanie przycisków Załaduj, Zapisz i Anuluj do składnika BindingNavigator

1. W programie Visual Studio Dodaj <xref:System.Windows.Forms.TextBox> kontrolkę do formularza.

2. Powiąż go z <xref:System.Windows.Forms.BindingSource> , który jest powiązany ze źródłem danych. W tym przykładzie jest on <xref:System.Windows.Forms.BindingSource> powiązany z bazą danych.

3. Po wygenerowaniu zestawu danych i karty tabeli przeciągnij <xref:System.Windows.Forms.BindingNavigator> kontrolkę do formularza.

4. Ustaw <xref:System.Windows.Forms.BindingNavigator> Właściwość kontrolki <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> <xref:System.Windows.Forms.BindingSource> na formularzu, który jest powiązany z kontrolkami.

5. Zaznacz <xref:System.Windows.Forms.BindingNavigator> kontrolkę.

6. Kliknij symbol akcji projektanta ( ![ Mała czarna strzałka ](./media/designer-actions-glyph.gif) ), aby okno dialogowe **BindingNavigator zadania** pojawiło się i wybierz pozycję **Edytuj elementy**.

     Zostanie wyświetlony **Edytor kolekcji Items** .

7. W **edytorze kolekcji elementów**wykonaj następujące czynności:

    1. Dodaj a <xref:System.Windows.Forms.ToolStripSeparator> i trzy <xref:System.Windows.Forms.ToolStripButton> elementy, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając przycisk **Dodaj** .

    2. Ustaw <xref:System.Windows.Forms.ToolStripItem.Name%2A> odpowiednio Właściwość przycisków na **LoadButton**, **SaveButton**i **CancelButton**.

    3. Ustaw <xref:System.Windows.Forms.ToolStripItem.Text%2A> Właściwość przycisków do **załadowania**, **zapisania**i **anulowania**.

    4. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Właściwość dla każdego przycisku na **tekst**. Alternatywnie możesz ustawić tę właściwość na **Image** lub **ImageAndText**i ustawić obraz, który ma być wyświetlany we <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości.

    5. Kliknij przycisk **OK**, aby zamknąć okno dialogowe. Przyciski zostaną dodane do <xref:System.Windows.Forms.ToolStrip> .

8. Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.

9. W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli. Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2. Kod powinien wyglądać podobnie do poniższego: `TableAdapterName.Fill(DataSetName.TableName)` . Najprawdopodobniej będzie to w <xref:System.Windows.Forms.Form.Load> przypadku zdarzenia formularza.

10. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **Load** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej ładowania i Przenieś do niego ten kod ładowania danych.

     Kod powinien teraz wyglądać podobnie do poniższego:

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **Save** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej zapisu i napisz kod, aby zaktualizować dane w tabeli, z którą jest powiązany formant.

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> składnik ma już przycisk **Zapisz** , ale nie Wygenerowano żadnego kodu przez Projektant formularzy systemu Windows. W takim przypadku można umieścić poprzedni kod w <xref:System.Windows.Forms.ToolStripItem.Click> obsłudze zdarzeń dla tego przycisku zamiast tworzyć zupełnie nowy przycisk na <xref:System.Windows.Forms.ToolStrip> . Jednak przycisk jest domyślnie wyłączony, dlatego należy ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> Właściwość przycisku na tak, aby `true` działał poprawnie.

12. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **anulowania** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisz kod, aby anulować wszystkie zmiany w wyświetlonym rekordzie danych.

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Metoda jest objęta zakresem wierszy danych. Zapisz wszelkie zmiany wprowadzone podczas wyświetlania danego rekordu przed przejściem do następnego rekordu.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator — Formant](bindingnavigator-control-windows-forms.md)
- [BindingSource — Informacje o składniku](bindingsource-component-overview.md)
