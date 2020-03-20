---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184835"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="80972-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="80972-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="80972-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia ASP.NET punkt końcowy z obsługą AJAX, który można wywołać z języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="80972-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="80972-104">Aby utworzyć taki punkt końcowy, można użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych programu Windows Communication Foundation (WCF) lub użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80972-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="80972-105">W tym temacie przedstawiono podejście konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80972-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="80972-106">Część procedury, która umożliwia punkt końcowy usługi, aby stać się ASP.NET ajax włączone polega <xref:System.ServiceModel.WebHttpBinding> na skonfigurowaniu punktu końcowego do korzystania i dodać [ \<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="80972-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="80972-107">Po skonfigurowaniu punktu końcowego kroki implementacji i hostowania usługi są podobne do tych używanych przez dowolną usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="80972-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="80972-108">Na przykład roboczy zobacz [usługę AJAX przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="80972-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="80972-109">Aby uzyskać więcej informacji na temat konfigurowania punktu końcowego ASP.NET AJAX bez użycia konfiguracji, zobacz [Jak: Dodawanie ASP.NET punktu końcowego AJAX bez użycia konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="80972-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="80972-110">Aby utworzyć podstawową usługę WCF</span><span class="sxs-lookup"><span data-stu-id="80972-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="80972-111">Zdefiniuj podstawową umowę serwisową <xref:System.ServiceModel.ServiceContractAttribute> WCF za pomocą interfejsu oznaczonego atrybutem.</span><span class="sxs-lookup"><span data-stu-id="80972-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="80972-112">Oznacz każdą operację <xref:System.ServiceModel.OperationContractAttribute>za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="80972-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="80972-113">Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="80972-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="80972-114">`ICalculator` Zaimplementuj `CalculatorService`umowę serwisową z programem .</span><span class="sxs-lookup"><span data-stu-id="80972-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="80972-115">Zdefiniuj `ICalculator` obszar `CalculatorService` nazw dla i implementacji, zawijając je w bloku obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="80972-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="80972-116">Aby utworzyć ASP.NET punkt końcowy AJAX dla usługi</span><span class="sxs-lookup"><span data-stu-id="80972-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="80972-117">Utwórz konfigurację zachowania i określ zachowanie [ \<>enableWebScript](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) dla ASP.NET punktów końcowych usługi obsługujących technologię AJAX.</span><span class="sxs-lookup"><span data-stu-id="80972-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="80972-118">Utwórz punkt końcowy dla usługi, <xref:System.ServiceModel.WebHttpBinding> która używa i ASP.NET zachowanie AJAX zdefiniowane w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="80972-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="80972-119">Aby hostować usługę w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="80972-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="80972-120">Aby hostować usługę w usługach IIS, należy utworzyć nowy plik o nazwie usługa z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80972-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="80972-121">Edytuj ten plik, [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dodając odpowiednie informacje o dyrektywie ServiceHost dla usługi.</span><span class="sxs-lookup"><span data-stu-id="80972-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="80972-122">Na przykład zawartość w pliku usługi `CalculatorService` dla próbki zawiera następujące informacje.</span><span class="sxs-lookup"><span data-stu-id="80972-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="80972-123">Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [Jak: Hostowanie usługi WCF w usługach IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="80972-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="80972-124">Aby zadzwonić do usługi</span><span class="sxs-lookup"><span data-stu-id="80972-124">To call the service</span></span>  
  
1. <span data-ttu-id="80972-125">Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku .svc, więc usługa jest teraz dostępna i może\<być wywoływana przez wysyłanie żądań do service.svc/ operation> — na przykład service.svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="80972-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="80972-126">Można go użyć, wprowadzając adres URL punktu końcowego do kolekcji Skrypty ASP.NET kontrolki Menedżera skryptów AJAX.</span><span class="sxs-lookup"><span data-stu-id="80972-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="80972-127">Na przykład zobacz [usługę AJAX przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="80972-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80972-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80972-128">See also</span></span>

- [<span data-ttu-id="80972-129">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80972-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="80972-130">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="80972-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
