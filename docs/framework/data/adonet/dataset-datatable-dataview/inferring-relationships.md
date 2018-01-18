---
title: Wnioskowanie relacji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 79f79c1dbc74b98cff10de81c2bd7bd32d7d286b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-relationships"></a><span data-ttu-id="cd6ce-102">Wnioskowanie relacji</span><span class="sxs-lookup"><span data-stu-id="cd6ce-102">Inferring Relationships</span></span>
<span data-ttu-id="cd6ce-103">Jeśli element, który jest wywnioskowany jako tabela ma element podrzędny, która jest również wykryta jako tabelę, <xref:System.Data.DataRelation> zostanie utworzona między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="cd6ce-104">Nową kolumnę o nazwie **ParentTableName_Id** zostaną dodane do tabeli utworzony dla elementu nadrzędnego oraz tabela utworzona dla elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="cd6ce-105">**ColumnMapping** zostanie ustawiona właściwość tej kolumny tożsamości do **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="cd6ce-106">Kolumna będzie zwiększanie automatycznie klucz podstawowy dla tabeli nadrzędnej i będzie służyć do **DataRelation** między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="cd6ce-107">Typ danych kolumny tożsamości dodano będzie **System.Int32**, w odróżnieniu od typu danych wszystkie inne wnioskowany kolumny, która jest **System.String**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="cd6ce-108">A <xref:System.Data.ForeignKeyConstraint> z **DeleteRule** = **Cascade** zostanie utworzony również w tabelach nadrzędne i podrzędne za pomocą nowej kolumny.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="cd6ce-109">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="cd6ce-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="cd6ce-110">Proces wnioskowania spowoduje utworzenie dwóch tabel: **Element1** i **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="cd6ce-111">**Element1** tabela będzie mieć dwie kolumny: **Element1_Id** i **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="cd6ce-112">**ColumnMapping** właściwość **Element1_Id** kolumny zostanie ustawiona do **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="cd6ce-113">**ColumnMapping** właściwość **ChildElement2** kolumny zostanie ustawiona do **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="cd6ce-114">**Element1_Id** kolumny zostanie ustawione jako klucz podstawowy **Element1** tabeli.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="cd6ce-115">**ChildElement1** tabela będzie miała trzy kolumny: **attr1**, **attr2** i **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="cd6ce-116">**ColumnMapping** właściwość **attr1** i **attr2** kolumn zostanie ustawiona do **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="cd6ce-117">**ColumnMapping** właściwość **Element1_Id** kolumny zostanie ustawiona do **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="cd6ce-118">A **DataRelation** i **ForeignKeyConstraint** zostanie utworzona z użyciem **Element1_Id** kolumny z obu tabel.</span><span class="sxs-lookup"><span data-stu-id="cd6ce-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="cd6ce-119">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="cd6ce-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="cd6ce-120">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="cd6ce-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="cd6ce-121">Element1_Id</span></span>|<span data-ttu-id="cd6ce-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="cd6ce-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="cd6ce-123">0</span><span class="sxs-lookup"><span data-stu-id="cd6ce-123">0</span></span>|<span data-ttu-id="cd6ce-124">Tekst2</span><span class="sxs-lookup"><span data-stu-id="cd6ce-124">Text2</span></span>|  
  
 <span data-ttu-id="cd6ce-125">**Tabela:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="cd6ce-126">attr1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-126">attr1</span></span>|<span data-ttu-id="cd6ce-127">attr2</span><span class="sxs-lookup"><span data-stu-id="cd6ce-127">attr2</span></span>|<span data-ttu-id="cd6ce-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="cd6ce-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="cd6ce-129">Wartość1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-129">value1</span></span>|<span data-ttu-id="cd6ce-130">Wartość2</span><span class="sxs-lookup"><span data-stu-id="cd6ce-130">value2</span></span>|<span data-ttu-id="cd6ce-131">0</span><span class="sxs-lookup"><span data-stu-id="cd6ce-131">0</span></span>|  
  
 <span data-ttu-id="cd6ce-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="cd6ce-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="cd6ce-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="cd6ce-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="cd6ce-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="cd6ce-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="cd6ce-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="cd6ce-137">**Zagnieżdżone:** wartość True</span><span class="sxs-lookup"><span data-stu-id="cd6ce-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="cd6ce-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="cd6ce-139">**Kolumna:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="cd6ce-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="cd6ce-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="cd6ce-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="cd6ce-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="cd6ce-142">**DeleteRule:** kaskadowo</span><span class="sxs-lookup"><span data-stu-id="cd6ce-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="cd6ce-143">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="cd6ce-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6ce-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd6ce-144">See Also</span></span>  
 [<span data-ttu-id="cd6ce-145">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cd6ce-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="cd6ce-146">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cd6ce-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="cd6ce-147">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cd6ce-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="cd6ce-148">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="cd6ce-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="cd6ce-149">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="cd6ce-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="cd6ce-150">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="cd6ce-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="cd6ce-151">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="cd6ce-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
