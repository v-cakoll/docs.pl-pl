---
title: Wnioskowanie tekstu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d8d64c0cbb0aecf736a54fa6816e286ab7efa191
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203528"
---
# <a name="inferring-element-text"></a><span data-ttu-id="6b6ae-102">Wnioskowanie tekstu elementu</span><span class="sxs-lookup"><span data-stu-id="6b6ae-102">Inferring Element Text</span></span>
<span data-ttu-id="6b6ae-103">Jeśli element zawiera tekst i nie ma żadnych elementów podrzędnych, które mają być wywnioskowane jako tabele (takie jak elementy z atrybutami lub powtarzalne elementy), Nowa kolumna o nazwie **TableName_Text** zostanie dodana do tabeli, która jest wywnioskowana dla elementu.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="6b6ae-104">Tekst zawarty w elemencie zostanie dodany do wiersza w tabeli i zapisany w nowej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="6b6ae-105">Właściwość **ColumnMapping** nowej kolumny zostanie ustawiona na wartość **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="6b6ae-106">Rozważmy na przykład następujący kod XML.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="6b6ae-107">Proces wnioskowania spowoduje utworzenie tabeli o nazwie **element1** z dwiema kolumnami: **attr1** i **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="6b6ae-108">Właściwość **ColumnMapping** kolumny **attr1** zostanie ustawiona na wartość **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="6b6ae-109">Właściwość **ColumnMapping** kolumny **Element1_Text** zostanie ustawiona na wartość **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="6b6ae-110">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6b6ae-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="6b6ae-111">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="6b6ae-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="6b6ae-112">attr1</span><span class="sxs-lookup"><span data-stu-id="6b6ae-112">attr1</span></span>|<span data-ttu-id="6b6ae-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="6b6ae-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="6b6ae-114">sekwencj</span><span class="sxs-lookup"><span data-stu-id="6b6ae-114">value1</span></span>|<span data-ttu-id="6b6ae-115">Organizacji1</span><span class="sxs-lookup"><span data-stu-id="6b6ae-115">Text1</span></span>|  
  
 <span data-ttu-id="6b6ae-116">Jeśli element zawiera tekst, ale również zawiera elementy podrzędne, które zawierają tekst, kolumna nie zostanie dodana do tabeli w celu przechowania tekstu zawartego w elemencie.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="6b6ae-117">Tekst zawarty w elemencie zostanie zignorowany, podczas gdy tekst w elementach podrzędnych zostanie uwzględniony w wierszu w tabeli.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="6b6ae-118">Rozważmy na przykład następujący kod XML.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="6b6ae-119">Proces wnioskowania spowoduje utworzenie tabeli o nazwie **element1** z jedną kolumną o nazwie **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="6b6ae-120">Tekst elementu **ChildElement1** zostanie uwzględniony w wierszu w tabeli.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="6b6ae-121">Drugi tekst zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-121">The other text will be ignored.</span></span> <span data-ttu-id="6b6ae-122">Właściwość **ColumnMapping** kolumny **ChildElement1** zostanie ustawiona na wartość **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="6b6ae-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="6b6ae-123">**Zestawu** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6b6ae-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="6b6ae-124">**Tabele** Element1</span><span class="sxs-lookup"><span data-stu-id="6b6ae-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="6b6ae-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="6b6ae-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="6b6ae-126">Text2</span><span class="sxs-lookup"><span data-stu-id="6b6ae-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b6ae-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b6ae-127">See also</span></span>

- [<span data-ttu-id="6b6ae-128">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="6b6ae-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="6b6ae-129">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="6b6ae-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="6b6ae-130">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="6b6ae-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="6b6ae-131">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="6b6ae-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="6b6ae-132">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="6b6ae-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="6b6ae-133">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6b6ae-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
