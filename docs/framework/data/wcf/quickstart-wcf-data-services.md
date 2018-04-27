---
title: Szybki Start (usługi danych WCF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf23c6f86900fd94d269e77dcefb05da0ace5ea0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="8be67-102">Szybki Start (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="8be67-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="8be67-103">Ta opcja szybkiego startu pomaga zapoznać się z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] i [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] przez kilka zadań, które obsługują tematy [wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8be67-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="8be67-104">Co dowiesz się</span><span class="sxs-lookup"><span data-stu-id="8be67-104">What You Will Learn</span></span>  
 <span data-ttu-id="8be67-105">Pierwszym zadaniem z tego przewodnika Szybki Start pokazano, jak utworzyć usługę danych do udostępnienia [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8be67-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="8be67-106">W tematach nowsze będą uzyskiwać dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych za pomocą przeglądarki sieci Web jak również tworzy aplikacja kliencka Windows Presentation Foundation (WPF), który wykorzystuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych przy użyciu bibliotek klienckich.</span><span class="sxs-lookup"><span data-stu-id="8be67-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8be67-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8be67-107">Prerequisites</span></span>  
 <span data-ttu-id="8be67-108">Aby ukończyć tego przewodnika Szybki Start, należy zainstalować następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="8be67-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="8be67-109">.</span><span class="sxs-lookup"><span data-stu-id="8be67-109">.</span></span>  
  
-   <span data-ttu-id="8be67-110">Wystąpienie [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8be67-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] SQL Server.</span></span> <span data-ttu-id="8be67-111">W tym programu SQL Server Express, który jest dostępny w domyślnej instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8be67-111">This includes SQL Server Express, which is included in a default installation of Visual Studio.</span></span>  
  
-   <span data-ttu-id="8be67-112">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8be67-112">The Northwind sample database.</span></span> <span data-ttu-id="8be67-113">Aby pobrać tej przykładowej bazy danych, zobacz stronę pobierania [przykładowe bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="8be67-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="8be67-114">Zadania szybkiego startu usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="8be67-114">WCF Data Services Quickstart Tasks</span></span>  
 [<span data-ttu-id="8be67-115">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="8be67-115">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
 <span data-ttu-id="8be67-116">Zdefiniuj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, definiują model danych, Utwórz usługę danych i umożliwiają dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="8be67-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="8be67-117">Uzyskiwanie dostępu do usługi z przeglądarki internetowej</span><span class="sxs-lookup"><span data-stu-id="8be67-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="8be67-118">Uruchom usługę z programu Visual Studio i uzyskania dostępu do usługi poprzez przesłanie żądania HTTP GET za pośrednictwem przeglądarki sieci Web do dostępnego źródła.</span><span class="sxs-lookup"><span data-stu-id="8be67-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="8be67-119">Tworzenie aplikacji klienckich programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8be67-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="8be67-120">Utwórz [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] korzystać z aplikacji klienckiej [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, wiązanie danych do formantów systemu Windows, Zmień dane w formantach powiązanych, a następnie wyślij, zmian z powrotem do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="8be67-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8be67-121">Pliki projektu z ukończoną wersję szybkiego startu można pobrać z [przykłady dokumentacji usługi danych WCF](http://go.microsoft.com/fwlink/?LinkId=179994) strony.</span><span class="sxs-lookup"><span data-stu-id="8be67-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8be67-122">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8be67-122">Next Steps</span></span>  
 <span data-ttu-id="8be67-123">[Uruchom Szybki Start](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="8be67-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be67-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8be67-124">See Also</span></span>  
 [<span data-ttu-id="8be67-125">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8be67-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
