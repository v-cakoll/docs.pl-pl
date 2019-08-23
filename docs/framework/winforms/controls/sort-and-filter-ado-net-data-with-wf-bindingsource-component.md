---
title: 'Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows'
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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960430"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows
Można uwidocznić możliwości <xref:System.Windows.Forms.BindingSource> sortowania i filtrowania kontroli <xref:System.Windows.Forms.BindingSource.Sort%2A> za pomocą właściwości i <xref:System.Windows.Forms.BindingSource.Filter%2A> . Można zastosować proste sortowanie <xref:System.ComponentModel.IBindingList>, gdy bazowe źródło danych jest i można zastosować filtrowanie i zaawansowane sortowanie, gdy źródło danych <xref:System.ComponentModel.IBindingListView>jest. Właściwość wymaga standardowej składni ADO.NET: ciąg reprezentujący nazwę kolumny danych w źródle danych, `ASC` po której następuje lub `DESC` aby wskazać, czy lista powinna być posortowana w kolejności rosnącej czy malejącej. <xref:System.Windows.Forms.BindingSource.Sort%2A> Można ustawić zaawansowane sortowanie lub sortowanie z wieloma kolumnami, oddzielając poszczególne kolumny średnikami. <xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość przyjmuje wyrażenie ciągu.  
  
> [!NOTE]
> Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Aby odfiltrować dane za pomocą parametru BindingSource  
  
- <xref:System.Windows.Forms.BindingSource.Filter%2A> Ustaw właściwość na wyrażenie, które chcesz.  
  
     W poniższym przykładzie kodu wyrażenie jest nazwą kolumny, a następnie wartością, która ma być dla kolumny.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Aby posortować dane za pomocą parametru BindingSource  
  
1. Ustaw właściwość na nazwę kolumny, która ma `ASC` się pojawić, lub `DESC` aby wskazać kolejność rosnącą lub malejącą. <xref:System.Windows.Forms.BindingSource.Sort%2A>  
  
2. Oddziel wiele kolumn przecinkami.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ładuje dane z tabeli Customers przykładowej bazy danych Northwind do <xref:System.Windows.Forms.DataGridView> kontrolki, a następnie filtruje i sortuje wyświetlane dane.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten przykład, wklej <xref:System.Windows.Forms.BindingSource> kod w postaci zawierającej nazwę `BindingSource1` i <xref:System.Windows.Forms.DataGridView> nazwę `dataGridView1`. Obsłuż `InitializeSortedFilteredBindingSource` zdarzenie dla formularza i wywołania w metodzie obsługi zdarzeń ładowania. <xref:System.Windows.Forms.Form.Load>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Instrukcje: Instalowanie przykładowych baz danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource, składnik](bindingsource-component.md)
