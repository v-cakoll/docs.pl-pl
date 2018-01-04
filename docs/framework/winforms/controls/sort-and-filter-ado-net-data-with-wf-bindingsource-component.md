---
title: "Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows"
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
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 310f90c7b95d74f1fab8ab2e9871d6c1a0937c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows
Mogą uwidaczniać sortowania i filtrowania możliwości <xref:System.Windows.Forms.BindingSource> kontrolować za pośrednictwem <xref:System.Windows.Forms.BindingSource.Sort%2A> i <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości. Możesz zastosować proste sortowanie, gdy źródła danych jest <xref:System.ComponentModel.IBindingList>, i można zastosować filtrowanie i sortowanie, gdy źródłem danych jest zaawansowane <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość wymaga standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Składnia: ciąg reprezentujący nazwę kolumny danych w źródle danych następuje `ASC` lub `DESC` wskazująca, czy listy mają być sortowane w kolejności rosnącej lub malejącej. Można ustawić sortowanie zaawansowane lub sortowanie wiele kolumn, rozdzielając każdej kolumny za pomocą przecinka jako separatora. <xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość przyjmuje wyrażenia ciągu.  
  
> [!NOTE]
>  Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Aby filtrować dane za pomocą elementu BindingSource  
  
-   Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> wyrażenie, które chcesz dla właściwości.  
  
     W poniższym przykładzie kodu wyrażenie jest nazwa kolumny, a następnie wartość, która ma kolumny.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Aby posortować dane za pomocą elementu BindingSource  
  
1.  Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> dla właściwości Nazwa kolumny, która ma następuje `ASC` lub `DESC` aby wskazać w kolejności rosnącej lub malejącej.  
  
2.  Wiele kolumn należy oddzielić przecinkami.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod ładowania danych z tabeli klientów Northwind przykładowej bazy danych do <xref:System.Windows.Forms.DataGridView> kontrolować oraz filtry i sortuje wyświetlanych danych.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten przykład, Wklej kod do formularza, który zawiera <xref:System.Windows.Forms.BindingSource> o nazwie `BindingSource1` i <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`. Obsługa <xref:System.Windows.Forms.Form.Load> zdarzenia dla formularza i wywołanie `InitializeSortedFilteredBindingSource` w metoda obsługi zdarzeń obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [Porady: Instalacja przykładowych baz danych](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
