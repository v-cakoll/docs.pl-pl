---
title: Konfigurowanie wartości limitów czasu w wiązaniu
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185288"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="26c3e-102">Konfigurowanie wartości limitów czasu w wiązaniu</span><span class="sxs-lookup"><span data-stu-id="26c3e-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="26c3e-103">Istnieje wiele ustawień limitu czasu dostępnych w WCF powiązania.</span><span class="sxs-lookup"><span data-stu-id="26c3e-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="26c3e-104">Prawidłowe ustawienie tych ustawień limitu czasu może poprawić nie tylko wydajność usługi, ale także odgrywać rolę w użyteczności i bezpieczeństwie usługi.</span><span class="sxs-lookup"><span data-stu-id="26c3e-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="26c3e-105">Następujące limity czasu są dostępne w powiązaniach WCF:</span><span class="sxs-lookup"><span data-stu-id="26c3e-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="26c3e-106">Czas otwarcia</span><span class="sxs-lookup"><span data-stu-id="26c3e-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="26c3e-107">Limit czasu zamknięcia</span><span class="sxs-lookup"><span data-stu-id="26c3e-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="26c3e-108">Limit czasu wysyłania</span><span class="sxs-lookup"><span data-stu-id="26c3e-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="26c3e-109">Receivetimeout</span><span class="sxs-lookup"><span data-stu-id="26c3e-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="26c3e-110">Limity czasu wiązania WCF</span><span class="sxs-lookup"><span data-stu-id="26c3e-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="26c3e-111">Każde z ustawień omówionych w tym temacie są dokonywane na samo powiązanie, w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="26c3e-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="26c3e-112">Poniższy kod pokazuje, jak programowo ustawić limity czasu na WCF powiązania w kontekście usługi hostowane samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="26c3e-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="26c3e-113">W poniższym przykładzie pokazano, jak skonfigurować limity czasu na powiązanie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="26c3e-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="26c3e-114">Więcej informacji na temat tych ustawień można <xref:System.ServiceModel.Channels.Binding> znaleźć w dokumentacji dla klasy.</span><span class="sxs-lookup"><span data-stu-id="26c3e-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="26c3e-115">Limity czasu po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="26c3e-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="26c3e-116">Po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="26c3e-116">On the client side:</span></span>  
  
1. <span data-ttu-id="26c3e-117">SendTimeout — służy do inicjowania OperationTimeout, który reguluje cały proces wysyłania wiadomości, w tym odbieranie wiadomości odpowiedzi dla operacji usługi żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="26c3e-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="26c3e-118">Ten limit czasu ma również zastosowanie podczas wysyłania wiadomości odpowiedzi z metody umowy wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="26c3e-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="26c3e-119">OpenTimeout — używany podczas otwierania kanałów, gdy nie określono jawnego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="26c3e-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="26c3e-120">CloseTimeout — używane podczas zamykania kanałów, gdy nie określono jawnego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="26c3e-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="26c3e-121">ReceiveTimeout – nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="26c3e-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="26c3e-122">Limity czasu po stronie usługi</span><span class="sxs-lookup"><span data-stu-id="26c3e-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="26c3e-123">Po stronie serwisowej:</span><span class="sxs-lookup"><span data-stu-id="26c3e-123">On the service side:</span></span>  
  
1. <span data-ttu-id="26c3e-124">SendTimeout, OpenTimeout, CloseTimeout są takie same jak na kliencie.</span><span class="sxs-lookup"><span data-stu-id="26c3e-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="26c3e-125">ReceiveTimeout — używane przez warstwę Service Framework do inicjowania limitu czasu bezczynności sesji, który kontroluje, jak długo sesja może być bezczynny przed limit czasu.</span><span class="sxs-lookup"><span data-stu-id="26c3e-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
