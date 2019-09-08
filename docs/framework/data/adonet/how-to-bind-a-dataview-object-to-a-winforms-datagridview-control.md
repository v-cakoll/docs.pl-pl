---
title: 'Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 3a3089073cdc5afb4ee51caca9114b401c740b45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795002"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant zapewnia zaawansowany i elastyczny sposób wyświetlania danych w formacie tabelarycznym. Formant obsługuje model powiązań danych w warstwie Standardowa Windows Forms, więc zostanie powiązany z <xref:System.Data.DataView> wieloma innymi źródłami danych i z nich. <xref:System.Windows.Forms.DataGridView> W większości sytuacji należy jednak powiązać ze <xref:System.Windows.Forms.BindingSource> składnikiem, który będzie zarządzać szczegółami współpracy ze źródłem danych.  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Forms.DataGridView> temat kontrolki, zobacz [formant DataGridView — Omówienie](../../winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Aby połączyć formant DataGridView z obiektem DataView  
  
1. Zaimplementuj metodę, aby obsłużyć Szczegóły pobierania danych z bazy danych. Poniższy przykład kodu implementuje `GetData` metodę <xref:System.Data.SqlClient.SqlDataAdapter> inicjującą składnik i <xref:System.Data.DataSet>używa jej do wypełnienia. Pamiętaj, aby ustawić `connectionString` zmienną na wartość odpowiednią dla bazy danych. Będziesz potrzebować dostępu do serwera z zainstalowaną przykładową bazą danych SQL Server AdventureWorks.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. W procedurze obsługi <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> `GetData` zdarzeń formularza Powiąż formant ze składnikiem i Wywołaj metodę, aby pobrać dane z bazy danych. <xref:System.Windows.Forms.Form.Load> Program jest tworzony na podstawie zapytania LINQ to DataSet w ramach kontaktu <xref:System.Data.DataTable> , a następnie <xref:System.Windows.Forms.BindingSource> jest powiązany ze składnikiem. <xref:System.Data.DataView>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
