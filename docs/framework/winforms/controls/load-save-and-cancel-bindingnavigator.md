---
title: Dodawanie przycisków Załaduj, Zapisz i Anuluj do kontrolki BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 0305df5e7566f9441ce09fa3346a8b2dc67c8943
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627971"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows

Formant <xref:System.Windows.Forms.BindingNavigator> to specjalny <xref:System.Windows.Forms.ToolStrip> formant, który jest przeznaczony do nawigowania i manipulowania kontrolkami w formularzu, które są powiązane z danymi.

Ponieważ jest to formant <xref:System.Windows.Forms.ToolStrip>, składnik <xref:System.Windows.Forms.BindingNavigator> można łatwo zmodyfikować w taki sposób, aby obejmował dodatkowe lub alternatywne polecenia dla użytkownika.

W poniższej procedurze formant <xref:System.Windows.Forms.TextBox> jest powiązany z danymi, a kontrolka <xref:System.Windows.Forms.ToolStrip>, która jest dodawana do formularza, zostanie zmodyfikowana w taki sposób, aby obejmowała przyciski Load, Save i Cancel.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Dodawanie przycisków Załaduj, Zapisz i Anuluj do składnika BindingNavigator

1. W programie Visual Studio Dodaj kontrolkę <xref:System.Windows.Forms.TextBox> do formularza.

2. Powiąż go z <xref:System.Windows.Forms.BindingSource>, który jest powiązany ze źródłem danych. W tym przykładzie <xref:System.Windows.Forms.BindingSource> jest powiązany z bazą danych.

3. Po wygenerowaniu karty zestawu danych i tabeli przeciągnij kontrolkę <xref:System.Windows.Forms.BindingNavigator> do formularza.

4. Ustaw właściwość <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> kontrolki <xref:System.Windows.Forms.BindingNavigator> na <xref:System.Windows.Forms.BindingSource> w formularzu, który jest powiązany z kontrolkami.

5. Wybierz kontrolkę <xref:System.Windows.Forms.BindingNavigator>.

6. Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)), a następnie wyświetlenie okna dialogowego **zadania BindingNavigator** i wybierz pozycję **Edytuj elementy**.

     Zostanie wyświetlony **Edytor kolekcji Items** .

7. W **edytorze kolekcji elementów**wykonaj następujące czynności:

    1. Dodaj <xref:System.Windows.Forms.ToolStripSeparator> i trzy elementy <xref:System.Windows.Forms.ToolStripButton>, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając przycisk **Dodaj** .

    2. Ustaw odpowiednio Właściwość <xref:System.Windows.Forms.ToolStripItem.Name%2A> przycisków **LoadButton**, **SaveButton**i **CancelButton**.

    3. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> przycisków do **załadowania**, **zapisania**i **anulowania**.

    4. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> dla każdego przycisku na **tekst**. Alternatywnie możesz ustawić tę właściwość na **Image** lub **ImageAndText**i ustawić obraz, który ma być wyświetlany we właściwości <xref:System.Windows.Forms.ToolStripItem.Image%2A>.

    5. Kliknij przycisk **OK**, aby zamknąć okno dialogowe. Przyciski są dodawane do <xref:System.Windows.Forms.ToolStrip>.

8. Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.

9. W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli. Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2. Kod powinien wyglądać podobnie do poniższego: `TableAdapterName.Fill(DataSetName.TableName)`. Najprawdopodobniej będzie to w zdarzeniu <xref:System.Windows.Forms.Form.Load> formularza.

10. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStripButton> **Załaduj** wcześniej utworzonego i Przenieś do niego ten kod ładowania danych.

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

11. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> utworzonego wcześniej<xref:System.Windows.Forms.ToolStripButton> **zapisywania** i napisz kod, aby zaktualizować dane w tabeli, z którą jest powiązany formant.

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
    > W niektórych przypadkach składnik <xref:System.Windows.Forms.BindingNavigator> ma już przycisk **Zapisz** , ale nie Wygenerowano żadnego kodu przez Projektant formularzy systemu Windows. W takim przypadku można umieścić poprzedni kod w obsłudze zdarzeń <xref:System.Windows.Forms.ToolStripItem.Click> dla tego przycisku zamiast tworzyć zupełnie nowy przycisk na <xref:System.Windows.Forms.ToolStrip>. Jednak przycisk jest domyślnie wyłączony, dlatego należy ustawić właściwość <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> przycisku, aby `true`, aby działał poprawnie.

12. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisz **kod, aby** anulować wszystkie zmiany w wyświetlonym rekordzie danych.

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
    > Metoda <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> jest objęta zakresem wierszy danych. Zapisz wszelkie zmiany wprowadzone podczas wyświetlania danego rekordu przed przejściem do następnego rekordu.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [BindingSource, składnik — omówienie](bindingsource-component-overview.md)
