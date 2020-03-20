---
title: Ograniczenia elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151289"
---
# <a name="datatable-constraints"></a><span data-ttu-id="1d5fa-102">Ograniczenia elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="1d5fa-102">DataTable Constraints</span></span>
<span data-ttu-id="1d5fa-103">Ograniczenia można użyć do wymuszenia ograniczeń <xref:System.Data.DataTable>dotyczących danych w programie , aby zachować integralność danych.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="1d5fa-104">Ograniczenie jest regułą automatyczną, zastosowaną do kolumny lub powiązanych kolumn, która określa przebieg akcji, gdy wartość wiersza jest w jakiś sposób zmieniona.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="1d5fa-105">Ograniczenia są wymuszane, `System.Data.DataSet.EnforceConstraints` <xref:System.Data.DataSet> gdy właściwość jest **true**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="1d5fa-106">Przykład kodu, który pokazuje, `EnforceConstraints` jak ustawić <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość, zobacz temat odwołania.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="1d5fa-107">Istnieją dwa rodzaje ograniczeń w ADO.NET: <xref:System.Data.ForeignKeyConstraint> i . <xref:System.Data.UniqueConstraint></span><span class="sxs-lookup"><span data-stu-id="1d5fa-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="1d5fa-108">Domyślnie oba ograniczenia są tworzone automatycznie podczas tworzenia relacji między dwiema <xref:System.Data.DataRelation> lub więcej tabelami przez dodanie a do **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="1d5fa-109">Jednak można wyłączyć to zachowanie, określając **createConstraints** = **false** podczas tworzenia relacji.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="1d5fa-110">Foreignkeyconstraint</span><span class="sxs-lookup"><span data-stu-id="1d5fa-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="1d5fa-111">**ForeignKeyConstraint** wymusza reguły dotyczące sposobu aktualizacji i usuwania powiązanych tabel są propagowane.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="1d5fa-112">Na przykład jeśli wartość w wierszu jednej tabeli jest aktualizowana lub usunięta, a ta sama wartość jest również używana w jednej lub kilku powiązanych tabelach, **ForeignKeyConstraint** określa, co się dzieje w powiązanych tabelach.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="1d5fa-113">Właściwości <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> i **ForeignKeyConstraint** zdefiniować akcję, która ma zostać podjęta, gdy użytkownik próbuje usunąć lub zaktualizować wiersz w powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="1d5fa-114">W poniższej tabeli opisano różne ustawienia dostępne dla **właściwości DeleteRule** i **UpdateRule** właściwości **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="1d5fa-115">Ustawienie reguły</span><span class="sxs-lookup"><span data-stu-id="1d5fa-115">Rule setting</span></span>|<span data-ttu-id="1d5fa-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1d5fa-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="1d5fa-117">**Kaskadowo**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-117">**Cascade**</span></span>|<span data-ttu-id="1d5fa-118">Usuwanie lub aktualizowanie powiązanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="1d5fa-119">**Setnull**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-119">**SetNull**</span></span>|<span data-ttu-id="1d5fa-120">Ustaw wartości w powiązanych wierszach na **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="1d5fa-121">**SetDefault (Domyślnie)**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-121">**SetDefault**</span></span>|<span data-ttu-id="1d5fa-122">Ustaw wartości w powiązanych wierszach na wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="1d5fa-123">**Brak**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-123">**None**</span></span>|<span data-ttu-id="1d5fa-124">Nie podejmuj żadnych działań w powiązanych wierszach.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-124">Take no action on related rows.</span></span> <span data-ttu-id="1d5fa-125">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-125">This is the default.</span></span>|  
  
 <span data-ttu-id="1d5fa-126">A **ForeignKeyConstraint** można ograniczyć, a także propagować zmiany w powiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="1d5fa-127">W zależności od właściwości ustawionych dla **ForeignKeyConstraint** kolumny, jeśli **EnforceConstraints** właściwość **DataSet** jest **true**, wykonywanie niektórych operacji w wierszu nadrzędnym spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="1d5fa-128">Na przykład jeśli **DeleteRule** właściwość **ForeignKeyConstraint** jest **Brak**, wiersz nadrzędny nie można usunąć, jeśli ma żadnych wierszy podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="1d5fa-129">Ograniczenie klucza obcego między pojedynczymi kolumnami lub między tablicą kolumn można utworzyć przy użyciu konstruktora **ForeignKeyConstraint.**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="1d5fa-130">Przekaż wynikowy **Obiekt ForeignKeyConstraint** do **Add** metody tabeli **Constraints** właściwości, która jest **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="1d5fa-131">Można również przekazać argumenty konstruktora do kilku przeciążeń **Add** metody **ConstraintCollection,** aby utworzyć **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="1d5fa-132">Podczas tworzenia **ForeignKeyConstraint**, można przekazać **DeleteRule** i **UpdateRule** wartości do konstruktora jako argumenty lub można ustawić je jako właściwości, jak w poniższym przykładzie (gdzie **Wartość DeleteRule** jest ustawiona na **Brak**).</span><span class="sxs-lookup"><span data-stu-id="1d5fa-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="1d5fa-133">Acceptrejectrule</span><span class="sxs-lookup"><span data-stu-id="1d5fa-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="1d5fa-134">Zmiany w wierszach można zaakceptować za pomocą **acceptChanges** metody lub anulować przy użyciu **RejectChanges** metody **DataSet**, **DataTable**lub **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="1d5fa-135">Gdy **zestaw danych** zawiera **foreignkeyconstraints**, wywoływanie **AcceptChanges** lub **RejectChanges** metody wymusza **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="1d5fa-136">**AcceptRejectRule** właściwość **ForeignKeyConstraint** określa, które działania zostaną podjęte w wierszach podrzędnych, gdy **AcceptChanges** lub **RejectChanges** jest wywoływana w wierszu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="1d5fa-137">W poniższej tabeli wymieniono dostępne ustawienia **reguły AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="1d5fa-138">Ustawienie reguły</span><span class="sxs-lookup"><span data-stu-id="1d5fa-138">Rule setting</span></span>|<span data-ttu-id="1d5fa-139">Opis</span><span class="sxs-lookup"><span data-stu-id="1d5fa-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="1d5fa-140">**Kaskadowo**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-140">**Cascade**</span></span>|<span data-ttu-id="1d5fa-141">Akceptowanie lub odrzucanie zmian w wierszach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="1d5fa-142">**Brak**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-142">**None**</span></span>|<span data-ttu-id="1d5fa-143">Nie podejmuj żadnych działań w wierszach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-143">Take no action on child rows.</span></span> <span data-ttu-id="1d5fa-144">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="1d5fa-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d5fa-145">Example</span></span>  
 <span data-ttu-id="1d5fa-146">Poniższy przykład <xref:System.Data.ForeignKeyConstraint>tworzy , ustawia kilka jego <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>właściwości, w tym <xref:System.Data.ConstraintCollection> , <xref:System.Data.DataTable> i dodaje go do obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="1d5fa-147">Uniqueconstraint</span><span class="sxs-lookup"><span data-stu-id="1d5fa-147">UniqueConstraint</span></span>  
 <span data-ttu-id="1d5fa-148">**UniqueConstraint** obiektu, który może być przypisany do jednej kolumny lub do tablicy kolumn w **DataTable**, zapewnia, że wszystkie dane w określonej kolumnie lub kolumnach jest unikatowy dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="1d5fa-149">Unikatowe ograniczenie dla kolumny lub tablicy kolumn można utworzyć za pomocą konstruktora **UniqueConstraint.**</span><span class="sxs-lookup"><span data-stu-id="1d5fa-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="1d5fa-150">Przekaż wynikowy **UniqueConstraint** obiektu do **Add** metody tabeli **Constraints** właściwości, która jest **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="1d5fa-151">Można również przekazać argumenty konstruktora do kilku przeciążeń **Add** metody **ConstraintCollection,** aby utworzyć **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="1d5fa-152">Podczas tworzenia **UniqueConstraint** dla kolumny lub kolumn, można opcjonalnie określić, czy kolumna lub kolumny są kluczem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="1d5fa-153">Można również utworzyć unikatowe ograniczenie dla kolumny, ustawiając **właściwość Unikatowa** kolumny na **true**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="1d5fa-154">Alternatywnie ustawienie **Unique** właściwość pojedynczej kolumny na **false** usuwa wszelkie unikatowe ograniczenie, które mogą istnieć.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="1d5fa-155">Zdefiniowanie kolumny lub kolumn jako klucza podstawowego tabeli spowoduje automatyczne utworzenie unikatowego ograniczenia dla określonej kolumny lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="1d5fa-156">Jeśli usuniesz kolumnę z **Właściwości PrimaryKey** **datatable,** **UniqueConstraint** zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="1d5fa-157">Poniższy przykład tworzy **UniqueConstraint** dla dwóch kolumn **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="1d5fa-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]
    {custTable.Columns["CustomerID"],
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d5fa-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d5fa-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="1d5fa-159">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="1d5fa-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="1d5fa-160">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="1d5fa-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1d5fa-161">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d5fa-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
