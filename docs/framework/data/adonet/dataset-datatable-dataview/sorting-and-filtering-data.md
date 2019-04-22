---
title: Sortowanie i filtrowanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 8d8bd85f65adfde5f239e1e2dd79d65517b745a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166247"
---
# <a name="sorting-and-filtering-data"></a>Sortowanie i filtrowanie danych
<xref:System.Data.DataView> Oferuje kilka sposobów, sortowania i filtrowania danych w <xref:System.Data.DataTable>:  
  
-   Możesz użyć <xref:System.Data.DataView.Sort%2A> właściwości w celu określenia jednej lub wielu kolumn, sortowanie zleceń i mają (rosnąco) ASC i DESC (malejąco) parametry.  
  
-   Możesz użyć <xref:System.Data.DataView.ApplyDefaultSort%2A> właściwości, aby automatycznie utworzyć porządek sortowania, w kolejności rosnącej na podstawie kolumny klucza podstawowego lub kolumny tabeli. <xref:System.Data.DataView.ApplyDefaultSort%2A> ma zastosowanie tylko jeśli **sortowania** właściwość jest odwołaniem do wartości null ani być pustym ciągiem, a jeśli ma zdefiniowany klucz podstawowy w tabeli.  
  
-   Możesz użyć <xref:System.Data.DataView.RowFilter%2A> właściwości w celu określenia podzbiór wierszy na podstawie ich wartości w kolumnach. Szczegółowe informacje na temat prawidłowych wyrażeń dla **RowFilter** właściwości, zobacz informacje referencyjne dotyczące <xref:System.Data.DataColumn.Expression%2A> właściwość <xref:System.Data.DataColumn> klasy.  
  
     Jeśli chcesz przywrócić, użyj wyników określonego zapytania na danych, zapewniając dynamiczny widok podzbiór danych, w przeciwieństwie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody **DataView** do osiągnięcia najlepszej wydajności zamiast ustawienie **RowFilter** właściwości. Ustawienie **RowFilter** właściwość odbudowania indeksu dla danych, obciążenie dodawanie do aplikacji i zmniejszenie wydajności. **RowFilter** właściwość najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki Wyświetla wyfiltrowanych wyników. **Znaleźć** i **FindRows** metody wykorzystać bieżącego indeksu bez konieczności indeksu odbudowania. Aby uzyskać więcej informacji na temat **znaleźć** i **FindRows** metod, zobacz [znajdowanie wierszy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Możesz użyć <xref:System.Data.DataView.RowStateFilter%2A> właściwości w celu określenia, które wersje wierszy do wyświetlenia. **DataView** niejawnie zarządza której wersji wiersza do udostępnienia, w zależności od **RowState** bazowego wiersza. Na przykład jeśli **Element RowStateFilter** ustawiono **DataViewRowState.Deleted**, **DataView** udostępnia **oryginalnego** wersji wierszy wszystkie **usunięte** wiersze, ponieważ nie istnieje żadne **bieżącego** wiersza wersji. Można określić, której wersji wiersza wiersza jest ujawniany przy użyciu **RowVersion** właściwość **DataRowView**.  
  
     W poniższej tabeli przedstawiono opcje **DataViewRowState**.  
  
    |Opcje DataViewRowState|Opis|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Bieżącego** wiersz wersję wszystkich **Unchanged**, **dodano**, i **zmodyfikowane** wierszy. Domyślnie włączone.|  
    |**Dodano**|**Bieżącego** wiersz wersję wszystkich **dodano** wierszy.|  
    |**Usunięto**|**Oryginalnego** wiersz wersję wszystkich **usunięte** wierszy.|  
    |**ModifiedCurrent**|**Bieżącego** wiersz wersję wszystkich **zmodyfikowane** wierszy.|  
    |**ModifiedOriginal**|**Oryginalnego** wiersz wersję wszystkich **zmodyfikowane** wierszy.|  
    |**Brak**|Brak wierszy.|  
    |**OriginalRows**|**Oryginalnego** wiersz wersję wszystkich **Unchanged**, **zmodyfikowane**, i **usunięte** wierszy.|  
    |**bez zmian**|**Bieżącego** wiersz wersję wszystkich **Unchanged** wierszy.|  
  
 Aby uzyskać więcej informacji na temat stany wiersza i wersje wiersza, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Poniższy przykład kodu tworzy widok, przedstawia wszystkie produkty, których liczba jednostek w magazynie jest mniejsza lub równa z poziomu której kolejność chcesz zmienić, najpierw posortowane według Identyfikatora dostawcy, a następnie według nazwy produktu.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
