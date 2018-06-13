---
title: 'Porady: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: f00d874f2a4afcea3498a64fe946a93c83eb7b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537089"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Porady: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy systemu Windows
Formularze systemu Windows można użyć <xref:System.Windows.Forms.ErrorProvider> składnik, aby wyświetlić błędy kolumny w obrębie zestawu danych lub inne źródła danych. Dla <xref:System.Windows.Forms.ErrorProvider> składnik, aby wyświetlić błędy danych na formularzu, nie musi być bezpośrednio skojarzony z formantem. Gdy jest ona powiązana ze źródłem danych, będzie możliwe wyświetlenie ikony błędu obok każdego formantu, który jest powiązany z tym samym źródłem danych.  
  
> [!NOTE]
>  Jeśli zmienisz dostawcy błąd <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> i <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> właściwości w czasie wykonywania, należy użyć <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metody w celu uniknięcia konfliktów.  
  
### <a name="to-display-data-errors"></a>Aby wyświetlić błędy danych  
  
1.  Powiąż składnik do określonej kolumny w tabeli danych.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2.  Ustaw <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwości formularza.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  Ustaw położenie bieżącego rekordu do wiersza, który zawiera błąd kolumny.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [ErrorProvider, składnik — omówienie](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Instrukcje: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
