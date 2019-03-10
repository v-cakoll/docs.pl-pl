---
title: 'Instrukcje: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d86ded0b93d876eac4b97938678cafbb22c3ac8a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722441"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Instrukcje: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy
<xref:System.Windows.Forms.BindingNavigator> Formant jest specjalny <xref:System.Windows.Forms.ToolStrip> formant, który jest przeznaczony do nawigowania i manipulowanie nimi formantów w formularzu, które są powiązane z danymi.  
  
 Ponieważ jest on <xref:System.Windows.Forms.ToolStrip> kontroli <xref:System.Windows.Forms.BindingNavigator> składnika można łatwo zmodyfikowany w celu dodania dodatkowych lub alternatywnych poleceń dla użytkownika.  
  
 W poniższej procedurze <xref:System.Windows.Forms.TextBox> kontrolka jest powiązana z danymi i <xref:System.Windows.Forms.ToolStrip> formant, który zostanie dodany do formularza zostanie zmodyfikowany na potrzeby obejmują Załaduj, Zapisz i przyciski "Anuluj".  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Aby dodać obciążenia, Zapisz i przyciski do składnika BindingNavigator "Anuluj"  
  
1.  Dodaj <xref:System.Windows.Forms.TextBox> formantu do formularza.  
  
2.  Powiązać <xref:System.Windows.Forms.BindingSource>, która jest powiązana ze źródłem danych. W tym przykładzie <xref:System.Windows.Forms.BindingSource> jest powiązana z bazą danych.  
  
3.  Po wygenerowaniu karty zestaw danych i tabeli, przeciągnij <xref:System.Windows.Forms.BindingNavigator> formantu do formularza.  
  
4.  Ustaw <xref:System.Windows.Forms.BindingNavigator> kontrolki <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> w formularzu, który jest powiązany z kontrolki.  
  
5.  Wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli.  
  
6.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) więc **zadania BindingNavigator** pojawi się okno dialogowe i wybierz **Edytuj elementy**.  
  
     **Edytor kolekcji elementów** pojawia się.  
  
7.  W **Edytor kolekcji elementów**, wykonaj następujące czynności:  
  
    1.  Dodaj <xref:System.Windows.Forms.ToolStripSeparator> i trzema <xref:System.Windows.Forms.ToolStripButton> elementów, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając **Dodaj** przycisku.  
  
    2.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Name%2A> właściwość przyciski **LoadButton**, **SaveButton**, i **CancelButton**, odpowiednio.  
  
    3.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość przyciski **obciążenia**, **Zapisz**, i **anulować**.  
  
    4.  Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości dla każdego z przycisków, aby **tekstu**. Alternatywnie, można ustawić tę właściwość **obraz** lub **ImageAndText**i Ustaw obraz, który ma być wyświetlany w <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości.  
  
    5.  Kliknij przycisk **OK** aby zamknąć okno dialogowe. Przyciski są dodawane do <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Kliknij prawym przyciskiem myszy formularz, a następnie wybierz **Wyświetl kod**.  
  
9. W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli. Ten kod został wygenerowany podczas tworzenia powiązań danych, w kroku 2. Kod powinien być podobny do następującego: `TableAdapterName.Fill(DataSetName.TableName)`. Będzie ono najbardziej prawdopodobnie w formie <xref:System.Windows.Forms.Form.Load> zdarzeń.  
  
10. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **obciążenia** <xref:System.Windows.Forms.ToolStripButton> utworzonej wcześniej i przenieść ten kod ładowania danych do niego.  
  
     Kod powinien teraz wyglądać podobnie do poniższej:  
  
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
  
11. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **Zapisz** <xref:System.Windows.Forms.ToolStripButton> została utworzona wcześniej, a następnie napisz kod, aby zaktualizować dane w tabeli formant jest powiązany z.  
  
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
    > W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> mają już składnik **Zapisz** przycisk, ale żaden kod nie zostanie wygenerowane przez Windows Forms Designer. W takim przypadku można umieścić powyższy kod w <xref:System.Windows.Forms.ToolStripItem.Click> program obsługi zdarzeń dla tego przycisku, zamiast tworzenia całkowicie nowego przycisku na <xref:System.Windows.Forms.ToolStrip>. Jednak przycisk jest domyślnie wyłączony, musisz więc ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości przycisku `true` poprawnie mieć funkcję przycisku.
  
12. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **anulować** <xref:System.Windows.Forms.ToolStripButton> utworzonej wcześniej i napisać kod, aby anulować wszelkie zmiany do rekordu danych, która jest wyświetlana.  
  
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
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metody jest ograniczone do wiersza danych. Zapisz wszelkie zmiany wprowadzone podczas wyświetlania tego pojedynczego rekordu przed przejdź do następnego rekordu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [BindingSource, składnik — omówienie](bindingsource-component-overview.md)
