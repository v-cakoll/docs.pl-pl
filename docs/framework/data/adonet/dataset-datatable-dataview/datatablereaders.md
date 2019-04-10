---
title: Elementy DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214004"
---
# <a name="datatablereaders"></a>Elementy DataTableReader
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
