---
title: Hosting usługi danych (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: c240a76ea54d57456ff13fee7a48981354f669de
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881273"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="795f8-102">Hosting usługi danych (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="795f8-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="795f8-103">Korzystając z usług danych WCF, można utworzyć usługę, która udostępnia dane jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-103">By using WCF Data Services, you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="795f8-104">Ta usługa danych jest zdefiniowany jako klasę, która dziedziczy z <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="795f8-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="795f8-105">Ta klasa udostępnia funkcje wymagane do przetwarzania komunikatów żądań, przeprowadzania aktualizacji względem źródła danych i generowanie wiadomości odpowiedzi, zgodnie z wymaganiami protokołu OData.</span><span class="sxs-lookup"><span data-stu-id="795f8-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="795f8-106">Jednak usługa danych nie można powiązać i nasłuchiwanie przychodzących żądań HTTP na gnieździe sieci.</span><span class="sxs-lookup"><span data-stu-id="795f8-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="795f8-107">Dla tej funkcji wymagane usługi danych opiera się na składniku hostingowych.</span><span class="sxs-lookup"><span data-stu-id="795f8-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="795f8-108">Host usługi danych wykonuje następujące zadania w imieniu usługi danych:</span><span class="sxs-lookup"><span data-stu-id="795f8-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="795f8-109">Nasłuchuje żądań i kieruje żądania do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="795f8-110">Tworzy wystąpienie usługi danych dla każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="795f8-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="795f8-111">Czy usługa danych przetwarzać żądania przychodzącego żądania.</span><span class="sxs-lookup"><span data-stu-id="795f8-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="795f8-112">Wysyła odpowiedź w imieniu usługi danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="795f8-113">Aby uprościć hostująca usługę danych, usługi danych WCF został zaprojektowany do integrowania za pomocą programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="795f8-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="795f8-114">Usługa danych udostępnia domyślną implementację WCF, która służy jako hosta usługi danych w aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="795f8-114">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="795f8-115">W związku z tym można hostować usługi danych w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="795f8-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="795f8-116">W aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="795f8-116">In an ASP.NET application.</span></span>

- <span data-ttu-id="795f8-117">W aplikacji zarządzanej, który obsługuje samodzielnie hostowanej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="795f8-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="795f8-118">W niektórych innych niestandardowych danych hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="795f8-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="795f8-119">Hosting usługi danych w aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="795f8-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="795f8-120">Kiedy używasz **Dodaj nowy element** okna dialogowego w programie Visual Studio 2015 do definiowania usługi danych w aplikacji ASP.NET, narzędzie generuje dwa nowe pliki w projekcie.</span><span class="sxs-lookup"><span data-stu-id="795f8-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="795f8-121">Pierwszy plik ma `.svc` rozszerzenia i powoduje, że środowisko wykonawcze programu WCF sposobu tworzenia wystąpienia usługi danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="795f8-122">Oto przykład tego pliku do usługi danych Northwind przykładowe utworzone po zakończeniu [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="795f8-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="795f8-123">Oznacza ona aplikacji do utworzenia hosta usługi dla klasy usługi danych o podanej nazwie za pomocą <xref:System.Data.Services.DataServiceHostFactory> klasy.</span><span class="sxs-lookup"><span data-stu-id="795f8-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="795f8-124">Strona związanym z kodem `.svc` plik zawiera klasę, która jest implementacją usługi danych, która jest zdefiniowana w następujący sposób usługi Northwind przykładowe dane:</span><span class="sxs-lookup"><span data-stu-id="795f8-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="795f8-125">Ponieważ usługa danych zachowuje się jak usługi WCF, Usługa danych integruje się z programem ASP.NET i jest zgodna z modelu programowania w sieci Web WCF.</span><span class="sxs-lookup"><span data-stu-id="795f8-125">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="795f8-126">Aby uzyskać więcej informacji, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) i [modelu programowania protokołu HTTP sieci Web programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="795f8-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="795f8-127">Usług hostowania samoobsługowego WCF</span><span class="sxs-lookup"><span data-stu-id="795f8-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="795f8-128">Ponieważ zawiera implementację usługi WCF, usług danych WCF obsługuje własnym hostująca usługę danych jako usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="795f8-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="795f8-129">Usługa może być samodzielnie hostowane w dowolnej aplikacji .NET Framework, takie jak aplikacja konsoli.</span><span class="sxs-lookup"><span data-stu-id="795f8-129">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="795f8-130"><xref:System.Data.Services.DataServiceHost> Klasy, która dziedziczy po elemencie <xref:System.ServiceModel.Web.WebServiceHost>, jest używany do utworzenia wystąpienia usługi danych pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="795f8-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="795f8-131">Hostingu samodzielnego może służyć do tworzenia i testowania, ponieważ jego ułatwia wdrażanie i rozwiązywanie problemów z usługi.</span><span class="sxs-lookup"><span data-stu-id="795f8-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="795f8-132">Jednak tego rodzaju hostingu nie zapewnia zaawansowane hostingu i funkcje zarządzania dostarczane przez platformę ASP.NET lub Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="795f8-132">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="795f8-133">Aby uzyskać więcej informacji, zobacz [hostowanie w aplikacji Managed](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="795f8-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="795f8-134">Definiowanie hosta usługi danych niestandardowych</span><span class="sxs-lookup"><span data-stu-id="795f8-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="795f8-135">W przypadkach, w których implementacja hosta usługi WCF jest zbyt restrykcyjne można również zdefiniować niestandardowy host usługi danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="795f8-136">Każda klasa implementująca <xref:System.Data.Services.IDataServiceHost> interfejs może służyć jako hosta sieci usługi danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="795f8-137">Niestandardowy host musi implementować <xref:System.Data.Services.IDataServiceHost> interfejs i obsługiwać następujące obowiązki podstawowe dane hosta usługi:</span><span class="sxs-lookup"><span data-stu-id="795f8-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="795f8-138">Usługi danych należy udostępnić ścieżkę katalogu głównego usługi.</span><span class="sxs-lookup"><span data-stu-id="795f8-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="795f8-139">Przetwarzania żądań i odpowiedzi informacji nagłówki do odpowiedniego <xref:System.Data.Services.IDataServiceHost> implementacji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="795f8-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="795f8-140">Obsługa wyjątków zgłaszanych przez usługę danych.</span><span class="sxs-lookup"><span data-stu-id="795f8-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="795f8-141">Sprawdza poprawność parametrów ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="795f8-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="795f8-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="795f8-142">See also</span></span>

- [<span data-ttu-id="795f8-143">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="795f8-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="795f8-144">Udostępnianie danych jako usługi</span><span class="sxs-lookup"><span data-stu-id="795f8-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="795f8-145">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="795f8-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
