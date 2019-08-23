---
title: 'Instrukcje: Określanie powiązania usługi w konfiguracji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: d3224b1d732fb82ffe68e8ce0bd410850004cb95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967154"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="059c3-102">Instrukcje: Określanie powiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="059c3-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="059c3-103">W tym przykładzie `ICalculator` jest definiowana umowa dla podstawowej usługi kalkulatora, usługa jest zaimplementowana `CalculatorService` w klasie, a następnie jej punkt końcowy jest skonfigurowany w pliku Web. config, gdzie jest określony <xref:System.ServiceModel.BasicHttpBinding> , że usługa używa .</span><span class="sxs-lookup"><span data-stu-id="059c3-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="059c3-104">Opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji można znaleźć w temacie [How to: Określ powiązanie usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="059c3-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="059c3-105">Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie.</span><span class="sxs-lookup"><span data-stu-id="059c3-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="059c3-106">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="059c3-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="059c3-107">Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="059c3-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="059c3-108">Wszystkie poniższe kroki konfiguracji można wykonać za pomocą [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="059c3-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="059c3-109">Aby uzyskać kopię źródła tego przykładu, [](../../../docs/framework/wcf/samples/basicbinding.md)Zobacz temat BasicBinding.</span><span class="sxs-lookup"><span data-stu-id="059c3-109">For the source copy of this example, see [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span></span>  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="059c3-110">Aby określić BasicHttpBinding do użycia w celu skonfigurowania usługi</span><span class="sxs-lookup"><span data-stu-id="059c3-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="059c3-111">Zdefiniuj kontrakt usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="059c3-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="059c3-112">Zaimplementuj kontrakt usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="059c3-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="059c3-113">Nie określono informacji o adresie lub powiązaniu w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="059c3-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="059c3-114">Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="059c3-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="059c3-115">Utwórz plik Web. config, aby skonfigurować punkt końcowy dla programu `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding>programu.</span><span class="sxs-lookup"><span data-stu-id="059c3-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="059c3-116">Utwórz plik Service. svc zawierający poniższy wiersz i umieść go w katalogu wirtualnym Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="059c3-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="059c3-117">Aby zmodyfikować wartości domyślne właściwości powiązania</span><span class="sxs-lookup"><span data-stu-id="059c3-117">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="059c3-118">Aby zmodyfikować jedną z domyślnych wartości <xref:System.ServiceModel.WSHttpBinding>właściwości, Utwórz nową nazwę konfiguracji powiązania — `<binding name="Binding1">` w obrębie elementu [ \<WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) i Ustaw nowe wartości atrybutów powiązania w ramach tego powiązania. postaci.</span><span class="sxs-lookup"><span data-stu-id="059c3-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="059c3-119">Na przykład aby zmienić domyślne wartości limitu czasu otwierania i zamykania z 1 minuty na 2 minuty, Dodaj następujący kod do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="059c3-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="059c3-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="059c3-120">See also</span></span>

- [<span data-ttu-id="059c3-121">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="059c3-121">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="059c3-122">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="059c3-122">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
