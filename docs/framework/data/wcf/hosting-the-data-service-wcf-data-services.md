---
title: Hostowanie usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: ea60ac132fdd94d4e3a3676891964070b7150857
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780273"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="105db-102">Hostowanie usługi danych (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="105db-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="105db-103">Za pomocą usługi danych programu WCF można utworzyć usługę, która udostępnia dane jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródło danych.</span><span class="sxs-lookup"><span data-stu-id="105db-103">By using WCF Data Services, you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="105db-104">Ta usługa danych jest definiowana jako Klasa, która dziedziczy z <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="105db-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="105db-105">Ta klasa udostępnia funkcje wymagane do przetwarzania komunikatów żądań, wykonywania aktualizacji względem źródła danych oraz generowania komunikatów odpowiedzi zgodnie z wymaganiami protokołu OData.</span><span class="sxs-lookup"><span data-stu-id="105db-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="105db-106">Jednak usługa danych nie może powiązać się z gniazdem sieciowym i nasłuchiwać w nich w ramach przychodzących żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="105db-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="105db-107">W przypadku tej wymaganej funkcji usługa danych opiera się na składniku hostingu.</span><span class="sxs-lookup"><span data-stu-id="105db-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="105db-108">Host usługi danych wykonuje następujące zadania w imieniu usługi danych:</span><span class="sxs-lookup"><span data-stu-id="105db-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="105db-109">Nasłuchuje żądań i kieruje je do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="105db-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="105db-110">Tworzy wystąpienie usługi danych dla każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="105db-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="105db-111">Żąda przetworzenia żądania przychodzącego przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="105db-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="105db-112">Wysyła odpowiedź w imieniu usługi danych.</span><span class="sxs-lookup"><span data-stu-id="105db-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="105db-113">Aby uprościć hosting usługi danych, Usługi danych programu WCF jest zaprojektowana do integracji z Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="105db-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="105db-114">Usługa danych zapewnia domyślną implementację programu WCF, która służy jako host usługi danych w aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="105db-114">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="105db-115">W związku z tym usługa danych może być hostowana w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="105db-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="105db-116">W aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="105db-116">In an ASP.NET application.</span></span>

- <span data-ttu-id="105db-117">W zarządzanej aplikacji, która obsługuje samoobsługowe usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="105db-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="105db-118">W innym niestandardowym hoście usługi danych.</span><span class="sxs-lookup"><span data-stu-id="105db-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="105db-119">Hosting usługi danych w aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="105db-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="105db-120">W przypadku korzystania z okna dialogowego **Dodawanie nowego elementu** w programie Visual Studio 2015 w celu zdefiniowania usługi danych w aplikacji ASP.NET narzędzie generuje dwa nowe pliki w projekcie.</span><span class="sxs-lookup"><span data-stu-id="105db-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="105db-121">Pierwszy plik ma `.svc` rozszerzenie i instruuje środowisko uruchomieniowe WCF o sposobie tworzenia wystąpienia usługi danych.</span><span class="sxs-lookup"><span data-stu-id="105db-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="105db-122">Poniżej znajduje się przykład tego pliku dla usługi przykładowych danych Northwind utworzonych po zakończeniu [przewodnika Szybki Start](quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="105db-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="105db-123">Ta dyrektywa nakazuje aplikacji utworzenie hosta usługi dla nazwanej klasy usługi danych przy użyciu <xref:System.Data.Services.DataServiceHostFactory> klasy.</span><span class="sxs-lookup"><span data-stu-id="105db-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="105db-124">Strona Poprzednia kodu dla `.svc` pliku zawiera klasę, która jest implementacją samej usługi danych, która została zdefiniowana w następujący sposób dla przykładowej usługi danych Northwind:</span><span class="sxs-lookup"><span data-stu-id="105db-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="105db-125">Ponieważ usługa danych zachowuje się jak usługa WCF, usługa danych integruje się z usługą ASP.NET i jest zgodna z modelem programowania sieci Web w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="105db-125">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="105db-126">Aby uzyskać więcej informacji, zobacz model programowania [usług WCF i](../../wcf/feature-details/wcf-services-and-aspnet.md) [http w sieci Web](../../wcf/feature-details/wcf-web-http-programming-model.md)ASP.NET i WCF.</span><span class="sxs-lookup"><span data-stu-id="105db-126">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="105db-127">Samoobsługowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="105db-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="105db-128">Ponieważ obejmuje implementację programu WCF, Usługi danych programu WCF obsługiwać samoobsługowego udostępniania usługi danych jako usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="105db-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="105db-129">Usługa może być samodzielna w dowolnej aplikacji .NET Framework, takiej jak Aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="105db-129">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="105db-130">Klasa, która dziedziczy z <xref:System.ServiceModel.Web.WebServiceHost>, jest używana do tworzenia wystąpienia usługi danych o określonym adresie. <xref:System.Data.Services.DataServiceHost></span><span class="sxs-lookup"><span data-stu-id="105db-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="105db-131">Funkcja samoobsługowego udostępniania może służyć do tworzenia i testowania, ponieważ ułatwia wdrażanie i rozwiązywanie problemów z usługą.</span><span class="sxs-lookup"><span data-stu-id="105db-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="105db-132">Jednak ten rodzaj hostingu nie oferuje zaawansowanych funkcji hostingu i zarządzania udostępnianych przez ASP.NET lub przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="105db-132">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="105db-133">Aby uzyskać więcej informacji, zobacz [hosting w aplikacji zarządzanej](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="105db-133">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="105db-134">Definiowanie niestandardowego hosta usługi danych</span><span class="sxs-lookup"><span data-stu-id="105db-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="105db-135">W przypadkach, w których implementacja hosta WCF jest zbyt restrykcyjna, można także zdefiniować hosta niestandardowego dla usługi danych.</span><span class="sxs-lookup"><span data-stu-id="105db-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="105db-136">Każda klasa implementująca <xref:System.Data.Services.IDataServiceHost> interfejs może być używana jako host sieciowy usługi danych.</span><span class="sxs-lookup"><span data-stu-id="105db-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="105db-137">Host niestandardowy musi implementować <xref:System.Data.Services.IDataServiceHost> interfejs i być w stanie obsłużyć następujące podstawowe obowiązki hosta usługi danych:</span><span class="sxs-lookup"><span data-stu-id="105db-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="105db-138">Podaj usługę danych z ścieżką katalogu głównego usługi.</span><span class="sxs-lookup"><span data-stu-id="105db-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="105db-139">Przetwarzaj informacje o nagłówkach żądań i odpowiedzi <xref:System.Data.Services.IDataServiceHost> do odpowiedniej implementacji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="105db-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="105db-140">Obsługa wyjątków zgłoszonych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="105db-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="105db-141">Sprawdź poprawność parametrów w ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="105db-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="105db-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="105db-142">See also</span></span>

- [<span data-ttu-id="105db-143">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="105db-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="105db-144">Udostępnianie danych jako usługi</span><span class="sxs-lookup"><span data-stu-id="105db-144">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="105db-145">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="105db-145">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
