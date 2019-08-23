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
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922726"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formant Windows Forms <xref:System.Windows.Forms.DataGrid> jest specjalnie zaprojektowany do wyświetlania informacji ze źródła danych. Można powiązać formant w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę. Mimo że można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i ich widoki.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>W celu programowego powiązania formantu DataGrid z danymi  
  
1. Napisz kod, aby wypełnić zestaw danych.  
  
     Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, Dodaj kod do formularza, aby wypełnić zestaw danych.  
  
     Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych pobiera dane. Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywoływana jest `Fill` Metoda adaptera danych, tak jak w poniższym przykładzie, który wypełnia zestaw danych o nazwie: `DsCategories1`  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Jeśli zestaw danych jest wypełniany z poziomu usługi sieci Web XML, zazwyczaj tworzysz wystąpienie usługi w kodzie, a następnie Wywołaj jedną z jej metod, aby zwrócić zestaw danych. Następnie należy scalić zestaw danych z usługi sieci Web XML do lokalnego zestawu danych. W poniższym przykładzie pokazano, jak utworzyć wystąpienie usługi sieci Web XML o nazwie `CategoriesService`, `GetCategories` wywołać metodę i scalić zestaw danych w lokalnym zestawie danych o nazwie `DsCategories1`:  
  
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
  
2. Wywołaj <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę kontrolki,przekazującjądoźródładanychielementuczłonkowskiegodanych.<xref:System.Windows.Forms.DataGrid> Jeśli nie musisz jawnie przekazać elementu członkowskiego danych, Przekaż pusty ciąg.  
  
    > [!NOTE]
    > Jeśli powiążesz siatkę po raz pierwszy, możesz ustawić kontrolkę <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> jej właściwości. Nie można jednak resetować tych właściwości po ich ustawieniu. Dlatego zaleca się, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.  
  
     Poniższy przykład pokazuje, jak można programowo powiązać z tabelą Customers w zestawie danych o nazwie `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Jeśli tabela Customers jest jedyną tabelą w zestawie danych, możesz alternatywnie powiązać siatkę w następujący sposób:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. Obowiązkowe Dodaj odpowiednie style tabeli i Style kolumn do siatki. Jeśli nie ma żadnych stylów tabeli, zostanie wyświetlona tabela, ale z minimalnym formatowaniem i wszystkimi kolumnami widocznymi.  
  
## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
