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
ms.openlocfilehash: fd4dbc66f37325afa64b7bf9720cad23e08c6bfb
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="e6e66-102">Uzyskiwanie dostępu do danych w aplikacjach Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6e66-102">Accessing data in Visual Basic applications</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e6e66-103"> zawiera kilka nowych funkcji ułatwiających projektowanie aplikacji uzyskujących dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="e6e66-103"> includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="e6e66-104">Powiązane z danymi formularzy dla aplikacji systemu Windows są tworzone przez przeciąganie elementów z [Data Sources — okno](/visualstudio/data-tools/add-new-data-sources) na formularzu.</span><span class="sxs-lookup"><span data-stu-id="e6e66-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="e6e66-105">Powiązanie formantów danych przez przeciąganie elementów z **Data Sources — okno** na istniejące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e6e66-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e6e66-106">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e6e66-106">Related sections</span></span>  
 [<span data-ttu-id="e6e66-107">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6e66-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
 <span data-ttu-id="e6e66-108">Dostarcza łącza do stron, które mówią o dołączaniu funkcji dostępu do danych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6e66-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

 [<span data-ttu-id="e6e66-109">Narzędzia do obsługi danych programu Visual Studio dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e6e66-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
 <span data-ttu-id="e6e66-110">Dostarcza łącza do stron dotyczących tworzenia aplikacji, które działają z danymi za pomocą [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6e66-110">Provides links to pages on creating applications that work with data, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
 [<span data-ttu-id="e6e66-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="e6e66-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="e6e66-112">Dostarcza łącza do tematów opisujących, jak używać programu LINQ z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e6e66-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>  
  
 [<span data-ttu-id="e6e66-113">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="e6e66-113">LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="e6e66-114">Dostarcza informacje na temat [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6e66-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e6e66-115">Zawiera przykłady programowania.</span><span class="sxs-lookup"><span data-stu-id="e6e66-115">Includes programming examples.</span></span>  
  
 [<span data-ttu-id="e6e66-116">LINQ do SQL narzędzia w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6e66-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 <span data-ttu-id="e6e66-117">Zawiera łącza do innych tematów dotyczących sposobu tworzenia [LINQ do SQL](../../../docs/framework/data/adonet/sql/linq/index.md) model obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6e66-117">Provides links to topics about how to create a [LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>  
  
 [<span data-ttu-id="e6e66-118">Praca z zestawami danych w aplikacjach n-warstwowych</span><span class="sxs-lookup"><span data-stu-id="e6e66-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
 <span data-ttu-id="e6e66-119">Dostarcza łącza do tematów dotyczących tworzenia wielowarstwowych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6e66-119">Provides links to topics about how to create multitiered data applications.</span></span>  
     
 [<span data-ttu-id="e6e66-120">Dodaj nowe połączenia</span><span class="sxs-lookup"><span data-stu-id="e6e66-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
 <span data-ttu-id="e6e66-121">Dostarcza łącza do stron o łączeniu aplikacji z danymi za pomocą narzędzi czasu projektowania i obiektów połączeń ADO.NET, z wykorzystaniem [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6e66-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  

 [<span data-ttu-id="e6e66-122">Narzędzia zestawu danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6e66-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
 <span data-ttu-id="e6e66-123">Dostarcza łącza do stron opisujących sposób ładowania danych do zestawów danych, a także sposób wykonania instrukcji SQL i procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="e6e66-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  
  
 [<span data-ttu-id="e6e66-124">Powiązywanie formantów z danymi w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6e66-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
 <span data-ttu-id="e6e66-125">Dostarcza łącza do stron, które opisują sposób wyświetlania danych na Windows Forms za pomocą powiązanych z danymi kontrolek.</span><span class="sxs-lookup"><span data-stu-id="e6e66-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>  
  
 [<span data-ttu-id="e6e66-126">Edytowanie danych w zestawach danych</span><span class="sxs-lookup"><span data-stu-id="e6e66-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
 <span data-ttu-id="e6e66-127">Dostarcza łącza do stron opisujących sposoby manipulowania danymi w tabelach danych zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="e6e66-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  
  
 [<span data-ttu-id="e6e66-128">Weryfikowanie danych w zestawach danych</span><span class="sxs-lookup"><span data-stu-id="e6e66-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
 <span data-ttu-id="e6e66-129">Dostarcza łącza do stron opisujących sposób dodawania do zestawu danych walidacji podczas zmian wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="e6e66-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>  
  
 [<span data-ttu-id="e6e66-130">Zapisywanie danych z powrotem w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e6e66-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
 <span data-ttu-id="e6e66-131">Dostarcza łącza do stron wyjaśniających jak wysyłać zaktualizowane dane z aplikacji do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e6e66-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>  
  
 [<span data-ttu-id="e6e66-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6e66-132">ADO.NET</span></span>](https://msdn.microsoft.com/library/e80y5yhx.aspx)  
 <span data-ttu-id="e6e66-133">Opisuje klasy ADO.NET, które ujawniają usługi dostępu do danych programiście .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6e66-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

 [<span data-ttu-id="e6e66-134">Dane w rozwiązaniach pakietu Office</span><span class="sxs-lookup"><span data-stu-id="e6e66-134">Data in Office Solutions</span></span>](https://msdn.microsoft.com/library/xx069ybh)  
 <span data-ttu-id="e6e66-135">Zawiera łącza do stron, które wyjaśniają jak działają dane w rozwiązaniach pakietu Office oraz zawierają informacje dotyczące programowania schematycznego, buforowania danych i dostępu do danych po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="e6e66-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
