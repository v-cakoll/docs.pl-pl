---
title: "Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych"
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 185c094b32f0de7a1a26da144601961d92a625b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki przeznaczone do wyświetlania informacji ze źródła danych. Powiązywanie formantu w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. Choć można wyświetlać danych z różnych źródeł danych, najbardziej typowe źródła są widoków danych i zestawów danych.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Do wiązania danych formantu DataGrid programowo  
  
1.  Napisać kod, aby wypełnić dataset.  
  
     Jeśli źródło danych jest wartość dataset lub widok danych na podstawie tabeli zestawu danych, należy dodać kodu do formularza, aby wypełnić dataset.  
  
     Dokładnego kodu, używanego zależy od tego, gdzie zestawu danych jest pobieranie danych. Jeśli jest on wypełnione zestawu danych bezpośrednio z bazy danych, należy zwykle wywołują `Fill` metody adapter danych, jak w poniższym przykładzie, który wypełnia zestawu danych o nazwie `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Jeśli zestaw danych jest wypełniany z usługi XML sieci Web, należy zwykle utworzenia wystąpienia usługi w kodzie, a następnie wywołać jednej z jego metod do zwrócenia zestawu danych. Zestaw danych z usługi XML sieci Web jest następnie scalić w lokalnym zestawu danych. W poniższym przykładzie pokazano, jak można utworzyć wystąpienia usługi XML sieci Web o nazwie `CategoriesService`, wywołaj jego `GetCategories` — metoda i merge Wynikowy zestaw danych do lokalnego zestawu danych o nazwie `DsCategories1`:  
  
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
  
2.  Wywołanie <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody przekazanie jej przez źródło danych i element członkowski danych. Jeśli jawnego przesłania element członkowski danych nie jest wymagane, należy przekazać pusty ciąg.  
  
    > [!NOTE]
    >  Siatki są wiązane po raz pierwszy, można ustawić formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości. Jednak te właściwości nie można zresetować po ich ustawieniu. Dlatego zalecane jest, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.  
  
     W poniższym przykładzie pokazano, jak można programowo powiązać tabeli Klienci w zestawie danych o nazwie `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Jeśli klienci jest tylko tabela w zestawie danych, można też powiąże siatki w ten sposób:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  (Opcjonalnie) Dodaj style właściwe tabeli i Style kolumn do tabeli. Jeśli nie ma żadnych stylów tabeli, zobaczysz tabeli, ale z minimalnym formatowanie i widoczne wszystkie kolumny.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o formancie DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Porady: Dodawanie tabel i kolumn do systemu Windows formantu DataGrid formularzy](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid — formant](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Powiązanie danych formularzy systemu Windows](../../../../docs/framework/winforms/windows-forms-data-binding.md)
