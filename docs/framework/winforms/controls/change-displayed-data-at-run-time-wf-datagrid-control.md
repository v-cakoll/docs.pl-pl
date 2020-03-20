---
title: Zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142384"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.DataGrid> do formantu; jednak <xref:System.Windows.Forms.DataGrid> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [Różnice między formami Windows DataGridView i DataGrid Formantów](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po utworzeniu formularzy <xref:System.Windows.Forms.DataGrid> systemu Windows przy użyciu funkcji czasu projektowania można <xref:System.Data.DataSet> również dynamicznie zmieniać elementy obiektu siatki w czasie wykonywania. Może to obejmować zmiany poszczególnych wartości tabeli lub zmiana źródła <xref:System.Windows.Forms.DataGrid> danych powiązanego z formantem. Zmiany poszczególnych wartości są <xref:System.Data.DataSet> wykonywane za <xref:System.Windows.Forms.DataGrid> pośrednictwem obiektu, a nie formantu.  
  
### <a name="to-change-data-programmatically"></a>Aby programowo zmienić dane  
  
1. Określ żądaną <xref:System.Data.DataSet> tabelę z obiektu oraz żądany wiersz i pole z tabeli i ustaw komórkę równą nowej wartości.  
  
    > [!NOTE]
    > Aby określić pierwszą <xref:System.Data.DataSet> tabelę lub pierwszy wiersz tabeli, użyj 0.  
  
     W poniższym przykładzie pokazano, jak zmienić drugi wpis pierwszego wiersza `Button1`pierwszej tabeli zestawu danych, klikając przycisk . ( <xref:System.Data.DataSet> `ds`) i`0` tabele ( i `1`) zostały wcześniej utworzone.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     (Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     W czasie wykonywania można <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> użyć metody <xref:System.Windows.Forms.DataGrid> do powiązania formantu z innym źródłem danych. Na przykład może mieć kilka formantów ADO.NET danych, każdy połączony z inną bazą danych.  
  
### <a name="to-change-the-datasource-programmatically"></a>Aby zmienić źródło danych programowo  
  
1. Ustaw <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę na nazwę źródła danych i tabeli, z którą chcesz się powiązać.  
  
     Poniższy przykład pokazuje, jak zmienić <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> źródło daty przy użyciu metody na formant danych ADO.NET (adoPubsAuthors), który jest połączony z tabeli Autorzy w bazie danych pubów.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Zestawy danych ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
