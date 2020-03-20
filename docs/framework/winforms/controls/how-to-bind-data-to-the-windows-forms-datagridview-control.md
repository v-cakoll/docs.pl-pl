---
title: Powiąż dane z formantem DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182275"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Jak: Powiązać dane z formantem DataGridView formularzy systemu Windows

Formant <xref:System.Windows.Forms.DataGridView> obsługuje standardowy model wiązania danych windows forms, dzięki czemu może wiązać się z różnymi źródłami danych. Zazwyczaj należy powiązać <xref:System.Windows.Forms.BindingSource> z, który zarządza interakcji ze źródłem danych. Może <xref:System.Windows.Forms.BindingSource> to być dowolne źródło danych Windows Forms, co zapewnia dużą elastyczność przy wyborze lub modyfikowaniu lokalizacji danych. Aby uzyskać więcej informacji <xref:System.Windows.Forms.DataGridView> na temat źródeł danych, które obsługuje formant, zobacz [omówienie kontroli DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio ma rozbudowaną obsługę powiązania danych z formantem DataGridView. Aby uzyskać więcej informacji, zobacz [Jak: Powiązać dane z formantem DataGridView formularzy systemu Windows za pomocą projektanta](bind-data-to-the-datagrid-using-the-designer.md).  

Aby połączyć formant DataGridView z danymi:

1. Zaimplementuj metodę obsługi szczegółów pobierania danych. Poniższy przykład kodu `GetData` implementuje metodę, <xref:System.Data.SqlClient.SqlDataAdapter>która inicjuje program , <xref:System.Data.DataTable>i używa jej do wypełniania pliku . Następnie wiąże się <xref:System.Data.DataTable> z <xref:System.Windows.Forms.BindingSource>.

2. W programie obsługi <xref:System.Windows.Forms.Form.Load> zdarzeń formularza <xref:System.Windows.Forms.DataGridView> powiąż formant z programem <xref:System.Windows.Forms.BindingSource>, i wywołaj `GetData` metodę pobierania danych.  

## <a name="example"></a>Przykład

Ten przykład pełnego kodu pobiera dane z bazy danych w celu wypełnienia formantu DataGridView w formularzu systemu Windows. Formularz zawiera również przyciski do ponownego ładowania danych i przesyłania zmian do bazy danych.  

Ten przykład wymaga:

- Dostęp do przykładowej bazy danych programu Northwind SQL Server. Aby uzyskać więcej informacji na temat instalowania przykładowej bazy danych Northwind, zobacz [Pobieranie przykładowych baz danych dla ADO.NET przykładowych kodu](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Odwołania do zestawów System, System.Windows.Forms, System.Data i System.Xml.  

Aby skompilować i uruchomić ten przykład, wklej kod do pliku kodu *Form1* w nowym projekcie Windows Forms. Aby uzyskać informacje o budowaniu z wiersza polecenia C# lub Visual Basic, zobacz [Tworzenie wiersza polecenia za pomocą pliku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilacja z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Wypełnij zmienną `connectionString` w przykładzie wartościami dla przykładowego połączenia bazy danych programu Northwind SQL Server. Uwierzytelnianie systemu Windows, nazywane również zintegrowanymi zabezpieczeniami, jest bezpieczniejszym sposobem łączenia się z bazą danych niż przechowywanie hasła w ciągu połączenia. Aby uzyskać więcej informacji na temat zabezpieczeń połączeń, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Wyświetlanie danych w formancie DataGridView formularzy systemu Windows](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
