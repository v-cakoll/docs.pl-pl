---
title: Wnioskowanie kolumn
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 2718cbcf29799f99c8648b129fdb6079a6f6d344
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786174"
---
# <a name="inferring-columns"></a><span data-ttu-id="229be-102">Wnioskowanie kolumn</span><span class="sxs-lookup"><span data-stu-id="229be-102">Inferring Columns</span></span>
<span data-ttu-id="229be-103">Po ustaleniu ADO.NET z dokumentu XML, który elementy do wnioskowania jako tabele dla <xref:System.Data.DataSet>a, następnie wnioskuje kolumny dla tych tabel.</span><span class="sxs-lookup"><span data-stu-id="229be-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="229be-104">W ADO.NET 2,0 wprowadzono nowy aparat wnioskowania schematu, który wnioskuje typ danych o jednoznacznie określonym typie dla każdego elementu **simpleType** .</span><span class="sxs-lookup"><span data-stu-id="229be-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="229be-105">W poprzednich wersjach typ danych wywnioskowanego elementu **simpleType** miał zawsze wartość **XSD: String**.</span><span class="sxs-lookup"><span data-stu-id="229be-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="229be-106">Migracja i zgodność z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="229be-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="229be-107">Metoda **ReadXml** przyjmuje argument typu **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="229be-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="229be-108">Ten argument umożliwia określenie zachowania wnioskowania zgodnego z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="229be-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="229be-109">Dostępne wartości wyliczenia **InferSchema** są przedstawione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="229be-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="229be-110">Zapewnia zgodność z poprzednimi wersjami przez zawsze wywnioskowanie <xref:System.String>typu prostego jako.</span><span class="sxs-lookup"><span data-stu-id="229be-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="229be-111">Wnioskuje typ danych o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="229be-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="229be-112">Zgłasza wyjątek, jeśli jest <xref:System.Data.DataTable>używany z.</span><span class="sxs-lookup"><span data-stu-id="229be-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="229be-113">Ignoruje wszystkie wbudowane schemat i odczytuje dane w istniejącym <xref:System.Data.DataSet> schemacie.</span><span class="sxs-lookup"><span data-stu-id="229be-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="229be-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="229be-114">Attributes</span></span>  
 <span data-ttu-id="229be-115">Zgodnie z definicją w [tabelach odwołujących](inferring-tables.md)element z atrybutami zostanie wywnioskowany jako tabela.</span><span class="sxs-lookup"><span data-stu-id="229be-115">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="229be-116">Atrybuty tego elementu zostaną następnie wywnioskowane jako kolumny dla tabeli.</span><span class="sxs-lookup"><span data-stu-id="229be-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="229be-117">Właściwość **ColumnMapping** kolumn zostanie ustawiona na wartość **MappingType. Attribute**, aby upewnić się, że nazwy kolumn będą zapisywane jako atrybuty, jeśli schemat jest zapisywana z powrotem do kodu XML.</span><span class="sxs-lookup"><span data-stu-id="229be-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="229be-118">Wartości atrybutów są przechowywane w wierszu w tabeli.</span><span class="sxs-lookup"><span data-stu-id="229be-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="229be-119">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="229be-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="229be-120">Proces wnioskowania spowoduje utworzenie tabeli o nazwie **element1** z dwiema kolumnami, **attr1** i **attr2**.</span><span class="sxs-lookup"><span data-stu-id="229be-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="229be-121">Właściwość **ColumnMapping** obu kolumn zostanie ustawiona na wartość **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="229be-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="229be-122">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="229be-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="229be-123">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="229be-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="229be-124">attr1</span><span class="sxs-lookup"><span data-stu-id="229be-124">attr1</span></span>|<span data-ttu-id="229be-125">attr2</span><span class="sxs-lookup"><span data-stu-id="229be-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="229be-126">sekwencj</span><span class="sxs-lookup"><span data-stu-id="229be-126">value1</span></span>|<span data-ttu-id="229be-127">wartość2</span><span class="sxs-lookup"><span data-stu-id="229be-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="229be-128">Elementy bez atrybutów lub elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="229be-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="229be-129">Jeśli element nie ma elementów podrzędnych ani atrybutów, zostanie wywnioskowany jako kolumna.</span><span class="sxs-lookup"><span data-stu-id="229be-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="229be-130">Właściwość **ColumnMapping** kolumny zostanie ustawiona na wartość **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="229be-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="229be-131">Tekst dla elementów podrzędnych jest przechowywany w wierszu w tabeli.</span><span class="sxs-lookup"><span data-stu-id="229be-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="229be-132">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="229be-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="229be-133">Proces wnioskowania spowoduje utworzenie tabeli o nazwie **element1** z dwiema kolumnami, **ChildElement1** i **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="229be-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="229be-134">Właściwość **ColumnMapping** obu kolumn zostanie ustawiona na wartość **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="229be-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="229be-135">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="229be-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="229be-136">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="229be-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="229be-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="229be-137">ChildElement1</span></span>|<span data-ttu-id="229be-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="229be-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="229be-139">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="229be-139">Text1</span></span>|<span data-ttu-id="229be-140">Text2</span><span class="sxs-lookup"><span data-stu-id="229be-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="229be-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="229be-141">See also</span></span>

- [<span data-ttu-id="229be-142">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="229be-142">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="229be-143">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="229be-143">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="229be-144">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="229be-144">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="229be-145">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="229be-145">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="229be-146">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="229be-146">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="229be-147">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="229be-147">ADO.NET Overview</span></span>](../ado-net-overview.md)
