---
title: Modyfikowanie DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3663b0317176495b13b1092652bd8bf4c79f30d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="modifying-dataviews"></a><span data-ttu-id="970cc-102">Modyfikowanie DataViews</span><span class="sxs-lookup"><span data-stu-id="970cc-102">Modifying DataViews</span></span>
<span data-ttu-id="970cc-103">Można użyć <xref:System.Data.DataView> na dodawanie, usuwanie i modyfikowanie wierszy danych w tabeli podstawowej.</span><span class="sxs-lookup"><span data-stu-id="970cc-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="970cc-104">Możliwość używania **DataView** można modyfikować danych w tabeli podstawowej jest kontrolowany przez ustawienia jednej z trzech logicznych właściwości **DataView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="970cc-105">Te właściwości są <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, i <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="970cc-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="970cc-106">Są ustawione **true** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="970cc-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="970cc-107">Jeśli **element AllowNew** jest **true**, można użyć <xref:System.Data.DataView.AddNew%2A> metody **DataView** do tworzenia nowego <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="970cc-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="970cc-108">Należy pamiętać, że nowy wiersz nie jest rzeczywiście dodane do odpowiadającego <xref:System.Data.DataTable> do momentu <xref:System.Data.DataRowView.EndEdit%2A> metody **DataRowView** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="970cc-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="970cc-109">Jeśli <xref:System.Data.DataRowView.CancelEdit%2A> metody **DataRowView** jest wywołana, nowy wiersz jest pomijany.</span><span class="sxs-lookup"><span data-stu-id="970cc-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="970cc-110">Należy też zauważyć, że można edytować tylko jeden **DataRowView** naraz.</span><span class="sxs-lookup"><span data-stu-id="970cc-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="970cc-111">Jeśli należy wywołać **AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit** jest wywoływany niejawnie na Oczekujące wiersza.</span><span class="sxs-lookup"><span data-stu-id="970cc-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="970cc-112">Gdy **EndEdit** jest wywołana, zmiany zostaną zastosowane do odpowiadającego **DataTable** lub nowszego mogą być zatwierdzone lub odrzucone, za pomocą **AcceptChanges** lub  **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiektu.</span><span class="sxs-lookup"><span data-stu-id="970cc-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="970cc-113">Jeśli **element AllowNew** jest **false**, jest zwracany wyjątek, jeśli wywołujesz **AddNew** metody **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="970cc-114">Jeśli **AllowEdit** jest **true**, możesz zmodyfikować zawartość **DataRow** za pośrednictwem **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="970cc-115">Można potwierdzić zmiany podstawowej za pomocą wiersza **DataRowView.EndEdit** lub Odrzuć zmiany przy użyciu **DataRowView.CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="970cc-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="970cc-116">Należy pamiętać, że aby tylko jeden wiersz może być edytowany w czasie.</span><span class="sxs-lookup"><span data-stu-id="970cc-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="970cc-117">Jeśli należy wywołać **AddNew** lub **BeginEdit** metody **DataRowView** podczas, gdy istnieje oczekujące wiersza, **EndEdit** jest wywoływany niejawnie na Oczekujące wiersza.</span><span class="sxs-lookup"><span data-stu-id="970cc-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="970cc-118">Gdy **EndEdit** jest wywoływana, proponowanych zmian są umieszczane w **bieżącego** wersja wiersza podstawowych **DataRow** lub nowszego mogą być zatwierdzone lub odrzucone, przy użyciu  **Metoda AcceptChanges** lub **RejectChanges** metody **DataTable**, **DataSet**, lub **DataRow** obiekt.</span><span class="sxs-lookup"><span data-stu-id="970cc-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="970cc-119">Jeśli **AllowEdit** jest **false**, jest zwracany wyjątek, jeśli próbuje zmodyfikować wartość w **DataView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="970cc-120">Kiedy istniejący **DataRowView** jest edytowany, zdarzenia podstawowych **DataTable** nadal będą zgłaszane z proponowanych zmian.</span><span class="sxs-lookup"><span data-stu-id="970cc-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="970cc-121">Należy pamiętać, że jeśli wywołujesz **EndEdit** lub **metoda CancelEdit** na podstawowych **DataRow**, oczekujące zmiany zostaną zastosowane lub anulowane niezależnie od tego, czy  **EndEdit** lub **metoda CancelEdit** jest wywoływana na **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="970cc-122">Jeśli **AllowDelete** jest **true**, można usunąć wierszy z **DataView** za pomocą **usunąć** metody **DataView**  lub **DataRowView** obiektu, a wiersze są usuwane z podstawową **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="970cc-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="970cc-123">Później można zatwierdzić lub odrzucić usuwa przy użyciu **AcceptChanges** lub **RejectChanges** odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="970cc-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="970cc-124">Jeśli **AllowDelete** jest **false**, jest zwracany wyjątek, jeśli wywołujesz **usunąć** metody **DataView** lub  **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="970cc-125">Poniższy przykład kodu wyłącza używanie **DataView** do usuwania wierszy i dodaje nowy wiersz do tabeli podstawowej, korzystając **DataView**.</span><span class="sxs-lookup"><span data-stu-id="970cc-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="970cc-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="970cc-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="970cc-127">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="970cc-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="970cc-128">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="970cc-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
