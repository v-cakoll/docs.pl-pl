---
title: 'Instrukcje: dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895080"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="d6a74-102">Instrukcje: dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d6a74-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="d6a74-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia punkt końcowy z obsługą technologii AJAX ASP.NET, który można wywołać z JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="d6a74-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="d6a74-104">Aby utworzyć taki punkt końcowy, możesz użyć pliku konfiguracji, podobnie jak w przypadku wszystkich innych punktów końcowych WCF, lub użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d6a74-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="d6a74-105">W tym temacie przedstawiono drugie podejście.</span><span class="sxs-lookup"><span data-stu-id="d6a74-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="d6a74-106">Aby można było tworzyć usługi z ASP.NETymi punktami końcowymi AJAX bez konfiguracji, usługi muszą być hostowane przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d6a74-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d6a74-107">Aby aktywować punkt końcowy ASP.NET AJAX przy użyciu tego podejścia, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki [ \@w dyrektywie ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) w pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="d6a74-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="d6a74-108">Ta fabryka niestandardowa jest składnikiem, który automatycznie konfiguruje punkt końcowy ASP.NET AJAX, aby można go było wywołać z JavaScript w klienckiej witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d6a74-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="d6a74-109">Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d6a74-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="d6a74-110">Aby uzyskać informacje na temat sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji, [zobacz How to: Użyj konfiguracji, aby dodać punkt końcowy](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d6a74-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="d6a74-111">Aby utworzyć podstawową usługę WCF</span><span class="sxs-lookup"><span data-stu-id="d6a74-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="d6a74-112">Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d6a74-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="d6a74-113">Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d6a74-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="d6a74-114">Upewnij się, <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> że właściwość jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="d6a74-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="d6a74-115">Zaimplementuj kontrakt `CalculatorService` `ICalculator` usługi za pomocą.</span><span class="sxs-lookup"><span data-stu-id="d6a74-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="d6a74-116">Zdefiniuj przestrzeń nazw dla `ICalculator` implementacji i `CalculatorService` , umieszczając je w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d6a74-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="d6a74-117">Aby hostować usługę w Internet Information Services bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d6a74-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="d6a74-118">Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d6a74-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="d6a74-119">Edytuj ten plik, dodając odpowiednie [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informacje o dyrektywie ServiceHost dla usługi.</span><span class="sxs-lookup"><span data-stu-id="d6a74-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="d6a74-120">Określ, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używana [ \@w dyrektywie ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) , aby automatycznie konfigurować punkt końcowy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d6a74-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="d6a74-121">Utwórz usługę i Wywołaj ją z poziomu klienta.</span><span class="sxs-lookup"><span data-stu-id="d6a74-121">Build the service and call it from the client.</span></span> <span data-ttu-id="d6a74-122">Internet Information Services (IIS) aktywuje usługę po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="d6a74-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="d6a74-123">Aby uzyskać więcej informacji na temat hostingu w usługach [IIS, zobacz How to: Hostowanie usługi WCF w usługach](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)IIS.</span><span class="sxs-lookup"><span data-stu-id="d6a74-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="d6a74-124">Aby wywołać usługę</span><span class="sxs-lookup"><span data-stu-id="d6a74-124">To call the service</span></span>  
  
1. <span data-ttu-id="d6a74-125">Punkt końcowy jest skonfigurowany pod adresem pustym względem pliku SVC, więc usługa jest teraz dostępna i może być wywoływana przez wysyłanie żądań do usługi Service. svc/\<Operation > — na przykład Service. svc/Add `Add` dla operacji.</span><span class="sxs-lookup"><span data-stu-id="d6a74-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="d6a74-126">Można go użyć, wprowadzając adres URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d6a74-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="d6a74-127">Aby zapoznać się z przykładem, zobacz [Usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d6a74-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6a74-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6a74-128">Example</span></span>  
  
 <span data-ttu-id="d6a74-129">Automatycznie skonfigurowany punkt końcowy jest tworzony pod pustym adresem względem podstawowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d6a74-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="d6a74-130">Plik konfiguracji można także dodać i użyć z tym podejściem.</span><span class="sxs-lookup"><span data-stu-id="d6a74-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="d6a74-131">Jeśli plik konfiguracji zawiera definicje punktów końcowych, te punkty końcowe są dodawane do automatycznie skonfigurowanego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d6a74-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="d6a74-132">Na przykład usługa Service. svc korzysta z <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> programu, a katalog usługi zawiera plik Web. config, który definiuje punkt końcowy dla tej samej usługi <xref:System.ServiceModel.BasicHttpBinding> przy użyciu adresu względnego "SOAP".</span><span class="sxs-lookup"><span data-stu-id="d6a74-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="d6a74-133">W takim przypadku usługa zawiera dwa punkty końcowe: jeden w usłudze Service. svc (który reaguje na żądania ASP.NET AJAX) i inny w usłudze Service. svc/SOAP (który reaguje na żądania protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="d6a74-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="d6a74-134">Jeśli plik konfiguracji definiuje punkt końcowy w pustym adresie względnym i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używany, zostanie zgłoszony wyjątek i uruchomienie usługi nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="d6a74-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="d6a74-135">Nie można użyć konfiguracji w celu zmodyfikowania ustawień w automatycznie skonfigurowanym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="d6a74-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="d6a74-136">Jeśli konieczne jest zmodyfikowanie dowolnego ustawienia (takiego jak przydział czytnika), nie należy używać podejścia <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> z bezpłatną konfiguracją, usuwając plik z pliku svc i tworząc wpis konfiguracji dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d6a74-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="d6a74-137">Jeśli usługa wymaga trybu zgodności ASP.NET — na przykład jeśli używa <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji ASP.NET — plik konfiguracji jest nadal wymagany do włączenia tego trybu.</span><span class="sxs-lookup"><span data-stu-id="d6a74-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="d6a74-138">Wymagany element konfiguracji jest [ \<elementem ServiceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) , który należy dodać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d6a74-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="d6a74-139">Aby uzyskać więcej informacji, zobacz temat [usługi WCF i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) .</span><span class="sxs-lookup"><span data-stu-id="d6a74-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="d6a74-140">Klasa jest klasą pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="d6a74-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="d6a74-141">Szczegółowy opis mechanizmu fabryki hosta usługi znajduje się w temacie [Rozszerzanie hostingu przy użyciu obiektu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) .</span><span class="sxs-lookup"><span data-stu-id="d6a74-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a74-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6a74-142">See also</span></span>

- [<span data-ttu-id="d6a74-143">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d6a74-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="d6a74-144">Instrukcje: Migrowanie usług sieci Web ASP.NET z obsługą technologii AJAX do programu WCF</span><span class="sxs-lookup"><span data-stu-id="d6a74-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
