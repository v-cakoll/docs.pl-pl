---
title: Przewodnik Szybki Start (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f20ffcf356aa0493b1e2356746d9ad7b27d9a1aa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480516"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="55842-102">Przewodnik Szybki Start (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="55842-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="55842-103">Ten przewodnik Szybki Start ułatwia zapoznanie się z usług danych WCF i [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] przez szereg zadań, które obsługują tematy w [wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="55842-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="55842-104">Dowiesz się</span><span class="sxs-lookup"><span data-stu-id="55842-104">What you'll learn</span></span>

<span data-ttu-id="55842-105">Pierwsze zadanie w tym przewodniku Szybki Start przedstawia sposób tworzenia usługi danych, aby udostępnić źródła danych z przykładowej bazy danych Northwind OData.</span><span class="sxs-lookup"><span data-stu-id="55842-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="55842-106">W kolejnych tematach będzie dostęp do usługi OData źródła danych za pomocą przeglądarki sieci Web, a także utworzyć Windows Presentation Foundation (WPF) aplikację kliencką, która zużywa OData źródła danych przy użyciu biblioteki klienta.</span><span class="sxs-lookup"><span data-stu-id="55842-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55842-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="55842-107">Prerequisites</span></span>

<span data-ttu-id="55842-108">Aby ukończyć ten przewodnik Szybki Start, musisz zainstalować następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="55842-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="55842-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55842-109">Visual Studio</span></span>

- <span data-ttu-id="55842-110">Wystąpienie programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="55842-110">An instance of SQL Server.</span></span> <span data-ttu-id="55842-111">W tym programu SQL Server Express, która jest ujęta w domyślnej instalacji programu Visual Studio 2015 lub jako część **przechowywanie i przetwarzanie danych** obciążenia w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="55842-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="55842-112">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="55842-112">The Northwind sample database.</span></span> <span data-ttu-id="55842-113">Aby pobrać tej przykładowej bazy danych, zobacz stronę pobierania [przykładowych baz danych programu SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="55842-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="55842-114">Zadania szybkiego startu usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="55842-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="55842-115">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="55842-115">Create the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

 <span data-ttu-id="55842-116">Zdefiniuj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, zdefiniowanie modelu danych, tworzenie usługi danych i zapewnianie dostępu do zasobów.</span><span class="sxs-lookup"><span data-stu-id="55842-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="55842-117">Dostęp do usługi z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="55842-117">Access the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="55842-118">Uruchom usługę za pomocą programu Visual Studio i uzyskania dostępu do usługi po przesłaniu żądania HTTP GET, za pośrednictwem przeglądarki sieci Web narażonych źródła danych.</span><span class="sxs-lookup"><span data-stu-id="55842-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="55842-119">Tworzenie aplikacji klienckich programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="55842-119">Create the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="55842-120">Tworzenie aplikacji WPF przyjmowania źródła danych OData, wiązanie danych kontrolek Windows, zmiany danych w formantach powiązanych, a następnie wysłać zmiany z powrotem do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="55842-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="55842-121">Pliki projektów z pełną wersję tego przewodnika Szybki Start można pobrać z [przykłady dokumentacji usług danych WCF](https://go.microsoft.com/fwlink/?LinkId=179994) strony.</span><span class="sxs-lookup"><span data-stu-id="55842-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="55842-122">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="55842-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55842-123">Uruchom samouczek Szybki Start</span><span class="sxs-lookup"><span data-stu-id="55842-123">Start the quickstart</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="55842-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55842-124">See also</span></span>

- [<span data-ttu-id="55842-125">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="55842-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
