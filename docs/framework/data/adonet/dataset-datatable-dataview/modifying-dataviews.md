---
title: Modyfikowanie elementów DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 6e340b9b72735598650d2eefa6e19ab40fffc2e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607417"
---
# <a name="modifying-dataviews"></a>Modyfikowanie elementów DataView
Możesz użyć <xref:System.Data.DataView> na dodawanie, usuwanie i modyfikowanie wierszy danych w tabeli podstawowej. Możliwość używania **DataView** do modyfikacji danych w tabeli podstawowej jest kontrolowana przez ustawienia jednej z trzech właściwości logiczna **DataView**. Te właściwości są <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, i <xref:System.Data.DataView.AllowDelete%2A>. Są one ustawione **true** domyślnie.  
  
 Jeśli **element AllowNew** jest **true**, możesz użyć <xref:System.Data.DataView.AddNew%2A> metody **DataView** do tworzenia nowego <xref:System.Data.DataRowView>. Należy zauważyć, że nowy wiersz nie jest faktycznie dodane do bazowego <xref:System.Data.DataTable> aż <xref:System.Data.DataRowView.EndEdit%2A> metody **DataRowView** jest wywoływana. Jeśli <xref:System.Data.DataRowView.CancelEdit%2A> metody **DataRowView** jest wywoływana, nowego wiersza są odrzucane. Należy zauważyć, że możesz edytować tylko jeden **DataRowView** w danym momencie. Jeśli wywołasz **działają funkcje AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit —** jest wywoływany niejawnie na Oczekujące wiersz. Gdy **EndEdit —** jest wywoływana, zmiany zostaną zastosowane do podstawowej **DataTable** i później może być zatwierdzone lub odrzucone, za pomocą **AcceptChanges** lub  **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiektu. Jeśli **element AllowNew** jest **false**, jest zgłaszany wyjątek, jeśli wywołasz **działają funkcje AddNew** metody **DataRowView**.  
  
 Jeśli **AllowEdit** jest **true**, możesz zmodyfikować zawartość **DataRow** za pośrednictwem **DataRowView**. Możesz sprawdzić zmiany do podstawowej przy użyciu wiersza **DataRowView.EndEdit** lub odrzucić zmiany, przy użyciu **DataRowView.CancelEdit**. Pamiętaj, że tylko jeden wiersz, mogą być edytowane w danym momencie. Jeśli wywołasz **działają funkcje AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit —** jest wywoływany niejawnie na Oczekujące wiersz. Podczas **EndEdit —** jest wywoływana, proponowane zmiany są umieszczane w **bieżącego** wersji wiersza elementu bazowego **DataRow** i później może być zatwierdzone lub odrzucone, za pomocą  **Metoda AcceptChanges** lub **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiekt. Jeśli **AllowEdit** jest **false**, jest zgłaszany wyjątek, Jeśli spróbujesz zmodyfikować wartość w **DataView**.  
  
 Kiedy istniejący **DataRowView** jest edytowany, zdarzenia bazowego **DataTable** nadal będą zgłaszane z proponowanych zmian. Należy pamiętać, że jeśli wywołasz **EndEdit —** lub **CancelEdit** na podstawowych **DataRow**, oczekujące zmiany zostaną zastosowane lub anulowane niezależnie od tego, czy  **EndEdit —** lub **CancelEdit** jest wywoływana w **DataRowView**.  
  
 Jeśli **AllowDelete** jest **true**, można usunąć wierszy z **DataView** przy użyciu **Usuń** metody **DataView**  lub **DataRowView** obiektu i wiersze zostaną usunięte z bazowego **DataTable**. Później można zatwierdzić lub odrzucić usuwa przy użyciu **AcceptChanges** lub **RejectChanges** odpowiednio. Jeśli **AllowDelete** jest **false**, jest zgłaszany wyjątek, jeśli wywołasz **Usuń** metody **DataView** lub  **DataRowView**.  
  
 Poniższy przykład kodu, który powoduje wyłączenie przy użyciu **DataView** do usuwania wierszy i dodaje nowy wiersz do tabeli podstawowej z użyciem **DataView**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
