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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917722"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy systemu Windows
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po utworzeniu Windows Forms <xref:System.Windows.Forms.DataGrid> przy użyciu funkcji czasu projektowania może być również konieczne dynamiczne zmianę elementów <xref:System.Data.DataSet> obiektu siatki w czasie wykonywania. Może to obejmować zmiany poszczególnych wartości tabeli lub zmiany źródła danych powiązanego <xref:System.Windows.Forms.DataGrid> z kontrolką. Zmiany poszczególnych wartości są wykonywane za pomocą <xref:System.Data.DataSet> obiektu, a <xref:System.Windows.Forms.DataGrid> nie formantu.  
  
### <a name="to-change-data-programmatically"></a>Aby programowo zmienić dane  
  
1. Określ odpowiednią tabelę z <xref:System.Data.DataSet> obiektu i żądany wiersz i pole z tabeli i ustaw komórkę równą nowej wartości.  
  
    > [!NOTE]
    > Aby określić pierwszą tabelę <xref:System.Data.DataSet> lub pierwszy wiersz tabeli, należy użyć 0.  
  
     Poniższy przykład pokazuje, jak zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając pozycję `Button1`. Zostały utworzone`ds`wcześniej`0` () i tabele `1`(i). <xref:System.Data.DataSet>  
  
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
  
     W czasie wykonywania można użyć metody, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> aby <xref:System.Windows.Forms.DataGrid> powiązać formant z innym źródłem danych. Na przykład może istnieć kilka ADO.NETch kontrolek danych połączonych z inną bazą danych.  
  
### <a name="to-change-the-datasource-programmatically"></a>Aby programowo zmienić źródło danych  
  
1. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Ustaw metodę na nazwę źródła danych i tabeli, do której chcesz utworzyć powiązanie.  
  
     Poniższy przykład pokazuje, jak zmienić źródło daty przy użyciu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody do kontrolki danych ADO.NET (adoPubsAuthors), która jest połączona z tabelą autorów w bazie danych pubs.  
  
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
- [Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Instrukcje: Powiązywanie kontrolki DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
