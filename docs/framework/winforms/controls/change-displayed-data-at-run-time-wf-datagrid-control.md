---
title: 'Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: 60ba1e9304320346d505f3f73e1ba93ff6edab63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315858"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po utworzeniu formularze Windows <xref:System.Windows.Forms.DataGrid> przy użyciu funkcje czasu projektowania, również możesz dynamicznie zmieniać elementy <xref:System.Data.DataSet> obiektu siatki w czasie wykonywania. Może to obejmować zmiany albo poszczególne wartości w tabeli lub zmienianie źródła danych, który jest powiązany z <xref:System.Windows.Forms.DataGrid> kontroli. Zmiany w poszczególnych wartości są wykonywane za pomocą <xref:System.Data.DataSet> obiektu nie <xref:System.Windows.Forms.DataGrid> kontroli.  
  
### <a name="to-change-data-programmatically"></a>Programowe zmienianie danych  
  
1. Określ odpowiednią tabelę z <xref:System.Data.DataSet> obiektu i żądany wiersz pola z tabeli i Ustawianie nowej wartości komórki.  
  
    > [!NOTE]
    >  Aby określić pierwszy spis <xref:System.Data.DataSet> lub pierwszy wiersz w tabeli, użyj wartości 0.  
  
     Poniższy przykład pokazuje, jak zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając `Button1`. <xref:System.Data.DataSet> (`ds`) I tabele (`0` i `1`) zostały utworzone wcześniej.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     W czasie, możesz użyć wykonywania <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby powiązać <xref:System.Windows.Forms.DataGrid> kontrolki do innego źródła danych. Na przykład masz kilka [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] formantami danych, każda jest połączona z inną bazą danych.  
  
### <a name="to-change-the-datasource-programmatically"></a>Aby programowo zmienić źródło danych  
  
1. Ustaw <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby nazwa źródła danych i chcesz powiązać z tabeli.  
  
     Poniższy przykład pokazuje, jak zmienić źródło daty przy użyciu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] formant danych (adoPubsAuthors), który jest połączony z tabelą autorów w bazie danych Pubs.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zestawy danych ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
