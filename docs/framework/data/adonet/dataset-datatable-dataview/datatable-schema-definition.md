---
title: Definicja schematu tabeli DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ae4d5af0238108d0f309ae311e172450bf226c23
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="59788-102">Definicja schematu tabeli DataTable</span><span class="sxs-lookup"><span data-stu-id="59788-102">DataTable Schema Definition</span></span>
<span data-ttu-id="59788-103">Schemat lub struktura tabeli jest reprezentowana przez kolumn i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="59788-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="59788-104">Zdefiniuj schemat <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataColumn> obiektów oraz <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint> obiektów.</span><span class="sxs-lookup"><span data-stu-id="59788-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="59788-105">Kolumn w tabeli można mapować do kolumn w źródle danych, zawierać obliczone wartości w wyrażeniach, automatycznie zwiększyć ich wartości lub wartości klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="59788-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="59788-106">Odwołania według nazwy kolumny, relacji i ograniczeń w tabeli jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="59788-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="59788-107">W tabeli, które mają taką samą nazwę, ale które różnią się wielkością liter w związku z tym może istnieć co najmniej dwie kolumny, relacji lub ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="59788-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="59788-108">Na przykład można mieć **Col1** i **col1**.</span><span class="sxs-lookup"><span data-stu-id="59788-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="59788-109">W przypadku, np. odwołanie do jednej z kolumn o nazwie muszą być zgodne wielkość liter nazwy kolumny; w przeciwnym razie jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59788-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="59788-110">Na przykład jeśli tabela **myTable** zawiera kolumny **Col1** i **col1**, czy odwołanie **Col1** według nazwy jako  **myTable.Columns["Col1"]**, i **col1** jako **myTable.Columns["col1"]**.</span><span class="sxs-lookup"><span data-stu-id="59788-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="59788-111">Próby odwołania z kolumn jako **myTable.Columns["COL1"]** wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59788-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="59788-112">Reguła uwzględnianie wielkości liter nie ma zastosowania, jeśli tylko jednej kolumny, relacji lub ograniczenia o określonej nazwie istnieje.</span><span class="sxs-lookup"><span data-stu-id="59788-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="59788-113">Oznacza to jeśli nie kolumny, relacji lub obiekt ograniczenie w tabeli jest zgodna z nazwą tej określonej kolumny, relacji lub ograniczenia obiektu, może odwoływać do obiektu o nazwie wszystkie wielkie i małe litery, a nie wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59788-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="59788-114">Na przykład, jeśli tabela zawiera tylko **Col1**, można odwoływać się za pomocą **Moje. Kolumny ["COL1"]**.</span><span class="sxs-lookup"><span data-stu-id="59788-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59788-115"><xref:System.Data.DataTable.CaseSensitive%2A> Właściwość **DataTable** nie ma wpływu na tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="59788-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="59788-116">**CaseSensitive** właściwość jest stosowana do danych w tabeli i wpływa na sortowanie, wyszukiwanie, filtrowanie, wymuszanie ograniczenia i tak dalej, ale nie do odwołania do kolumny, relacji i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="59788-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59788-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="59788-117">In This Section</span></span>  
 [<span data-ttu-id="59788-118">Dodawanie kolumn do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="59788-118">Adding Columns to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 <span data-ttu-id="59788-119">Opisuje sposób definiowania kolumn tabeli, używając **DataColumn** obiektów.</span><span class="sxs-lookup"><span data-stu-id="59788-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="59788-120">Tworzenie kolumn wyrażeń</span><span class="sxs-lookup"><span data-stu-id="59788-120">Creating Expression Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 <span data-ttu-id="59788-121">Wyjaśniono, jak **wyrażenie** właściwość kolumny może być używane do obliczania wartości na podstawie wartości z innych kolumn w wierszu.</span><span class="sxs-lookup"><span data-stu-id="59788-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="59788-122">Tworzenie kolumn typu AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="59788-122">Creating AutoIncrement Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 <span data-ttu-id="59788-123">W tym artykule opisano, jak kolumny można ustawić na automatyczne zwiększenie wartości liczbowe, aby upewnić się, wartość unikatową kolumnę w wierszu.</span><span class="sxs-lookup"><span data-stu-id="59788-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="59788-124">Definiowanie kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="59788-124">Defining Primary Keys</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 <span data-ttu-id="59788-125">Opisuje sposób określenia klucza podstawowego tabeli z jednej lub wielu **DataColumn** obiektów.</span><span class="sxs-lookup"><span data-stu-id="59788-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="59788-126">Ograniczenia elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="59788-126">DataTable Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 <span data-ttu-id="59788-127">Opisuje sposób zdefiniowania foreign key i ograniczenia unikalne dla kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="59788-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59788-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59788-128">See Also</span></span>  
 [<span data-ttu-id="59788-129">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="59788-129">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="59788-130">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="59788-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
