---
title: Usuwanie elementu DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 57f51ada00bf24617ca3e295a010aae64f0aa849
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879869"
---
# <a name="datarow-deletion"></a>Usuwanie elementu DataRow
Istnieją dwie metody, które służy do usuwania <xref:System.Data.DataRow> obiektu z <xref:System.Data.DataTable> obiektu: **Usuń** metody <xref:System.Data.DataRowCollection> obiektu i <xref:System.Data.DataRow.Delete%2A> metody **DataRow**obiektu. Natomiast <xref:System.Data.DataRowCollection.Remove%2A> usuwa metoda **DataRow** z **kolekcji DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metody oznacza tylko wiersz do usunięcia. Rzeczywiste usuwanie występuje, gdy aplikacja wywołuje **AcceptChanges** metody. Za pomocą <xref:System.Data.DataRow.Delete%2A>, można programowo sprawdzić wiersze, które zostały oznaczone do usunięcia przed ich faktycznego usuwania. Jeśli wiersz jest oznaczona do usunięcia, jego <xref:System.Data.DataRow.RowState%2A> właściwość jest ustawiona na <xref:System.Data.DataRow.Delete%2A>.  
  
 Ani <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> powinna być wywoływana podczas iteracji w pętli foreach <xref:System.Data.DataRowCollection> obiektu. <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> modyfikowanie stanu kolekcji.  
  
 Korzystając z <xref:System.Data.DataSet> lub **DataTable** w połączeniu z **DataAdapter** i relacyjnym źródłem danych, użyj **Usuń** metody  **DataRow** do usunięcia wiersza. **Usuń** metody oznacza wiersza jako **usunięte** w **DataSet** lub **DataTable** , ale nie spowoduje usunięcia go. Zamiast tego, kiedy **DataAdapter** napotka oznaczonego jako **usunięte**, wykonuje jego **elementu DeleteCommand** metodę, aby usunąć wiersz w źródle danych. Wiersz można następnie trwale usunięte za pomocą **AcceptChanges** metody. Jeśli używasz **Usuń** można usunąć wiersza, wiersz jest całkowicie usunięte z tabeli, ale **DataAdapter** nie spowoduje usunięcia wierszy w źródle danych.  
  
 **Usuń** metody **kolekcji DataRowCollection** przyjmuje **DataRow** jako argument i usuwa go z kolekcji, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Natomiast poniższy przykład pokazuje sposób wywołania **Usuń** metody **DataRow** można zmienić jego **RowState** do **usunięte** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Jeśli wiersz jest oznaczona do usunięcia i wywołania **AcceptChanges** metody **DataTable** obiektu wiersza zostanie usunięty z **DataTable**. Z drugiej strony, jeśli wywołasz **RejectChanges**, **RowState** wiersza przywraca sprzed oznaczony jako **usunięte**.  
  
> [!NOTE]
>  Jeśli **RowState** z **DataRow** jest **dodano**, czyli został właśnie dodany do tabeli, a następnie jest oznaczony jako **usunięte**, jest usunięte z tabeli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
