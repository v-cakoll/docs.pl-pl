---
title: Powiąż kontrolkę ComboBox lub ListBox z danymi
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
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742036"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="11c00-102">Porady: powiązanie formantu ComboBox lub ListBox (Formularze systemu Windows) z danymi</span><span class="sxs-lookup"><span data-stu-id="11c00-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="11c00-103">Można powiązać <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> z danymi, aby wykonywać zadania, takie jak przeglądanie danych w bazie danych, wprowadzanie nowych danych lub edytowanie istniejących danych.</span><span class="sxs-lookup"><span data-stu-id="11c00-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="11c00-104">Aby powiązać formant ComboBox lub ListBox</span><span class="sxs-lookup"><span data-stu-id="11c00-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="11c00-105">Ustaw właściwość `DataSource` na obiekt źródła danych.</span><span class="sxs-lookup"><span data-stu-id="11c00-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="11c00-106">Możliwe źródła danych obejmują <xref:System.Windows.Forms.BindingSource> powiązane z danymi, tabelą danych, widokiem danych, zestawem danych, menedżerem widoku dane, tablicą lub dowolną klasą, która implementuje interfejs <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="11c00-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="11c00-107">Aby uzyskać więcej informacji, zobacz [źródła danych obsługiwane przez Windows Forms](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="11c00-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="11c00-108">Jeśli tworzysz powiązanie z tabelą, ustaw właściwość `DisplayMember` na nazwę kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="11c00-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="11c00-109">\- lub —</span><span class="sxs-lookup"><span data-stu-id="11c00-109">\- or -</span></span>  
  
     <span data-ttu-id="11c00-110">Jeśli tworzysz powiązanie z <xref:System.Collections.IList>, Ustaw element członkowski wyświetlania na publiczną właściwość typu na liście.</span><span class="sxs-lookup"><span data-stu-id="11c00-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="11c00-111">Jeśli masz powiązanie ze źródłem danych, które nie implementuje interfejsu <xref:System.ComponentModel.IBindingList>, takiego jak <xref:System.Collections.ArrayList>, dane kontrolki powiązanej nie zostaną zaktualizowane po aktualizacji źródła danych.</span><span class="sxs-lookup"><span data-stu-id="11c00-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="11c00-112">Na przykład jeśli masz pole kombi powiązane z <xref:System.Collections.ArrayList>em, a dane są dodawane do <xref:System.Collections.ArrayList>, te nowe elementy nie będą wyświetlane w polu kombi.</span><span class="sxs-lookup"><span data-stu-id="11c00-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="11c00-113">Można jednak wymusić aktualizację pola kombi, wywołując <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metody w wystąpieniu klasy <xref:System.Windows.Forms.BindingContext>, do której jest powiązany formant.</span><span class="sxs-lookup"><span data-stu-id="11c00-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c00-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11c00-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="11c00-115">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11c00-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="11c00-116">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11c00-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="11c00-117">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="11c00-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
