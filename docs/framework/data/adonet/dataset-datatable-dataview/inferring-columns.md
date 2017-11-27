---
title: Wnioskowanie kolumn
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba06bce55db53de1da1c07d2a6451d5664fa23bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-columns"></a><span data-ttu-id="271b6-102">Wnioskowanie kolumn</span><span class="sxs-lookup"><span data-stu-id="271b6-102">Inferring Columns</span></span>
<span data-ttu-id="271b6-103">Po ADO.NET stwierdził z dokumentu XML które elementy do wywnioskowania jako tabele dla <xref:System.Data.DataSet>, następnie wnioskuje kolumn dla tych tabel.</span><span class="sxs-lookup"><span data-stu-id="271b6-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="271b6-104">ADO.NET 2.0 wprowadzono nowy aparat wnioskowania schematu, którego wnioskuje typ silnie typizowane dane dla każdego **simpleType** elementu.</span><span class="sxs-lookup"><span data-stu-id="271b6-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="271b6-105">W poprzednich wersjach, dane typu wywnioskowane **simpleType** był zawsze **element xsd: String**.</span><span class="sxs-lookup"><span data-stu-id="271b6-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="271b6-106">Migracji i zgodności z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="271b6-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="271b6-107">**ReadXml** metoda przyjmuje argument typu **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="271b6-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="271b6-108">Ten argument można określić zachowanie wnioskowania zgodność z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="271b6-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="271b6-109">Dostępne wartości **InferSchema** wyliczenie przedstawiono w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="271b6-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="271b6-110">Zapewnia zgodność z poprzednimi wersjami przez zawsze wnioskowanie typu prostego jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="271b6-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="271b6-111">Wnioskuje typ silnie typizowane dane.</span><span class="sxs-lookup"><span data-stu-id="271b6-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="271b6-112">Zgłasza wyjątek, jeśli jest używana z <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="271b6-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="271b6-113">Ignoruje wszystkie wbudowanego schematu i odczytuje dane do istniejącego <xref:System.Data.DataSet> schematu.</span><span class="sxs-lookup"><span data-stu-id="271b6-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="271b6-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="271b6-114">Attributes</span></span>  
 <span data-ttu-id="271b6-115">Zgodnie z definicją w [wnioskowanie tabel](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), będzie można wywnioskować elementu z atrybutami jako tabelę.</span><span class="sxs-lookup"><span data-stu-id="271b6-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="271b6-116">Atrybuty elementu następnie będzie można wywnioskować jako kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="271b6-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="271b6-117">**ColumnMapping** będzie mieć ustawioną właściwość kolumn **MappingType.Attribute**, aby upewnić się, że nazwy kolumn zostanie zapisany jako atrybuty Jeśli schemat nie są zapisywane do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="271b6-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="271b6-118">Wartości atrybutów są przechowywane w wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="271b6-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="271b6-119">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="271b6-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="271b6-120">Proces wnioskowania spowoduje utworzenie tabeli o nazwie **Element1** z dwiema kolumnami, **attr1** i **attr2**.</span><span class="sxs-lookup"><span data-stu-id="271b6-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="271b6-121">**ColumnMapping** właściwości obie kolumny zostanie ustawiona do **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="271b6-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="271b6-122">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="271b6-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="271b6-123">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="271b6-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="271b6-124">attr1</span><span class="sxs-lookup"><span data-stu-id="271b6-124">attr1</span></span>|<span data-ttu-id="271b6-125">attr2</span><span class="sxs-lookup"><span data-stu-id="271b6-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="271b6-126">Wartość1</span><span class="sxs-lookup"><span data-stu-id="271b6-126">value1</span></span>|<span data-ttu-id="271b6-127">Wartość2</span><span class="sxs-lookup"><span data-stu-id="271b6-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="271b6-128">Elementy bez atrybuty i elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="271b6-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="271b6-129">Jeśli element nie ma elementów podrzędnych ani atrybutów, będzie można wywnioskować jako kolumna.</span><span class="sxs-lookup"><span data-stu-id="271b6-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="271b6-130">**ColumnMapping** będzie mieć ustawioną właściwość kolumny **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="271b6-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="271b6-131">Tekst dla elementy podrzędne są przechowywane w wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="271b6-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="271b6-132">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="271b6-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="271b6-133">Proces wnioskowania spowoduje utworzenie tabeli o nazwie **Element1** z dwiema kolumnami, **ChildElement1** i **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="271b6-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="271b6-134">**ColumnMapping** właściwości obie kolumny zostanie ustawiona do **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="271b6-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="271b6-135">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="271b6-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="271b6-136">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="271b6-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="271b6-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="271b6-137">ChildElement1</span></span>|<span data-ttu-id="271b6-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="271b6-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="271b6-139">Tekst1</span><span class="sxs-lookup"><span data-stu-id="271b6-139">Text1</span></span>|<span data-ttu-id="271b6-140">Tekst2</span><span class="sxs-lookup"><span data-stu-id="271b6-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="271b6-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="271b6-141">See Also</span></span>  
 [<span data-ttu-id="271b6-142">Wnioskowanie struktury zestawu danych relacyjnych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="271b6-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="271b6-143">Podczas ładowania zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="271b6-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="271b6-144">Ładowanie informacji o schemacie zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="271b6-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="271b6-145">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="271b6-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="271b6-146">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="271b6-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="271b6-147">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="271b6-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
