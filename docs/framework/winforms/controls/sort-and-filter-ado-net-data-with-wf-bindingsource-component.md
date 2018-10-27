---
title: 'Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 932d30d356225d88d7ef149561cc4c5cc8ac4dd0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188758"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows
Należy udostępnić sortowanie i filtrowanie możliwości <xref:System.Windows.Forms.BindingSource> kontrolować za pośrednictwem <xref:System.Windows.Forms.BindingSource.Sort%2A> i <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości. Można zastosować proste sortowania, jeśli bazowe źródło danych jest <xref:System.ComponentModel.IBindingList>, i można zastosować filtrowanie zaawansowane, sortowanie, gdy źródłem danych jest <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość wymaga standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Składnia: ciąg reprezentujący nazwę kolumny danych w źródle danych następuje `ASC` lub `DESC` do wskazania, czy lista powinny być sortowane w kolejności rosnącej lub malejącej. Możesz ustawić zaawansowane sortowania lub wiele kolumn, sortowanie, rozdzielając każda kolumna przecinka jako separatora. <xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość przyjmuje wyrażenia ciągu.  
  
> [!NOTE]
>  Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Aby filtrować dane przy użyciu kontrolki BindingSource  
  
-   Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości do wyrażenia, które chcesz.  
  
     W poniższym przykładzie kodu wyrażenie jest nazwa kolumny, a następnie wartość, która ma kolumny.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Aby posortować dane przy użyciu kontrolki BindingSource  
  
1.  Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość na nazwę kolumny, która ma następuje `ASC` lub `DESC` do wskazania kolejności rosnącej lub malejącej.  
  
2.  Wiele kolumn należy oddzielić przecinkami.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod ładuje dane z tabeli Klienci w bazie danych Northwind do <xref:System.Windows.Forms.DataGridView> kontrolować, filtry i sortuje wyświetlanych danych.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten przykład, Wklej kod do formularza, który zawiera <xref:System.Windows.Forms.BindingSource> o nazwie `BindingSource1` i <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`. Obsługa <xref:System.Windows.Forms.Form.Load> zdarzenie w formularzu i wywołania `InitializeSortedFilteredBindingSource` w metodzie obsługi zdarzenia obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [Porady: Instalowanie przykładowych baz danych](https://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
