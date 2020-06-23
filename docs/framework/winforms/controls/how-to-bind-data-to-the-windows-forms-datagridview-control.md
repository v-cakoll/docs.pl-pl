---
title: Powiązywanie danych z kontrolką DataGridView
ms.date: 02/08/2019
description: Dowiedz się, jak formant DataGridView obsługuje standardowy model powiązań danych Windows Forms, aby można było powiązać z różnymi źródłami danych.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904419"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Instrukcje: powiązywanie danych z Windows Forms formant DataGridView

<xref:System.Windows.Forms.DataGridView>Formant obsługuje model powiązań danych w warstwie standardowa Windows Forms, więc można powiązać z wieloma źródłami danych. Zwykle wiąże się to z <xref:System.Windows.Forms.BindingSource> usługą, która zarządza interakcją ze źródłem danych. <xref:System.Windows.Forms.BindingSource>Może to być dowolne Windows Forms źródła danych, co zapewnia dużą elastyczność podczas wybierania lub modyfikowania lokalizacji danych. Aby uzyskać więcej informacji o źródłach danych <xref:System.Windows.Forms.DataGridView> obsługiwanych przez kontrolkę, zobacz [formant DataGridView — Omówienie](datagridview-control-overview-windows-forms.md).  

Program Visual Studio ma rozbudowaną obsługę powiązań danych z formantem DataGridView. Aby uzyskać więcej informacji, zobacz [jak: powiązywanie danych z kontrolką DataGridView Windows Forms przy użyciu narzędzia Projektant](bind-data-to-the-datagrid-using-the-designer.md).  

Aby połączyć formant DataGridView z danymi:

1. Zaimplementuj metodę, aby obsłużyć Szczegóły pobierania danych. Poniższy przykład kodu implementuje `GetData` metodę inicjującą a <xref:System.Data.SqlClient.SqlDataAdapter> i używa jej do wypełnienia <xref:System.Data.DataTable> . Następnie tworzy powiązanie z <xref:System.Data.DataTable> <xref:System.Windows.Forms.BindingSource> .

2. W programie <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń formularza Powiąż formant z <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> i Wywołaj `GetData` metodę, aby pobrać dane.  

## <a name="example"></a>Przykład

Ten kompletny przykład kodu pobiera dane z bazy danych, aby wypełnić formant DataGridView w formularzu systemu Windows. Formularz zawiera również przyciski do ponownego ładowania danych i przesyłania zmian w bazie danych.  

Ten przykład wymaga:

- Dostęp do przykładowej bazy danych Northwind SQL Server. Aby uzyskać więcej informacji na temat instalowania przykładowej bazy danych Northwind, zobacz [Pobieranie przykładowych baz danych dla przykładów kodu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Odwołania do zestawów system, system. Windows. Forms, system. Data i System.Xml.  

Aby skompilować i uruchomić ten przykład, wklej kod do pliku kodu *Form1* w nowym projekcie Windows Forms. Aby uzyskać informacje na temat kompilowania z poziomu wiersza polecenia C# lub Visual Basic, zobacz wiersz [polecenia kompilacja z csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompiluj z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Wypełnij `connectionString` zmienną w przykładzie wartościami dla przykładowego połączenia bazy danych Northwind SQL Server. Uwierzytelnianie systemu Windows, nazywane również zabezpieczeniami zintegrowanymi, jest bezpieczniejszym sposobem łączenia się z bazą danych niż przechowywanie hasła w parametrach połączenia. Aby uzyskać więcej informacji o zabezpieczeniach połączeń, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Wyświetlanie danych w kontrolce DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
