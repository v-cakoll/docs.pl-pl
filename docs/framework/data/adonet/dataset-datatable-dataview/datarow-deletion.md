---
title: Usuwanie elementu DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 3f48339539f08bbc1c2c15035741375bd9ade553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784723"
---
# <a name="datarow-deletion"></a><span data-ttu-id="a957c-102">Usuwanie elementu DataRow</span><span class="sxs-lookup"><span data-stu-id="a957c-102">DataRow Deletion</span></span>
<span data-ttu-id="a957c-103">Istnieją dwie metody, których można użyć, aby usunąć <xref:System.Data.DataRow> obiekt <xref:System.Data.DataTable> z obiektu: <xref:System.Data.DataRow.Delete%2A> metodę <xref:System.Data.DataRowCollection> **Remove** obiektu i metodę obiektu **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="a957c-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="a957c-104">Natomiast Metoda usuwa element **DataRow** z obiektu **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> Metoda oznacza tylko wiersz do usunięcia. <xref:System.Data.DataRowCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="a957c-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="a957c-105">Faktyczne usunięcie odbywa się, gdy aplikacja wywołuje metodę **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="a957c-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="a957c-106">Za pomocą <xref:System.Data.DataRow.Delete%2A>programu można programowo sprawdzić, które wiersze są oznaczone do usunięcia przed ich faktycznym usunięciem.</span><span class="sxs-lookup"><span data-stu-id="a957c-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="a957c-107">Gdy wiersz jest oznaczony do usunięcia, jego <xref:System.Data.DataRow.RowState%2A> właściwość jest ustawiona na. <xref:System.Data.DataRow.Delete%2A></span><span class="sxs-lookup"><span data-stu-id="a957c-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="a957c-108">Nie <xref:System.Data.DataRow.Delete%2A> należy wywoływać ani wywołać w <xref:System.Data.DataRowCollection> pętli Foreach podczas iterowania za pomocą obiektu. <xref:System.Data.DataRowCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="a957c-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="a957c-109"><xref:System.Data.DataRow.Delete%2A>ani <xref:System.Data.DataRowCollection.Remove%2A> modyfikować stanu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a957c-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="a957c-110">W przypadku używania <xref:System.Data.DataSet> elementu **DataTable** w połączeniu z elementem **DataAdapter** i relacyjnym źródłem danych Użyj metody **delete** obiektu **DataRow** , aby usunąć wiersz.</span><span class="sxs-lookup"><span data-stu-id="a957c-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="a957c-111">Metoda **delete** oznacza wiersz jako **usunięty** w **zestawie danych** lub **DataTable** , ale nie usuwa go.</span><span class="sxs-lookup"><span data-stu-id="a957c-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="a957c-112">Zamiast tego, gdy element **DataAdapter** napotka wiersz oznaczony jako **usunięty**, wykonuje jego metodę **DeleteCommand** , aby usunąć wiersz w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a957c-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="a957c-113">Wiersz można następnie trwale usunąć za pomocą metody **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="a957c-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="a957c-114">Jeśli używasz **Usuń** do usunięcia wiersza, wiersz zostanie usunięty całkowicie z tabeli, ale element **DataAdapter** nie usunie wiersza ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a957c-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="a957c-115">Metoda **Remove** obiektu **DataRowCollection** przyjmuje element **DataRow** jako argument i usuwa go z kolekcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a957c-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="a957c-116">W poniższym przykładzie pokazano, jak wywołać metodę **delete** dla elementu **DataRow** , aby zmienić **RowState** na **usunięty**.</span><span class="sxs-lookup"><span data-stu-id="a957c-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="a957c-117">Jeśli wiersz jest oznaczony do usunięcia i wywoływana jest metoda **AcceptChanges** obiektu **DataTable** , wiersz zostanie usunięty z **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a957c-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="a957c-118">Z drugiej strony, jeśli wywołasz **RejectChanges**, **RowState** wiersza powróci do tego, co było przed oznaczeniem jako **usunięte**.</span><span class="sxs-lookup"><span data-stu-id="a957c-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a957c-119">Jeśli **RowState** elementu **DataRow** zostanie **dodany**, oznacza to, że został on właśnie dodany do tabeli, a następnie jest oznaczony jako **usunięty**, zostanie usunięty z tabeli.</span><span class="sxs-lookup"><span data-stu-id="a957c-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a957c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a957c-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a957c-121">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="a957c-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a957c-122">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a957c-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
