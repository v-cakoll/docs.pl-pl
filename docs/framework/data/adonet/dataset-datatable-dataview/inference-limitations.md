---
title: Ograniczenia wnioskowania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98ea3d5fa4427b391ef06b3fc6ace9a05dfb819a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inference-limitations"></a><span data-ttu-id="36df5-102">Ograniczenia wnioskowania</span><span class="sxs-lookup"><span data-stu-id="36df5-102">Inference Limitations</span></span>
<span data-ttu-id="36df5-103">Proces wnioskowanie <xref:System.Data.DataSet> schematu z pliku XML może spowodować schematy różne w zależności od elementów XML do każdego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="36df5-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="36df5-104">Rozważmy na przykład w następujących dokumentach XML.</span><span class="sxs-lookup"><span data-stu-id="36df5-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="36df5-105">Dokument1:</span><span class="sxs-lookup"><span data-stu-id="36df5-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="36df5-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="36df5-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="36df5-107">Dla "Dokument1," tworzy proces wnioskowania **DataSet** o nazwie "DocumentElement" i tabeli o nazwie "Element1", ponieważ powtarzający się element "Element1".</span><span class="sxs-lookup"><span data-stu-id="36df5-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="36df5-108">**Zestaw danych:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="36df5-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="36df5-109">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="36df5-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="36df5-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="36df5-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="36df5-111">Tekst1</span><span class="sxs-lookup"><span data-stu-id="36df5-111">Text1</span></span>|  
|<span data-ttu-id="36df5-112">Tekst2</span><span class="sxs-lookup"><span data-stu-id="36df5-112">Text2</span></span>|  
  
 <span data-ttu-id="36df5-113">Jednak dla "Document2," proces wnioskowania tworzy **DataSet** o nazwie "NewDataSet" i tabeli o nazwie "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="36df5-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="36df5-114">"Element1" jest wywnioskowany jako kolumny, ponieważ ma ona żadnych atrybutów i elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="36df5-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="36df5-115">**Zestaw danych:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="36df5-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="36df5-116">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="36df5-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="36df5-117">Element1</span><span class="sxs-lookup"><span data-stu-id="36df5-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="36df5-118">Tekst1</span><span class="sxs-lookup"><span data-stu-id="36df5-118">Text1</span></span>|  
  
 <span data-ttu-id="36df5-119">Te dwa dokumenty XML mogą przeznaczone do tworzenia tego samego schematu, ale proces wnioskowania daje różne wyniki, oparte na elementy zawarte w każdej dokumentu.</span><span class="sxs-lookup"><span data-stu-id="36df5-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="36df5-120">Aby uniknąć niezgodności, które mogą wystąpić podczas generowania schematu z dokumentu XML, firma Microsoft zaleca, jawnie określ schemat przy użyciu języka definicji schematu XML (XSD) lub danych XML (XDR) podczas ładowania **DataSet** z KOD XML.</span><span class="sxs-lookup"><span data-stu-id="36df5-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="36df5-121">Aby uzyskać więcej informacji na temat jawne określenie **DataSet** schematu ze schematem XML, zobacz [wyprowadzanie struktury relacyjne zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="36df5-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36df5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36df5-122">See Also</span></span>  
 [<span data-ttu-id="36df5-123">Wnioskowanie struktury zestawu danych relacyjnych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="36df5-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="36df5-124">Podczas ładowania zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="36df5-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="36df5-125">Ładowanie informacji o schemacie zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="36df5-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="36df5-126">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="36df5-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="36df5-127">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="36df5-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="36df5-128">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="36df5-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
