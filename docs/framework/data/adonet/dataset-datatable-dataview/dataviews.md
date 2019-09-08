---
title: Elementy DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 8a06accb11631f2dce6b0d39587d7274223c0e68
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786347"
---
# <a name="dataviews"></a><span data-ttu-id="c7f48-102">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="c7f48-102">DataViews</span></span>
<span data-ttu-id="c7f48-103">A <xref:System.Data.DataView> umożliwia tworzenie różnych widoków danych przechowywanych <xref:System.Data.DataTable>w programie, które są często używane w aplikacjach do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="c7f48-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="c7f48-104">Za pomocą elementu **DataView**można uwidocznić dane w tabeli z różnymi kolejności sortowania i można filtrować dane według stanu wiersza lub w oparciu o wyrażenie filtru.</span><span class="sxs-lookup"><span data-stu-id="c7f48-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="c7f48-105">**Element DataView** udostępnia dynamiczny widok danych w źródłowej **tabeli DataTable**: zawartość, kolejność i członkostwo odzwierciedlają zmiany w miarę ich występowania.</span><span class="sxs-lookup"><span data-stu-id="c7f48-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="c7f48-106">To zachowanie różni się od metody **SELECT** **elementu DataTable**, <xref:System.Data.DataRow> która zwraca tablicę z tabeli na podstawie określonego filtru i/lub porządku sortowania: Ta zawartość odzwierciedla zmiany w tabeli podstawowej, ale jego członkostwo i Porządkowanie pozostaje statyczne.</span><span class="sxs-lookup"><span data-stu-id="c7f48-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: this content reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="c7f48-107">Dynamiczne możliwości obiektu **DataView** sprawiają, że są idealnym rozwiązaniem dla aplikacji do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="c7f48-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="c7f48-108">**Element DataView** udostępnia dynamiczny widok pojedynczego zestawu danych, podobnie jak widok bazy danych, do którego można zastosować różne kryteria sortowania i filtrowania.</span><span class="sxs-lookup"><span data-stu-id="c7f48-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="c7f48-109">W przeciwieństwie do widoku bazy danych, jednak **element DataView** nie może być traktowany jako tabela i nie może zawierać widoku sprzężonych tabel.</span><span class="sxs-lookup"><span data-stu-id="c7f48-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="c7f48-110">Nie można również wykluczyć kolumn istniejących w tabeli źródłowej ani dodawać kolumn, takich jak kolumny obliczeniowe, które nie istnieją w tabeli źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c7f48-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="c7f48-111">Aby zarządzać ustawieniami widoku <xref:System.Data.DataView.DataViewManager%2A> dla wszystkich tabel w **zestawie danych**, można użyć elementu.</span><span class="sxs-lookup"><span data-stu-id="c7f48-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="c7f48-112">Element **DataViewManager** zapewnia wygodny sposób zarządzania domyślnymi ustawieniami widoku dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c7f48-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="c7f48-113">W przypadku wiązania kontrolki z więcej niż jedną tabelą **zestawu danych**powiązanie z elementem **DataViewManager** jest idealnym wyborem.</span><span class="sxs-lookup"><span data-stu-id="c7f48-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7f48-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c7f48-114">In This Section</span></span>  
 [<span data-ttu-id="c7f48-115">Tworzenie elementu DataView</span><span class="sxs-lookup"><span data-stu-id="c7f48-115">Creating a DataView</span></span>](creating-a-dataview.md)  
 <span data-ttu-id="c7f48-116">Opisuje sposób tworzenia elementu **DataView** dla **elementu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c7f48-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="c7f48-117">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="c7f48-117">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)  
 <span data-ttu-id="c7f48-118">Opisuje sposób ustawiania właściwości elementu **DataView** do zwracania podzbiorów wierszy danych spełniających kryteria filtrowania lub do zwracania danych w określonej kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="c7f48-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="c7f48-119">Elementy DataRow i DataRowView</span><span class="sxs-lookup"><span data-stu-id="c7f48-119">DataRows and DataRowViews</span></span>](datarows-and-datarowviews.md)  
 <span data-ttu-id="c7f48-120">Opisuje sposób uzyskiwania dostępu do danych uwidocznionych przez **Widok DataView**.</span><span class="sxs-lookup"><span data-stu-id="c7f48-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="c7f48-121">Znajdowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="c7f48-121">Finding Rows</span></span>](finding-rows.md)  
 <span data-ttu-id="c7f48-122">Opisuje, jak znaleźć konkretny wiersz w **widoku**danych.</span><span class="sxs-lookup"><span data-stu-id="c7f48-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="c7f48-123">Elementy ChildView i relacje</span><span class="sxs-lookup"><span data-stu-id="c7f48-123">ChildViews and Relations</span></span>](childviews-and-relations.md)  
 <span data-ttu-id="c7f48-124">Opisuje sposób tworzenia widoków danych z relacji nadrzędny-podrzędny przy użyciu elementu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c7f48-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="c7f48-125">Modyfikowanie elementów DataView</span><span class="sxs-lookup"><span data-stu-id="c7f48-125">Modifying DataViews</span></span>](modifying-dataviews.md)  
 <span data-ttu-id="c7f48-126">Opisuje, jak modyfikować dane w źródłowej **DataTable** za pośrednictwem **widoku**danych, w tym Włączanie lub wyłączanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="c7f48-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="c7f48-127">Obsługa zdarzeń elementu DataView</span><span class="sxs-lookup"><span data-stu-id="c7f48-127">Handling DataView Events</span></span>](handling-dataview-events.md)  
 <span data-ttu-id="c7f48-128">Opisuje sposób korzystania z zdarzenia **ListChanged** w celu otrzymywania powiadomień w przypadku aktualizowania zawartości lub kolejności elementu **DataView** .</span><span class="sxs-lookup"><span data-stu-id="c7f48-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="c7f48-129">Zarządzanie elementami DataView</span><span class="sxs-lookup"><span data-stu-id="c7f48-129">Managing DataViews</span></span>](managing-dataviews.md)  
 <span data-ttu-id="c7f48-130">Opisuje, w jaki sposób używać elementu **DataViewManager** do zarządzania ustawieniami **DataView** dla każdej tabeli w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="c7f48-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7f48-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c7f48-131">Related Sections</span></span>  
 <span data-ttu-id="c7f48-132">[Aplikacje internetowe ASP.NET](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7f48-132">[ASP.NET Web Applications](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))</span></span>  
 <span data-ttu-id="c7f48-133">Oferuje przeglądy i szczegółowe procedury krok po kroku dotyczące tworzenia aplikacji ASP.NET, formularzy sieci Web i usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c7f48-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 <span data-ttu-id="c7f48-134">[Aplikacje systemu Windows](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7f48-134">[Windows Applications](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))</span></span>  
 <span data-ttu-id="c7f48-135">Zawiera szczegółowe informacje dotyczące pracy z aplikacjami Windows Forms i konsolą programu.</span><span class="sxs-lookup"><span data-stu-id="c7f48-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="c7f48-136">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="c7f48-136">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="c7f48-137">Opisuje obiekt **DataSet** i jak można go użyć do zarządzania danymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7f48-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="c7f48-138">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="c7f48-138">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="c7f48-139">Opisuje obiekt **DataTable** i sposób, w jaki można go użyć do zarządzania danymi aplikacji przez siebie lub jako część **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="c7f48-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="c7f48-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c7f48-140">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="c7f48-141">Opisuje architekturę i składniki ADO.NET oraz sposób używania ADO.NET do uzyskiwania dostępu do istniejących źródeł danych i zarządzania danymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7f48-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f48-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7f48-142">See also</span></span>

- [<span data-ttu-id="c7f48-143">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c7f48-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
