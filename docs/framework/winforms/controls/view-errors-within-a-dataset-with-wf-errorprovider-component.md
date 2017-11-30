---
title: "Porady: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy systemu Windows"
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
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28c90df258db8480f68eea05f922b36f30d81a3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="16308-102">Porady: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16308-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="16308-103">Formularze systemu Windows można użyć <xref:System.Windows.Forms.ErrorProvider> składnik, aby wyświetlić błędy kolumny w obrębie zestawu danych lub inne źródła danych.</span><span class="sxs-lookup"><span data-stu-id="16308-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="16308-104">Dla <xref:System.Windows.Forms.ErrorProvider> składnik, aby wyświetlić błędy danych na formularzu, nie musi być bezpośrednio skojarzony z formantem.</span><span class="sxs-lookup"><span data-stu-id="16308-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="16308-105">Gdy jest ona powiązana ze źródłem danych, będzie możliwe wyświetlenie ikony błędu obok każdego formantu, który jest powiązany z tym samym źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="16308-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16308-106">Jeśli zmienisz dostawcy błąd <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> i <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> właściwości w czasie wykonywania, należy użyć <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metody w celu uniknięcia konfliktów.</span><span class="sxs-lookup"><span data-stu-id="16308-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="16308-107">Aby wyświetlić błędy danych</span><span class="sxs-lookup"><span data-stu-id="16308-107">To display data errors</span></span>  
  
1.  <span data-ttu-id="16308-108">Powiąż składnik do określonej kolumny w tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="16308-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2.  <span data-ttu-id="16308-109">Ustaw <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwości formularza.</span><span class="sxs-lookup"><span data-stu-id="16308-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  <span data-ttu-id="16308-110">Ustaw położenie bieżącego rekordu do wiersza, który zawiera błąd kolumny.</span><span class="sxs-lookup"><span data-stu-id="16308-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="16308-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16308-111">See Also</span></span>  
 [<span data-ttu-id="16308-112">Informacje o składniku ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="16308-112">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="16308-113">Porady: wyświetlanie ikon błędów dotyczących weryfikacji formularza z systemu Windows składnika ErrorProvider formularzy</span><span class="sxs-lookup"><span data-stu-id="16308-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
