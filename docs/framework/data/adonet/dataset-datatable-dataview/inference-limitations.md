---
title: Ograniczenia wnioskowania
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: d113df98cdd339300b3e75ceda49a56d4f346d3c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137229"
---
# <a name="inference-limitations"></a><span data-ttu-id="2ec06-102">Ograniczenia wnioskowania</span><span class="sxs-lookup"><span data-stu-id="2ec06-102">Inference Limitations</span></span>
<span data-ttu-id="2ec06-103">Proces wnioskowanie <xref:System.Data.DataSet> schemat z pliku XML może spowodować różne schematy, w zależności od elementów XML w każdym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="2ec06-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="2ec06-104">Na przykład należy wziąć pod uwagę następujące dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="2ec06-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="2ec06-105">Dokument1:</span><span class="sxs-lookup"><span data-stu-id="2ec06-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2ec06-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="2ec06-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2ec06-107">Dla "Dokument1", generuje procesu wnioskowania **DataSet** o nazwie "elementu DocumentElement" i tabeli o nazwie "Element1", ponieważ powtarzający się element "Element1".</span><span class="sxs-lookup"><span data-stu-id="2ec06-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="2ec06-108">**Zestaw danych:** elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2ec06-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="2ec06-109">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="2ec06-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="2ec06-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="2ec06-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="2ec06-111">TEXT1</span><span class="sxs-lookup"><span data-stu-id="2ec06-111">Text1</span></span>|  
|<span data-ttu-id="2ec06-112">Tekst2</span><span class="sxs-lookup"><span data-stu-id="2ec06-112">Text2</span></span>|  
  
 <span data-ttu-id="2ec06-113">Jednak dla "Document2," procesu wnioskowania tworzy **DataSet** o nazwie "NewDataSet" i tabeli o nazwie "elementu DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="2ec06-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="2ec06-114">"Element1" jest wnioskowany jako kolumny, ponieważ zawiera ona żadnych atrybutów i nie elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="2ec06-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="2ec06-115">**Zestaw danych:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="2ec06-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="2ec06-116">**Tabela:** elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2ec06-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="2ec06-117">element1</span><span class="sxs-lookup"><span data-stu-id="2ec06-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="2ec06-118">TEXT1</span><span class="sxs-lookup"><span data-stu-id="2ec06-118">Text1</span></span>|  
  
 <span data-ttu-id="2ec06-119">Tych dwóch dokumentów XML zostały przeznaczone do tworzenia ten sam schemat, ale procesu wnioskowania daje różne wyniki oparte na elementach zawartych w poszczególnych dokumentów.</span><span class="sxs-lookup"><span data-stu-id="2ec06-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="2ec06-120">Aby uniknąć niezgodności, które mogą wystąpić podczas generowania schematu z dokumentu XML, firma Microsoft zaleca, jawnie określ schemat przy użyciu języka definicji schematu XML (XSD) lub danych XML (XDR), podczas ładowania **DataSet** z PLIK XML.</span><span class="sxs-lookup"><span data-stu-id="2ec06-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="2ec06-121">Aby uzyskać więcej informacji na temat jawne określenie **DataSet** schematu przy użyciu schematu XML, zobacz [elementu pochodnego dla zestawu danych relacyjnej struktury z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="2ec06-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec06-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ec06-122">See Also</span></span>  
 [<span data-ttu-id="2ec06-123">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="2ec06-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="2ec06-124">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="2ec06-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="2ec06-125">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="2ec06-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="2ec06-126">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="2ec06-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="2ec06-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="2ec06-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="2ec06-128">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2ec06-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
