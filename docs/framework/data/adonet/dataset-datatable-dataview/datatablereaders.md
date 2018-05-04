---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 8305629bb267805cd79455e2edf990e72a12dc10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
