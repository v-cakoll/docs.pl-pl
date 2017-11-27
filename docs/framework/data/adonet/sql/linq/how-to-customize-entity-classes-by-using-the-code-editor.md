---
title: "Porady: dostosowywanie klas jednostek za pomocą edytora kodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5586e28e784c43488245db814abf32d863232fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="517c4-102">Porady: dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="517c4-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="517c4-103">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia lub dostosowywania ich klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="517c4-103">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="517c4-104">Można również użyć [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] edytora kodu, należy napisać kod mapowania lub dostosować kod, który został już wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="517c4-104">You can also use the [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="517c4-105">Aby uzyskać więcej informacji, zobacz [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="517c4-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="517c4-106">Tematy w tej sekcji opisano sposób dostosowywania modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="517c4-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="517c4-107">Porady: Określanie nazwy bazy danych</span><span class="sxs-lookup"><span data-stu-id="517c4-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="517c4-108">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-109">Porady: reprezentuje tabele jako klasy</span><span class="sxs-lookup"><span data-stu-id="517c4-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="517c4-110">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="517c4-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="517c4-111">Porady: reprezentuje kolumn jako elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="517c4-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="517c4-112">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="517c4-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="517c4-113">Porady: reprezentuje kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="517c4-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="517c4-114">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-115">Porady: Mapowanie relacji w bazie danych</span><span class="sxs-lookup"><span data-stu-id="517c4-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="517c4-116">Przykłady użycia <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="517c4-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="517c4-117">Porady: reprezentuje kolumn jako baza danych wygenerowała</span><span class="sxs-lookup"><span data-stu-id="517c4-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="517c4-118">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-119">Porady: reprezentowały kolumny znaczników czasu lub kolumny wersji</span><span class="sxs-lookup"><span data-stu-id="517c4-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="517c4-120">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-121">Porady: Określanie typów danych bazy danych</span><span class="sxs-lookup"><span data-stu-id="517c4-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="517c4-122">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-123">Porady: reprezentuje kolumny obliczane</span><span class="sxs-lookup"><span data-stu-id="517c4-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="517c4-124">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-125">Porady: Określ pola magazynu prywatnych</span><span class="sxs-lookup"><span data-stu-id="517c4-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="517c4-126">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-127">Porady: reprezentować kolumny dopuszczającej wartości Null</span><span class="sxs-lookup"><span data-stu-id="517c4-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="517c4-128">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="517c4-129">Porady: mapowania hierarchii dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="517c4-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="517c4-130">W tym artykule opisano mapowania wymagane, aby określić hierarchię dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="517c4-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="517c4-131">Porady: Określanie Sprawdzanie konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="517c4-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="517c4-132">Informacje dotyczące używania <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="517c4-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517c4-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="517c4-133">See Also</span></span>  
 [<span data-ttu-id="517c4-134">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="517c4-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
