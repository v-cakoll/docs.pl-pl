---
title: Wnioskowanie tabel
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: b14cbc39b02136ac7f226faf2636a69ac072f529
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="81836-102">Wnioskowanie tabel</span><span class="sxs-lookup"><span data-stu-id="81836-102">Inferring Tables</span></span>
<span data-ttu-id="81836-103">Gdy wnioskowanie schematu dla <xref:System.Data.DataSet> z dokumentu XML ADO.NET najpierw określi, elementy XML, które reprezentują tabel.</span><span class="sxs-lookup"><span data-stu-id="81836-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="81836-104">Następujące struktury XML powoduje tabelę dla **DataSet** schematu:</span><span class="sxs-lookup"><span data-stu-id="81836-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="81836-105">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="81836-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="81836-106">Elementów z elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="81836-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="81836-107">Powtarzających się elementów</span><span class="sxs-lookup"><span data-stu-id="81836-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="81836-108">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="81836-108">Elements with Attributes</span></span>  
 <span data-ttu-id="81836-109">Elementów, które mają atrybuty określone w nich spowodować wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="81836-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="81836-110">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="81836-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="81836-111">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="81836-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="81836-112">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="81836-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="81836-113">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="81836-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="81836-114">attr1</span><span class="sxs-lookup"><span data-stu-id="81836-114">attr1</span></span>|<span data-ttu-id="81836-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="81836-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="81836-116">Wartość1</span><span class="sxs-lookup"><span data-stu-id="81836-116">value1</span></span>||  
|<span data-ttu-id="81836-117">Wartość2</span><span class="sxs-lookup"><span data-stu-id="81836-117">value2</span></span>|<span data-ttu-id="81836-118">Tekst1</span><span class="sxs-lookup"><span data-stu-id="81836-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="81836-119">Elementów z elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="81836-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="81836-120">Elementów, które mają wynik elementów podrzędnych w wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="81836-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="81836-121">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="81836-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="81836-122">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="81836-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="81836-123">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="81836-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="81836-124">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="81836-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="81836-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="81836-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="81836-126">Tekst1</span><span class="sxs-lookup"><span data-stu-id="81836-126">Text1</span></span>|  
  
 <span data-ttu-id="81836-127">Dokument lub kluczu głównym elementu wynik tabeli wykrywany, jeśli ma ona atrybuty i elementy podrzędne, które są wywnioskować jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="81836-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="81836-128">Jeśli element dokumentu nie atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, element jest wywnioskowany jako **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="81836-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="81836-129">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="81836-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="81836-130">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="81836-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="81836-131">**Zestaw danych:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="81836-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="81836-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="81836-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="81836-133">Element1</span><span class="sxs-lookup"><span data-stu-id="81836-133">Element1</span></span>|<span data-ttu-id="81836-134">Element2</span><span class="sxs-lookup"><span data-stu-id="81836-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="81836-135">Tekst1</span><span class="sxs-lookup"><span data-stu-id="81836-135">Text1</span></span>|<span data-ttu-id="81836-136">Tekst2</span><span class="sxs-lookup"><span data-stu-id="81836-136">Text2</span></span>|  
  
 <span data-ttu-id="81836-137">Możesz też wziąć pod uwagę następujące XML:</span><span class="sxs-lookup"><span data-stu-id="81836-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="81836-138">W procesie wnioskowania **DataSet** o nazwie "DocumentElement", który zawiera tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="81836-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="81836-139">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="81836-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="81836-140">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="81836-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="81836-141">attr1</span><span class="sxs-lookup"><span data-stu-id="81836-141">attr1</span></span>|<span data-ttu-id="81836-142">attr2</span><span class="sxs-lookup"><span data-stu-id="81836-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="81836-143">Wartość1</span><span class="sxs-lookup"><span data-stu-id="81836-143">value1</span></span>|<span data-ttu-id="81836-144">Wartość2</span><span class="sxs-lookup"><span data-stu-id="81836-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="81836-145">Powtarzające się elementy</span><span class="sxs-lookup"><span data-stu-id="81836-145">Repeating Elements</span></span>  
 <span data-ttu-id="81836-146">Elementy, które Powtórz wynik w jednej tabeli wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="81836-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="81836-147">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="81836-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="81836-148">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="81836-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="81836-149">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="81836-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="81836-150">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="81836-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="81836-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="81836-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="81836-152">Tekst1</span><span class="sxs-lookup"><span data-stu-id="81836-152">Text1</span></span>|  
|<span data-ttu-id="81836-153">Tekst2</span><span class="sxs-lookup"><span data-stu-id="81836-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81836-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81836-154">See Also</span></span>  
 [<span data-ttu-id="81836-155">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="81836-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="81836-156">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="81836-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="81836-157">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="81836-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="81836-158">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="81836-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="81836-159">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="81836-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="81836-160">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="81836-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
