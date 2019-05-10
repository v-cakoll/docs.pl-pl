---
title: Wnioskowanie tabel
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 174d305688c7090c163df60a11e233aea24b8f79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587359"
---
# <a name="inferring-tables"></a><span data-ttu-id="ecdde-102">Wnioskowanie tabel</span><span class="sxs-lookup"><span data-stu-id="ecdde-102">Inferring Tables</span></span>
<span data-ttu-id="ecdde-103">Podczas wnioskowania schematu dla <xref:System.Data.DataSet> z dokumentu XML ADO.NET najpierw określi, elementy XML, które reprezentują tabele.</span><span class="sxs-lookup"><span data-stu-id="ecdde-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="ecdde-104">Następujące struktury XML wynik w tabeli **DataSet** schematu:</span><span class="sxs-lookup"><span data-stu-id="ecdde-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="ecdde-105">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="ecdde-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="ecdde-106">Elementy z elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="ecdde-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="ecdde-107">Powtarzalne elementy</span><span class="sxs-lookup"><span data-stu-id="ecdde-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="ecdde-108">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="ecdde-108">Elements with Attributes</span></span>  
 <span data-ttu-id="ecdde-109">Elementy, które mają atrybuty określone w nich spowodować wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="ecdde-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="ecdde-110">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ecdde-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ecdde-111">Procesu wnioskowania tworzy tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="ecdde-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="ecdde-112">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ecdde-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="ecdde-113">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="ecdde-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="ecdde-114">attr1</span><span class="sxs-lookup"><span data-stu-id="ecdde-114">attr1</span></span>|<span data-ttu-id="ecdde-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="ecdde-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="ecdde-116">value1</span><span class="sxs-lookup"><span data-stu-id="ecdde-116">value1</span></span>||  
|<span data-ttu-id="ecdde-117">value2</span><span class="sxs-lookup"><span data-stu-id="ecdde-117">value2</span></span>|<span data-ttu-id="ecdde-118">TEXT1</span><span class="sxs-lookup"><span data-stu-id="ecdde-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="ecdde-119">Elementy z elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="ecdde-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="ecdde-120">Elementy, które mają wynik elementy podrzędne w wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="ecdde-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="ecdde-121">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ecdde-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ecdde-122">Procesu wnioskowania tworzy tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="ecdde-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="ecdde-123">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ecdde-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="ecdde-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="ecdde-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="ecdde-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ecdde-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="ecdde-126">TEXT1</span><span class="sxs-lookup"><span data-stu-id="ecdde-126">Text1</span></span>|  
  
 <span data-ttu-id="ecdde-127">Dokumentu lub katalogu głównego, element wynik tabeli wykrywany, jeśli ma on atrybutów lub elementów podrzędnych, które są wnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="ecdde-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="ecdde-128">Jeśli element dokumentu ma żadnych atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, element jest wnioskowany jako **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="ecdde-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="ecdde-129">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ecdde-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ecdde-130">Procesu wnioskowania tworzy tabelę o nazwie "elementu DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="ecdde-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="ecdde-131">**Zestaw danych:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="ecdde-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="ecdde-132">**Tabela:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ecdde-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="ecdde-133">element1</span><span class="sxs-lookup"><span data-stu-id="ecdde-133">Element1</span></span>|<span data-ttu-id="ecdde-134">element2</span><span class="sxs-lookup"><span data-stu-id="ecdde-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="ecdde-135">TEXT1</span><span class="sxs-lookup"><span data-stu-id="ecdde-135">Text1</span></span>|<span data-ttu-id="ecdde-136">Tekst2</span><span class="sxs-lookup"><span data-stu-id="ecdde-136">Text2</span></span>|  
  
 <span data-ttu-id="ecdde-137">Można również rozważyć następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ecdde-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ecdde-138">Tworzy procesu wnioskowania **DataSet** o nazwie elementu "DocumentElement", który zawiera tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="ecdde-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="ecdde-139">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ecdde-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="ecdde-140">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="ecdde-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="ecdde-141">attr1</span><span class="sxs-lookup"><span data-stu-id="ecdde-141">attr1</span></span>|<span data-ttu-id="ecdde-142">attr2</span><span class="sxs-lookup"><span data-stu-id="ecdde-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="ecdde-143">value1</span><span class="sxs-lookup"><span data-stu-id="ecdde-143">value1</span></span>|<span data-ttu-id="ecdde-144">value2</span><span class="sxs-lookup"><span data-stu-id="ecdde-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="ecdde-145">Powtarzalne elementy</span><span class="sxs-lookup"><span data-stu-id="ecdde-145">Repeating Elements</span></span>  
 <span data-ttu-id="ecdde-146">Elementy, które Powtórz wynik w jednej tabeli wykrywany.</span><span class="sxs-lookup"><span data-stu-id="ecdde-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="ecdde-147">Na przykład rozważmy następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ecdde-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ecdde-148">Procesu wnioskowania tworzy tabelę o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="ecdde-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="ecdde-149">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ecdde-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="ecdde-150">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="ecdde-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="ecdde-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="ecdde-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="ecdde-152">TEXT1</span><span class="sxs-lookup"><span data-stu-id="ecdde-152">Text1</span></span>|  
|<span data-ttu-id="ecdde-153">Tekst2</span><span class="sxs-lookup"><span data-stu-id="ecdde-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecdde-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecdde-154">See also</span></span>

- [<span data-ttu-id="ecdde-155">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="ecdde-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="ecdde-156">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="ecdde-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="ecdde-157">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="ecdde-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ecdde-158">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="ecdde-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="ecdde-159">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="ecdde-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="ecdde-160">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ecdde-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
