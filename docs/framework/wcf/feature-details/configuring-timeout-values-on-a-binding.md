---
title: Konfigurowanie wartości limitów czasu w wiązaniu
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773249"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="3d30d-102">Konfigurowanie wartości limitów czasu w wiązaniu</span><span class="sxs-lookup"><span data-stu-id="3d30d-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="3d30d-103">Istnieje kilka ustawień limitu czasu są dostępne w powiązaniach WCF.</span><span class="sxs-lookup"><span data-stu-id="3d30d-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="3d30d-104">Ustawienia te timeout ustawienia poprawnie ulepszyć nie tylko z usługą wydajność, ale również odtwarzania roli w użyteczność i zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="3d30d-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="3d30d-105">Następujące limity czasu są dostępne na powiązaniami WCF:</span><span class="sxs-lookup"><span data-stu-id="3d30d-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="3d30d-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="3d30d-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="3d30d-107">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="3d30d-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="3d30d-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="3d30d-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="3d30d-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="3d30d-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="3d30d-110">Powiązania WCF przekroczeń limitu czasu</span><span class="sxs-lookup"><span data-stu-id="3d30d-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="3d30d-111">Wszystkie ustawienia omówione w tym temacie są dokonywane na powiązanie, albo w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3d30d-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="3d30d-112">Poniższy kod pokazuje, jak programowo ustawić limity czasu w powiązaniu usługi WCF w kontekście samodzielnie hostowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="3d30d-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="3d30d-113">Poniższy przykład pokazuje, jak skonfigurować limity czasu w powiązaniu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3d30d-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="3d30d-114">Więcej informacji na temat tych ustawień można znaleźć w dokumentacji dotyczącej <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d30d-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="3d30d-115">Przekroczenia limitu czasu po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="3d30d-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="3d30d-116">Po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="3d30d-116">On the client side:</span></span>  
  
1. <span data-ttu-id="3d30d-117">Właściwości SendTimeout — używane do zainicjowania OperationTimeout, rządzące całego procesu wysyłania wiadomości, w tym odebranie komunikatu odpowiedzi dla operacji usługowej żądanie/nietypizowana odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="3d30d-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="3d30d-118">Tego limitu czasu ma również zastosowanie, podczas wysyłania komunikatów odpowiedzi z metodą kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3d30d-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="3d30d-119">OpenTimeout — które są używane podczas otwierania kanały, gdy określona jest wartość nie jawnego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="3d30d-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="3d30d-120">CloseTimeout — używany podczas zamykania kanałów, gdy określona jest wartość limitu czasu jawne nie.</span><span class="sxs-lookup"><span data-stu-id="3d30d-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="3d30d-121">ReceiveTimeout — nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="3d30d-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="3d30d-122">Przekroczenia limitu czasu po stronie usługi</span><span class="sxs-lookup"><span data-stu-id="3d30d-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="3d30d-123">Na stronie usługi:</span><span class="sxs-lookup"><span data-stu-id="3d30d-123">On the service side:</span></span>  
  
1. <span data-ttu-id="3d30d-124">Właściwości SendTimeout, OpenTimeout, CloseTimeout są takie same, jak na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="3d30d-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="3d30d-125">ReceiveTimeout — używane przez warstwę Framework usługi do zainicjowania czasu bezczynności sesji, określający, jak długo sesja może być bezczynne przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="3d30d-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
