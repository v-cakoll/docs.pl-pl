---
title: Usuwanie elementu DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 46109ee1781b8b509df87b4203c51a55b9f596ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205107"
---
# <a name="datarow-deletion"></a>Usuwanie elementu DataRow
Istnieją dwie metody, których można użyć, aby usunąć <xref:System.Data.DataRow> obiekt <xref:System.Data.DataTable> z obiektu: <xref:System.Data.DataRow.Delete%2A> metodę <xref:System.Data.DataRowCollection> **Remove** obiektu i metodę obiektu **DataRow** . Natomiast Metoda usuwa element **DataRow** z obiektu **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> Metoda oznacza tylko wiersz do usunięcia. <xref:System.Data.DataRowCollection.Remove%2A> Faktyczne usunięcie odbywa się, gdy aplikacja wywołuje metodę **AcceptChanges** . Za pomocą <xref:System.Data.DataRow.Delete%2A>programu można programowo sprawdzić, które wiersze są oznaczone do usunięcia przed ich faktycznym usunięciem. Gdy wiersz jest oznaczony do usunięcia, jego <xref:System.Data.DataRow.RowState%2A> właściwość jest ustawiona na. <xref:System.Data.DataRow.Delete%2A>  
  
 Nie <xref:System.Data.DataRow.Delete%2A> należy wywoływać ani wywołać w <xref:System.Data.DataRowCollection> pętli Foreach podczas iterowania za pomocą obiektu. <xref:System.Data.DataRowCollection.Remove%2A> <xref:System.Data.DataRow.Delete%2A>ani <xref:System.Data.DataRowCollection.Remove%2A> modyfikować stanu kolekcji.  
  
 W przypadku używania <xref:System.Data.DataSet> elementu **DataTable** w połączeniu z elementem **DataAdapter** i relacyjnym źródłem danych Użyj metody **delete** obiektu **DataRow** , aby usunąć wiersz. Metoda **delete** oznacza wiersz jako **usunięty** w **zestawie danych** lub **DataTable** , ale nie usuwa go. Zamiast tego, gdy element **DataAdapter** napotka wiersz oznaczony jako **usunięty**, wykonuje jego metodę **DeleteCommand** , aby usunąć wiersz w źródle danych. Wiersz można następnie trwale usunąć za pomocą metody **AcceptChanges** . Jeśli używasz **Usuń** do usunięcia wiersza, wiersz zostanie usunięty całkowicie z tabeli, ale element **DataAdapter** nie usunie wiersza ze źródła danych.  
  
 Metoda **Remove** obiektu DataRowCollection przyjmuje element **DataRow** jako argument i usuwa go z kolekcji, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 W poniższym przykładzie pokazano, jak wywołać metodę **delete** dla elementu **DataRow** , aby zmienić **RowState** na **usunięty**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Jeśli wiersz jest oznaczony do usunięcia i wywoływana jest metoda **AcceptChanges** obiektu **DataTable** , wiersz zostanie usunięty z **tabeli DataTable**. Z drugiej strony, jeśli wywołasz **RejectChanges**, **RowState** wiersza powróci do tego, co było przed oznaczeniem jako **usunięte**.  
  
> [!NOTE]
> Jeśli **RowState** elementu **DataRow** zostanie **dodany**, oznacza to, że został on właśnie dodany do tabeli, a następnie jest oznaczony jako **usunięty**, zostanie usunięty z tabeli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
