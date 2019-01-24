---
title: Wnioskowanie tabel
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: f777b225f9fbf4e8ce38778842d30a0a3054e22a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573503"
---
# <a name="inferring-tables"></a><span data-ttu-id="661ff-102">Wnioskowanie tabel</span><span class="sxs-lookup"><span data-stu-id="661ff-102">Inferring Tables</span></span>
<span data-ttu-id="661ff-103">Podczas wnioskowania schematu dla <xref:System.Data.DataSet> z dokumentu XML ADO.NET najpierw określi, elementy XML, które reprezentują tabele.</span><span class="sxs-lookup"><span data-stu-id="661ff-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="661ff-104">Następujące struktury XML wynik w tabeli **DataSet** schematu:</span><span class="sxs-lookup"><span data-stu-id="661ff-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="661ff-105">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="661ff-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="661ff-106">Elementy z elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="661ff-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="661ff-107">Powtarzalne elementy</span><span class="sxs-lookup"><span data-stu-id="661ff-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="661ff-108">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="661ff-108">Elements with Attributes</span></span>  
 <span data-ttu-id="661ff-109">Elementy, które mają atrybuty określone w nich spowodować wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="661ff-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="661ff-110">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="661ff-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="661ff-111">Procesu wnioskowania tworzy tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="661ff-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="661ff-112">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="661ff-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="661ff-113">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="661ff-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="661ff-114">attr1</span><span class="sxs-lookup"><span data-stu-id="661ff-114">attr1</span></span>|<span data-ttu-id="661ff-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="661ff-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="661ff-116">value1</span><span class="sxs-lookup"><span data-stu-id="661ff-116">value1</span></span>||  
|<span data-ttu-id="661ff-117">value2</span><span class="sxs-lookup"><span data-stu-id="661ff-117">value2</span></span>|<span data-ttu-id="661ff-118">TEXT1</span><span class="sxs-lookup"><span data-stu-id="661ff-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="661ff-119">Elementy z elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="661ff-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="661ff-120">Elementy, które mają wynik elementy podrzędne w wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="661ff-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="661ff-121">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="661ff-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="661ff-122">Procesu wnioskowania tworzy tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="661ff-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="661ff-123">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="661ff-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="661ff-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="661ff-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="661ff-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="661ff-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="661ff-126">TEXT1</span><span class="sxs-lookup"><span data-stu-id="661ff-126">Text1</span></span>|  
  
 <span data-ttu-id="661ff-127">Dokumentu lub katalogu głównego, element wynik tabeli wykrywany, jeśli ma on atrybutów lub elementów podrzędnych, które są wnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="661ff-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="661ff-128">Jeśli element dokumentu ma żadnych atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, element jest wnioskowany jako **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="661ff-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="661ff-129">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="661ff-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="661ff-130">Procesu wnioskowania tworzy tabelę o nazwie "elementu DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="661ff-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="661ff-131">**Zestaw danych:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="661ff-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="661ff-132">**Tabela:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="661ff-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="661ff-133">element1</span><span class="sxs-lookup"><span data-stu-id="661ff-133">Element1</span></span>|<span data-ttu-id="661ff-134">element2</span><span class="sxs-lookup"><span data-stu-id="661ff-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="661ff-135">TEXT1</span><span class="sxs-lookup"><span data-stu-id="661ff-135">Text1</span></span>|<span data-ttu-id="661ff-136">Tekst2</span><span class="sxs-lookup"><span data-stu-id="661ff-136">Text2</span></span>|  
  
 <span data-ttu-id="661ff-137">Można również rozważyć następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="661ff-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="661ff-138">Tworzy procesu wnioskowania **DataSet** o nazwie elementu "DocumentElement", który zawiera tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="661ff-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="661ff-139">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="661ff-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="661ff-140">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="661ff-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="661ff-141">attr1</span><span class="sxs-lookup"><span data-stu-id="661ff-141">attr1</span></span>|<span data-ttu-id="661ff-142">attr2</span><span class="sxs-lookup"><span data-stu-id="661ff-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="661ff-143">value1</span><span class="sxs-lookup"><span data-stu-id="661ff-143">value1</span></span>|<span data-ttu-id="661ff-144">value2</span><span class="sxs-lookup"><span data-stu-id="661ff-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="661ff-145">Powtarzalne elementy</span><span class="sxs-lookup"><span data-stu-id="661ff-145">Repeating Elements</span></span>  
 <span data-ttu-id="661ff-146">Elementy, które Powtórz wynik w jednej tabeli wykrywany.</span><span class="sxs-lookup"><span data-stu-id="661ff-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="661ff-147">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="661ff-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="661ff-148">Procesu wnioskowania tworzy tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="661ff-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="661ff-149">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="661ff-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="661ff-150">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="661ff-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="661ff-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="661ff-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="661ff-152">TEXT1</span><span class="sxs-lookup"><span data-stu-id="661ff-152">Text1</span></span>|  
|<span data-ttu-id="661ff-153">Tekst2</span><span class="sxs-lookup"><span data-stu-id="661ff-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="661ff-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="661ff-154">See also</span></span>
- [<span data-ttu-id="661ff-155">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="661ff-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="661ff-156">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="661ff-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="661ff-157">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="661ff-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="661ff-158">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="661ff-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="661ff-159">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="661ff-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="661ff-160">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="661ff-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
