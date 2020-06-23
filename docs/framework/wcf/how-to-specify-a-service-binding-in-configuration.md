---
title: 'Instrukcje: Określanie wiązania usługi w konfiguracji'
description: Dowiedz się, jak skonfigurować punkt końcowy dla usługi WCF w pliku konfiguracji. Kontrakt jest zdefiniowany dla usługi i zaimplementowany w klasie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 92d0834091a1f243df6be214f606fbf0093dca54
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244559"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="4cac1-104">Instrukcje: Określanie wiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4cac1-104">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="4cac1-105">W tym przykładzie `ICalculator` jest definiowana umowa dla podstawowej usługi kalkulatora, usługa jest zaimplementowana w `CalculatorService` klasie, a następnie jej punkt końcowy jest skonfigurowany w pliku Web.config, w którym zostanie określony, że usługa używa usługi <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="4cac1-105">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="4cac1-106">Opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji można znaleźć [w temacie How to: Określanie powiązania usługi w kodzie](how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="4cac1-106">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="4cac1-107">Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4cac1-107">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="4cac1-108">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="4cac1-108">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="4cac1-109">Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4cac1-109">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="4cac1-110">Wszystkie poniższe kroki konfiguracji można wykonać przy użyciu [Narzędzia Edytora konfiguracji (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4cac1-110">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="4cac1-111">Aby uzyskać kopię źródła tego przykładu, zobacz temat [BasicBinding](./samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4cac1-111">For the source copy of this example, see [BasicBinding](./samples/basicbinding.md).</span></span>  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="4cac1-112">Aby określić BasicHttpBinding do użycia w celu skonfigurowania usługi</span><span class="sxs-lookup"><span data-stu-id="4cac1-112">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="4cac1-113">Zdefiniuj kontrakt usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="4cac1-113">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="4cac1-114">Zaimplementuj kontrakt usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="4cac1-114">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="4cac1-115">Nie określono informacji o adresie lub powiązaniu w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4cac1-115">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="4cac1-116">Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="4cac1-116">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="4cac1-117">Utwórz plik Web.config, aby skonfigurować punkt końcowy dla programu `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="4cac1-117">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
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
  
4. <span data-ttu-id="4cac1-118">Utwórz plik Service. svc zawierający poniższy wiersz i umieść go w katalogu wirtualnym Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="4cac1-118">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="4cac1-119">Aby zmodyfikować wartości domyślne właściwości powiązania</span><span class="sxs-lookup"><span data-stu-id="4cac1-119">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="4cac1-120">Aby zmodyfikować jedną z domyślnych wartości właściwości <xref:System.ServiceModel.WSHttpBinding> , Utwórz nową nazwę konfiguracji powiązania — `<binding name="Binding1">` w obrębie [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) elementu i Ustaw nowe wartości atrybutów powiązania w tym elemencie powiązania.</span><span class="sxs-lookup"><span data-stu-id="4cac1-120">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="4cac1-121">Na przykład aby zmienić domyślne wartości limitu czasu otwierania i zamykania z 1 minuty na 2 minuty, Dodaj następujący kod do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4cac1-121">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4cac1-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cac1-122">See also</span></span>

- [<span data-ttu-id="4cac1-123">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4cac1-123">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4cac1-124">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="4cac1-124">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
