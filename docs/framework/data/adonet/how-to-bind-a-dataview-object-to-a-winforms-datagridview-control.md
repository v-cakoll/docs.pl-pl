---
title: "Porady: powiązanie obiektu DataView do formantu DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 70a3004bb074c453ae1ef3aff32df0f657d6531e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Porady: powiązanie obiektu DataView do formantu DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym. <xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje standardowy model powiązanie danych formularzy systemu Windows, więc będzie powiązać <xref:System.Data.DataView> i różnych innych źródeł danych. W większości sytuacji należy jednak użytkownik zostanie z nim powiązane <xref:System.Windows.Forms.BindingSource> składnik, który będzie zarządzać szczegółowe informacje o interakcji ze źródłem danych.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [informacje o formancie DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Aby nawiązać połączenie DataView formantu DataGridView  
  
1.  Implementuje metody obsługi szczegóły pobieranie danych z bazy danych. Poniższy kod przykładowy implementuje `GetData` metodę, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter> składnika i używa go do wypełnienia <xref:System.Data.DataSet>. Należy ustawić `connectionString` zmiennej na wartość, która jest odpowiednia dla Twojej bazy danych. Konieczne będzie dostęp do serwera z bazą danych przykładowych AdventureWorks programu SQL Server, które zostały zainstalowane.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  W <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń formularza, powiązać <xref:System.Windows.Forms.DataGridView> formant <xref:System.Windows.Forms.BindingSource> składnika i wywołania `GetData` metody do pobierania danych z bazy danych. <xref:System.Data.DataView> Jest tworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie dotyczące kontaktu <xref:System.Data.DataTable> , a następnie jest powiązany z <xref:System.Windows.Forms.BindingSource> składnika.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
