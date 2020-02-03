---
title: Wyświetlanie błędów w ramach zestawu danych za pomocą składnika ErrorProvider
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 8c2155bf288db89b5d53567738fd399b915d50b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745454"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="93545-102">Porady: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="93545-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="93545-103">Można użyć składnika <xref:System.Windows.Forms.ErrorProvider> Windows Forms, aby wyświetlić błędy kolumn w zestawie danych lub innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="93545-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="93545-104">Aby składnik <xref:System.Windows.Forms.ErrorProvider> wyświetlał błędy danych w formularzu, nie musi być bezpośrednio skojarzony z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="93545-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="93545-105">Gdy jest on powiązany ze źródłem danych, może wyświetlić ikonę błędu obok każdej kontrolki, która jest powiązana z tym samym źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="93545-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93545-106">W przypadku zmiany właściwości <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> i <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> dostawcy błędów w czasie wykonywania należy użyć metody <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A>, aby uniknąć konfliktów.</span><span class="sxs-lookup"><span data-stu-id="93545-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="93545-107">Aby wyświetlić błędy danych</span><span class="sxs-lookup"><span data-stu-id="93545-107">To display data errors</span></span>  
  
1. <span data-ttu-id="93545-108">Powiąż składnik z określoną kolumną w tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="93545-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2. <span data-ttu-id="93545-109">Ustaw właściwość <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> na formularz.</span><span class="sxs-lookup"><span data-stu-id="93545-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. <span data-ttu-id="93545-110">Ustaw pozycję bieżącego rekordu na wiersz zawierający błąd kolumny.</span><span class="sxs-lookup"><span data-stu-id="93545-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="93545-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93545-111">See also</span></span>

- [<span data-ttu-id="93545-112">ErrorProvider, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="93545-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="93545-113">Instrukcje: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93545-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
