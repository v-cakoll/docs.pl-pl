---
title: 'Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea90c3532203a61beded5eceeee5cf535a74b87b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po utworzeniu formularzy systemu Windows <xref:System.Windows.Forms.DataGrid> przy użyciu funkcje czasu projektowania, możesz również dynamicznie zmiany elementów <xref:System.Data.DataSet> obiektu siatki w czasie wykonywania. Może to obejmować zmiany albo poszczególnych wartości w tabeli lub zmiana źródła danych jest powiązany z <xref:System.Windows.Forms.DataGrid> formantu. Zmiany w poszczególnych wartości są wykonywane za pomocą <xref:System.Data.DataSet> obiektu nie <xref:System.Windows.Forms.DataGrid> formantu.  
  
### <a name="to-change-data-programmatically"></a>Aby programowo zmienić danych  
  
1.  Określ żądaną tabelę z <xref:System.Data.DataSet> obiekt i żądanego wiersza i pola z tabeli oraz ustaw nowe wartości komórki.  
  
    > [!NOTE]
    >  Aby określić w pierwszej tabeli z <xref:System.Data.DataSet> lub pierwszego wiersza tabeli, użyj wartości 0.  
  
     Poniższy przykład przedstawia sposób zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając `Button1`. <xref:System.Data.DataSet> (`ds`) I tabele (`0` i `1`) wcześniej zostały utworzone.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     W czasie, można użyć wykonywania <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby powiązać <xref:System.Windows.Forms.DataGrid> formantu z innym źródłem danych. Na przykład może mieć kilka [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] formantów danych każdy jest połączony z inną bazą danych.  
  
### <a name="to-change-the-datasource-programmatically"></a>Aby programowo zmienić źródła danych  
  
1.  Ustaw <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę nazwę źródła danych i chcesz powiązać z tabeli.  
  
     Poniższy przykład przedstawia sposób zmienić przy użyciu źródła Data <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] formantu danych (adoPubsAuthors), który jest podłączony do tabeli Autorzy w bazie danych Pubs.  
  
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
 [Zestawy danych ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
