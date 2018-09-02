---
title: Podsumowanie procesu wnioskowania schematu zestawu danych
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1583d5232a3dd483bbe2a6fa0b1bc8a3ae6a659f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395826"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="38a13-102">Podsumowanie procesu wnioskowania schematu zestawu danych</span><span class="sxs-lookup"><span data-stu-id="38a13-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="38a13-103">Procesu wnioskowania najpierw określi, z dokumentu XML, które elementy zostanie wywnioskowany, jako tabele.</span><span class="sxs-lookup"><span data-stu-id="38a13-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="38a13-104">Z pozostałych pliku XML procesu wnioskowania Określa kolumny dla tych tabel.</span><span class="sxs-lookup"><span data-stu-id="38a13-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="38a13-105">W przypadku zagnieżdżonych tabel generuje procesu wnioskowania zagnieżdżonych <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint> obiektów.</span><span class="sxs-lookup"><span data-stu-id="38a13-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="38a13-106">Poniżej przedstawiono krótkie podsumowanie reguły wnioskowania:</span><span class="sxs-lookup"><span data-stu-id="38a13-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="38a13-107">Elementy, które mają atrybuty są wnioskowane jako tabele.</span><span class="sxs-lookup"><span data-stu-id="38a13-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="38a13-108">Elementy, które mają elementy podrzędne są wnioskowane jako tabele.</span><span class="sxs-lookup"><span data-stu-id="38a13-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="38a13-109">Elementy, które powtarzają się wywnioskować jako pojedynczą tabelę.</span><span class="sxs-lookup"><span data-stu-id="38a13-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="38a13-110">Jeśli element dokumentu lub katalogu głównego, ma żadnych atrybutów i nie elementy podrzędne, które będzie można wywnioskować jako kolumny, jest wnioskowany jako <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="38a13-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="38a13-111">W przeciwnym razie element dokumentu jest wnioskowany w postaci tabeli.</span><span class="sxs-lookup"><span data-stu-id="38a13-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="38a13-112">Atrybuty są wnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="38a13-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="38a13-113">Elementów, które mają nie atrybutów lub elementów podrzędnych i nie powtórzyć, są wnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="38a13-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="38a13-114">Dla elementów, które są wnioskowane jako zagnieżdżoną tabelę w obrębie innych elementów, które również są wnioskowane jako tabele, zagnieżdżoną **DataRelation** utworzeniu między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="38a13-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="38a13-115">Nowy, podstawowej kolumny klucza o nazwie **TableName_Id** jest dodawane do obu tabel i używana przez **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="38a13-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="38a13-116">A **ForeignKeyConstraint** jest tworzony między dwiema tabelami, za pomocą **TableName_Id** kolumny.</span><span class="sxs-lookup"><span data-stu-id="38a13-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="38a13-117">Dla elementów, które są wnioskowane jako tabele i który zawiera tekst, ale mieć żadnych elementów podrzędnych, nową kolumnę o nazwie **TableName_Text** jest tworzona dla poszczególnych elementów tekstu.</span><span class="sxs-lookup"><span data-stu-id="38a13-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="38a13-118">Jeśli element jest wnioskowany w postaci tabeli i zawiera tekst, ale ma również elementy podrzędne, tekst zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="38a13-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a13-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38a13-119">See Also</span></span>  
 [<span data-ttu-id="38a13-120">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="38a13-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="38a13-121">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="38a13-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="38a13-122">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="38a13-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="38a13-123">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="38a13-123">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="38a13-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="38a13-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="38a13-125">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="38a13-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
