---
title: "Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd45b33fb1f99c280e126b9e601692a85da5dba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows
<xref:System.Windows.Forms.BindingNavigator> Formant jest specjalnych <xref:System.Windows.Forms.ToolStrip> formant, który jest przeznaczony do nawigowania i operowanie nimi formantów w formularzu, które są związane z danymi.  
  
 Ponieważ jest on <xref:System.Windows.Forms.ToolStrip> kontroli, <xref:System.Windows.Forms.BindingNavigator> składnika można łatwo zmodyfikowany w celu dodania dodatkowych lub alternatywnych poleceń dla użytkownika.  
  
 W poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany z danymi, a <xref:System.Windows.Forms.ToolStrip> formant, który zostanie dodany do formularza są modyfikowane w celu uwzględnienia obciążenia, Zapisz, a przyciski "Anuluj".  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Aby dodać obciążenia, Zapisz i Anuluj przycisków składnika BindingNavigator  
  
1.  Dodaj <xref:System.Windows.Forms.TextBox> sterowania do formularza.  
  
2.  Aby powiązać <xref:System.Windows.Forms.BindingSource>, która jest powiązana ze źródłem danych. Na przykład <xref:System.Windows.Forms.BindingSource> jest powiązany z bazą danych.  
  
3.  Po wygenerowaniu zestawu danych i tabeli karty, przeciągnij <xref:System.Windows.Forms.BindingNavigator> sterowania do formularza.  
  
4.  Ustaw <xref:System.Windows.Forms.BindingNavigator> formantu <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> na formularz, który jest powiązany z kontrolki.  
  
5.  Wybierz <xref:System.Windows.Forms.BindingNavigator> formantu.  
  
6.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tak **zadania BindingNavigator** pojawi się okno dialogowe i wybierz **edytowanie elementów**.  
  
     **Edytora kolekcji elementy** pojawi się.  
  
7.  W **edytora kolekcji elementy**, wykonaj następujące czynności:  
  
    1.  Dodaj <xref:System.Windows.Forms.ToolStripSeparator> i trzy <xref:System.Windows.Forms.ToolStripButton> elementów, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając **Dodaj** przycisku.  
  
    2.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Name%2A> właściwości przycisków, aby**LoadButton**,**SaveButton**, i**CancelButton**odpowiednio.  
  
    3.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości przycisków, aby**obciążenia** `,` **zapisać**, i**anulować**.  
  
    4.  Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości dla każdego z przycisków, aby**tekstu**. Można też ustawić tę właściwość na**obrazu**lub**ImageAndText**i Ustaw obraz, który ma być wyświetlany w <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości.  
  
    5.  Kliknij przycisk **OK** aby zamknąć okno dialogowe. Przyciski są dodawane do <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Kliknij prawym przyciskiem myszy formularz, a następnie wybierz pozycję **kod widoku**.  
  
9. W edytorze kodu Znajdź wiersz kodu wczytuje dane do karty tabeli. Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2. Kod powinien być podobny do następującego: `TableAdapterName.Fill(DataSetName.TableName)`. Będzie on większość prawdopodobnie w postaci <xref:System.Windows.Forms.Form.Load> zdarzeń.  
  
10. Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie**obciążenia** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i Przenieś ten kod ładowania danych do niego.  
  
     Kod powinna wyglądać podobnie do poniższej:  
  
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
  
11. Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **zapisać** <xref:System.Windows.Forms.ToolStripButton> wcześniej utworzony i kod zapisu, aby zaktualizować dane w tabeli formant jest powiązany z.  
  
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
    >  W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> składnik nie ma jeszcze**zapisać** przycisku, ale żaden kod nie zostanie wygenerowane przez projektanta formularzy systemu Windows. W takim przypadku można umieścić w powyższym kodzie <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla tego przycisku, zamiast tworzenia zupełnie nowy przycisk na <xref:System.Windows.Forms.ToolStrip>. Jednak przycisku jest domyślnie wyłączona, dlatego należy ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwość przycisk, aby `true` mają poprawnie funkcja przycisku.  
  
12. Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie**anulować** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisać kod, aby anulować wszystkie zmiany do rekordu danych, która jest wyświetlana.  
  
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
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda obejmuje wiersz danych. Zapisz wszelkie zmiany wprowadzone podczas wyświetlania tego pojedynczego rekordu przed przejście do następnego rekordu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [BindingNavigator, kontrolka](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [BindingSource, składnik — omówienie](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
