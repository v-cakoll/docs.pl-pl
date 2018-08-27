---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3a3474dc04ce2cda63157e68597d1184e9b2bf15
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934410"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="87e9e-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87e9e-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="87e9e-103">Windows Communication Foundation (WCF) pozwala utworzyć usługę, która sprawia, że obsługą ASP.NET AJAX punkt końcowy dostępny, którą można wywołać z kodu JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="87e9e-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="87e9e-104">Aby utworzyć punkt końcowy, można za pomocą pliku konfiguracji, jak wszystkie inne punkty końcowe usług Windows Communication Foundation (WCF) lub należy użyć metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87e9e-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="87e9e-105">W tym temacie przedstawiono metody konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87e9e-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="87e9e-106">Część procedury, która umożliwia punkt końcowy usługi staną się obsługą ASP.NET AJAX składa się z Konfigurowanie punkt końcowy do użycia <xref:System.ServiceModel.WebHttpBinding> i dodawanie [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="87e9e-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="87e9e-107">Po skonfigurowaniu punktu końcowego, kroki do wdrażania i obsługi usługi są podobne do tych używanych przez żadnej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="87e9e-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="87e9e-108">Aby uzyskać przykład pracy, zobacz [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="87e9e-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="87e9e-109">Aby uzyskać więcej informacji o sposobie konfigurowania punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [porady: Dodawanie platformy ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="87e9e-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="87e9e-110">Aby utworzyć podstawowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="87e9e-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="87e9e-111">Zdefiniuj podstawowego kontraktu usługi WCF z interfejsem oznaczone <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="87e9e-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="87e9e-112">Oznaczania każdej operacji za pomocą <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="87e9e-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="87e9e-113">Pamiętaj ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="87e9e-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="87e9e-114">Implementowanie `ICalculator` kontraktu usługi o `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="87e9e-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="87e9e-115">Definiowanie przestrzeni nazw `ICalculator` i `CalculatorService` implementacje opakowując w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="87e9e-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="87e9e-116">Aby utworzyć punktu końcowego ASP.NET AJAX dla usługi</span><span class="sxs-lookup"><span data-stu-id="87e9e-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="87e9e-117">Utwórz konfigurację zachowania i określ [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie dla komputerów z obsługą ASP.NET AJAX punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="87e9e-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="87e9e-118">Utworzenie punktu końcowego usługi, która używa <xref:System.ServiceModel.WebHttpBinding> i zachowanie ASP.NET AJAX, zdefiniowane w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="87e9e-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="87e9e-119">Do hostowania usługi w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="87e9e-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="87e9e-120">Aby hostować usługi w programie IIS, Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87e9e-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="87e9e-121">Edytuj ten plik, dodając odpowiednie [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="87e9e-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="87e9e-122">Na przykład zawartość w pliku usługi `CalculatorService` przykład zawiera następujące informacje.</span><span class="sxs-lookup"><span data-stu-id="87e9e-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  <span data-ttu-id="87e9e-123">Aby uzyskać więcej informacji o hostingu w usługach IIS, zobacz [instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="87e9e-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="87e9e-124">Do wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="87e9e-124">To call the service</span></span>  
  
1.  <span data-ttu-id="87e9e-125">Konfigurowany jest punkt końcowy adresem pusty względem pliku SVC, dzięki czemu usługa jest teraz dostępny i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="87e9e-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="87e9e-126">Używając go, wprowadzając adres URL punktu końcowego w kolekcji skryptów kontrolki Menedżera skryptów AJAX programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="87e9e-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="87e9e-127">Aby uzyskać przykład, zobacz [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="87e9e-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e9e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87e9e-128">See Also</span></span>  
 [<span data-ttu-id="87e9e-129">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="87e9e-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="87e9e-130">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="87e9e-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
