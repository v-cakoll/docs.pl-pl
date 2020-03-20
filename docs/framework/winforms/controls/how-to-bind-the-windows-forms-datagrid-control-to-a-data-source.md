---
title: Powiąż formant datagrid ze źródłem danych
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
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182242"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.DataGrid> do formantu; jednak <xref:System.Windows.Forms.DataGrid> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [Różnice między formami Windows DataGridView i DataGrid Formantów](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formant <xref:System.Windows.Forms.DataGrid> Formularze systemu Windows został specjalnie zaprojektowany do wyświetlania informacji ze źródła danych. Formant należy powiązać w <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> czasie wykonywania, wywołując metodę. Chociaż można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i widoki danych.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Aby programowo powiązać dane, formant DataGrid  
  
1. Napisz kod, aby wypełnić zestaw danych.  
  
     Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, dodaj kod do formularza, aby wypełnić zestaw danych.  
  
     Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych jest pobieranie danych. Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywołana `Fill` jest metoda karty danych, jak w `DsCategories1`poniższym przykładzie, która wypełnia zestaw danych o nazwie:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Jeśli zestaw danych jest wypełniany z usługi sieci Web XML, zazwyczaj tworzy się wystąpienie usługi w kodzie, a następnie wywołanie jednej z jego metod, aby zwrócić zestaw danych. Następnie należy scalić zestaw danych z usługi sieci Web XML z lokalnym zestawem danych. Poniższy przykład pokazuje, jak można utworzyć wystąpienie `CategoriesService`usługi sieci `GetCategories` Web XML o nazwie , wywołać `DsCategories1`jego metodę i scalić wynikowy zestaw danych do lokalnego zestawu danych o nazwie:  
  
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
  
2. Wywołanie <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody formantu, przekazując ją źródło danych i element członkowski danych. Jeśli nie trzeba jawnie przekazać element członkowski danych, przekazać pusty ciąg.  
  
    > [!NOTE]
    > Jeśli są wiązanie siatki po raz pierwszy, można <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> ustawić formantu i właściwości. Jednak nie można zresetować te właściwości po ich ustawieniu. W związku z tym zaleca się, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.  
  
     W poniższym przykładzie pokazano, jak programowo można powiązać `DsCustomers1`z tabelą Klienci w zestawie danych o nazwie:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Jeśli tabela Klienci jest jedyną tabelą w zestawie danych, można alternatywnie powiązać siatkę w ten sposób:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Opcjonalnie) Dodaj odpowiednie style tabel i style kolumn do siatki. Jeśli nie ma żadnych stylów tabeli, zobaczysz tabelę, ale z minimalnym formatowaniem i widocznymi wszystkimi kolumnami.  
  
## <a name="see-also"></a>Zobacz też

- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
