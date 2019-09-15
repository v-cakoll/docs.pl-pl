---
title: 'Instrukcje: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991742"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Instrukcje: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows

Formant jest formantem specjalnego przeznaczenia <xref:System.Windows.Forms.ToolStrip> , który jest przeznaczony do nawigowania i manipulowania kontrolkami w formularzu, które są powiązane z danymi. <xref:System.Windows.Forms.BindingNavigator>

Ponieważ jest <xref:System.Windows.Forms.ToolStrip> to formant <xref:System.Windows.Forms.BindingNavigator> , składnik można łatwo zmodyfikować w taki sposób, aby obejmował dodatkowe lub alternatywne polecenia dla użytkownika.

W poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany z danymi, <xref:System.Windows.Forms.ToolStrip> a kontrolka dodana do formularza zostanie zmodyfikowana w celu uwzględnienia przycisków ładowania, zapisywania i anulowania.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Dodawanie przycisków Załaduj, Zapisz i Anuluj do składnika BindingNavigator

1. W programie Visual Studio Dodaj <xref:System.Windows.Forms.TextBox> kontrolkę do formularza.

2. Powiąż go z <xref:System.Windows.Forms.BindingSource>, który jest powiązany ze źródłem danych. W tym przykładzie <xref:System.Windows.Forms.BindingSource> jest on powiązany z bazą danych.

3. Po wygenerowaniu zestawu danych i karty tabeli przeciągnij <xref:System.Windows.Forms.BindingNavigator> kontrolkę do formularza.

4. <xref:System.Windows.Forms.BindingNavigator> Ustaw Właściwość<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> kontrolki na formularzu, który jest powiązany z kontrolkami. <xref:System.Windows.Forms.BindingSource>

5. <xref:System.Windows.Forms.BindingNavigator> Zaznacz kontrolkę.

6. Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), aby otworzyć okno dialogowe **zadania** , a następnie wybierz pozycję **Edytuj elementy**.

     Zostanie wyświetlony **Edytor kolekcji Items** .

7. W **edytorze kolekcji elementów**wykonaj następujące czynności:

    1. Dodaj a <xref:System.Windows.Forms.ToolStripButton>itrzy elementy, <xref:System.Windows.Forms.ToolStripItem> wybierając odpowiedni typ i klikając przycisk Dodaj. <xref:System.Windows.Forms.ToolStripSeparator>

    2. Ustaw odpowiednioWłaściwość przycisków na LoadButton, SaveButton i CancelButton. <xref:System.Windows.Forms.ToolStripItem.Name%2A>

    3. Ustaw właściwość przycisków do **załadowania**, **zapisania**i **anulowania.** <xref:System.Windows.Forms.ToolStripItem.Text%2A>

    4. Ustaw właściwość dla każdego przycisku na **tekst.** <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Alternatywnie możesz ustawić tę właściwość na **Image** lub **ImageAndText**i ustawić obraz, który ma być <xref:System.Windows.Forms.ToolStripItem.Image%2A> wyświetlany we właściwości.

    5. Kliknij przycisk **OK** , aby zamknąć okno dialogowe. Przyciski zostaną dodane do <xref:System.Windows.Forms.ToolStrip>.

8. Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.

9. W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli. Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2. Kod powinien wyglądać podobnie do poniższego: `TableAdapterName.Fill(DataSetName.TableName)`. Najprawdopodobniej będzie to w <xref:System.Windows.Forms.Form.Load> przypadku zdarzenia formularza.

10. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia utworzonego wcześniej **ładowania** <xref:System.Windows.Forms.ToolStripButton> i Przenieś do niego ten kod ładowania danych.

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

11. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia utworzonego wcześniej **zapisu** <xref:System.Windows.Forms.ToolStripButton> i napisz kod, aby zaktualizować dane w tabeli, z którą jest powiązany formant.

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
    > W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> składnik ma już przycisk **Zapisz** , ale nie Wygenerowano żadnego kodu przez Projektant formularzy systemu Windows. W takim przypadku można umieścić poprzedni kod w <xref:System.Windows.Forms.ToolStripItem.Click> obsłudze zdarzeń dla tego przycisku zamiast tworzyć zupełnie nowy przycisk <xref:System.Windows.Forms.ToolStrip>na. Jednak przycisk jest domyślnie wyłączony, dlatego należy ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwość przycisku na `true` tak, aby działał poprawnie.

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda jest objęta zakresem wierszy danych. Zapisz wszelkie zmiany wprowadzone podczas wyświetlania danego rekordu przed przejściem do następnego rekordu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [BindingSource, składnik — omówienie](bindingsource-component-overview.md)
