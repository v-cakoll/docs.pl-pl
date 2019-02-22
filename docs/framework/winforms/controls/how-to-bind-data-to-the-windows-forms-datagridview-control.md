---
title: 'Instrukcje: Powiąż dane z formantu DataGridView formularzy Windows'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f98f095f888a8ef3622fabbf4c4745af60e930e3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584060"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Instrukcje: Powiąż dane z formantu DataGridView formularzy Windows

<xref:System.Windows.Forms.DataGridView> Kontrolka obsługuje standardowy model powiązanie danych formularzy Windows, dzięki czemu można powiązać różnorodne źródła danych. Zazwyczaj można powiązać <xref:System.Windows.Forms.BindingSource> który zarządza interakcji ze źródłem danych. <xref:System.Windows.Forms.BindingSource> Mogą być dowolnego źródła danych Windows Forms, co zapewnia dużą elastyczność podczas wybierania lub modyfikowania lokalizacji usługi danych. Aby uzyskać więcej informacji o źródłach danych <xref:System.Windows.Forms.DataGridView> kontrolować obsługuje, zobacz [— informacje o formancie DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  

Program Visual Studio została rozbudowana Obsługa powiązanie danych z kontrolką DataGridView. Aby uzyskać więcej informacji, zobacz [jak: Powiąż dane z formantu DataGridView formularzy Windows za pomocą projektanta](bind-data-to-the-datagrid-using-the-designer.md).  

Do formantu DataGridView połączyć się z danymi:

1. Implementuje metodę do obsługi Szczegóły pobierania danych. Poniższy kod implementuje przykład `GetData` metodę, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter>i używa ich do wypełnienia <xref:System.Data.DataTable>. Następnie powiąże <xref:System.Data.DataTable> do <xref:System.Windows.Forms.BindingSource>. 

2. W formularzu <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń, powiązania <xref:System.Windows.Forms.DataGridView> kontrolę <xref:System.Windows.Forms.BindingSource>i wywoływać `GetData` metody do pobierania danych.  

## <a name="example"></a>Przykład

Ten przykład kompletny kod pobiera dane z bazy danych do wypełnienia formantu DataGridView w formularzu Windows. Formularz zawiera również przycisków, aby ponownie załadować danych i przesyłanie zmian do bazy danych.  

Ten przykład wymaga: 

- Dostęp do przykładowej bazy danych Northwind programu SQL Server. Aby uzyskać więcej informacji na temat Instalowanie przykładowej bazy danych Northwind, zobacz [przykładowych baz danych należy uzyskać przykłady kodu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms, dane systemowe i System.Xml.  

Aby skompilować i uruchomić ten przykład, Wklej kod do *Form1* pliku z kodem w nowym projekcie Windows Form. Aby uzyskać informacje dotyczące tworzenia aplikacji z C# lub wiersza polecenia programu Visual Basic, zobacz [za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [kompilacji z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Wypełnij `connectionString` zmiennej w przykładzie z wartościami połączenia programu SQL Server Northwind przykładowej bazy danych. Uwierzytelnianie Windows, nazywany również zabezpieczenia zintegrowane jest bardziej bezpieczny sposób łączenia z bazą danych niż przechowywanie hasła w parametrach połączenia. Aby uzyskać więcej informacji na temat zabezpieczeń połączeń, zobacz [chronić informacje o połączeniu](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Wyświetlanie danych w formancie DataGridView formularzy Windows](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
