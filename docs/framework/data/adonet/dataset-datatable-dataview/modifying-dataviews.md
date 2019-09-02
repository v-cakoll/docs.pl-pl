---
title: Modyfikowanie elementów DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 0b2bfd1b0490572e78c8ce365491a8d48db87684
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204575"
---
# <a name="modifying-dataviews"></a>Modyfikowanie elementów DataView
Można użyć <xref:System.Data.DataView> do dodawania, usuwania lub modyfikowania wierszy danych w tabeli źródłowej. Możliwość używania elementu **DataView** do modyfikowania danych w źródłowej tabeli jest kontrolowana przez ustawienie jednej z trzech właściwości logicznych elementu **DataView**. Te właściwości to <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>i <xref:System.Data.DataView.AllowDelete%2A>. Domyślnie ustawiono **wartość true** .  
  
 Jeśli **AllowNew** ma **wartość true**, <xref:System.Data.DataView.AddNew%2A> można użyć metody **widoku** danych, aby utworzyć nowy <xref:System.Data.DataRowView>. Należy zauważyć, że nowy wiersz nie jest faktycznie dodawany do elementu <xref:System.Data.DataTable> bazowego <xref:System.Data.DataRowView.EndEdit%2A> do momentu wywołania metody **DataRowView** . Jeśli wywoływana jest MetodaDataRowView,nowywierszjestodrzucany<xref:System.Data.DataRowView.CancelEdit%2A> . Należy zauważyć, że można edytować tylko jeden **DataRowView** w danym momencie. W przypadku wywołania metody **AddNew** lub **elementu BeginEdit** **DataRowView** , gdy istnieje oczekujący wiersz, **EndEdit** jest wywoływana niejawnie w oczekującym wierszu. Gdy **EndEdit** jest wywoływana, zmiany są stosowane do bazowego **elementu DataTable** i później mogą być zatwierdzane lub odrzucane przy użyciu metod **AcceptChanges** lub RejectChanges **tabeli DataTable**, **zestawu danych**lub  **Obiekt DataRow** . Jeśli **AllowNew** ma **wartość false**, wyjątek jest zgłaszany w przypadku wywołania metody **AddNew** elementu **DataRowView**.  
  
 Jeśli **AllowEdit** ma **wartość true**, można zmodyfikować zawartość obiektu **DataRow** za pośrednictwem **DataRowView**. Można potwierdzić zmiany w wierszu źródłowym przy użyciu **DataRowView. EndEdit** lub odrzucić zmiany przy użyciu **DataRowView. CancelEdit**. Należy zauważyć, że w danym momencie można edytować tylko jeden wiersz. W przypadku wywołania metody **AddNew** lub **elementu BeginEdit** **DataRowView** , gdy istnieje oczekujący wiersz, **EndEdit** jest wywoływana niejawnie w oczekującym wierszu. Gdy **EndEdit** jest wywoływana, proponowane zmiany są umieszczane w **bieżącej** wersji wiersza bazowego elementu **DataRow** i później mogą być zatwierdzane lub odrzucane przy użyciu metod **AcceptChanges lub RejectChanges Obiekt DataTable**, **DataSet**lub **DataRow** . Jeśli **AllowEdit** ma **wartość false**, wyjątek jest zgłaszany w przypadku próby zmodyfikowania wartości w **widoku**danych.  
  
 Podczas edytowania istniejącej **DataRowView** zdarzenia powiązanej **tabeli DataTable** będą nadal zgłaszane z proponowanymi zmianami. Należy pamiętać, że jeśli wywołasz **EndEdit** lub **CancelEdit** na bazowym elemencie **DataRow**, oczekujące zmiany zostaną zastosowane lub anulowane niezależnie od tego, czy **EndEdit** lub **CancelEdit** są wywoływane na **DataRowView**.  
  
 Jeśli **AllowDelete** ma **wartość true**, można usunąć wiersze z **widoku** danych za pomocą metody **delete** obiektu **DataView** lub **DataRowView** , a wiersze są usuwane z bazowego **elementu DataTable**. Można później zatwierdzać lub odrzucać usunięcia przy użyciu metody **AcceptChanges** lub **RejectChanges** . Jeśli **AllowDelete** ma **wartość false**, wyjątek jest zgłaszany w przypadku wywołania metody **delete** elementu **DataView** lub **DataRowView**.  
  
 Poniższy przykład kodu wyłącza używanie elementu **DataView** do usuwania wierszy i dodaje nowy wiersz do źródłowej tabeli przy użyciu **widoku**danych.  
  
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
- [Elementy DataView](dataviews.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
