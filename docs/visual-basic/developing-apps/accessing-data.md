---
title: "Uzyskiwanie dostępu do danych w aplikacjach Visual Basic"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da2fb9171a6b09ad94cea62877445bcb77c521ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="49e93-102">Uzyskiwanie dostępu do danych w aplikacjach Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49e93-102">Accessing data in Visual Basic applications</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="49e93-103"> zawiera kilka nowych funkcji ułatwiających projektowanie aplikacji uzyskujących dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="49e93-103"> includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="49e93-104">Powiązane z danymi formularzy dla aplikacji systemu Windows są tworzone przez przeciąganie elementów z [Data Sources — okno](/visualstudio/data-tools/add-new-data-sources) na formularzu.</span><span class="sxs-lookup"><span data-stu-id="49e93-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="49e93-105">Powiązanie formantów danych przez przeciąganie elementów z **Data Sources — okno** na istniejące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="49e93-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49e93-106">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="49e93-106">Related sections</span></span>  
 [<span data-ttu-id="49e93-107">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49e93-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
 <span data-ttu-id="49e93-108">Dostarcza łącza do stron, które mówią o dołączaniu funkcji dostępu do danych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e93-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

 [<span data-ttu-id="49e93-109">Visual Studio tools danych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="49e93-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
 <span data-ttu-id="49e93-110">Dostarcza łącza do stron dotyczących tworzenia aplikacji, które działają z danymi za pomocą [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e93-110">Provides links to pages on creating applications that work with data, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
 [<span data-ttu-id="49e93-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="49e93-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="49e93-112">Dostarcza łącza do tematów opisujących, jak używać programu LINQ z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="49e93-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>  
  
 [<span data-ttu-id="49e93-113">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="49e93-113">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 <span data-ttu-id="49e93-114">Dostarcza informacje na temat [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e93-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="49e93-115">Zawiera przykłady programowania.</span><span class="sxs-lookup"><span data-stu-id="49e93-115">Includes programming examples.</span></span>  
  
 [<span data-ttu-id="49e93-116">LINQ do SQL narzędzia w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49e93-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 <span data-ttu-id="49e93-117">Zawiera łącza do innych tematów dotyczących sposobu tworzenia [LINQ do SQL](https://msdn.microsoft.com/library/bb386976) model obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e93-117">Provides links to topics about how to create a [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) object model in applications.</span></span>  
  
 [<span data-ttu-id="49e93-118">Praca z zestawami danych w aplikacjach warstwowych</span><span class="sxs-lookup"><span data-stu-id="49e93-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
 <span data-ttu-id="49e93-119">Dostarcza łącza do tematów dotyczących tworzenia wielowarstwowych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e93-119">Provides links to topics about how to create multitiered data applications.</span></span>  
     
 [<span data-ttu-id="49e93-120">Dodaj nowe połączenia</span><span class="sxs-lookup"><span data-stu-id="49e93-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
 <span data-ttu-id="49e93-121">Dostarcza łącza do stron o łączeniu aplikacji z danymi za pomocą narzędzi czasu projektowania i obiektów połączeń ADO.NET, z wykorzystaniem [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49e93-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  

 [<span data-ttu-id="49e93-122">Narzędzia zestawu danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49e93-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
 <span data-ttu-id="49e93-123">Dostarcza łącza do stron opisujących sposób ładowania danych do zestawów danych, a także sposób wykonania instrukcji SQL i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="49e93-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  
  
 [<span data-ttu-id="49e93-124">Powiązywanie formantów z danymi w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49e93-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
 <span data-ttu-id="49e93-125">Dostarcza łącza do stron, które opisują sposób wyświetlania danych na Windows Forms za pomocą powiązanych z danymi kontrolek.</span><span class="sxs-lookup"><span data-stu-id="49e93-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>  
  
 [<span data-ttu-id="49e93-126">Edytowanie danych w zestawach danych</span><span class="sxs-lookup"><span data-stu-id="49e93-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
 <span data-ttu-id="49e93-127">Dostarcza łącza do stron opisujących sposoby manipulowania danymi w tabelach danych zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="49e93-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  
  
 [<span data-ttu-id="49e93-128">Sprawdzanie poprawności danych w zestawach danych</span><span class="sxs-lookup"><span data-stu-id="49e93-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
 <span data-ttu-id="49e93-129">Dostarcza łącza do stron opisujących sposób dodawania do zestawu danych walidacji podczas zmian wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="49e93-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>  
  
 [<span data-ttu-id="49e93-130">Zapisywanie danych w bazie danych</span><span class="sxs-lookup"><span data-stu-id="49e93-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
 <span data-ttu-id="49e93-131">Dostarcza łącza do stron wyjaśniających jak wysyłać zaktualizowane dane z aplikacji do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49e93-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>  
  
 [<span data-ttu-id="49e93-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49e93-132">ADO.NET</span></span>](https://msdn.microsoft.com/library/e80y5yhx.aspx)  
 <span data-ttu-id="49e93-133">Opisuje klasy ADO.NET, które ujawniają usługi dostępu do danych programiście .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49e93-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

 [<span data-ttu-id="49e93-134">Dane w rozwiązaniach pakietu Office</span><span class="sxs-lookup"><span data-stu-id="49e93-134">Data in Office Solutions</span></span>](https://msdn.microsoft.com/library/xx069ybh)  
 <span data-ttu-id="49e93-135">Zawiera łącza do stron, które wyjaśniają jak działają dane w rozwiązaniach pakietu Office oraz zawierają informacje dotyczące programowania schematycznego, buforowania danych i dostępu do danych po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="49e93-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
