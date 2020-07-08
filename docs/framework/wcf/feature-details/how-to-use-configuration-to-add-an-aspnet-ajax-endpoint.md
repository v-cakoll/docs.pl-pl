---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 97f8174161068f2c72b6bd2bc4e8a3044f5bccdd
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051665"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="13963-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="13963-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="13963-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia punkt końcowy z obsługą technologii AJAX ASP.NET, który może być wywoływany z JavaScript w klienckiej witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="13963-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="13963-104">Aby utworzyć taki punkt końcowy, możesz użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych programu Windows Communication Foundation (WCF), lub użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="13963-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="13963-105">W tym temacie przedstawiono podejście konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="13963-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="13963-106">Część procedury, która umożliwia przeznaczenie punktu końcowego usługi ASP.NET z włączoną obsługą technologii AJAX, obejmuje skonfigurowanie punktu końcowego do użycia <xref:System.ServiceModel.WebHttpBinding> i do dodania [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="13963-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="13963-107">Po skonfigurowaniu punktu końcowego czynności do wdrożenia i hostowania usługi są podobne do tych, które są używane przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="13963-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="13963-108">Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX przy użyciu protokołu HTTP Post](../samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="13963-108">For a working example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="13963-109">Aby uzyskać więcej informacji o konfigurowaniu punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [How to: Add a ASP.NET AJAX Endpoint bez using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="13963-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="13963-110">Aby utworzyć podstawową usługę WCF</span><span class="sxs-lookup"><span data-stu-id="13963-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="13963-111">Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="13963-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="13963-112">Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="13963-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="13963-113">Upewnij się, że właściwość jest ustawiona <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="13963-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="13963-114">Zaimplementuj `ICalculator` kontrakt usługi za pomocą `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="13963-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
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
  
3. <span data-ttu-id="13963-115">Zdefiniuj przestrzeń nazw dla `ICalculator` implementacji i, `CalculatorService` umieszczając je w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="13963-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="13963-116">Aby utworzyć punkt końcowy ASP.NET AJAX dla usługi</span><span class="sxs-lookup"><span data-stu-id="13963-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="13963-117">Utwórz konfigurację zachowań i określ [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) zachowanie dla punktów końcowych z obsługą technologii AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="13963-117">Create a behavior configuration and specify the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="13963-118">Utwórz punkt końcowy dla usługi używającej <xref:System.ServiceModel.WebHttpBinding> zachowania ASP.NET AJAX zdefiniowanej w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="13963-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="13963-119">Aby hostować usługę w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="13963-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="13963-120">Aby hostować usługę w usługach IIS, Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13963-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="13963-121">Edytuj ten plik, dodając odpowiednie informacje o dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) dla usługi.</span><span class="sxs-lookup"><span data-stu-id="13963-121">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="13963-122">Na przykład zawartość pliku usługi dla `CalculatorService` przykładu zawiera poniższe informacje.</span><span class="sxs-lookup"><span data-stu-id="13963-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="13963-123">Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [How to: hosting a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="13963-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="13963-124">Aby wywołać usługę</span><span class="sxs-lookup"><span data-stu-id="13963-124">To call the service</span></span>  
  
1. <span data-ttu-id="13963-125">Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku SVC, więc usługa jest teraz dostępna i może być wywoływana przez wysyłanie żądań do usługi Service. svc/ \<operation> -na przykład Service. svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="13963-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="13963-126">Można go użyć, wprowadzając adres URL punktu końcowego do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="13963-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="13963-127">Aby zapoznać się z przykładem, zobacz [usługi AJAX przy użyciu protokołu HTTP Post](../samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="13963-127">For an example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13963-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13963-128">See also</span></span>

- [<span data-ttu-id="13963-129">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="13963-129">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="13963-130">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="13963-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
