---
title: Szybki Start (Usługi danych programu WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: d0002182c5ae519c36348acdd2587bca499fe72e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975140"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="61b96-102">Szybki Start (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="61b96-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="61b96-103">Ten przewodnik Szybki Start pomaga zapoznać się z Usługi danych programu WCF i protokołem Open Data Protocol (OData), korzystając z szeregu zadań, które obsługują tematy w programie [wprowadzenie](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="61b96-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="61b96-104">Dowiesz się</span><span class="sxs-lookup"><span data-stu-id="61b96-104">What you'll learn</span></span>

<span data-ttu-id="61b96-105">Pierwsze zadanie w tym przewodniku szybki start przedstawia sposób tworzenia usługi danych w celu udostępnienia źródła strumieniowego OData z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="61b96-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="61b96-106">W kolejnych tematach można uzyskać dostęp do źródła danych OData przy użyciu przeglądarki sieci Web, a także utworzyć aplikację kliencką Windows Presentation Foundation (WPF), która korzysta ze źródła danych OData przy użyciu bibliotek klienckich.</span><span class="sxs-lookup"><span data-stu-id="61b96-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="61b96-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="61b96-107">Prerequisites</span></span>

<span data-ttu-id="61b96-108">Aby ukończyć ten przewodnik Szybki Start, należy zainstalować następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="61b96-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="61b96-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="61b96-109">Visual Studio</span></span>

- <span data-ttu-id="61b96-110">Wystąpienie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="61b96-110">An instance of SQL Server.</span></span> <span data-ttu-id="61b96-111">Obejmuje to SQL Server Express, które są dołączone do domyślnej instalacji programu Visual Studio 2015 lub w ramach obciążenia **magazynu i przetwarzania danych** w programie visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="61b96-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="61b96-112">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="61b96-112">The Northwind sample database.</span></span> <span data-ttu-id="61b96-113">Aby pobrać tę przykładową bazę danych, zobacz stronę pobierania, [przykładowe bazy danych dla SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="61b96-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="61b96-114">Zadania szybkiego startu usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="61b96-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="61b96-115">Tworzenie usługi danych</span><span class="sxs-lookup"><span data-stu-id="61b96-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="61b96-116">Zdefiniuj aplikację ASP.NET, zdefiniuj model danych, Utwórz usługę danych i Włącz dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="61b96-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="61b96-117">Uzyskiwanie dostępu do usługi z przeglądarki sieci Web</span><span class="sxs-lookup"><span data-stu-id="61b96-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="61b96-118">Uruchom usługę z programu Visual Studio i uzyskaj dostęp do usługi, przesyłając żądania HTTP GET za pośrednictwem przeglądarki sieci Web do uwidocznionego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="61b96-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="61b96-119">Tworzenie aplikacji klienckiej .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61b96-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="61b96-120">Utwórz aplikację WPF do korzystania ze źródła danych OData, powiąż dane z kontrolkami systemu Windows, Zmień dane w formantach powiązanych, a następnie Wyślij zmiany z powrotem do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="61b96-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="61b96-121">Pliki projektu z kompletnej wersji przewodnika Szybki Start można pobrać ze strony [przykładów dokumentacji usługi danych programu WCF](https://go.microsoft.com/fwlink/?LinkId=179994) .</span><span class="sxs-lookup"><span data-stu-id="61b96-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="61b96-122">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="61b96-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="61b96-123">Rozpocznij Przewodnik Szybki Start</span><span class="sxs-lookup"><span data-stu-id="61b96-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="61b96-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61b96-124">See also</span></span>

- [<span data-ttu-id="61b96-125">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="61b96-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
