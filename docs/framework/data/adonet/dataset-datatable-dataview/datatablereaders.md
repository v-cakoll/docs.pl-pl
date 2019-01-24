---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 9984dc9c215a34ab35524560e4dcbcd6bd12596d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602848"
---
# <a name="datatablereaders"></a>DataTableReaders
<xref:System.Data.DataTableReader> Przedstawia zawartość <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> w postaci co najmniej jeden wynik tylko do odczytu, tylko do przodu ustawia.  
  
 Po utworzeniu **elementu DataTableReader** z **DataTable**, wynikowy **elementu DataTableReader** obiekt zawiera jeden zestaw wyników z tych samych danych co  **DataTable** z której została utworzona, z wyjątkiem wszystkich wierszy, które zostały oznaczone jako usunięte. Kolumny są wyświetlane w tej samej kolejności jak w oryginalnym **DataTable**.  
  
 A **elementu DataTableReader** może zawierać wiele zestawów wyników, jeśli został utworzony przez wywołanie metody <xref:System.Data.DataSet.CreateDataReader%2A>. Wyniki są w tej samej kolejności jak **DataTables** w **DataSet** obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementu DataReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 W tym artykule omówiono sposób tworzenia **elementu DataTableReader** obiektu.  
  
 [Nawigowanie w elementach DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 W tym artykule opisano korzystanie z **odczytu** metodę, aby przeglądać zawartość **elementu DataTableReader**.  
  
## <a name="see-also"></a>Zobacz także
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
