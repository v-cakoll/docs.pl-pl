---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8d9d9b55bbeade5aa337719ba19ea9f386dfd6a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="62292-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="62292-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="62292-103"> Służy do tworzenia usługi, która przedstawia włączone ASP.NET AJAX punktu końcowego, który można wywołać z poziomu języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="62292-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="62292-104">Można utworzyć punktu końcowego, można użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych WCF lub użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62292-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="62292-105">W tym temacie przedstawiono drugiej metody.</span><span class="sxs-lookup"><span data-stu-id="62292-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="62292-106">Do tworzenia usług z punktów końcowych ASP.NET AJAX bez konfiguracji, usługi musi być obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="62292-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="62292-107">Aby aktywować punktu końcowego ASP.NET AJAX przy użyciu tej metody, należy określić <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki w [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w pliku svc.</span><span class="sxs-lookup"><span data-stu-id="62292-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="62292-108">Ta fabryka niestandardowych jest składnik, który automatycznie konfiguruje punktu końcowego ASP.NET AJAX, dzięki czemu mogą być wywoływane z JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="62292-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="62292-109">Na przykład pracy, zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="62292-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="62292-110">Omówienie sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji dla [porady: Użyj konfiguracji można dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="62292-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="62292-111">Aby utworzyć podstawowej usługi WCF</span><span class="sxs-lookup"><span data-stu-id="62292-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="62292-112">Zdefiniuj podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="62292-112">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="62292-113">Oznacz każdej operacji z <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="62292-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="62292-114">Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="62292-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="62292-115">Implementowanie `ICalculator` kontraktu usługi o `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="62292-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="62292-116">Zdefiniuj przestrzeń nazw dla `ICalculator` i `CalculatorService` implementacje zawijania je w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="62292-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="62292-117">Do obsługi usługi przez Internetowe usługi informacyjne bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="62292-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="62292-118">Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62292-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="62292-119">Edytowanie tego pliku, dodając odpowiednie [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="62292-119">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="62292-120">Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy do automatycznego konfigurowania punktu końcowego ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="62292-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="62292-121">Tworzenie usługi i wywołać go z klienta.</span><span class="sxs-lookup"><span data-stu-id="62292-121">Build the service and call it from the client.</span></span> <span data-ttu-id="62292-122">Internet Information Services (IIS) aktywuje usługę po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="62292-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="62292-123">Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="62292-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="62292-124">Do wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="62292-124">To call the service</span></span>  
  
1.  <span data-ttu-id="62292-125">Punkt końcowy jest skonfigurowana pod adresem pusty względem pliku SVC, dlatego usługa jest teraz dostępna i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="62292-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="62292-126">Można go przy użyciu adresu URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="62292-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="62292-127">Na przykład zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="62292-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62292-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="62292-128">Example</span></span>  
  
 <span data-ttu-id="62292-129">Punkt końcowy skonfigurowany automatycznie jest tworzony w pusty adres względem podstawowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="62292-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="62292-130">Plik konfiguracji można również dodany i używany z tą metodą.</span><span class="sxs-lookup"><span data-stu-id="62292-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="62292-131">Jeśli plik konfiguracji zawiera definicje punktu końcowego, te punkty końcowe są dodawane do punktu końcowego skonfigurowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="62292-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="62292-132">Na przykład używa service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> i katalog usługi zawiera plik Web.config, który definiuje punktu końcowego dla tego samego przy użyciu usługi <xref:System.ServiceModel.BasicHttpBinding> pod adresem względnej "soap".</span><span class="sxs-lookup"><span data-stu-id="62292-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="62292-133">W takim przypadku usługa zawiera dwa punkty końcowe: po service.svc (który odpowiada na żądania środowiska ASP.NET AJAX) i drugi w service.svc/soap (który odpowiada na żądania SOAP).</span><span class="sxs-lookup"><span data-stu-id="62292-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="62292-134">Jeśli plik konfiguracyjny definiuje punkt końcowy pod adresem pustą względnej i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używana, jest zwracany wyjątek, i nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="62292-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="62292-135">Nie można użyć konfiguracji, aby zmodyfikować ustawienia automatycznie konfigurowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="62292-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="62292-136">Jeśli wszystkie ustawienia (np. czytnik limit przydziału) musi być zmodyfikowana, nie można używać bez konfiguracji korzystania przez usunięcie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> w pliku svc i tworzenie pozycji konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="62292-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="62292-137">Jeśli usługa wymaga tryb zgodności ASP.NET — na przykład, gdy jest używana funkcja <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji programu ASP.NET — plik konfiguracji jest nadal wymagane, aby włączyć ten tryb.</span><span class="sxs-lookup"><span data-stu-id="62292-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="62292-138">Element konfiguracji, wymagane jest [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który musi zostać dodany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="62292-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="62292-139">Aby uzyskać więcej informacji, zobacz [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="62292-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="62292-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Klasy jest klasy pochodnej z <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="62292-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="62292-141">Aby uzyskać szczegółowy opis mechanizmu fabryki hosta usługi, zobacz [rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="62292-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62292-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62292-142">See Also</span></span>  
 [<span data-ttu-id="62292-143">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="62292-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="62292-144">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="62292-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
