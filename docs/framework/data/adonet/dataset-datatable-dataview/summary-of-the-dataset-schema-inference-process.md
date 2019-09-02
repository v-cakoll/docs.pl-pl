---
title: Podsumowanie procesu wnioskowania schematu elementu DataSet
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 5266d08212e5259bd5b242a70d61e29ad9008006
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203245"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="cf246-102">Podsumowanie procesu wnioskowania schematu elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="cf246-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="cf246-103">Proces wnioskowania najpierw określa, z dokumentu XML, które elementy zostaną wywnioskowane jako tabele.</span><span class="sxs-lookup"><span data-stu-id="cf246-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="cf246-104">W pozostałej postaci kodu XML proces wnioskowania określa kolumny dla tych tabel.</span><span class="sxs-lookup"><span data-stu-id="cf246-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="cf246-105">W przypadku zagnieżdżonych tabel proces wnioskowania generuje zagnieżdżone <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint> obiekty.</span><span class="sxs-lookup"><span data-stu-id="cf246-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="cf246-106">Poniżej przedstawiono krótkie podsumowanie reguł wnioskowania:</span><span class="sxs-lookup"><span data-stu-id="cf246-106">Following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="cf246-107">Elementy, które mają atrybuty są wywnioskowane jako tabele.</span><span class="sxs-lookup"><span data-stu-id="cf246-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="cf246-108">Elementy, które mają elementy podrzędne są wywnioskowane jako tabele.</span><span class="sxs-lookup"><span data-stu-id="cf246-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="cf246-109">Elementy, które powtarzają się, są wywnioskowane jako jedna tabela.</span><span class="sxs-lookup"><span data-stu-id="cf246-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="cf246-110">Jeśli dokument lub element główny nie ma żadnych atrybutów i żadne elementy podrzędne, które zostałyby wywnioskowane jako kolumny, zostanie wywnioskowane jako <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="cf246-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cf246-111">W przeciwnym razie element dokumentu jest wywnioskowany jako tabela.</span><span class="sxs-lookup"><span data-stu-id="cf246-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="cf246-112">Atrybuty są wywnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="cf246-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="cf246-113">Elementy, które nie mają atrybutów ani elementów podrzędnych, i które nie powtarzają się, są wywnioskowane jako kolumny.</span><span class="sxs-lookup"><span data-stu-id="cf246-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="cf246-114">W przypadku elementów, które są wywnioskowane jako zagnieżdżone tabele w innych elementach, które są również wywnioskowane jako tabele, zagnieżdżona relacja między dwiema tabelami zostanie utworzona.</span><span class="sxs-lookup"><span data-stu-id="cf246-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="cf246-115">Nowa kolumna klucza podstawowego o nazwie **TableName_Id** jest dodawana do obu tabel i używana przez **relację**.</span><span class="sxs-lookup"><span data-stu-id="cf246-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="cf246-116">**Element ForeignKeyConstraint** jest tworzony między dwiema tabelami przy użyciu kolumny **TableName_Id** .</span><span class="sxs-lookup"><span data-stu-id="cf246-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="cf246-117">Dla elementów, które są wywnioskowane jako tabele i które zawierają tekst, ale nie zawierają elementów podrzędnych, dla tekstu każdego elementu jest tworzona nowa kolumna o nazwie **TableName_Text** .</span><span class="sxs-lookup"><span data-stu-id="cf246-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="cf246-118">Jeśli element jest wywnioskowany jako tabela i zawiera tekst, ale również zawiera elementy podrzędne, tekst jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="cf246-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf246-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf246-119">See also</span></span>

- [<span data-ttu-id="cf246-120">Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cf246-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="cf246-121">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cf246-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="cf246-122">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="cf246-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="cf246-123">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="cf246-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="cf246-124">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="cf246-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="cf246-125">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="cf246-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
