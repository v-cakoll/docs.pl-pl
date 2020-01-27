---
title: Zmiana wyświetlanych danych w czasie wykonywania w formancie DataGrid
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
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740587"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po utworzeniu <xref:System.Windows.Forms.DataGrid> Windows Forms przy użyciu funkcji czasu projektowania, można również dynamicznie zmieniać elementy obiektu <xref:System.Data.DataSet> siatki w czasie wykonywania. Może to obejmować zmiany poszczególnych wartości tabeli lub zmianę źródła danych powiązanego z kontrolką <xref:System.Windows.Forms.DataGrid>. Zmiany poszczególnych wartości są wykonywane za pomocą obiektu <xref:System.Data.DataSet>, a nie formantu <xref:System.Windows.Forms.DataGrid>.  
  
### <a name="to-change-data-programmatically"></a>Aby programowo zmienić dane  
  
1. Określ żądaną tabelę z obiektu <xref:System.Data.DataSet> i żądany wiersz i pole z tabeli i ustaw komórkę równą nowej wartości.  
  
    > [!NOTE]
    > Aby określić pierwszą tabelę <xref:System.Data.DataSet> lub pierwszy wiersz tabeli, należy użyć 0.  
  
     Poniższy przykład pokazuje, jak zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając `Button1`. Wcześniej utworzono <xref:System.Data.DataSet> (`ds`) i tabele (`0` i `1`).  
  
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
  
     (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     W czasie wykonywania można użyć metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>, aby powiązać formant <xref:System.Windows.Forms.DataGrid> z innym źródłem danych. Na przykład może istnieć kilka ADO.NETch kontrolek danych połączonych z inną bazą danych.  
  
### <a name="to-change-the-datasource-programmatically"></a>Aby programowo zmienić źródło danych  
  
1. Ustaw metodę <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> na nazwę źródła danych i tabeli, do której chcesz utworzyć powiązanie.  
  
     Poniższy przykład pokazuje, jak zmienić źródło danych przy użyciu metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> na ADO.NET (adoPubsAuthors), która jest połączona z tabelą autorów w bazie danych pubs.  
  
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
- [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
