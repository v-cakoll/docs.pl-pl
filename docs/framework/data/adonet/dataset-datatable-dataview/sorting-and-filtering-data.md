---
title: Sortowanie i filtrowanie danych
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2411307623c714ae521d00dcffca05d3569a656e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-and-filtering-data"></a>Sortowanie i filtrowanie danych
<xref:System.Data.DataView> Udostępnia kilka sposobów, sortowanie i filtrowanie danych w <xref:System.Data.DataTable>:  
  
-   Można użyć <xref:System.Data.DataView.Sort%2A> właściwości w celu określenia jednej lub wielu kolumn sortowanie zleceń i mają (rosnąco) ASC i DESC (malejąco) parametry.  
  
-   Można użyć <xref:System.Data.DataView.ApplyDefaultSort%2A> właściwość, aby automatycznie utworzyć porządek sortowania, w kolejności rosnącej na podstawie kolumny klucza podstawowego lub kolumny tabeli. <xref:System.Data.DataView.ApplyDefaultSort%2A>ma zastosowanie tylko w przypadku **sortowania** właściwość jest odwołanie o wartości null lub pusty ciąg, i gdy tabela ma zdefiniowany klucz podstawowy.  
  
-   Można użyć <xref:System.Data.DataView.RowFilter%2A> właściwości w celu określenia podzbiór wierszy na podstawie ich kolumny wartości. Aby uzyskać więcej informacji o prawidłowe wyrażenia dla **RowFilter** właściwości, zobacz informacje referencyjne dotyczące <xref:System.Data.DataColumn.Expression%2A> właściwość <xref:System.Data.DataColumn> klasy.  
  
     Jeśli chcesz zwrócić wyników określonego zapytania na danych, a nie udostępnia dynamiczny widok podzbiór danych, użyj <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody **DataView** Aby uzyskać najlepszą wydajność, a nie ustawienie **RowFilter** właściwości. Ustawienie **RowFilter** właściwości odtwarza indeksu dla danych narzut dodawanie do swojej aplikacji i zmniejszenie wydajności. **RowFilter** właściwości najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki wyświetla filtrowane wyniki. **Znaleźć** i **FindRows** metody wykorzystać bieżącego indeksu bez konieczności indeksu, który ma zostać również przebudowany. Aby uzyskać więcej informacji na temat **znaleźć** i **FindRows** metod, zobacz [znajdowanie wierszy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Można użyć <xref:System.Data.DataView.RowStateFilter%2A> właściwości w celu określenia, które wersje wierszy do wyświetlenia. **DataView** niejawnie zarządza wersji wierszy do udostępnienia, w zależności od **RowState** podstawowej wiersza. Na przykład jeśli **Element RowStateFilter** ustawiono **DataViewRowState.Deleted**, **DataView** przedstawia **oryginalnego** wersja wiersza wszystkie **usunięte** wierszy, ponieważ nie istnieje żadne **bieżącego** wersja wiersza. Można określić wersji wiersza wiersza jest ujawniany przy użyciu **RowVersion** właściwość **DataRowView**.  
  
     W poniższej tabeli przedstawiono opcje **DataViewRowState**.  
  
    |Opcje DataViewRowState|Opis|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Bieżącego** wersja wiersza wszystkich **Unchanged**, **Added**, i **zmodyfikowane** wierszy. Domyślnie włączone.|  
    |**Dodane**|**Bieżącego** wersja wiersza wszystkich **Added** wierszy.|  
    |**Usunięte**|**Oryginalnego** wersja wiersza wszystkich **usunięte** wierszy.|  
    |**ModifiedCurrent**|**Bieżącego** wersja wiersza wszystkich **zmodyfikowane** wierszy.|  
    |**ModifiedOriginal**|**Oryginalnego** wersja wiersza wszystkich **zmodyfikowane** wierszy.|  
    |**Brak**|Żadne wiersze.|  
    |**OriginalRows**|**Oryginalnego** wersja wiersza wszystkich **Unchanged**, **zmodyfikowane**, i **usunięte** wierszy.|  
    |**Unchanged**|**Bieżącego** wersja wiersza wszystkich **Unchanged** wierszy.|  
  
 Aby uzyskać więcej informacji na temat stany wiersza i wersje wiersza, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Poniższy przykład kodu tworzy widok czy przedstawia wszystkie produkty, których liczba jednostek w magazynie jest mniejsza lub równa poziomu zmiany kolejności, w najpierw posortowane według Identyfikatora dostawcy, a następnie według nazwy produktu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
