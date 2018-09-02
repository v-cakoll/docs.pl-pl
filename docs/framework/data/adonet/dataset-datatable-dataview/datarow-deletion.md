---
title: Usuwanie elementu DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: e7e687dfa6af47161be9d26054eb58f319a5099d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425599"
---
# <a name="datarow-deletion"></a><span data-ttu-id="fe68c-102">Usuwanie elementu DataRow</span><span class="sxs-lookup"><span data-stu-id="fe68c-102">DataRow Deletion</span></span>
<span data-ttu-id="fe68c-103">Istnieją dwie metody, które służy do usuwania <xref:System.Data.DataRow> obiektu z <xref:System.Data.DataTable> obiektu: **Usuń** metody <xref:System.Data.DataRowCollection> obiektu i <xref:System.Data.DataRow.Delete%2A> metody **DataRow**obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe68c-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="fe68c-104">Natomiast <xref:System.Data.DataRowCollection.Remove%2A> usuwa metoda **DataRow** z **kolekcji DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metody oznacza tylko wiersz do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fe68c-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="fe68c-105">Rzeczywiste usuwanie występuje, gdy aplikacja wywołuje **AcceptChanges** metody.</span><span class="sxs-lookup"><span data-stu-id="fe68c-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="fe68c-106">Za pomocą <xref:System.Data.DataRow.Delete%2A>, można programowo sprawdzić wiersze, które zostały oznaczone do usunięcia przed ich faktycznego usuwania.</span><span class="sxs-lookup"><span data-stu-id="fe68c-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="fe68c-107">Jeśli wiersz jest oznaczona do usunięcia, jego <xref:System.Data.DataRow.RowState%2A> właściwość jest ustawiona na <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe68c-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="fe68c-108">Ani <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> powinna być wywoływana podczas iteracji w pętli foreach <xref:System.Data.DataRowCollection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe68c-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="fe68c-109"><xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> modyfikowanie stanu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fe68c-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="fe68c-110">Korzystając z <xref:System.Data.DataSet> lub **DataTable** w połączeniu z **DataAdapter** i relacyjnym źródłem danych, użyj **Usuń** metody  **DataRow** do usunięcia wiersza.</span><span class="sxs-lookup"><span data-stu-id="fe68c-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="fe68c-111">**Usuń** metody oznacza wiersza jako **usunięte** w **DataSet** lub **DataTable** , ale nie spowoduje usunięcia go.</span><span class="sxs-lookup"><span data-stu-id="fe68c-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="fe68c-112">Zamiast tego, kiedy **DataAdapter** napotka oznaczonego jako **usunięte**, wykonuje jego **elementu DeleteCommand** metodę, aby usunąć wiersz w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="fe68c-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="fe68c-113">Wiersz można następnie trwale usunięte za pomocą **AcceptChanges** metody.</span><span class="sxs-lookup"><span data-stu-id="fe68c-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="fe68c-114">Jeśli używasz **Usuń** można usunąć wiersza, wiersz jest całkowicie usunięte z tabeli, ale **DataAdapter** nie spowoduje usunięcia wierszy w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="fe68c-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="fe68c-115">**Usuń** metody **kolekcji DataRowCollection** przyjmuje **DataRow** jako argument i usuwa go z kolekcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe68c-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="fe68c-116">Natomiast poniższy przykład pokazuje sposób wywołania **Usuń** metody **DataRow** można zmienić jego **RowState** do **usunięte** .</span><span class="sxs-lookup"><span data-stu-id="fe68c-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="fe68c-117">Jeśli wiersz jest oznaczona do usunięcia i wywołania **AcceptChanges** metody **DataTable** obiektu wiersza zostanie usunięty z **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="fe68c-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="fe68c-118">Z drugiej strony, jeśli wywołasz **RejectChanges**, **RowState** wiersza przywraca sprzed oznaczony jako **usunięte**.</span><span class="sxs-lookup"><span data-stu-id="fe68c-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe68c-119">Jeśli **RowState** z **DataRow** jest **dodano**, czyli został właśnie dodany do tabeli, a następnie jest oznaczony jako **usunięte**, jest usunięte z tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe68c-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe68c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe68c-120">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="fe68c-121">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="fe68c-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="fe68c-122">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fe68c-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
