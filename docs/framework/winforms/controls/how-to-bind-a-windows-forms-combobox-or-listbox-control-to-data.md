---
title: "Porady: powiązanie formantu ComboBox lub ListBox (Formularze systemu Windows) z danymi"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6193e4cc86a470f046c220dc21150e0fc0bf792a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="cc116-102">Porady: powiązanie formantu ComboBox lub ListBox (Formularze systemu Windows) z danymi</span><span class="sxs-lookup"><span data-stu-id="cc116-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="cc116-103">Możesz powiązać <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> z danymi w celu wykonania zadań, takich jak przeglądanie danych w bazie danych, wprowadzania nowych danych lub edycji istniejących danych.</span><span class="sxs-lookup"><span data-stu-id="cc116-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="cc116-104">Aby powiązanie formantu ComboBox lub ListBox</span><span class="sxs-lookup"><span data-stu-id="cc116-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="cc116-105">Ustaw `DataSource` właściwości obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cc116-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="cc116-106">Źródła danych zawierają <xref:System.Windows.Forms.BindingSource> powiązany z danymi, tabelę danych, widoku danych, zestawu danych, dane widoku, Menedżer, tablicy lub dowolnej klasy, która implementuje <xref:System.Collections.IList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc116-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="cc116-107">Aby uzyskać więcej informacji, zobacz [danych źródła obsługiwane przez program Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cc116-107">For more information, see [Data Sources Supported by Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="cc116-108">Ustaw są wiązane tabeli `DisplayMember` dla właściwości Nazwa kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="cc116-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="cc116-109">\-lub -</span><span class="sxs-lookup"><span data-stu-id="cc116-109">\- or -</span></span>  
  
     <span data-ttu-id="cc116-110">Są wiązane <xref:System.Collections.IList>, ustawioną członkiem wyświetlania właściwości publicznej typu na liście.</span><span class="sxs-lookup"><span data-stu-id="cc116-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    >  <span data-ttu-id="cc116-111">Jeśli jest powiązana ze źródłem danych, który nie implementuje <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.Collections.ArrayList>, powiązanej kontrolki danych nie zostanie zaktualizowany po zaktualizowaniu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cc116-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="cc116-112">Na przykład, jeśli masz pola kombi są powiązane z <xref:System.Collections.ArrayList> i dane są dodawane do <xref:System.Collections.ArrayList>, te nowe elementy nie będą wyświetlane w polu kombi.</span><span class="sxs-lookup"><span data-stu-id="cc116-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="cc116-113">Można jednak wymusić pola kombi do zaktualizowania przez wywołanie metody <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metod w wystąpieniu <xref:System.Windows.Forms.BindingContext> klasa do jest związany dany formant.</span><span class="sxs-lookup"><span data-stu-id="cc116-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc116-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc116-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="cc116-115">Powiązanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc116-115">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="cc116-116">Powiązanie danych i formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc116-116">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="cc116-117">Formanty używane do obsługi opcji List formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc116-117">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
