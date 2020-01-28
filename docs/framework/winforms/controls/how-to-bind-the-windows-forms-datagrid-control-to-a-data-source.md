---
title: Powiązywanie formantu DataGrid ze źródłem danych
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
ms.openlocfilehash: 2634a6bd8ace36bcf7a49120162474a8c04b2b83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746684"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Kontrolka <xref:System.Windows.Forms.DataGrid> Windows Forms jest przeznaczona specjalnie do wyświetlania informacji ze źródła danych. Można powiązać formant w czasie wykonywania, wywołując metodę <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>. Mimo że można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i ich widoki.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>W celu programowego powiązania formantu DataGrid z danymi  
  
1. Napisz kod, aby wypełnić zestaw danych.  
  
     Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, Dodaj kod do formularza, aby wypełnić zestaw danych.  
  
     Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych pobiera dane. Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywoływana jest metoda `Fill` adaptera danych, tak jak w poniższym przykładzie, który wypełnia zestaw danych o nazwie `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Jeśli zestaw danych jest wypełniany z poziomu usługi sieci Web XML, zazwyczaj tworzysz wystąpienie usługi w kodzie, a następnie Wywołaj jedną z jej metod, aby zwrócić zestaw danych. Następnie należy scalić zestaw danych z usługi sieci Web XML do lokalnego zestawu danych. Poniższy przykład pokazuje, jak utworzyć wystąpienie usługi sieci Web XML o nazwie `CategoriesService`, wywołać metodę `GetCategories` i scalić zestaw danych z lokalnym zestawem danych o nazwie `DsCategories1`:  
  
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
  
2. Wywołaj metodę <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> formantu <xref:System.Windows.Forms.DataGrid>, przekazując ją do źródła danych i elementu członkowskiego danych. Jeśli nie musisz jawnie przekazać elementu członkowskiego danych, Przekaż pusty ciąg.  
  
    > [!NOTE]
    > Jeśli powiążesz siatkę po raz pierwszy, możesz ustawić właściwości <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> formantu. Nie można jednak resetować tych właściwości po ich ustawieniu. Dlatego zaleca się, aby zawsze używać metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.  
  
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
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
