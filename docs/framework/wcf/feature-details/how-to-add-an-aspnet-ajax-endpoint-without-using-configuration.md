---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185138"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="f71cf-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f71cf-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="f71cf-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia ASP.NET punkt końcowy z obsługą AJAX, który można wywołać z języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="f71cf-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="f71cf-104">Aby utworzyć taki punkt końcowy, można użyć pliku konfiguracji, podobnie jak w przypadku wszystkich innych punktów końcowych WCF lub użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f71cf-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="f71cf-105">W tym temacie przedstawiono drugie podejście.</span><span class="sxs-lookup"><span data-stu-id="f71cf-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="f71cf-106">Aby utworzyć usługi z ASP.NET punktami końcowymi AJAX bez konfiguracji, usługi muszą być hostowane przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="f71cf-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="f71cf-107">Aby aktywować punkt końcowy ASP.NET AJAX przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> tej metody, należy określić jako Factory parametru w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="f71cf-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="f71cf-108">Ta niestandardowa fabryka jest składnikiem, który automatycznie konfiguruje ASP.NET punkt końcowy AJAX, dzięki czemu można go wywołać z języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="f71cf-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="f71cf-109">Na przykład roboczy zobacz [usługę AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f71cf-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="f71cf-110">Aby uzyskać kontur sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracyjnych, zobacz [Jak: Dodawanie ASP.NET punktu końcowego ajaxu za pomocą funkcji Konfigurowania.](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)</span><span class="sxs-lookup"><span data-stu-id="f71cf-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="f71cf-111">Aby utworzyć podstawową usługę WCF</span><span class="sxs-lookup"><span data-stu-id="f71cf-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="f71cf-112">Zdefiniuj podstawową umowę serwisową <xref:System.ServiceModel.ServiceContractAttribute> WCF za pomocą interfejsu oznaczonego atrybutem.</span><span class="sxs-lookup"><span data-stu-id="f71cf-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="f71cf-113">Oznacz każdą operację <xref:System.ServiceModel.OperationContractAttribute>za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="f71cf-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="f71cf-114">Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="f71cf-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="f71cf-115">`ICalculator` Zaimplementuj `CalculatorService`umowę serwisową z programem .</span><span class="sxs-lookup"><span data-stu-id="f71cf-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="f71cf-116">Zdefiniuj `ICalculator` obszar `CalculatorService` nazw dla i implementacji, zawijając je w bloku obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="f71cf-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="f71cf-117">Hostować usługę w internetowych usługach informacyjnych bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f71cf-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="f71cf-118">Utwórz nowy plik o nazwie usługa z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f71cf-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="f71cf-119">Edytuj ten plik, [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dodając odpowiednie informacje o dyrektywie ServiceHost dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f71cf-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="f71cf-120">Określ, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> że ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować ASP.NET punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="f71cf-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="f71cf-121">Skompiluj usługę i wywołaj ją od klienta.</span><span class="sxs-lookup"><span data-stu-id="f71cf-121">Build the service and call it from the client.</span></span> <span data-ttu-id="f71cf-122">Internetowe usługi informacyjne (IIS) aktywują usługę po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="f71cf-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="f71cf-123">Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [Jak: Hostowanie usługi WCF w usługach IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="f71cf-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="f71cf-124">Aby zadzwonić do usługi</span><span class="sxs-lookup"><span data-stu-id="f71cf-124">To call the service</span></span>  
  
1. <span data-ttu-id="f71cf-125">Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku .svc, więc usługa jest teraz dostępna i może\<być wywoływana przez wysyłanie żądań do service.svc/ operation> — na przykład service.svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="f71cf-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="f71cf-126">Można go użyć, wprowadzając adres URL usługi do kolekcji Skrypty ASP.NET kontrolki Menedżera skryptów AJAX.</span><span class="sxs-lookup"><span data-stu-id="f71cf-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="f71cf-127">Na przykład zobacz [usługę AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f71cf-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f71cf-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f71cf-128">Example</span></span>  
  
 <span data-ttu-id="f71cf-129">Automatycznie skonfigurowany punkt końcowy jest tworzony przy pustym adresie względem podstawowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="f71cf-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="f71cf-130">Plik konfiguracji można również dodać i używać z tym podejściem.</span><span class="sxs-lookup"><span data-stu-id="f71cf-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="f71cf-131">Jeśli plik konfiguracji zawiera definicje punktów końcowych, te punkty końcowe są dodawane do automatycznie skonfigurowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f71cf-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="f71cf-132">Na przykład service.svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> katalogu usługi i zawiera plik Web.config, który definiuje punkt końcowy <xref:System.ServiceModel.BasicHttpBinding> dla tej samej usługi przy użyciu w "mydło" względny adres.</span><span class="sxs-lookup"><span data-stu-id="f71cf-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="f71cf-133">W takim przypadku usługa zawiera dwa punkty końcowe: jeden w service.svc (który odpowiada na żądania ASP.NET AJAX) i inny w service.svc/soap (który odpowiada na żądania protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="f71cf-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="f71cf-134">Jeśli plik konfiguracji definiuje punkt końcowy przy pustym <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> adresie względnym i jest używany, wyjątek jest zgłaszany i usługa nie może się uruchomić.</span><span class="sxs-lookup"><span data-stu-id="f71cf-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="f71cf-135">Nie można użyć konfiguracji do modyfikowania ustawień w automatycznie skonfigurowanym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="f71cf-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="f71cf-136">Jeśli należy zmodyfikować dowolne ustawienie (takie jak przydział czytnika), nie należy <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> używać podejścia bezkonfiguracyjnego, usuwając z pliku .svc i tworząc wpis konfiguracji dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f71cf-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="f71cf-137">Jeśli usługa wymaga ASP.NET trybu zgodności — na przykład, jeśli <xref:System.Web.HttpContext> używa mechanizmów autoryzacji klasy lub ASP.NET — do włączenia tego trybu nadal jest wymagany plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="f71cf-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="f71cf-138">Wymagany element konfiguracji jest [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który należy dodać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f71cf-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="f71cf-139">Aby uzyskać więcej informacji, zobacz [WCF Services i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f71cf-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="f71cf-140">Klasa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest klasą pochodną . <xref:System.ServiceModel.Activation.ServiceHostFactory></span><span class="sxs-lookup"><span data-stu-id="f71cf-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="f71cf-141">Aby uzyskać szczegółowe wyjaśnienie mechanizmu fabrycznego hosta usługi, zobacz [rozszerzenie hostingu przy użyciu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f71cf-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71cf-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f71cf-142">See also</span></span>

- [<span data-ttu-id="f71cf-143">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f71cf-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="f71cf-144">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="f71cf-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
