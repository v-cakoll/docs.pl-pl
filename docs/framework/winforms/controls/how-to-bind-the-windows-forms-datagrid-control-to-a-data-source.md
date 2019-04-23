---
title: 'Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 920a93894cc126f85bc6b618efbe6e9cedea4881
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332576"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze Windows <xref:System.Windows.Forms.DataGrid> kontroli jest specjalnie przeznaczona do wyświetlania informacji ze źródła danych. Powiązywanie formantu w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. Choć można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła są zestawy danych i widokami danych.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Do wiązania danych w formancie DataGrid programowe  
  
1. Pisz kod, aby wypełnić dataset.  
  
     W przypadku zestawu danych lub widoku danych, na podstawie tabeli zestawu danych źródła danych należy dodać kod do formularza, aby wypełnić dataset.  
  
     Dokładne kod, który możesz użyć zależy od tego, gdzie zestaw danych jest wprowadzenie danych. Jeśli trwa wypełnianie zestawu danych bezpośrednio z bazy danych, zazwyczaj wywołujesz `Fill` metody w obrębie adaptera danych, jak w poniższym przykładzie, który wypełnia zestaw danych o nazwie `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Jeśli zestaw danych jest wypełniany z usługi sieci Web XML, zwykle tworzysz wystąpienia usługi w kodzie, a następnie wywołać jedną z jego metod, aby zwrócić zestaw danych. Zestaw danych z usługi sieci Web XML jest następnie Scal do lokalnego zestawu danych. W poniższym przykładzie pokazano, jak utworzyć wystąpienie usługi XML sieci Web o nazwie `CategoriesService`, wywoływanie jej `GetCategories` metoda i scalanie Wynikowy zestaw danych do lokalnego zestawu danych o nazwie `DsCategories1`:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. Wywołaj <xref:System.Windows.Forms.DataGrid> kontrolki <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody przekazanie jej w źródle danych i element członkowski danych. Jeśli jest konieczne jawne przekazywanie element członkowski danych, należy przekazać pusty ciąg.  
  
    > [!NOTE]
    >  Siatki są wiązane po raz pierwszy, można ustawić formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości. Jednak nie można zresetować te właściwości, gdy zostały ustawione. Dlatego zalecane jest, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.  
  
     W poniższym przykładzie pokazano, jak można programowo powiązać tabelę Klienci w zestawie danych o nazwie `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Jeśli klienci jest tylko tabela w zestawie danych, można też powiążesz siatki w ten sposób:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Opcjonalnie) Dodaj style odpowiedniej tabeli i kolumn do siatki. Jeśli nie ma żadnych style tabeli, tabeli, zostanie wyświetlony, ale z minimalnym formatowania i widoczne dla wszystkich kolumn.  
  
## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
