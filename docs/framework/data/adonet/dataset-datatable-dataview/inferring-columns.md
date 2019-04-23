---
title: Wnioskowanie kolumn
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107214"
---
# <a name="inferring-columns"></a><span data-ttu-id="4b73d-102">Wnioskowanie kolumn</span><span class="sxs-lookup"><span data-stu-id="4b73d-102">Inferring Columns</span></span>
<span data-ttu-id="4b73d-103">Po ADO.NET stwierdził z dokumentu XML które elementy, które działają jako tabele <xref:System.Data.DataSet>, następnie wnioskuje kolumn dla tych tabel.</span><span class="sxs-lookup"><span data-stu-id="4b73d-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="4b73d-104">ADO.NET w wersji 2.0 wprowadzono nowy aparat wnioskowania schematu, który wnioskuje typ silnie typizowanych danych dla każdego **simpleType** elementu.</span><span class="sxs-lookup"><span data-stu-id="4b73d-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="4b73d-105">W poprzednich wersjach, typ danych wnioskowanym **simpleType** element był to zawsze ciąg **element xsd: String**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="4b73d-106">Migracja i zgodności z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="4b73d-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="4b73d-107">**ReadXml** metoda przyjmuje argument typu **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="4b73d-108">Tego argumentu można określić zachowanie wnioskowania zgodność z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="4b73d-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="4b73d-109">Dostępne wartości dla **InferSchema** wyliczenia są wyświetlane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b73d-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="4b73d-110">Zapewnia zgodność z poprzednimi wersjami, zawsze wnioskowanie typu prostego jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4b73d-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="4b73d-111">Wnioskuje typ silnie typizowanych danych.</span><span class="sxs-lookup"><span data-stu-id="4b73d-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="4b73d-112">Zgłasza wyjątek, jeśli używana z <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4b73d-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="4b73d-113">Ignoruje wszelkie wbudowanego schematu i odczytuje dane z istniejącymi <xref:System.Data.DataSet> schematu.</span><span class="sxs-lookup"><span data-stu-id="4b73d-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="4b73d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b73d-114">Attributes</span></span>  
 <span data-ttu-id="4b73d-115">Zgodnie z definicją w [wnioskowanie tabel](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), elementu z atrybutami zostanie wywnioskowany, jako tabelę.</span><span class="sxs-lookup"><span data-stu-id="4b73d-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="4b73d-116">Atrybuty tego elementu następnie będzie można wywnioskować jako kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b73d-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="4b73d-117">**ColumnMapping** właściwość kolumn zostanie ustawiona **MappingType.Attribute**, aby upewnić się, że nazwy kolumn zostanie zapisany jako atrybuty Jeśli schemat nie są zapisywane do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="4b73d-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="4b73d-118">Wartości atrybutów są przechowywane w wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b73d-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="4b73d-119">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="4b73d-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4b73d-120">Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** z dwiema kolumnami **attr1** i **attr2**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="4b73d-121">**ColumnMapping** właściwość obie kolumny jest równa **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="4b73d-122">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4b73d-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4b73d-123">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="4b73d-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4b73d-124">attr1</span><span class="sxs-lookup"><span data-stu-id="4b73d-124">attr1</span></span>|<span data-ttu-id="4b73d-125">attr2</span><span class="sxs-lookup"><span data-stu-id="4b73d-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="4b73d-126">value1</span><span class="sxs-lookup"><span data-stu-id="4b73d-126">value1</span></span>|<span data-ttu-id="4b73d-127">value2</span><span class="sxs-lookup"><span data-stu-id="4b73d-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="4b73d-128">Elementy bez atrybutów lub elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="4b73d-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="4b73d-129">Jeśli element nie ma elementów podrzędnych lub atrybuty, będzie można wywnioskować jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="4b73d-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="4b73d-130">**ColumnMapping** właściwości kolumny jest równa **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="4b73d-131">Tekst dla elementów podrzędnych są przechowywane w wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b73d-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="4b73d-132">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="4b73d-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4b73d-133">Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** z dwiema kolumnami **ChildElement1** i **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="4b73d-134">**ColumnMapping** właściwość obie kolumny jest równa **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="4b73d-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="4b73d-135">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4b73d-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4b73d-136">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="4b73d-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4b73d-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="4b73d-137">ChildElement1</span></span>|<span data-ttu-id="4b73d-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="4b73d-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="4b73d-139">TEXT1</span><span class="sxs-lookup"><span data-stu-id="4b73d-139">Text1</span></span>|<span data-ttu-id="4b73d-140">Tekst2</span><span class="sxs-lookup"><span data-stu-id="4b73d-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b73d-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b73d-141">See also</span></span>

- [<span data-ttu-id="4b73d-142">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="4b73d-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="4b73d-143">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="4b73d-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="4b73d-144">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="4b73d-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="4b73d-145">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="4b73d-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="4b73d-146">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="4b73d-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="4b73d-147">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="4b73d-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
