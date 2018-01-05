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
ms.workload: dotnet
ms.openlocfilehash: b671910ac77b7456492cab871ace3abb61ac7fd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Porady: powiązanie formantu ComboBox lub ListBox (Formularze systemu Windows) z danymi
Możesz powiązać <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> z danymi w celu wykonania zadań, takich jak przeglądanie danych w bazie danych, wprowadzania nowych danych lub edycji istniejących danych.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Aby powiązanie formantu ComboBox lub ListBox  
  
1.  Ustaw `DataSource` właściwości obiektu źródła danych. Źródła danych zawierają <xref:System.Windows.Forms.BindingSource> powiązany z danymi, tabelę danych, widoku danych, zestawu danych, dane widoku, Menedżer, tablicy lub dowolnej klasy, która implementuje <xref:System.Collections.IList> interfejsu. Aby uzyskać więcej informacji, zobacz [danych źródła obsługiwane przez program Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
2.  Ustaw są wiązane tabeli `DisplayMember` dla właściwości Nazwa kolumny w źródle danych.  
  
     \-lub -  
  
     Są wiązane <xref:System.Collections.IList>, ustawioną członkiem wyświetlania właściwości publicznej typu na liście.  
  
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
    >  Jeśli jest powiązana ze źródłem danych, który nie implementuje <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.Collections.ArrayList>, powiązanej kontrolki danych nie zostanie zaktualizowany po zaktualizowaniu źródła danych. Na przykład, jeśli masz pola kombi są powiązane z <xref:System.Collections.ArrayList> i dane są dodawane do <xref:System.Collections.ArrayList>, te nowe elementy nie będą wyświetlane w polu kombi. Można jednak wymusić pola kombi do zaktualizowania przez wywołanie metody <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> i <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metod w wystąpieniu <xref:System.Windows.Forms.BindingContext> klasa do jest związany dany formant.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Wiązanie danych i formularzy Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
