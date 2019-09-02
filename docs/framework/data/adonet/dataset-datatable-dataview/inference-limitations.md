---
title: Ograniczenia wnioskowania
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 4e0f63776162b60c9333ba47be58ea78a9b6805d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204833"
---
# <a name="inference-limitations"></a><span data-ttu-id="1a23d-102">Ograniczenia wnioskowania</span><span class="sxs-lookup"><span data-stu-id="1a23d-102">Inference Limitations</span></span>
<span data-ttu-id="1a23d-103">Proces wywnioskowania <xref:System.Data.DataSet> schematu z XML może skutkować różnymi schematami w zależności od elementów XML w poszczególnych dokumentach.</span><span class="sxs-lookup"><span data-stu-id="1a23d-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="1a23d-104">Rozważmy na przykład następujące dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="1a23d-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="1a23d-105">Document1</span><span class="sxs-lookup"><span data-stu-id="1a23d-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1a23d-106">Document2</span><span class="sxs-lookup"><span data-stu-id="1a23d-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1a23d-107">W przypadku "document1" proces wnioskowania tworzy **zestaw danych** o nazwie "DocumentElement" i tabelę o nazwie "element1", ponieważ "element1" jest elementem powtarzającym się.</span><span class="sxs-lookup"><span data-stu-id="1a23d-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="1a23d-108">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1a23d-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1a23d-109">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="1a23d-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1a23d-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1a23d-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="1a23d-111">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="1a23d-111">Text1</span></span>|  
|<span data-ttu-id="1a23d-112">Text2</span><span class="sxs-lookup"><span data-stu-id="1a23d-112">Text2</span></span>|  
  
 <span data-ttu-id="1a23d-113">Jednak w przypadku "Document2" proces wnioskowania tworzy **zestaw danych** o nazwie "NewDataSet" i tabelę o nazwie "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="1a23d-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="1a23d-114">Element "element1" jest wywnioskowany jako kolumna, ponieważ nie ma atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1a23d-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="1a23d-115">**Zestawu** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="1a23d-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="1a23d-116">**Tabele** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1a23d-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="1a23d-117">Element1</span><span class="sxs-lookup"><span data-stu-id="1a23d-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="1a23d-118">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="1a23d-118">Text1</span></span>|  
  
 <span data-ttu-id="1a23d-119">Te dwa dokumenty XML mogą być przeznaczone do tworzenia tego samego schematu, ale proces wnioskowania generuje bardzo różne wyniki w zależności od elementów zawartych w każdym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="1a23d-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="1a23d-120">Aby uniknąć niezgodności, które mogą wystąpić podczas generowania schematu z dokumentu XML, zalecamy jawnie określić schemat przy użyciu języka definicji schematu XML (XSD) lub XML-Data zredukowany (XDR) podczas ładowania **zestawu danych** z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="1a23d-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="1a23d-121">Aby uzyskać więcej informacji na temat jawnego określania schematu **zestawu danych** ze schematem XML, zobacz [wyprowadzanie relacyjnej struktury zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="1a23d-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a23d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a23d-122">See also</span></span>

- [<span data-ttu-id="1a23d-123">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1a23d-123">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="1a23d-124">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1a23d-124">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="1a23d-125">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1a23d-125">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="1a23d-126">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="1a23d-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1a23d-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="1a23d-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1a23d-128">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1a23d-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
