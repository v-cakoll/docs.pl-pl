---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 18c02644319dd9d11be39ac4956a4dcf50db3078
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525142"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="0d92a-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0d92a-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="0d92a-103">Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia obsługą ASP.NET AJAX punktu końcowego, który może zostać wywołana z języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="0d92a-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="0d92a-104">Aby utworzyć punkt końcowy, można za pomocą pliku konfiguracji, jak wszystkie inne punkty końcowe WCF lub należy użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0d92a-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="0d92a-105">W tym temacie przedstawiono drugiego podejścia.</span><span class="sxs-lookup"><span data-stu-id="0d92a-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="0d92a-106">Aby tworzyć usługi przy użyciu punktów końcowych ASP.NET AJAX bez konfiguracji, usług musi być hostowany przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="0d92a-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0d92a-107">Aby aktywować tę funkcję punktu końcowego ASP.NET AJAX przy użyciu tej metody, należy określić <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w pliku svc.</span><span class="sxs-lookup"><span data-stu-id="0d92a-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="0d92a-108">Ta fabryka niestandardowego jest składnikiem, który automatycznie konfiguruje punktu końcowego ASP.NET AJAX, dzięki czemu może ona zostać wywołana z kodu JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="0d92a-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="0d92a-109">Aby uzyskać przykład pracy, zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0d92a-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="0d92a-110">Aby uzyskać omówienie sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji, zobacz [porady: Użyj konfiguracji, aby dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="0d92a-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="0d92a-111">Aby utworzyć podstawowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="0d92a-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="0d92a-112">Zdefiniuj podstawowego kontraktu usługi WCF z interfejsem oznaczone <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0d92a-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="0d92a-113">Oznaczania każdej operacji za pomocą <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0d92a-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="0d92a-114">Pamiętaj ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d92a-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="0d92a-115">Implementowanie `ICalculator` kontraktu usługi o `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="0d92a-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="0d92a-116">Definiowanie przestrzeni nazw `ICalculator` i `CalculatorService` implementacje opakowując w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0d92a-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="0d92a-117">Do hostowania usługi w programie Internet Information Services bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0d92a-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="0d92a-118">Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d92a-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="0d92a-119">Edytuj ten plik, dodając odpowiednie [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="0d92a-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="0d92a-120">Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować punktu końcowego ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0d92a-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="0d92a-121">Twórz usługi i wywołać go z klienta.</span><span class="sxs-lookup"><span data-stu-id="0d92a-121">Build the service and call it from the client.</span></span> <span data-ttu-id="0d92a-122">Internet Information Services (IIS) aktywuje usługę, gdy zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="0d92a-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="0d92a-123">Aby uzyskać więcej informacji o hostingu w usługach IIS, zobacz [instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="0d92a-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="0d92a-124">Do wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="0d92a-124">To call the service</span></span>  
  
1.  <span data-ttu-id="0d92a-125">Konfigurowany jest punkt końcowy adresem pusty względem pliku SVC, dzięki czemu usługa jest teraz dostępny i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="0d92a-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="0d92a-126">Używając go, wprowadzając adres URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0d92a-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="0d92a-127">Aby uzyskać przykład, zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0d92a-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d92a-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d92a-128">Example</span></span>  
  
 <span data-ttu-id="0d92a-129">Punkt końcowy automatycznie konfigurowany jest tworzony w pusty adres względem podstawowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="0d92a-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="0d92a-130">Plik konfiguracji mogą być również dodawane lub używany w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="0d92a-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="0d92a-131">Jeśli plik konfiguracji zawiera definicji punktów końcowych, tych punktów końcowych są dodawane do endpoint automatycznie konfigurowane.</span><span class="sxs-lookup"><span data-stu-id="0d92a-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="0d92a-132">Na przykład używa service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> i katalog usługi zawiera pliku Web.config, który definiuje punktu końcowego dla tej samej usługi za pomocą <xref:System.ServiceModel.BasicHttpBinding> pod adresem względna "soap".</span><span class="sxs-lookup"><span data-stu-id="0d92a-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="0d92a-133">W tym przypadku usługa zawiera dwa punkty końcowe: pojedynczo service.svc (co odpowiada na żądania ASP.NET AJAX), a drugi na service.svc/soap (co odpowiada na żądania protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="0d92a-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="0d92a-134">Jeśli plik konfiguracyjny definiuje punkt końcowy na pusty adres względny i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używany, zostanie zgłoszony wyjątek i nie można uruchomić usługi.</span><span class="sxs-lookup"><span data-stu-id="0d92a-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="0d92a-135">Nie można użyć konfiguracji, aby zmodyfikować ustawienia w punkcie końcowym automatycznie konfigurowane.</span><span class="sxs-lookup"><span data-stu-id="0d92a-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="0d92a-136">Jeśli wszystkie ustawienia (np. czytnik limit przydziału) musi być zmodyfikowany, nie można używać bezpłatnie konfiguracji podejście, usuwając <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> z pliku svc i tworzenie wpisu konfiguracji dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0d92a-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="0d92a-137">Jeśli usługa wymaga tryb zgodności ASP.NET — na przykład, jeśli używa <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji platformy ASP.NET — plik konfiguracji jest nadal wymagane, aby włączyć ten tryb.</span><span class="sxs-lookup"><span data-stu-id="0d92a-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="0d92a-138">Element konfiguracji, wymagane jest [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który musi zostać dodany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="0d92a-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="0d92a-139">Aby uzyskać więcej informacji, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="0d92a-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="0d92a-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Klasa jest klasy pochodnej <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="0d92a-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="0d92a-141">Aby uzyskać szczegółowy opis mechanizm fabryka hostów usługi zobacz [rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="0d92a-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d92a-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d92a-142">See Also</span></span>  
 [<span data-ttu-id="0d92a-143">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0d92a-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="0d92a-144">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="0d92a-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
