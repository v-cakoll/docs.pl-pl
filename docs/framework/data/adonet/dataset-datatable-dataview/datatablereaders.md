---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b5160f5a2c68cab798dde154275c062e2bf31739
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="datatablereaders"></a>DataTableReaders
<xref:System.Data.DataTableReader> Przedstawia informacje o zawartości <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> w formie co najmniej jeden wynik tylko do odczytu, tylko do przodu.  
  
 Po utworzeniu **Element DataTableReader** z **DataTable**, powstałe w ten sposób **Element DataTableReader** obiekt zawiera jeden zestaw danych o tej samej jako wyników  **Element DataTable** z którego został utworzony, z wyjątkiem wszystkie wiersze, które zostały oznaczone jako usunięte. Kolumny pojawiają się w tej samej kolejności jak w oryginalnym **DataTable**.  
  
 A **Element DataTableReader** może zawierać wiele zestawów wyników, jeśli została utworzona przez wywołanie metody <xref:System.Data.DataSet.CreateDataReader%2A>. Wyniki są w tej samej kolejności jak **DataTables** w **DataSet** obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementu DataReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 W tym artykule omówiono sposób tworzenia **Element DataTableReader** obiektu.  
  
 [Nawigowanie w elementach DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 Opisuje **odczytu** metody, aby przeglądać zawartość **Element DataTableReader**.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
