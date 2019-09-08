---
title: Wnioskowanie tabel
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 52ffd3fe90eb491dd01acf8538276cc828fdb309
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784491"
---
# <a name="inferring-tables"></a><span data-ttu-id="8add9-102">Wnioskowanie tabel</span><span class="sxs-lookup"><span data-stu-id="8add9-102">Inferring Tables</span></span>
<span data-ttu-id="8add9-103">Gdy wywnioskowano schemat dla programu <xref:System.Data.DataSet> z dokumentu XML, ADO.net najpierw określa, które elementy XML reprezentują tabele.</span><span class="sxs-lookup"><span data-stu-id="8add9-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="8add9-104">Poniższe struktury XML powodują powstanie tabeli dla schematu **zestawu danych** :</span><span class="sxs-lookup"><span data-stu-id="8add9-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="8add9-105">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="8add9-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="8add9-106">Elementy z elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="8add9-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="8add9-107">Powtarzające się elementy</span><span class="sxs-lookup"><span data-stu-id="8add9-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="8add9-108">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="8add9-108">Elements with Attributes</span></span>  
 <span data-ttu-id="8add9-109">Elementy, które mają określone atrybuty, powodują wywnioskowane tabele.</span><span class="sxs-lookup"><span data-stu-id="8add9-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="8add9-110">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="8add9-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8add9-111">Proces wnioskowania tworzy tabelę o nazwie "element1".</span><span class="sxs-lookup"><span data-stu-id="8add9-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="8add9-112">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8add9-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8add9-113">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="8add9-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8add9-114">attr1</span><span class="sxs-lookup"><span data-stu-id="8add9-114">attr1</span></span>|<span data-ttu-id="8add9-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="8add9-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="8add9-116">sekwencj</span><span class="sxs-lookup"><span data-stu-id="8add9-116">value1</span></span>||  
|<span data-ttu-id="8add9-117">wartość2</span><span class="sxs-lookup"><span data-stu-id="8add9-117">value2</span></span>|<span data-ttu-id="8add9-118">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="8add9-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="8add9-119">Elementy z elementami podrzędnymi</span><span class="sxs-lookup"><span data-stu-id="8add9-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="8add9-120">Elementy, które mają elementy podrzędne, powodują wywnioskowane tabele.</span><span class="sxs-lookup"><span data-stu-id="8add9-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="8add9-121">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="8add9-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8add9-122">Proces wnioskowania tworzy tabelę o nazwie "element1".</span><span class="sxs-lookup"><span data-stu-id="8add9-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="8add9-123">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8add9-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8add9-124">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="8add9-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8add9-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8add9-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="8add9-126">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="8add9-126">Text1</span></span>|  
  
 <span data-ttu-id="8add9-127">Dokument lub element główny, wynik w tabeli wywnioskowanej, jeśli ma atrybuty lub elementy podrzędne, które są wywnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="8add9-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="8add9-128">Jeśli element dokumentu nie ma żadnych atrybutów i żadne elementy podrzędne, które zostałyby wywnioskowane jako kolumny, element jest wywnioskowany jako **zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="8add9-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="8add9-129">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="8add9-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8add9-130">Proces wnioskowania tworzy tabelę o nazwie "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="8add9-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="8add9-131">**Zestawu** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="8add9-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="8add9-132">**Tabele** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8add9-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="8add9-133">Element1</span><span class="sxs-lookup"><span data-stu-id="8add9-133">Element1</span></span>|<span data-ttu-id="8add9-134">Element2</span><span class="sxs-lookup"><span data-stu-id="8add9-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="8add9-135">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="8add9-135">Text1</span></span>|<span data-ttu-id="8add9-136">Text2</span><span class="sxs-lookup"><span data-stu-id="8add9-136">Text2</span></span>|  
  
 <span data-ttu-id="8add9-137">Alternatywnie należy wziąć pod uwagę następujące elementy XML:</span><span class="sxs-lookup"><span data-stu-id="8add9-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8add9-138">Proces wnioskowania generuje **zestaw danych** o nazwie "DocumentElement", który zawiera tabelę o nazwie "element1".</span><span class="sxs-lookup"><span data-stu-id="8add9-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="8add9-139">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8add9-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8add9-140">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="8add9-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8add9-141">attr1</span><span class="sxs-lookup"><span data-stu-id="8add9-141">attr1</span></span>|<span data-ttu-id="8add9-142">attr2</span><span class="sxs-lookup"><span data-stu-id="8add9-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="8add9-143">sekwencj</span><span class="sxs-lookup"><span data-stu-id="8add9-143">value1</span></span>|<span data-ttu-id="8add9-144">wartość2</span><span class="sxs-lookup"><span data-stu-id="8add9-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="8add9-145">Powtarzające się elementy</span><span class="sxs-lookup"><span data-stu-id="8add9-145">Repeating Elements</span></span>  
 <span data-ttu-id="8add9-146">Elementy powtarzające się powodują powstanie pojedynczej tabeli wywnioskowanej.</span><span class="sxs-lookup"><span data-stu-id="8add9-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="8add9-147">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="8add9-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8add9-148">Proces wnioskowania tworzy tabelę o nazwie "element1".</span><span class="sxs-lookup"><span data-stu-id="8add9-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="8add9-149">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8add9-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8add9-150">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="8add9-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8add9-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="8add9-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="8add9-152">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="8add9-152">Text1</span></span>|  
|<span data-ttu-id="8add9-153">Text2</span><span class="sxs-lookup"><span data-stu-id="8add9-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8add9-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8add9-154">See also</span></span>

- [<span data-ttu-id="8add9-155">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="8add9-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="8add9-156">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="8add9-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="8add9-157">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="8add9-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="8add9-158">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="8add9-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="8add9-159">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="8add9-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8add9-160">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8add9-160">ADO.NET Overview</span></span>](../ado-net-overview.md)
