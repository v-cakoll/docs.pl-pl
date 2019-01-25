---
title: Wnioskowanie tekstu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d457985bfbec924748d1a418e318609b6837b9d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745171"
---
# <a name="inferring-element-text"></a><span data-ttu-id="1d538-102">Wnioskowanie tekstu elementu</span><span class="sxs-lookup"><span data-stu-id="1d538-102">Inferring Element Text</span></span>
<span data-ttu-id="1d538-103">Jeśli element zawiera tekst, a nie ma żadnych elementów podrzędnych, aby był wywnioskowany, ponieważ tabele takie jak (elementy przy użyciu atrybutów) lub powtarzalne elementy nową kolumnę o nazwie **TableName_Text** zostaną dodane do tabeli, która jest wnioskowany dla elementu.</span><span class="sxs-lookup"><span data-stu-id="1d538-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="1d538-104">Tekst zawarty w elemencie zostaną dodane do wiersza w tabeli i przechowywane w nowej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="1d538-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="1d538-105">**ColumnMapping** właściwości nowej kolumny, która będzie równa **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="1d538-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="1d538-106">Na przykład rozważmy następujący kod XML.</span><span class="sxs-lookup"><span data-stu-id="1d538-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1d538-107">Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** zawierającą dwie kolumny: **attr1** i **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="1d538-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="1d538-108">**ColumnMapping** właściwość **attr1** kolumna zostanie ustawiona **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="1d538-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="1d538-109">**ColumnMapping** właściwość **Element1_Text** kolumna zostanie ustawiona **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="1d538-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="1d538-110">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1d538-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1d538-111">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="1d538-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1d538-112">attr1</span><span class="sxs-lookup"><span data-stu-id="1d538-112">attr1</span></span>|<span data-ttu-id="1d538-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1d538-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="1d538-114">value1</span><span class="sxs-lookup"><span data-stu-id="1d538-114">value1</span></span>|<span data-ttu-id="1d538-115">TEXT1</span><span class="sxs-lookup"><span data-stu-id="1d538-115">Text1</span></span>|  
  
 <span data-ttu-id="1d538-116">Jeśli element zawiera tekst, ale ma również elementy podrzędne, które zawierają tekst, nie można dodać kolumny do tabeli do przechowywania tekstu zawarte w elemencie.</span><span class="sxs-lookup"><span data-stu-id="1d538-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="1d538-117">Tekst zawarty w elemencie będą ignorowane, gdy tekst w elementy podrzędne są objęte wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1d538-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="1d538-118">Na przykład rozważmy następujący kod XML.</span><span class="sxs-lookup"><span data-stu-id="1d538-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="1d538-119">Procesu wnioskowania będzie utworzyć tabelę o nazwie **Element1** z jedną kolumną o nazwie **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="1d538-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="1d538-120">Tekst dla **ChildElement1** element zostaną uwzględnione w wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1d538-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="1d538-121">Inne teksty zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="1d538-121">The other text will be ignored.</span></span> <span data-ttu-id="1d538-122">**ColumnMapping** właściwość **ChildElement1** kolumna zostanie ustawiona **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="1d538-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="1d538-123">**Zestaw danych:** Elementu DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1d538-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1d538-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="1d538-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1d538-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="1d538-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="1d538-126">Tekst2</span><span class="sxs-lookup"><span data-stu-id="1d538-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d538-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d538-127">See also</span></span>
- [<span data-ttu-id="1d538-128">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1d538-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="1d538-129">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1d538-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="1d538-130">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1d538-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="1d538-131">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="1d538-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="1d538-132">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="1d538-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="1d538-133">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1d538-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
