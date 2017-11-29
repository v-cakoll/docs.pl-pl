---
title: "Instrukcje: Określanie powiązania usługi w konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 204ea09a7a6c14188b85f23829fc3a9446aaadd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="554e2-102">Instrukcje: Określanie powiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="554e2-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="554e2-103">W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi podstawowe Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest skonfigurowana w pliku Web.config, w którym jest określone, że usługa używa <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="554e2-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="554e2-104">Opis sposobu konfigurowania tej usługi przy użyciu kodu zamiast konfiguracji, zobacz [porady: Określanie powiązania usługi w kodzie](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="554e2-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="554e2-105">Jest zwykle najlepszym rozwiązaniem, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie imperatively w kodzie.</span><span class="sxs-lookup"><span data-stu-id="554e2-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="554e2-106">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane.</span><span class="sxs-lookup"><span data-stu-id="554e2-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="554e2-107">Ogólnie rzecz biorąc pamiętając powiązania i adresowanie poza kod umożliwia im to zmienić bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="554e2-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="554e2-108">Wszystkie z następujących kroków konfiguracji można podjąć przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="554e2-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="554e2-109">Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="554e2-109">For the source copy of this example, see [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span></span>  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="554e2-110">Aby określić BasicHttpBinding służący do konfigurowania usługi</span><span class="sxs-lookup"><span data-stu-id="554e2-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1.  <span data-ttu-id="554e2-111">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="554e2-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="554e2-112">Implementowanie kontraktu usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="554e2-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="554e2-113">Nie określono informacji o adresie lub powiązania wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="554e2-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="554e2-114">Ponadto kodu nie ma do zapisania można pobrać informacji z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="554e2-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3.  <span data-ttu-id="554e2-115">Utwórz plik Web.config do konfigurowania punktu końcowego dla `CalculatorService` używającą <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="554e2-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  <span data-ttu-id="554e2-116">Utwórz plik Service.svc, który zawiera następujący wiersz i umieść go w katalogu wirtualnym programu Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="554e2-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="554e2-117">Aby zmodyfikować wartości domyślne we właściwościach powiązania</span><span class="sxs-lookup"><span data-stu-id="554e2-117">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="554e2-118">Modyfikowania domyślnych wartości właściwości z <xref:System.ServiceModel.WSHttpBinding>, Utwórz nową nazwę konfiguracji powiązania - `<binding name="Binding1">` — poziomu [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element i ustaw nowe wartości dla atrybutów powiązanie, w tym elemencie powiązania.</span><span class="sxs-lookup"><span data-stu-id="554e2-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="554e2-119">Na przykład aby zmienić domyślne Otwórz i zamknij wartości limitu czasu wynoszącym 1 minutę do 2 minuty, Dodaj do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="554e2-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="554e2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="554e2-120">See Also</span></span>  
 [<span data-ttu-id="554e2-121">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="554e2-121">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="554e2-122">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="554e2-122">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
