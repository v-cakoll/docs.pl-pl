---
title: 'Instrukcje: Wyświetl błędy w zestawie danych za pomocą składnika ErrorProvider formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 6202ac758d2cbf599c7e48a31ed2804608c70977
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705392"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="13835-102">Instrukcje: Wyświetl błędy w zestawie danych za pomocą składnika ErrorProvider formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="13835-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="13835-103">Można używać formularzy Windows <xref:System.Windows.Forms.ErrorProvider> składnika, aby wyświetlić błędy kolumny w ramach zestawu danych lub innego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="13835-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="13835-104">Aby uzyskać <xref:System.Windows.Forms.ErrorProvider> składnika, aby wyświetlić błędy danych na formularzu, nie musi być bezpośrednio powiązany z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="13835-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="13835-105">Gdy jest powiązany ze źródłem danych, ona wyświetlona ikona błędu obok żadnego formantu, który jest powiązany z tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="13835-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13835-106">Jeśli zmienisz dostawcy błąd <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> i <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> właściwości w czasie wykonywania, należy użyć <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metody w celu uniknięcia konfliktów.</span><span class="sxs-lookup"><span data-stu-id="13835-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="13835-107">Aby wyświetlić błędy danych</span><span class="sxs-lookup"><span data-stu-id="13835-107">To display data errors</span></span>  
  
1.  <span data-ttu-id="13835-108">Powiąż składnik do określonej kolumny w tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="13835-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2.  <span data-ttu-id="13835-109">Ustaw <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwości formularza.</span><span class="sxs-lookup"><span data-stu-id="13835-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  <span data-ttu-id="13835-110">Ustaw pozycję bieżącego rekordu do wiersza, który zawiera błąd kolumny.</span><span class="sxs-lookup"><span data-stu-id="13835-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="13835-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13835-111">See also</span></span>
- [<span data-ttu-id="13835-112">ErrorProvider, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="13835-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="13835-113">Instrukcje: Wyświetlanie ikon błędów weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="13835-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
