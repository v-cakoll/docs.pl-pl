---
title: Wnioskowanie tabel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6f7827b7206544ff7547cc04f44b7cda34bef8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-tables"></a><span data-ttu-id="cc241-102">Wnioskowanie tabel</span><span class="sxs-lookup"><span data-stu-id="cc241-102">Inferring Tables</span></span>
<span data-ttu-id="cc241-103">Gdy wnioskowanie schematu dla <xref:System.Data.DataSet> z dokumentu XML ADO.NET najpierw określi, elementy XML, które reprezentują tabel.</span><span class="sxs-lookup"><span data-stu-id="cc241-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="cc241-104">Następujące struktury XML powoduje tabelę dla **DataSet** schematu:</span><span class="sxs-lookup"><span data-stu-id="cc241-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="cc241-105">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="cc241-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="cc241-106">Elementów z elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="cc241-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="cc241-107">Powtarzających się elementów</span><span class="sxs-lookup"><span data-stu-id="cc241-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="cc241-108">Elementy z atrybutami</span><span class="sxs-lookup"><span data-stu-id="cc241-108">Elements with Attributes</span></span>  
 <span data-ttu-id="cc241-109">Elementów, które mają atrybuty określone w nich spowodować wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="cc241-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="cc241-110">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="cc241-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="cc241-111">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="cc241-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="cc241-112">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="cc241-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="cc241-113">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="cc241-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="cc241-114">attr1</span><span class="sxs-lookup"><span data-stu-id="cc241-114">attr1</span></span>|<span data-ttu-id="cc241-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="cc241-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="cc241-116">Wartość1</span><span class="sxs-lookup"><span data-stu-id="cc241-116">value1</span></span>||  
|<span data-ttu-id="cc241-117">Wartość2</span><span class="sxs-lookup"><span data-stu-id="cc241-117">value2</span></span>|<span data-ttu-id="cc241-118">Tekst1</span><span class="sxs-lookup"><span data-stu-id="cc241-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="cc241-119">Elementów z elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="cc241-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="cc241-120">Elementów, które mają wynik elementów podrzędnych w wywnioskować tabel.</span><span class="sxs-lookup"><span data-stu-id="cc241-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="cc241-121">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="cc241-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="cc241-122">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="cc241-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="cc241-123">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="cc241-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="cc241-124">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="cc241-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="cc241-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="cc241-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="cc241-126">Tekst1</span><span class="sxs-lookup"><span data-stu-id="cc241-126">Text1</span></span>|  
  
 <span data-ttu-id="cc241-127">Dokument lub kluczu głównym elementu wynik tabeli wykrywany, jeśli ma ona atrybuty i elementy podrzędne, które są wywnioskować jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="cc241-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="cc241-128">Jeśli element dokumentu nie atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, element jest wywnioskowany jako **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="cc241-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="cc241-129">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="cc241-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="cc241-130">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="cc241-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="cc241-131">**Zestaw danych:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="cc241-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="cc241-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="cc241-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="cc241-133">Element1</span><span class="sxs-lookup"><span data-stu-id="cc241-133">Element1</span></span>|<span data-ttu-id="cc241-134">Element2</span><span class="sxs-lookup"><span data-stu-id="cc241-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="cc241-135">Tekst1</span><span class="sxs-lookup"><span data-stu-id="cc241-135">Text1</span></span>|<span data-ttu-id="cc241-136">Tekst2</span><span class="sxs-lookup"><span data-stu-id="cc241-136">Text2</span></span>|  
  
 <span data-ttu-id="cc241-137">Możesz też wziąć pod uwagę następujące XML:</span><span class="sxs-lookup"><span data-stu-id="cc241-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="cc241-138">W procesie wnioskowania **DataSet** o nazwie "DocumentElement", który zawiera tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="cc241-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="cc241-139">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="cc241-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="cc241-140">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="cc241-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="cc241-141">attr1</span><span class="sxs-lookup"><span data-stu-id="cc241-141">attr1</span></span>|<span data-ttu-id="cc241-142">attr2</span><span class="sxs-lookup"><span data-stu-id="cc241-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="cc241-143">Wartość1</span><span class="sxs-lookup"><span data-stu-id="cc241-143">value1</span></span>|<span data-ttu-id="cc241-144">Wartość2</span><span class="sxs-lookup"><span data-stu-id="cc241-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="cc241-145">Powtarzające się elementy</span><span class="sxs-lookup"><span data-stu-id="cc241-145">Repeating Elements</span></span>  
 <span data-ttu-id="cc241-146">Elementy, które Powtórz wynik w jednej tabeli wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="cc241-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="cc241-147">Rozważmy na przykład następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="cc241-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="cc241-148">Proces wnioskowania spowoduje utworzenie tabeli o nazwie "Element1."</span><span class="sxs-lookup"><span data-stu-id="cc241-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="cc241-149">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="cc241-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="cc241-150">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="cc241-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="cc241-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="cc241-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="cc241-152">Tekst1</span><span class="sxs-lookup"><span data-stu-id="cc241-152">Text1</span></span>|  
|<span data-ttu-id="cc241-153">Tekst2</span><span class="sxs-lookup"><span data-stu-id="cc241-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc241-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc241-154">See Also</span></span>  
 [<span data-ttu-id="cc241-155">Wnioskowanie struktury zestawu danych relacyjnych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cc241-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="cc241-156">Podczas ładowania zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cc241-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="cc241-157">Ładowanie informacji o schemacie zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cc241-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="cc241-158">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="cc241-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="cc241-159">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="cc241-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="cc241-160">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="cc241-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
