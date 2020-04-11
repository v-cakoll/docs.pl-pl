---
title: Szybki start (usługi danych WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121223"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="a693c-102">Szybki start (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="a693c-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="a693c-103">Ten przewodnik Szybki start ułatwia zapoznanie się z usługami WCF Data Services i protokołem OData (Open Data Protocol) za pomocą szeregu zadań, które obsługują tematy w [obszarze Wprowadzenie.](getting-started-with-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="a693c-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="a693c-104">Zawartość</span><span class="sxs-lookup"><span data-stu-id="a693c-104">What you'll learn</span></span>

<span data-ttu-id="a693c-105">Pierwsze zadanie w tym przewodniku Szybki start pokazuje, jak utworzyć usługę danych, aby udostępnić źródło danych OData z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a693c-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="a693c-106">W późniejszych tematach można uzyskać dostęp do źródła danych OData za pomocą przeglądarki sieci Web, a także utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która zużywa źródło danych OData przy użyciu bibliotek klienckich.</span><span class="sxs-lookup"><span data-stu-id="a693c-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a693c-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a693c-107">Prerequisites</span></span>

<span data-ttu-id="a693c-108">Aby ukończyć ten szybki start, zainstaluj następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="a693c-108">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="a693c-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a693c-109">Visual Studio</span></span>

- <span data-ttu-id="a693c-110">Wystąpienie programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a693c-110">An instance of SQL Server.</span></span> <span data-ttu-id="a693c-111">Obejmuje to program SQL Server Express, który jest uwzględniony w domyślnej instalacji programu Visual Studio 2015 lub jako część obciążenia **magazynu i przetwarzania danych** w programie Visual Studio 2017 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="a693c-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="a693c-112">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a693c-112">The Northwind sample database.</span></span> <span data-ttu-id="a693c-113">Aby zainstalować bazę danych, uruchom skrypt Transact-SQL z [northwind i pubów przykładowych baz danych dla programu Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="a693c-113">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="a693c-114">Zadania szybkiego startu usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="a693c-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="a693c-115">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="a693c-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="a693c-116">Zdefiniuj ASP.NET aplikacji, zdefiniuj model danych, utwórz usługę danych i włącz dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="a693c-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="a693c-117">Dostęp do usługi za pomocą przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="a693c-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="a693c-118">Uruchom usługę z programu Visual Studio i uzyskać dostęp do usługi, przesyłając żądania HTTP GET za pośrednictwem przeglądarki sieci Web do udostępnianego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a693c-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="a693c-119">Tworzenie aplikacji klienckiej programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a693c-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="a693c-120">Utwórz aplikację WPF, aby korzystać z źródła danych OData, powiązać dane z formantami systemu Windows, zmienić dane w formantach powiązanych, a następnie wysłać zmiany z powrotem do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="a693c-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="a693c-121">Pliki projektu z ukończonej wersji przewodnika Szybki start można pobrać z [gitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span><span class="sxs-lookup"><span data-stu-id="a693c-121">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a693c-122">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a693c-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a693c-123">Uruchamianie przewodnika Szybki start</span><span class="sxs-lookup"><span data-stu-id="a693c-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="a693c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a693c-124">See also</span></span>

- [<span data-ttu-id="a693c-125">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a693c-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
