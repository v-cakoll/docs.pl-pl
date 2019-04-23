---
title: 'Instrukcje: powiązanie kontrolki ComboBox lub ListBox (Formularze systemu Windows) z danymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306056"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="3fdc4-102">Instrukcje: powiązanie kontrolki ComboBox lub ListBox (Formularze systemu Windows) z danymi</span><span class="sxs-lookup"><span data-stu-id="3fdc4-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="3fdc4-103">Możesz powiązać <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> z danymi w celu wykonania zadania, takie jak przeglądanie danych w bazie danych, wprowadzając nowe dane lub edycji istniejących danych.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="3fdc4-104">Do wiązania kontrolki ComboBox lub ListBox</span><span class="sxs-lookup"><span data-stu-id="3fdc4-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="3fdc4-105">Ustaw `DataSource` właściwość do obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="3fdc4-106">Źródła danych zawierają <xref:System.Windows.Forms.BindingSource> powiązany z danymi, tabeli danych, widoku danych, zestaw danych, dane widoku menedżera, tablicy lub dowolnej klasy, która implementuje <xref:System.Collections.IList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="3fdc4-107">Aby uzyskać więcej informacji, zobacz [źródła danych obsługiwane przez formularze Windows](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3fdc4-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="3fdc4-108">Jeśli powiązania do tabeli `DisplayMember` właściwość na nazwę kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="3fdc4-109">\- lub —</span><span class="sxs-lookup"><span data-stu-id="3fdc4-109">\- or -</span></span>  
  
     <span data-ttu-id="3fdc4-110">Jeśli dokonywane jest wiązanie <xref:System.Collections.IList>, ustaw członka wyświetlana właściwość publiczną typu na liście.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3fdc4-111">Jeśli jesteś zobowiązany do źródła danych, który nie implementuje <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.Collections.ArrayList>, powiązanej kontrolki danych nie zostanie zaktualizowany, gdy źródło danych zostanie zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="3fdc4-112">Na przykład, jeśli masz pole kombi są powiązane z <xref:System.Collections.ArrayList> i dane są dodawane do <xref:System.Collections.ArrayList>, te nowe elementy nie będą wyświetlane w polu kombi.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="3fdc4-113">Jednak można wymusić pola kombi do zaktualizowania przez wywołanie metody <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metod w wystąpieniu programu <xref:System.Windows.Forms.BindingContext> klasy, do którego formantem.</span><span class="sxs-lookup"><span data-stu-id="3fdc4-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fdc4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fdc4-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="3fdc4-115">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3fdc4-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="3fdc4-116">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3fdc4-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="3fdc4-117">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="3fdc4-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
