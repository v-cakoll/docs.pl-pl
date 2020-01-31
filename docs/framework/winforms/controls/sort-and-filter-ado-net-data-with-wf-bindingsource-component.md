---
title: Sortuj i Filtruj dane ADO.NET za pomocą składnika BindingSource
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
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742975"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows
Można uwidocznić możliwości sortowania i filtrowania <xref:System.Windows.Forms.BindingSource> kontroli za pomocą właściwości <xref:System.Windows.Forms.BindingSource.Sort%2A> i <xref:System.Windows.Forms.BindingSource.Filter%2A>. Można zastosować proste sortowanie, gdy bazowe źródło danych jest <xref:System.ComponentModel.IBindingList>i można zastosować filtrowanie i zaawansowane sortowanie, gdy źródło danych jest <xref:System.ComponentModel.IBindingListView>. Właściwość <xref:System.Windows.Forms.BindingSource.Sort%2A> wymaga standardowej składni ADO.NET: ciąg reprezentujący nazwę kolumny danych w źródle danych, po której następuje `ASC` lub `DESC`, aby wskazać, czy lista powinna być posortowana w kolejności rosnącej czy malejącej. Można ustawić zaawansowane sortowanie lub sortowanie z wieloma kolumnami, oddzielając poszczególne kolumny średnikami. Właściwość <xref:System.Windows.Forms.BindingSource.Filter%2A> przyjmuje wyrażenie ciągu.  
  
> [!NOTE]
> Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Aby odfiltrować dane za pomocą parametru BindingSource  
  
- Ustaw właściwość <xref:System.Windows.Forms.BindingSource.Filter%2A> na wyrażenie, które chcesz.  
  
     W poniższym przykładzie kodu wyrażenie jest nazwą kolumny, a następnie wartością, która ma być dla kolumny.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Aby posortować dane za pomocą parametru BindingSource  
  
1. Ustaw właściwość <xref:System.Windows.Forms.BindingSource.Sort%2A> na nazwę kolumny, która ma następować `ASC` lub `DESC`, aby wskazać kolejność rosnącą lub malejącą.  
  
2. Oddziel wiele kolumn przecinkami.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ładuje dane z tabeli Customers przykładowej bazy danych Northwind do kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie filtruje i sortuje wyświetlane dane.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten przykład, wklej kod do formularza zawierającego <xref:System.Windows.Forms.BindingSource> o nazwie `BindingSource1` i <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`. Obsłuż zdarzenie <xref:System.Windows.Forms.Form.Load> dla `InitializeSortedFilteredBindingSource` formularzy i wywołań w metodzie obsługi zdarzeń ładowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Instrukcje: Instalowanie przykładowych baz danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource, składnik](bindingsource-component.md)
