---
title: 'Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 33f99161034db2aa142a422139406a1a68d42b2c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972276"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="22036-102">Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="22036-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="22036-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia punkt końcowy z obsługą technologii AJAX ASP.NET, który może być wywoływany z JavaScript w klienckiej witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="22036-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="22036-104">Aby utworzyć taki punkt końcowy, możesz użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych programu Windows Communication Foundation (WCF), lub użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="22036-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="22036-105">W tym temacie przedstawiono podejście konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="22036-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="22036-106">Część procedury, która umożliwia przeznaczenie punktu końcowego usługi ASP.NET z włączoną obsługą technologii AJAX, obejmuje skonfigurowanie punktu końcowego do użycia <xref:System.ServiceModel.WebHttpBinding> i [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) dodanie zachowania punktu końcowego > enableWebScript.</span><span class="sxs-lookup"><span data-stu-id="22036-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="22036-107">Po skonfigurowaniu punktu końcowego czynności do wdrożenia i hostowania usługi są podobne do tych, które są używane przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="22036-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="22036-108">Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX przy użyciu protokołu HTTP Post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="22036-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="22036-109">Aby uzyskać więcej informacji o konfigurowaniu punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [How to: Dodaj punkt końcowy ASP.NET AJAX bez użycia opcji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)Configuration.</span><span class="sxs-lookup"><span data-stu-id="22036-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="22036-110">Aby utworzyć podstawową usługę WCF</span><span class="sxs-lookup"><span data-stu-id="22036-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="22036-111">Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="22036-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="22036-112">Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="22036-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="22036-113">Upewnij się, <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> że właściwość jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="22036-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="22036-114">Zaimplementuj kontrakt `CalculatorService` `ICalculator` usługi za pomocą.</span><span class="sxs-lookup"><span data-stu-id="22036-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="22036-115">Zdefiniuj przestrzeń nazw dla `ICalculator` implementacji i `CalculatorService` , umieszczając je w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22036-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="22036-116">Aby utworzyć punkt końcowy ASP.NET AJAX dla usługi</span><span class="sxs-lookup"><span data-stu-id="22036-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="22036-117">Utwórz konfigurację zachowań i określ [ \<zachowanie > enableWebScript](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) dla punktów końcowych z obsługą technologii AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="22036-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="22036-118">Utwórz punkt końcowy dla usługi używającej <xref:System.ServiceModel.WebHttpBinding> zachowania ASP.NET AJAX zdefiniowanej w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="22036-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="22036-119">Aby hostować usługę w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="22036-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="22036-120">Aby hostować usługę w usługach IIS, Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22036-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="22036-121">Edytuj ten plik, dodając odpowiednie [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informacje o dyrektywie ServiceHost dla usługi.</span><span class="sxs-lookup"><span data-stu-id="22036-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="22036-122">Na przykład zawartość pliku usługi dla `CalculatorService` przykładu zawiera poniższe informacje.</span><span class="sxs-lookup"><span data-stu-id="22036-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="22036-123">Aby uzyskać więcej informacji na temat hostingu w usługach [IIS, zobacz How to: Hostowanie usługi WCF w usługach](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)IIS.</span><span class="sxs-lookup"><span data-stu-id="22036-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="22036-124">Aby wywołać usługę</span><span class="sxs-lookup"><span data-stu-id="22036-124">To call the service</span></span>  
  
1. <span data-ttu-id="22036-125">Punkt końcowy jest skonfigurowany pod adresem pustym względem pliku SVC, więc usługa jest teraz dostępna i może być wywoływana przez wysyłanie żądań do usługi Service. svc/\<Operation > — na przykład Service. svc/Add `Add` dla operacji.</span><span class="sxs-lookup"><span data-stu-id="22036-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="22036-126">Można go użyć, wprowadzając adres URL punktu końcowego do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="22036-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="22036-127">Aby zapoznać się z przykładem, zobacz [usługi AJAX przy użyciu protokołu HTTP Post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="22036-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22036-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22036-128">See also</span></span>

- [<span data-ttu-id="22036-129">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="22036-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="22036-130">Instrukcje: Migrowanie usług sieci Web ASP.NET z obsługą technologii AJAX do programu WCF</span><span class="sxs-lookup"><span data-stu-id="22036-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
