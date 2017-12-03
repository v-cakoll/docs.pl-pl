---
title: "Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4db4b105bc958a19dc803aa74dc9193e8a8a7edb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="ff2cb-102">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ff2cb-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ff2cb-103">Służy do tworzenia usługi, która sprawia, że włączone ASP.NET AJAX punktu końcowego dostępne, który można wywołać z poziomu języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-103"> allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="ff2cb-104">Aby utworzyć punkt końcowy, możesz użyć pliku konfiguracji, tak jak w przypadku wszystkich innych [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punktów końcowych lub użyj metody, która nie wymaga żadnych elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-104">To create such an endpoint, you can either use a configuration file, as with all other [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="ff2cb-105">W tym temacie przedstawiono podejście konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="ff2cb-106">Część tej procedury, która umożliwia punktu końcowego usługi stać się z obsługą środowiska ASP.NET AJAX składa się z konfigurowania punktu końcowego, aby użyć <xref:System.ServiceModel.WebHttpBinding> i dodać [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="ff2cb-107">Po skonfigurowaniu punktu końcowego, kroki do wdrażania i obsługi usługi są podobne do tych używanych przez dowolną [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="ff2cb-108">Na przykład pracy, zobacz [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="ff2cb-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ff2cb-109">sposobu konfigurowania punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [porady: Dodawanie ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ff2cb-109"> how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="ff2cb-110">Aby utworzyć podstawowej usługi WCF</span><span class="sxs-lookup"><span data-stu-id="ff2cb-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="ff2cb-111">Zdefiniuj podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-111">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="ff2cb-112">Oznacz każdej operacji z <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="ff2cb-113">Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="ff2cb-114">Implementowanie `ICalculator` kontraktu usługi o `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="ff2cb-115">Zdefiniuj przestrzeń nazw dla `ICalculator` i `CalculatorService` implementacje zawijania je w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="ff2cb-116">Można utworzyć punktu końcowego ASP.NET AJAX dla usługi</span><span class="sxs-lookup"><span data-stu-id="ff2cb-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="ff2cb-117">Utwórz konfigurację zachowania i określ [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie dla komputerów z obsługą środowiska ASP.NET AJAX punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="ff2cb-118">Tworzenie punktu końcowego usługi, która używa <xref:System.ServiceModel.WebHttpBinding> i zachowanie środowiska ASP.NET AJAX, zdefiniowane w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="ff2cb-119">Do obsługi usługi w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="ff2cb-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="ff2cb-120">Do obsługi usługi w usługach IIS, Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="ff2cb-121">Edytowanie tego pliku, dodając odpowiednie [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="ff2cb-122">Na przykład zawartość w pliku usługi `CalculatorService` przykład zawiera następujące informacje.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ff2cb-123">hosting w usługach IIS, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="ff2cb-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="ff2cb-124">Do wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="ff2cb-124">To call the service</span></span>  
  
1.  <span data-ttu-id="ff2cb-125">Punkt końcowy jest skonfigurowana pod adresem pusty względem pliku SVC, dlatego usługa jest teraz dostępna i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="ff2cb-126">Można go przy użyciu adresu URL punktu końcowego do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ff2cb-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="ff2cb-127">Na przykład zobacz [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="ff2cb-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2cb-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff2cb-128">See Also</span></span>  
 [<span data-ttu-id="ff2cb-129">Tworzenie usług WCF dla środowiska ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="ff2cb-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="ff2cb-130">Porady: Migrowanie usług sieci Web ASP.NET włączoną obsługą technologii AJAX do programu WCF</span><span class="sxs-lookup"><span data-stu-id="ff2cb-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
