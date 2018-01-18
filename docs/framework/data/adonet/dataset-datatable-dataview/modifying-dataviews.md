---
title: Modyfikowanie DataViews
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
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c31f256bb86f007a9d083370d116464607cde236
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="modifying-dataviews"></a>Modyfikowanie DataViews
Można użyć <xref:System.Data.DataView> na dodawanie, usuwanie i modyfikowanie wierszy danych w tabeli podstawowej. Możliwość używania **DataView** można modyfikować danych w tabeli podstawowej jest kontrolowany przez ustawienia jednej z trzech logicznych właściwości **DataView**. Te właściwości są <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, i <xref:System.Data.DataView.AllowDelete%2A>. Są ustawione **true** domyślnie.  
  
 Jeśli **element AllowNew** jest **true**, można użyć <xref:System.Data.DataView.AddNew%2A> metody **DataView** do tworzenia nowego <xref:System.Data.DataRowView>. Należy pamiętać, że nowy wiersz nie jest rzeczywiście dodane do odpowiadającego <xref:System.Data.DataTable> do momentu <xref:System.Data.DataRowView.EndEdit%2A> metody **DataRowView** jest wywoływana. Jeśli <xref:System.Data.DataRowView.CancelEdit%2A> metody **DataRowView** jest wywołana, nowy wiersz jest pomijany. Należy też zauważyć, że można edytować tylko jeden **DataRowView** naraz. Jeśli należy wywołać **AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit** jest wywoływany niejawnie na Oczekujące wiersza. Gdy **EndEdit** jest wywołana, zmiany zostaną zastosowane do odpowiadającego **DataTable** lub nowszego mogą być zatwierdzone lub odrzucone, za pomocą **AcceptChanges** lub  **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiektu. Jeśli **element AllowNew** jest **false**, jest zwracany wyjątek, jeśli wywołujesz **AddNew** metody **DataRowView**.  
  
 Jeśli **AllowEdit** jest **true**, możesz zmodyfikować zawartość **DataRow** za pośrednictwem **DataRowView**. Można potwierdzić zmiany podstawowej za pomocą wiersza **DataRowView.EndEdit** lub Odrzuć zmiany przy użyciu **DataRowView.CancelEdit**. Należy pamiętać, że aby tylko jeden wiersz może być edytowany w czasie. Jeśli należy wywołać **AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit** jest wywoływany niejawnie na Oczekujące wiersza. Gdy **EndEdit** jest wywoływana, proponowanych zmian są umieszczane w **bieżącego** wersja wiersza podstawowych **DataRow** lub nowszego mogą być zatwierdzone lub odrzucone, przy użyciu  **Metoda AcceptChanges** lub **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiekt. Jeśli **AllowEdit** jest **false**, jest zwracany wyjątek, jeśli próbuje zmodyfikować wartość w **DataView**.  
  
 Kiedy istniejący **DataRowView** jest edytowany, zdarzenia podstawowych **DataTable** nadal będą zgłaszane z proponowanych zmian. Należy pamiętać, że jeśli wywołujesz **EndEdit** lub **metoda CancelEdit** na podstawowych **DataRow**, oczekujące zmiany zostaną zastosowane lub anulowane niezależnie od tego, czy  **EndEdit** lub **metoda CancelEdit** jest wywoływana na **DataRowView**.  
  
 Jeśli **AllowDelete** jest **true**, można usunąć wierszy z **DataView** za pomocą **usunąć** metody **DataView**  lub **DataRowView** obiektu, a wiersze są usuwane z podstawową **DataTable**. Później można zatwierdzić lub odrzucić usuwa przy użyciu **AcceptChanges** lub **RejectChanges** odpowiednio. Jeśli **AllowDelete** jest **false**, jest zwracany wyjątek, jeśli wywołujesz **usunąć** metody **DataView** lub  **DataRowView**.  
  
 Poniższy przykład kodu wyłącza używanie **DataView** do usuwania wierszy i dodaje nowy wiersz do tabeli podstawowej, korzystając **DataView**.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
