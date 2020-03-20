---
title: 'Instrukcje: Określanie wiązania usługi w konfiguracji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 245fe50ed5a80c51163652defb642cebefd55dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184030"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="ed105-102">Instrukcje: Określanie wiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ed105-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="ed105-103">W tym przykładzie `ICalculator` kontrakt jest zdefiniowany dla podstawowej usługi kalkulatora, usługa jest implementowana w `CalculatorService` klasie, a następnie jej punkt końcowy jest konfigurowany w pliku Web.config, gdzie określono, że usługa używa <xref:System.ServiceModel.BasicHttpBinding>. .</span><span class="sxs-lookup"><span data-stu-id="ed105-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="ed105-104">Aby uzyskać opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji, zobacz [Jak: Określanie powiązania usługi w kodzie](how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="ed105-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="ed105-105">Zazwyczaj jest najlepszym rozwiązaniem, aby określić informacje dotyczące powiązania i adresu deklaratywnie w konfiguracji, a nie bezwzględnie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ed105-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="ed105-106">Definiowanie punktów końcowych w kodzie zwykle nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi zazwyczaj różnią się od tych używanych podczas opracowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="ed105-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="ed105-107">Bardziej ogólnie, utrzymywanie powiązanie i adresowanie informacji z kodu pozwala na ich zmiany bez konieczności ponownego kompilowania lub ponownego rozmieszczenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ed105-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="ed105-108">Wszystkie następujące kroki konfiguracji można wykonać za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](configuration-editor-tool-svcconfigeditor-exe.md)</span><span class="sxs-lookup"><span data-stu-id="ed105-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="ed105-109">Aby zapoznać się z kopią źródłową tego przykładu, zobacz [BasicBinding](./samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ed105-109">For the source copy of this example, see [BasicBinding](./samples/basicbinding.md).</span></span>  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="ed105-110">Aby określić podstawowe powiązaniehttpa, które ma być używane do konfigurowania usługi</span><span class="sxs-lookup"><span data-stu-id="ed105-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="ed105-111">Zdefiniuj umowę serwisową dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="ed105-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="ed105-112">Zaimplementuj umowę serwisową w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="ed105-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="ed105-113">Adres lub wiążące informacje nie jest określony wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="ed105-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="ed105-114">Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed105-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="ed105-115">Utwórz plik Web.config, aby skonfigurować `CalculatorService` punkt końcowy <xref:System.ServiceModel.WSHttpBinding>dla punktu, który używa pliku .</span><span class="sxs-lookup"><span data-stu-id="ed105-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
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
  
4. <span data-ttu-id="ed105-116">Utwórz plik Service.svc zawierający następujący wiersz i umieść go w katalogu wirtualnym internetowych usług informacyjnych (IIS).</span><span class="sxs-lookup"><span data-stu-id="ed105-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="ed105-117">Aby zmodyfikować wartości domyślne właściwości wiązania</span><span class="sxs-lookup"><span data-stu-id="ed105-117">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="ed105-118">Aby zmodyfikować jedną z domyślnych wartości właściwości <xref:System.ServiceModel.WSHttpBinding>, `<binding name="Binding1">` utwórz nową nazwę konfiguracji powiązania - — w ramach [ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element i ustawić nowe wartości dla atrybutów powiązania w tym elemencie wiązania.</span><span class="sxs-lookup"><span data-stu-id="ed105-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="ed105-119">Na przykład, aby zmienić domyślne wartości limitu czasu otwarcia i zamknięcia od 1 minuty do 2 minut, dodaj następujące wartości do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed105-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ed105-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed105-120">See also</span></span>

- [<span data-ttu-id="ed105-121">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ed105-121">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ed105-122">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="ed105-122">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
