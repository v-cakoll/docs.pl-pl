---
title: Wnioskowanie relacji
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666853"
---
# <a name="inferring-relationships"></a><span data-ttu-id="e20cc-102">Wnioskowanie relacji</span><span class="sxs-lookup"><span data-stu-id="e20cc-102">Inferring Relationships</span></span>
<span data-ttu-id="e20cc-103">Jeśli element, który jest wnioskowany jako tabela ma element podrzędny, która została wywnioskowana, także jako tabelę, <xref:System.Data.DataRelation> zostaną utworzone między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="e20cc-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="e20cc-104">Nową kolumnę o nazwie **ParentTableName_Id** zostaną dodane do tabeli, który został utworzony dla elementu nadrzędnego i tabelę utworzoną dla elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="e20cc-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="e20cc-105">**ColumnMapping** właściwość ta kolumna identity jest równa **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="e20cc-106">Kolumna będzie zwiększenie automatycznie klucz podstawowy dla tabeli nadrzędnej i będą używane dla **DataRelation** między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="e20cc-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="e20cc-107">Typ danych w kolumnie tożsamości dodano będzie **System.Int32**, inaczej niż w przypadku wszystkich pozostałych kolumn wywnioskowane na typ danych, który jest **System.String**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="e20cc-108">A <xref:System.Data.ForeignKeyConstraint> z **DeleteRule** = **Cascade** zostanie również utworzony przy użyciu nowej kolumny w tabelach nadrzędne i podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e20cc-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="e20cc-109">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="e20cc-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e20cc-110">Procesu wnioskowania dadzą dwie tabele: **Element1** i **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="e20cc-111">**Element1** tabela będzie zawierać dwie kolumny: **Element1_Id** i **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="e20cc-112">**ColumnMapping** właściwość **Element1_Id** kolumna zostanie ustawiona **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="e20cc-113">**ColumnMapping** właściwość **ChildElement2** kolumna zostanie ustawiona **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="e20cc-114">**Element1_Id** kolumny zostanie ustawiony jako klucz podstawowy **Element1** tabeli.</span><span class="sxs-lookup"><span data-stu-id="e20cc-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="e20cc-115">**ChildElement1** tabela ma trzy kolumny: **attr1**, **attr2** i **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="e20cc-116">**ColumnMapping** właściwość **attr1** i **attr2** kolumny zostaną ustawione **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="e20cc-117">**ColumnMapping** właściwość **Element1_Id** kolumna zostanie ustawiona **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="e20cc-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="e20cc-118">A **DataRelation** i **ForeignKeyConstraint** zostanie utworzona z użyciem **Element1_Id** kolumny z obu tabel.</span><span class="sxs-lookup"><span data-stu-id="e20cc-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="e20cc-119">**Zestaw danych:** elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e20cc-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e20cc-120">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="e20cc-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e20cc-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e20cc-121">Element1_Id</span></span>|<span data-ttu-id="e20cc-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="e20cc-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="e20cc-123">0</span><span class="sxs-lookup"><span data-stu-id="e20cc-123">0</span></span>|<span data-ttu-id="e20cc-124">Tekst2</span><span class="sxs-lookup"><span data-stu-id="e20cc-124">Text2</span></span>|  
  
 <span data-ttu-id="e20cc-125">**Tabela:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e20cc-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="e20cc-126">attr1</span><span class="sxs-lookup"><span data-stu-id="e20cc-126">attr1</span></span>|<span data-ttu-id="e20cc-127">attr2</span><span class="sxs-lookup"><span data-stu-id="e20cc-127">attr2</span></span>|<span data-ttu-id="e20cc-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e20cc-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="e20cc-129">Wartość1</span><span class="sxs-lookup"><span data-stu-id="e20cc-129">value1</span></span>|<span data-ttu-id="e20cc-130">Wartość2</span><span class="sxs-lookup"><span data-stu-id="e20cc-130">value2</span></span>|<span data-ttu-id="e20cc-131">0</span><span class="sxs-lookup"><span data-stu-id="e20cc-131">0</span></span>|  
  
 <span data-ttu-id="e20cc-132">**DataRelation —:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e20cc-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="e20cc-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="e20cc-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="e20cc-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e20cc-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="e20cc-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e20cc-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="e20cc-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e20cc-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="e20cc-137">**Zagnieżdżone:** True</span><span class="sxs-lookup"><span data-stu-id="e20cc-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="e20cc-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e20cc-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="e20cc-139">**Kolumna:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e20cc-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="e20cc-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="e20cc-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="e20cc-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e20cc-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="e20cc-142">**DeleteRule:** kaskadowo</span><span class="sxs-lookup"><span data-stu-id="e20cc-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="e20cc-143">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="e20cc-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20cc-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e20cc-144">See Also</span></span>  
 [<span data-ttu-id="e20cc-145">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="e20cc-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="e20cc-146">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="e20cc-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="e20cc-147">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="e20cc-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="e20cc-148">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="e20cc-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="e20cc-149">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="e20cc-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="e20cc-150">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="e20cc-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="e20cc-151">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e20cc-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
