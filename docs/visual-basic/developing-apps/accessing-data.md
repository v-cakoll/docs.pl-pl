---
title: Uzyskiwanie dostępu do danych w aplikacjach Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
ms.openlocfilehash: 0f17df93fc4ef22ef45f7ceff89bfb5f1ab1c18d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523956"
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="bd7d8-102">Uzyskiwanie dostępu do danych w aplikacjach Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd7d8-102">Accessing data in Visual Basic applications</span></span>

<span data-ttu-id="bd7d8-103">Visual Basic obejmuje kilka nowych funkcji ułatwiających opracowywanie aplikacji, które uzyskują dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-103">Visual Basic includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="bd7d8-104">Formularze powiązane z danymi dla aplikacji systemu Windows są tworzone przez przeciąganie elementów z [okna źródła danych](/visualstudio/data-tools/add-new-data-sources) na formularz.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="bd7d8-105">Można powiązać kontrolki z danymi przez przeciąganie elementów z **okna źródła danych** do istniejących kontrolek.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>

## <a name="related-sections"></a><span data-ttu-id="bd7d8-106">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bd7d8-106">Related sections</span></span>

[<span data-ttu-id="bd7d8-107">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd7d8-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
<span data-ttu-id="bd7d8-108">Dostarcza łącza do stron, które mówią o dołączaniu funkcji dostępu do danych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

[<span data-ttu-id="bd7d8-109">Narzędzia do obsługi danych programu Visual Studio dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bd7d8-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
<span data-ttu-id="bd7d8-110">Zawiera łącza do stron dotyczących tworzenia aplikacji, które działają z danymi przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-110">Provides links to pages on creating applications that work with data, using Visual Studio.</span></span>

[<span data-ttu-id="bd7d8-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="bd7d8-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
<span data-ttu-id="bd7d8-112">Dostarcza łącza do tematów opisujących, jak używać programu LINQ z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>

[<span data-ttu-id="bd7d8-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bd7d8-113">LINQ to SQL</span></span>](../../framework/data/adonet/sql/linq/index.md)  
<span data-ttu-id="bd7d8-114">Dostarcza informacje na temat [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd7d8-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="bd7d8-115">Zawiera przykłady programowania.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-115">Includes programming examples.</span></span>  

[<span data-ttu-id="bd7d8-116">Narzędzia LINQ to SQL Tools w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd7d8-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
<span data-ttu-id="bd7d8-117">Zawiera łącza do tematów dotyczących sposobu tworzenia modelu obiektów [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-117">Provides links to topics about how to create a [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>

[<span data-ttu-id="bd7d8-118">Praca z zestawami danych w aplikacjach n-warstwowych</span><span class="sxs-lookup"><span data-stu-id="bd7d8-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
<span data-ttu-id="bd7d8-119">Dostarcza łącza do tematów dotyczących tworzenia wielowarstwowych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-119">Provides links to topics about how to create multitiered data applications.</span></span>

[<span data-ttu-id="bd7d8-120">Dodawanie nowych połączeń</span><span class="sxs-lookup"><span data-stu-id="bd7d8-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
<span data-ttu-id="bd7d8-121">Oferuje linki do stron na potrzeby łączenia aplikacji z danymi za pomocą narzędzi czasu projektowania i obiektów połączeń ADO.NET przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using Visual Studio.</span></span>

[<span data-ttu-id="bd7d8-122">Narzędzia zestawu danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd7d8-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
<span data-ttu-id="bd7d8-123">Dostarcza łącza do stron opisujących sposób ładowania danych do zestawów danych, a także sposób wykonania instrukcji SQL i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  

[<span data-ttu-id="bd7d8-124">Wiązanie kontrolek z danymi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd7d8-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
<span data-ttu-id="bd7d8-125">Dostarcza łącza do stron, które opisują sposób wyświetlania danych na Windows Forms za pomocą powiązanych z danymi kontrolek.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>

[<span data-ttu-id="bd7d8-126">Edytuj dane w zestawach danych</span><span class="sxs-lookup"><span data-stu-id="bd7d8-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
<span data-ttu-id="bd7d8-127">Dostarcza łącza do stron opisujących sposoby manipulowania danymi w tabelach danych zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  

[<span data-ttu-id="bd7d8-128">Weryfikowanie danych w zestawach danych</span><span class="sxs-lookup"><span data-stu-id="bd7d8-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
<span data-ttu-id="bd7d8-129">Dostarcza łącza do stron opisujących sposób dodawania do zestawu danych walidacji podczas zmian wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>

[<span data-ttu-id="bd7d8-130">Zapisywanie danych z powrotem w bazie danych</span><span class="sxs-lookup"><span data-stu-id="bd7d8-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
<span data-ttu-id="bd7d8-131">Dostarcza łącza do stron wyjaśniających jak wysyłać zaktualizowane dane z aplikacji do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>

[<span data-ttu-id="bd7d8-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bd7d8-132">ADO.NET</span></span>](../../framework/data/adonet/index.md)  
<span data-ttu-id="bd7d8-133">Opisuje klasy ADO.NET, które ujawniają usługi dostępu do danych programiście .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

[<span data-ttu-id="bd7d8-134">Dane w rozwiązaniach pakietu Office</span><span class="sxs-lookup"><span data-stu-id="bd7d8-134">Data in Office Solutions</span></span>](/visualstudio/vsto/data-in-office-solutions)  
<span data-ttu-id="bd7d8-135">Zawiera linki do stron, które wyjaśniają, jak dane działają w rozwiązaniach pakietu Office, w tym informacje o programowaniu zorientowanym na schematach, buforowaniu danych i dostępie do danych po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
