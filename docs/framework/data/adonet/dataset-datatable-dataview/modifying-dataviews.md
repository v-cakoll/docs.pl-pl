---
title: Modyfikowanie elementów DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3b1e0cbfc6118ad9ca670f5d91183b78b2c99d89
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225649"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="6f8dd-102">Modyfikowanie elementów DataView</span><span class="sxs-lookup"><span data-stu-id="6f8dd-102">Modifying DataViews</span></span>
<span data-ttu-id="6f8dd-103">Możesz użyć <xref:System.Data.DataView> na dodawanie, usuwanie i modyfikowanie wierszy danych w tabeli podstawowej.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="6f8dd-104">Możliwość używania **DataView** do modyfikacji danych w tabeli podstawowej jest kontrolowana przez ustawienia jednej z trzech właściwości logiczna **DataView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="6f8dd-105">Te właściwości są <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, i <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="6f8dd-106">Są one ustawione **true** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="6f8dd-107">Jeśli **element AllowNew** jest **true**, możesz użyć <xref:System.Data.DataView.AddNew%2A> metody **DataView** do tworzenia nowego <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="6f8dd-108">Należy zauważyć, że nowy wiersz nie jest faktycznie dodane do bazowego <xref:System.Data.DataTable> aż <xref:System.Data.DataRowView.EndEdit%2A> metody **DataRowView** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="6f8dd-109">Jeśli <xref:System.Data.DataRowView.CancelEdit%2A> metody **DataRowView** jest wywoływana, nowego wiersza są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="6f8dd-110">Należy zauważyć, że możesz edytować tylko jeden **DataRowView** w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="6f8dd-111">Jeśli wywołasz **działają funkcje AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit —** jest wywoływany niejawnie na Oczekujące wiersz.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="6f8dd-112">Gdy **EndEdit —** jest wywoływana, zmiany zostaną zastosowane do podstawowej **DataTable** i później może być zatwierdzone lub odrzucone, za pomocą **AcceptChanges** lub  **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiektu.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="6f8dd-113">Jeśli **element AllowNew** jest **false**, jest zgłaszany wyjątek, jeśli wywołasz **działają funkcje AddNew** metody **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="6f8dd-114">Jeśli **AllowEdit** jest **true**, możesz zmodyfikować zawartość **DataRow** za pośrednictwem **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="6f8dd-115">Możesz sprawdzić zmiany do podstawowej przy użyciu wiersza **DataRowView.EndEdit** lub odrzucić zmiany, przy użyciu **DataRowView.CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="6f8dd-116">Pamiętaj, że tylko jeden wiersz, mogą być edytowane w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="6f8dd-117">Jeśli wywołasz **działają funkcje AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit —** jest wywoływany niejawnie na Oczekujące wiersz.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="6f8dd-118">Podczas **EndEdit —** jest wywoływana, proponowane zmiany są umieszczane w **bieżącego** wersji wiersza elementu bazowego **DataRow** i później może być zatwierdzone lub odrzucone, za pomocą  **Metoda AcceptChanges** lub **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiekt.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="6f8dd-119">Jeśli **AllowEdit** jest **false**, jest zgłaszany wyjątek, Jeśli spróbujesz zmodyfikować wartość w **DataView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="6f8dd-120">Kiedy istniejący **DataRowView** jest edytowany, zdarzenia bazowego **DataTable** nadal będą zgłaszane z proponowanych zmian.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="6f8dd-121">Należy pamiętać, że jeśli wywołasz **EndEdit —** lub **CancelEdit** na podstawowych **DataRow**, oczekujące zmiany zostaną zastosowane lub anulowane niezależnie od tego, czy  **EndEdit —** lub **CancelEdit** jest wywoływana w **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="6f8dd-122">Jeśli **AllowDelete** jest **true**, można usunąć wierszy z **DataView** przy użyciu **Usuń** metody **DataView**  lub **DataRowView** obiektu i wiersze zostaną usunięte z bazowego **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="6f8dd-123">Później można zatwierdzić lub odrzucić usuwa przy użyciu **AcceptChanges** lub **RejectChanges** odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="6f8dd-124">Jeśli **AllowDelete** jest **false**, jest zgłaszany wyjątek, jeśli wywołasz **Usuń** metody **DataView** lub  **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="6f8dd-125">Poniższy przykład kodu, który powoduje wyłączenie przy użyciu **DataView** do usuwania wierszy i dodaje nowy wiersz do tabeli podstawowej z użyciem **DataView**.</span><span class="sxs-lookup"><span data-stu-id="6f8dd-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f8dd-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f8dd-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="6f8dd-127">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="6f8dd-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="6f8dd-128">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6f8dd-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
